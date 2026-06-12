---
title: "Installation stops after loading in start"
date: 2004-10-25
forum: Installation &amp; Upgrades
---

### Post by flame on 2004-10-25
Hi

The installation stops after i have chosen language and loading cd-roms and some ide-stuff.

What to do, what to do ? :-/

---

### Post by sfw5000 on 2004-10-25
It could be that your CD is corrupted? Did you check the md5sum? When it stops does it give you any error messages?

---

### Post by flame on 2004-10-25
How do I check the md5 ?


No, I didn't get any errors at all.. So I waited for 10 mins, and nothing happened.  :-k

---

### Post by sfw5000 on 2004-10-25
After you download the .ISO you should check the md5sum to make sure that the file is not currupted. Let's say you downloaded the .ISO from here: [http://releases.ubuntu.com/warty/](http://releases.ubuntu.com/warty/) There is a directory called MD5SUMS (here: [http://releases.ubuntu.com/warty/MD5SUMS](http://releases.ubuntu.com/warty/MD5SUMS)) that lists the MD5SUM which is a long string.

In linux there is a program called md5sum which allows you to check the md5sum of the file you downloaded and make sure it matches what is listed on the site. Just open a terminal and type md5sum filename where filename is the complete name of the iso file. It will scan the file and print out the string.

Are you using linux now or is it windows? Also, what kind of computer is this? You might want to re-download and/or re-burn the image.

---

### Post by flame on 2004-10-25
I'm using windows.

What kind of PC ?
Specs ?

Asus a7n8x deluxe mainboard
Xp2800+ cpu
512mb ram
Radeon 9800pro gfx



Thanks for the help so far. I'll try to download the ISO again this night.

---

### Post by FLeiXiuS on 2004-10-25
Or perhaps your PC may be over heating / locking up.  Always many many issues to check when troubleshooting.

---

### Post by flame on 2004-10-25
I have checked the system-temp, and It's not very hot exactly. :)

---

### Post by sfw5000 on 2004-10-25
OK --  I found this link for testing md5sums with Windows,

[http://www.etree.org/md5com.html](http://www.etree.org/md5com.html)

---

### Post by flame on 2004-10-25
I can't find install instructions there for Windows XP  :(

---

### Post by sfw5000 on 2004-10-25
Oh, I think you just need to click on the md5sum.exe thing to install the program -- it's probably a tiny program that does need to actually install, just download it and you should be able to use it.

---

### Post by FLeiXiuS on 2004-10-25
This is what I did to get it working.

Placed md5sum in ```
C:/windows/system32 
``` directory.  Then I oppened a command prompt: (Start > Run > Command)  After this, md5sum filename.iso

I  hope this helps!

---

