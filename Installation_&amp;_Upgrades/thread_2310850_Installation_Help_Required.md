---
title: "Installation Help Required"
date: 2016-01-22
forum: Installation &amp; Upgrades
---

### Post by prasanna10 on 2016-01-22
[COLOR=#000000]Hello All,[/COLOR]

[COLOR=#000000]I am a new ubuntu user and got the error as below ;[/COLOR]

[COLOR=#000000]Traceback (most recent call last):[/COLOR]
[COLOR=#000000]File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__[/COLOR]
[COLOR=#000000]File "\lib\wubi\backends\common\backend.py", line 600, in get_iso[/COLOR]
[COLOR=#000000]Exception: Could not retrieve the required installation files[/COLOR]
[COLOR=#000000]01-22 18:23 DEBUG TaskList: # Cancelling tasklist[/COLOR]
[COLOR=#000000]01-22 18:23 DEBUG TaskList: # Finished tasklist[/COLOR]


[COLOR=#000000]Also did try the same setup file on my friends Laptop and it works as expected, Mine is a pretty old PC :([/COLOR]
[COLOR=#000000]I have also add the error logs for reference.[/COLOR]

[COLOR=#000000]Problems that i have noticed as of now :[/COLOR]

[COLOR=#000000]1. My Bios is not working properly as the bios settings are not getting saved.(Checksum Error)[/COLOR]
[COLOR=#000000]2. I have already installed Win Xp on my C:/ drive and trying to install Ubuntu on D:/ Drive (I really like ubuntu and want to install it on my PC ASAP)(I have left around 13 Gigs of space on D:/ and also have some data still on it)[/COLOR]


[COLOR=#000000]Since my BIOS Settings are not proper i am unable to install the Ubuntu from my Pendrive as every time the bios settings are back to normal i am not getting an prompt to load from my pendrive.[/COLOR]

[COLOR=#000000]Hence i directly installed the Ubuntu from the Pendrive which is giving the above error.[/COLOR]

[COLOR=#000000]Any trial and error method from the logs are much appreciated.Waiting to have ubuntu successfully installed on my machine.[/COLOR]

[COLOR=#000000]Thanks in advance.[/COLOR]


[COLOR=#000000]Regards,[/COLOR]
[COLOR=#000000]Prasanna.M[/COLOR]

---

### Post by khelben1979 on 2016-01-22
"My Bios is not working properly as the bios settings are not getting saved"

I would recommend to either let someone help you to insert a new clock battery in that computer, or you open it up and fix it yourself. They are cheap and will save you much hassle. In the meantime, I have 2 questions:
1. What is the exact model of the laptop?
2. What version of Ubuntu are you trying to install?

---

### Post by QIII on 2016-01-22
Wubi is no longer actively maintained and its use is not recommended.

I suggest a proper dual-boot instead.

---

### Post by prasanna10 on 2016-02-09
Hi khelben,


Apologies for the delayed response.


I dont exactly think this should be related to my BIOS Battery.


I have a few batteries with me and i have tried them all with the same results sadly.


To answer your questions :


1.This is not a laptop, its a desktop (Compaq Pesario SR1720IL)
2. Ubuntu ubuntu-15.04-desktop-i386.iso

---

### Post by mörgæs on 2016-02-09
The unsupported XP is a security hazard. Are you sure that you want to keep it? 

I would suggest a single boot Lubuntu 15.10 install.

---

### Post by leunam12 on 2016-02-09
I would try re-flashing the BIOS with the latest firmware and if that doesn't work I would try to get a new motherboard.

---

### Post by Geoffrey_Arndt on 2016-02-09
This whole install is a total disaster.    Bad install software, bad hardware, bad XP, residual "files" on the install partition ???   As Morgaes has already written, a sole install of Lubuntu may very well be the only option, and if that doesn't work, try the latest ISO of antiX . . . . . . see [http://www.distrowatch.com](http://www.distrowatch.com) for listing of all distros (versions) of desktop linux, with links to obtain the iso's.

You should consider XP like an infected, diseased Rat . . . . . and kill it, kill it, wipe it off the PC . . . [-X

Of course, there are MANY older used desktops available that are very Linux friendly.   Look for all Intel systems from Dell or Lenovo, and you'll be good to go!!!  (And with one of those models - having 2 GiB or more,  and Intel graphics, you'll actually be able to install the "mother - distro" . . . Ubuntu).

---

### Post by Bucky Ball on 2016-02-09
*Thread moved to **Installation & Upgrades**.*

Better chance here. ;)

15.04 is no longer supported. Forget that for a start. You want 14.04 LTS (probably a good choice for a beginner as very stable) or 15.10 if you have very new hardware. The former has five years support until 2019, the latter July this year.

Download the ISO of a supported release, burn install media, start again. When you've done that, if you are still having issues, run the bootinfoscript and post the link or output (between code tags, see link in my signature) here.

BootInfoScript download:
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Instructions:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Be aware: You must have free space to install Ubuntu to, not a partition that 'still has data on it' or an NTFS partition you created with Windows. Just leave free space, start the install. That's it.

And D: drive, etc., is Win-speak. Partitions are referred to as partitions here, not the Win-speak 'disks', and C: partition on your first disk would be described as sda1. This will prepare you for when you have Ubuntu installed and are dealing with this naming, not D: etc. for partition naming. ;)

* And as mentioned, forget Wubi. Not supported so don't go there. And go for Lubuntu if you have very old hardware that is sluggishly slow or doesn't work at all under Ubuntu.

---

