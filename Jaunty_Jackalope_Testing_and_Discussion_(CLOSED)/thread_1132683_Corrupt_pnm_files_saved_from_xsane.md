---
title: "Corrupt pnm files saved from xsane"
date: 2009-04-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by twigusa on 2009-04-22
Hi,

I've recently scanned about 180 or so images using xsane in Jaunty and saving as .pnm files. I did the scanning in two batches: Sunday 12 Apr and Tuesday 21 Apr.

After opening up the folder today to view the files I've noticed that one image from the Sunday set is corrupt but much more worrying more than half of those from the Tuesday set are corrupt. 

I'm running ext4 on a fresh install. The file sizes are showing as 1.6MB regardless of whether or not they are corrupt.

The error I get when trying to open the files is:

Could not load image 'foo.pnm' 
PNM loader did not find expected integer

Any ideas?

---

### Post by twigusa on 2009-04-22
Forgot to mention. I've tried running fsck and also copying the files to a windows machine to open but no joy.

---

### Post by twigusa on 2009-04-22
For what it's worth, some of these files were somehow in the wrong resolution and were recoverable by installing imagemagick and using the convert command:

convert file a.pnm -strip -resize (new resolution) fileb.pnm

However, some were not recoverable and I'm at a loss to explain it. Hope this helps anyone with a similar issue.

---

