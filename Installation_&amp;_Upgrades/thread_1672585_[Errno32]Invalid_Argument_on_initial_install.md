---
title: "[Errno32]Invalid Argument on initial install?"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by SewerWaste on 2011-01-21
So I gave in on the Linux OS. I decided I'd give it a try after many months ot temptation.

I burned the .iso file onto a CD so I could then install it off the CD. The progress bar will make it to about halfway while installing ubuntu-10.10 before I get an error. I saw in the [[wubi] MEGATHREAD](http://ubuntuforums.org/showthread.php?t=1639198) it said it was probably the most common error, but I have yet to solve my problem. I do not have a windows recovery CD handy, if it came to it I probably could download/find one.

The 2nd solution is to download ubuntu on a usb or LiveCD(what is this? normal cd?) and then from there you can change the settings.

I'd like to run ubuntu on my F Drive, which is an internal backup drive that is completely empty.

When I went through my error log it sent me to, it looks as if the error is listed in here:
[I]IOError: [Errno 22] Invalid argument
01-21 00:35 DEBUG  TaskList: # Cancelling tasklist
01-21 00:35 DEBUG  TaskList: New task check_iso
01-21 00:35 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
01-21 00:35 DEBUG  CommonBackend: Searching for local ISO
01-21 00:35 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
01-21 00:35 DEBUG  TaskList: New task get_metalink
01-21 00:35 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
01-21 00:35 DEBUG  TaskList: # Cancelling tasklist
01-21 00:35 DEBUG  TaskList: # Finished tasklist[/I]

[img]http://gyazo.com/038bcf872ef74218ef292f4195033d48.png[/img]
[IMG]http://gyazo.com/f154515e820345e6d12df8b7d7b9a27f.png[/IMG]


Any suggestions? Hints? Help? Fixes?

Lay them down!

P.S. Running Windows XP.

Questions:
What is GRUB2 and Wubi? What are they used for? Are they necessary for running ubuntu?

---

### Post by SewerWaste on 2011-01-21
Still having this issue, it was moved back a few pages. So;

~Bump~

I can provide any further information when requested.

---

### Post by bcbc on 2011-01-21
Grub2 is the bootloader that Ubuntu uses by default. [http://en.wikipedia.org/wiki/Booting](http://en.wikipedia.org/wiki/Booting)

Wubi is a windows-installer - that allows you to install Ubuntu without creating a separate physical disk partition for it. It is a convenient method to try out Ubuntu with near-normal speed and data persistence. It's not recommended for long term use because it uses a virtual disk (a single file) that is less reliable than a physical partition. It also has a unique set of issues for which there is less available community support.

Wubi also uses grub2 but it boots via the Windows Boot Manager, and chains into grub2 using something called Grub4dos. Wubi has been particularly vulnerable to grub2 updates lately and there is a special megathread dedicated for this now: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If you already have a dedicated "F: drive" for Ubuntu - it's actually a partition - then you might as well install Ubuntu directly to it. The difference between this method will be that Grub2 will become your default bootloader (not Windows). 

If you still just want to try Wubi, then download the .iso and wubi.exe into the same folder, and run wubi from there. Make sure you have internet access available.

---

### Post by SewerWaste on 2011-01-21
> **bcbc said:**
> Grub2 is the bootloader that Ubuntu uses by default. [http://en.wikipedia.org/wiki/Booting](http://en.wikipedia.org/wiki/Booting)

Wubi is a windows-installer - that allows you to install Ubuntu without creating a separate physical disk partition for it. It is a convenient method to try out Ubuntu with near-normal speed and data persistence. It's not recommended for long term use because it uses a virtual disk (a single file) that is less reliable than a physical partition. It also has a unique set of issues for which there is less available community support.

Wubi also uses grub2 but it boots via the Windows Boot Manager, and chains into grub2 using something called Grub4dos. Wubi has been particularly vulnerable to grub2 updates lately and there is a special megathread dedicated for this now: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If you already have a dedicated "F: drive" for Ubuntu - it's actually a partition - then you might as well install Ubuntu directly to it. The difference between this method will be that Grub2 will become your default bootloader (not Windows). 

If you still just want to try Wubi, then download the .iso and wubi.exe into the same folder, and run wubi from there. Make sure you have internet access available.

Ok, that answers my questions. Now, how would I get ubuntu to boot from my computer?

---

### Post by bcbc on 2011-01-21
> **bcbc said:**
> If you still just want to try Wubi, then download the .iso and wubi.exe into the same folder, and run wubi from there. Make sure you have internet access available.

If you want Wubi then see above. Is that what you are asking? 

If you want a diagnosis on the particular error you can copy the whole log file, but I've seen some installs from CD fail due to hardware (the CD works on one computer, but not another) and from a bad burn (using incompatible software, or burning incorrectly).
You can boot from the CD - press a key when you see the little keyboard icon at the bottom centre - then from the extended menu that follows, check the disk for errors.

If you can boot from the CD, also use the "Try without installing" option - check that it's compatible with your hardware.

If you want to install it directly to the partition represented by the F: drive, then install after booting from the CD (not in windows). Be careful not to overwrite Windows ([10.10 has a confusing installer]("http://ubuntuforums.org/showthread.php?t=1622388"))

---

