---
title: "zlib"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by srinath on 2005-09-07
I downloaded Ubuntu recently and tried to install it. I burnt the ISO Image. When it was at the installation of the base system, it came up with the error 'couldn't retrive zlib16' It suggested that it could be because of a bad burn. So, I burnt a new cd at a lower speed. Still the same error. I looked for the zlib files and I have got them but I do not know which is the more recent version. The dite said it was put up in July this year. And I got Ubuntu in August.

How do I tackle this problem? Would appriciate the help.

Thank you.
Srinath

---

### Post by primeirocrime on 2005-09-07
did you do a checksum? try downloading the md5 from [http://us.releases.ubuntu.com/releases/5.04/MD5SUMS](http://us.releases.ubuntu.com/releases/5.04/MD5SUMS)

and compare with the md5sum on a terminal.

ex:  ```
#md5sum blablabalbalwhatever.iso  
```

---

### Post by srinath on 2005-09-07
No. I did not do a checksum. I have a MD5SUM.txt file. Do I just have to open the textfile and make comparisons? Sorry. I really did not understand. I am blank when it comes to Linux

---

### Post by primeirocrime on 2005-09-07
yes, you must open that MD5SUM.txt and compare that number to the one you got from the terminal output. If they match your have another problem, if they don't you have a corrupt instalation disk. 
Don't worry about being blank, we all are at some point. 

I've been thru that before :)
[edit]
damn! are you using Microsoft Windows?

[http://www.pc-tools.net/win32/md5sums/](http://www.pc-tools.net/win32/md5sums/)


if they match, then try to burn at slower speed.

---

### Post by srinath on 2005-09-07
4e4bc1e4aa50f9bf13e9a0adeb3f803a *ubuntu-5.04-install-i386.iso
This is what I got.  

I have a corrupt iso, then. =(
I should have gotten f6b3f164c99761234858a4d2c12d0840  ubuntu-5.04-install-i386.iso

Thank you for your help. I'll get the file again. yeah! windows

Do I try a different mirror??!

---

