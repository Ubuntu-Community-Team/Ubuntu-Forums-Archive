---
title: "I can't access windows or Ubuntu"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by cadenn on 2010-12-25
I recently installed ubuntu onto my computer using the wubi installer so that i could dual os. I was running windows 7 32 bit originally and set 20gb of space for ubuntu 64 bit in the wubi installer. 

I was able to access Ubuntu and installed updates and was prompted to restart and I did so. I'm not sure what happened but currently I'm unable to access either windows or ubuntu. All I get is a message saying that "Error: something could not be red xxxxxx-xxxxxxxxx-xxxxxxxx" something along the lines of that, and a grub rescue appeared. 

I'm hoping i can fix this problem by not reformatting the hard drive because I still have important documents on there. Is there anyway I can do this? Also on a side note, I'm using a T510 Lenovo computer and the BIOS are locked (I got this lappy through school).

---

### Post by searchfgold6789 on 2010-12-25
Well, first of all you don't need to use wubi for a dual boot install, you can enjoy a full installatioin of Ubuntu linux that plays well with Windows by just installing it alongside the other operating system from the Live CD.
My recommendation for solving the problem:
First make a Live CD. I'm not sure how you would do this with your broken computer, but maybe you can use someone else's.
Then, boot from it using your laptop. The bios will probably detect the CD and boot from it. Maybe you could ask the school nicely for the BIOS password.
Then, open up a terminal in the Live desktop environment (a.k.a. "Try without installing"). Type in ```
sudo blkid
``` and make sure the numbers from the output match those that are in the file on your ubuntu system which is at /etc/fstab . If you need to edit this file, type ```
sudo gedit
``` and open the /etc/fstab file on your ubuntu install from there.
If you need any help feel free to post back.
Oh yeah ... and while you are in the Live CD, maybe you could post the output of the bootscript which is available from sourceforge.net. Maybe we could give you better answers then :)

---

### Post by wilee-nilee on 2010-12-25
Last advice wont work, grub is in the mbr most likely.

Here is a W7 recovery disc download it burn it to a cd. Boot it accept language prompt then hit r for repair or click on repair. Go to the command line and enter.
```
bootrec.exe /fixmbr
```

Here is a wubi thread if needed.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by cadenn on 2010-12-26
> **wilee-nilee said:**
> Last advice wont work, grub is in the mbr most likely.

Here is a W7 recovery disc download it burn it to a cd. Boot it accept language prompt then hit r for repair or click on repair. Go to the command line and enter.
```
bootrec.exe /fixmbr
```

Here is a wubi thread if needed.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Where's the W7 recovery disc link???

Edit: Nvm, Thanks I ended up being able to fix my lappy because of your advice! I really appreciate it!

---

### Post by jeff3211 on 2010-12-26
Check this page to see if you can get the WIN 7 recovery disc you need...
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by jeff3211 on 2010-12-26
I got some great assistance in reinstalling the grub loader in this thread...
[http://ubuntuforums.org/showthread.php?t=1651380](http://ubuntuforums.org/showthread.php?t=1651380)

Also if you can create the WIN 7 boot disc with the download from the link I posted earlier, then you can also download and create an ubuntu 10.10 LiveCd. I encourage you to do so, as the resources on the disc will help you make the necessary repairs.

---

### Post by jeff3211 on 2010-12-26
If you've made the repair, please post your fix and mark this thread as solved by using thread tools at the top of your thread.

---

