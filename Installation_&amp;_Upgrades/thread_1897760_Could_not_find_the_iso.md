---
title: "Could not find the iso"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by alastairjohnjack on 2011-12-19
I downloaded the latest Wubi and Ubuntu (wubi.exe and ubuntu-11.10-desktop-amd64.iso) and placed them in a folder together, I then started Wubi and left it as the default options (on C drive, 18gb instal size) then put a password in, clicked install, clicked the restart option.

Then it started up with a pink Ubuntu loading screen, but after that it went to a black screen and the thing that stood out was: 

Could not find the iso /ubuntu/installer/installation.iso
It then listed some steps about gracefully shutting the computer down and rebooting etc. which seems irrelevant because I tried those steps and did not help (it shutdown/rebooted fine to begin with anyway).

I've tried uninstalling and installing multiple times but get the same error (could not find iso) each time.

________________

System specs if it helps:

i5 2400
AMD Radeon 6850
Windows 7 64 bit

---

### Post by hackb0y294 on 2011-12-19
I haven't heard of installing Wubi that way, though it's quite possible I'm uninformed. Did it have some sort of option to select the ISO image in Wubi? And was there a reason you didn't just mount the ISO and install from there? You can use free programs such as MagicDisk to mount ISOs in Windows, which IMO would be the way to go.

---

### Post by alastairjohnjack on 2011-12-19
The method I used was posted here:
[http://ubuntuforums.org/showpost.php?p=11474270&postcount=4](http://ubuntuforums.org/showpost.php?p=11474270&postcount=4)
As just using Wubi by itself gave me that "gave up waiting for root device" error.

Clarification on your response: are you recommending mounting the ISO and just installing it that way without using Wubi at all?

---

### Post by hackb0y294 on 2011-12-19
Hmm, that Wubi method sure sounds odd to me. No, I was suggesting running Wubi from the mounted image.  What was the original method you used that gave you the error?

---

### Post by alastairjohnjack on 2011-12-19
Okay, I mounted the ISO and just used the Wubi in the ISO, installed it, then I get the same error mentioned in the first post (after it starts up Ubuntu, screen goes black and says cannot find the iso).

---

### Post by hackb0y294 on 2011-12-19
I just re-read your first post, and it appears that Wubi can't read the ISO image. I just found this in the Wubi Guide ([https://wiki.ubuntu.com/WubiGuide):]("https://wiki.ubuntu.com/WubiGuide%29:")

> If you do not have a CD, try to find a computer with Internet access,  and download both Wubi.exe and the required Desktop ISO from the same  location (**the release has to match**):  So maybe try downloading the Wubi installer from here (scroll to the bottom) and see if that works for you:
[http://releases.ubuntu.com/oneiric/](http://releases.ubuntu.com/oneiric/)

---

### Post by alastairjohnjack on 2011-12-19
Yeah I did download from there already.

---

### Post by hackb0y294 on 2011-12-19
I'm sorry I've not been of any help. The only other thing I can think of right now is to put both files in another folder (maybe Desktop) and try from there...

---

### Post by alastairjohnjack on 2011-12-19
I was running it from my download folder, so I tried putting it on the desktop but that didn't make a difference. Thanks for trying to help, I didn't think Linux would work anyway.

---

### Post by bcbc on 2011-12-20
The windows part worked fine. The problems you've had after rebooting is the part where Ubuntu boots and it installs to the virtual disks. (So redoing or modifying the way you do it on Windows makes no difference).

I don't know why Ubuntu cannot find the installation.iso since it's copied to the drive as part of the installation process. So my recommendation would be to run 'chkdsk /r' from windows, maybe defragment (if your drive is fragmented - based on your judgement). If all that does nothing, then I've no idea what the issue is. 

Also, if you can boot an Ubuntu CD and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") it may provide some clues.

---

### Post by alastairjohnjack on 2011-12-20
I get the following when I run that chkdsk thing:


[IMG]http://dl.dropbox.com/u/1024727/chckskd.PNG[/IMG]

---

### Post by bcbc on 2011-12-20
It's normal if you're running it on the c: drive. Select Y and then reboot to complete.

---

### Post by alastairjohnjack on 2011-12-20
I just ran that 'chkdsk /r' thing and I tried installing it again, wasn't sure if I was suppose to do that after or not. But yeah after that, still says the same thing. I did try defragging at the start of today, said it was 2% fragmented.

---

### Post by bcbc on 2011-12-20
I recommend burning an Ubuntu CD, and booting from it as a live CD (select "Try Ubuntu") and then running the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). There is some issue with Ubuntu/grub reading the partition. Just no way to know really without some diagnostics.

Or if you're left at a grub> prompt you can run a few commands to see which partitions/files it can view:
ls (lower case LS) shows the drives/partitions as (hd0) (first drive) and (hd0,1) first partition on first drive.
For each partition you can browse the files as:
ls (hd0,1)/
ls (hd0,2)/

(The above command is similar to: dir C:\ (depending on which partition C: is on).

Note, sometimes grub uses (hd0,msdos1) instead of (hd0,1) (both work okay), and sometimes ('dev/sda',msdos1).

On older computers the BIOS cannot read physically beyond 137GB on the drive, so that can be an issue if the files are located outside this range. Not so common anymore, but if your computer is more than a few years old it's worth checking.

---

