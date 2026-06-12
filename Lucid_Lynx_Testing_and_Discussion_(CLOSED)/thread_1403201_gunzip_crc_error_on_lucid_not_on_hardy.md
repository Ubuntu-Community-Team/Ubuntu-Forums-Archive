---
title: "gunzip crc error on lucid not on hardy"
date: 2010-02-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by amsterdamharu on 2010-02-10
gunzip has the same version on hardy as it has on lucid yet I keep getting the same error in gunzip in lucid (not on hardy where it juzt unzips):
invalid compressed data--crc error

It is a file called tinycore.gz in the tinycore iso, thought it might be corrupted when copied so copied the file back from lucid to hardy and did a cmp on the 2 files, they are identical.

gzip -V gives same output on both machines:

 1.3.12

---

