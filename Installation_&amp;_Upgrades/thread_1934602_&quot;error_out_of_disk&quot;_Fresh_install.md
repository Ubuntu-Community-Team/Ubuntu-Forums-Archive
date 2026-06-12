---
title: "&quot;error: out of disk&quot; Fresh install"
date: 2012-03-02
forum: Installation &amp; Upgrades
---

### Post by ku5e on 2012-03-02
I am attempting (for the last two days) to install Ubuntu12 64 on a Compaq nx7400 dual boot with Windows7. I have a 250gb HD partitioned accroding to the Grub rescue prompt as:
(hd0) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1) 
so two for win and 2 for linux.

When I boot I get 
error: out of disk
grub rescue>

At that prompt I ran ls and got the results above
Then I ran 
ls (hd0,msdos5)/
and received
./ ../ lost+found/ etc/ media/ var/ bin/ boot/ ........
then I ran 
ls (hd0,msdos5)/boot
and received 

error: out of disk

then I ran 
ls (hd0,msdos5)/etc
and received 

error: out of disk

Looks to me that Grub can't read the directories, WHY? How do I fix it?

Any and all help is appreciated.


PS> I can use Boot-Repair to repair the MBR and boot into Windows fine, but then I can't do ubuntu. [My pastebin results from Boot-Repair.]("http://paste.ubuntu.com/865439/") But I want Grub to do its job. It is pretty urgent for me as well.

---

### Post by ku5e on 2012-03-02
OP here,

I tried [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
terminal method.
Got the same error. 

SO I followed the instructions and held left Shift Key and I got kind of the same error:
GRUB loading.
error: out of disk.
grub rescue>


Still trying to find a solution:confused:
HELP!

---

### Post by YannBuntu on 2012-03-16
Hello
run Boot-Repair,click "Advanced options", go to the "GRUB options" tab, tick the "out-of-disk" option, then apply.

---

### Post by gabak on 2012-06-10
How do i do this what u r saying? With a live ubuntu cd? Where r thosr options??


QUOTE=YannBuntu;11770058]Hello
run Boot-Repair,click "Advanced options", go to the "GRUB options" tab, tick the "out-of-disk" option, then apply.[/QUOTE]

---

### Post by YannBuntu on 2012-06-10
From a live-CD (either a Boot-Repair-Disk or Ubuntu-Secure-Remix which come with preinstalled Boot-Repair, or a Ubuntu CD in which you install Boot-Repair).
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

