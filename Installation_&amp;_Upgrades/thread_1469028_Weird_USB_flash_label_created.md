---
title: "Weird USB flash label created"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Oldhacker on 2010-05-01
After finally getting Ubuntu 10.04 installed (with a few disasters along the way) I sought to recreate a shell script for backing up critical files that I had been using with 9.04

The destination for the files was /media/disk (with "disk" being the name that I had given to the USB flash drives in the past with 9.04.) One drive mounted perfectly, and the shell script ran as it normally should. However, two other drives gave "file or directory not found" error messages and no files were copied.
One of the drives lists its name as a very forbidding "/media/5d588180-19eb-4656-8677-b652c4ed0003.

I attempted to re-name it to "disk", using e2label after un-mounting it, but that did not work. ????

Are there any pertinent suggestions to try? If I run the shell script on several different USB flash drives that I alternate, they must all have the same name.

---

### Post by Oldhacker on 2010-05-02
I was accessing the wrong /dev
When I used the correct /dev designation, e2label worked perfectly. The moral:

"Never make changes to your computer when you have not had enough rest."

---

