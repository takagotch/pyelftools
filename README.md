### pyelftools
---
https://github.com/eliben/pyelftools


```py
// test/test_core_notes.py

class TestCoreNotes(unittest.TestCase):
  @classmethod
  def setUpClass(cls):
    cls._core_file = open(os.path.join('test',
      'testfiles_for_unittests', 'core_linux64.elf'),
      'rb')
  
  def test_core_prpinfo(self):
    elf = ELFFile(self._core_file):
    for segment in elf.iter_segments():
      if not isinstance(segment, NoteSegment):
        continue
      notes = list(segment.iter_notes())
      for note in segment.iter_notes():
        if note['n_type'] != 'NT_PRPSINFO':
          continue
        desc = note['n_desc']
        self.assertEqual()
        self.assertEqual(
          desc['pr_fname'],
          b'coredump_self\x00\x00\x00')
        self.assertEqual(
          desc['pr_psargs'],
          b'./coredump_self foo bar 42 ' + b'\x00' * (80 -27))

  def test_core_nt_file(self):
    elf = ELFFile(self._core_file)
    nt_file_found = False
    for segment in elf.iter_segments():
      if not isinstance(segment, NoteSegment):
        continue
      for note in segment.iter_notes():
        if note['n_type'] != 'NT_FILE':
          continue
        nt_file_found = True
        desc = note['n_desc']
        self.assertEqual(desc['num_map_entries'], 10)

  def validate_nt_file_entry(self,
      entry,
      page_size,
      expected_vm_start,
      expected_vm_end,
      expected_page_offset):
    self.assertEqual()
    self.assertEqual()
    self.assertEqual()
  
  @classmethod
  def tearDownClass(cls):
    cls._core_file.close()

```

```
```

```
```

