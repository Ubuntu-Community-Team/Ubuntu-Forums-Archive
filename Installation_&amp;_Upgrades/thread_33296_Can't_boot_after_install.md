---
title: "Can't boot after install"
date: 2005-05-10
forum: Installation &amp; Upgrades
---

### Post by Battousai on 2005-05-10
Hi all,
I tried to install Ubuntu on my Laptop today.
The installation went smoothly and I installed Grub (I have winxp too). 

The problem is : I can't load anything after the initial reset:
"Hard disk boot sector invalid
Press 'H' to retry Hard Disk, any other key for floppy"

I can't get past that screen.
So , what should I do? I already tried to reinstall Ubuntu twice , each time by erasing the Ubuntu partition then installing again on it.

Since I can't even get to Dos , I can't post more informations (I'm on another computer now).

Any help would be greatly appreciated.

---

### Post by Zelut on 2005-05-10
Where did you install the GRUB loader?  I had a similar problem in the past when I tried to install it anywhere other than the MBR.  Is that where you've put it?

I'm sure you'll be able to get back into your DOS partitions soon enough, dont worry about losing your data..

---

### Post by kosmic on 2005-05-10
[QUOTE=Battousai]Hi all,
I tried to install Ubuntu on my Laptop today.
The installation went smoothly and I installed Grub (I have winxp too). 

The problem is : I can't load anything after the initial reset:
"Hard disk boot sector invalid
Press 'H' to retry Hard Disk, any other key for floppy"

I can't get past that screen.
So , what should I do? I already tried to reinstall Ubuntu twice , each time by erasing the Ubuntu partition then installing again on it.

Since I can't even get to Dos , I can't post more informations (I'm on another computer now).

Any help would be greatly appreciated.[/QUOTE]
 When you choose to install ubuntu where did you choose to put the Grub Loader ? in the MBR ? (Master boot record) ??

---

### Post by Battousai on 2005-05-10
I don't really know : I didn't get the choice when I installed (I choosed a YES option somewhere). So I guess it was the default choice.

EDIT: so here's the latest deal: I ran my windiws disk and choose to repair my installation:
fixboot says the boot sector has been rewritten correctly , but nothing changes
fixmbr says the same , but it doesn't change anything either.

---

### Post by bigbangbigbigbang on 2005-05-10
[QUOTE=Battousai]I don't really know : I didn't get the choice when I installed (I choosed a YES option somewhere). So I guess it was the default choice.

EDIT: so here's the latest deal: I ran my windiws disk and choose to repair my installation:
fixboot says the boot sector has been rewritten correctly , but nothing changes
fixmbr says the same , but it doesn't change anything either.[/QUOTE]

Have you got a Knoppix at hand? I can guide you through the repair

---

### Post by Battousai on 2005-05-10
Err no I haven't ,but I can download the live cd now and burn it right away.
Isn't there any way to do it with the windows cd? At this point I don't care anymore about Ubuntu , but I care about my files...

EDIT : oh , but I have the Ubuntu Live cd , is it good too?

---

### Post by bigbangbigbigbang on 2005-05-10
Don't worry about your files, everything will be allright.
The windows cd has very limited repair capabilities compared to knoppix.
So grab it and tell me when you are ready to go

The Ubuntu live cd also works but is quite a bit slower to boot and I am not as familiar with it repairing as with Knoppix

---

### Post by Battousai on 2005-05-10
Ok the file is downloaded. The disc should be ready in five minutes
Thanks for your patience!

---

### Post by bigbangbigbigbang on 2005-05-10
I sent you my AIM account, it would be easyer to continue with that.
We can post the protocol at the end to the forum

---

### Post by Battousai on 2005-05-10
[QUOTE=bigbangbigbigbang]I sent you my AIM account, it would be easyer to continue with that.
We can post the protocol at the end to the forum[/QUOTE]
 Your mail doesn't seem to be working , and I don't have AIM :s

---

### Post by bigbangbigbigbang on 2005-05-10
[QUOTE=Battousai]Your mail doesn't seem to be working , and I don't have AIM :s[/QUOTE]

OK. Just boot with knoppix 2 (this is faster, goes to the console without X)
when it's up, do ls /mnt and tell me what is in there

PS. Ubuntuforums is getting damn slow on my side...

---

### Post by sci on 2005-05-22
I have exactly the same problem. Is ther a solution to this? I need to the the computer up and runnnign ASAP (currently running Ubuntu Live CD).

Erik

PS. I installed GRUB to the MBR. DS.

---

### Post by Battousai on 2005-05-22
With the help of bigbangbigbang , I could repair the thing.

I had to manually reinstall grub while using a live cd. 
I can't exactly remember how it went...
I know grub is in boot/grub/ . There I could reinstall grub and that I could edit the start menu.

---

### Post by SamheG on 2006-07-24
Hi !
I've tried to install Ubuntu on a laptop (Packard Bell K5266) but I got the same error at the boot :
Invalid boot sector, press H ....

I've tried to reinstall grub but I still have this error.

I've seen on the web that some laptops are protected (especially hp and packard bell)

So does someone know what I could do to boot on my HDD ?

Thanx

---

### Post by kash on 2006-07-29
hello.
I have a problem regarding booting of ubuntu. Everything of the installation part goes on well, but when it starts to boot, it halts at a point where the display is "hotplug subsytem". at this point the booting process stops and never seem to continue. Can anyone help??.

---

