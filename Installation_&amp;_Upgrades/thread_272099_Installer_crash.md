---
title: "Installer crash"
date: 2006-10-05
forum: Installation &amp; Upgrades
---

### Post by mdubs on 2006-10-05
I am attempting to install ubuntu 6.06 on a ThinkPad T41p. The whole process goes well through the partitioning phase. Once it reaches the installation phase, I get the code presented below.

Has anyone else had this problem? Please help.

```
We're sorry; the installer crashed. Please file a new bug report at https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug (do not attach your details to any existing bug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/installer/syslog, /var/log/syslog, and /var/log/partman:

Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 266, in run
    self.process_step()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 755, in process_step
    self.mountpoints_to_summary()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1114, in mountpoints_to_summary
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 550, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s\n%s" %
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1263, in ?
    if install.run():
  File "/usr/share/ubiquity/install.py", line 284, in run
    if not self.copy_all():Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 266, in run
    self.process_step()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 755, in process_step
    self.mountpoints_to_summary()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1114, in mountpoints_to_summary
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontenTraceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 266, in run
    self.process_step()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 755, in process_step
    self.mountpoints_to_summary()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1114, in mountpoints_to_summary
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 550, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s\n%s" %
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1263, in ?
    if install.run():
  File "/usr/share/ubiquity/install.py", line 284, in run
    if not self.copy_all():
  File "/usr/share/ubiquity/install.py", line 469, in copy_all
    os.lchown(targetpath, st.st_uid, st.st_gid)
OSError: [Errno 30] Read-only file system: '/target/boot'
d/gtkui.py", line 550, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s\n%s" %
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1263, in ?
    if install.run():
  File "/usr/share/ubiquity/install.py", line 284, in run
    if not self.copy_all():
  File "/usr/share/ubiquity/install.py", line 469, in copy_all
    os.lchown(targetpath, st.st_uid, st.st_gid)
OSError: [Errno 30] Read-only file system: '/target/boot'

  File "/usr/share/ubiquity/install.py", line 469, in copy_all
    os.lchown(targetpath, st.st_uid, st.st_gid)
OSError: [Errno 30] Read-only file system: '/target/boot'

    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 266, in run
    self.process_step()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 755, in process_step
    self.mountpoints_to_summary()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1114, in mountpoints_to_summary
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 550, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s\n%s" %
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1263, in ?
    if install.run():
  File "/usr/share/ubiquity/install.py", line 284, in run
    if not self.copy_all():
  File "/usr/share/ubiquity/install.py", line 469, in copy_all
    os.lchown(targetpath, st.st_uid, st.st_gid)
OSError: [Errno 30] Read-only file system: '/target/boot'


```

---

### Post by wpshooter on 2006-10-05
Are you installing Dapper 6.06.1 and if so, are you installing from DESKTOP CD or from ALTERNATE CD ?

Also, did you check the integrity of your Ubuntu CD by running the verification function found on the initial Ubuntu boot screen menu ?

---

### Post by mpbb77 on 2006-10-16
It looks like I have the same problem (don't have the log to compare at hand). I'm installing Edgy Eft beta from desktop install CD and I'm running it on a small freed partition sda4 on quadruple boot WinXP/SuSE 10.1/Mandriva 2007 just for making my mind between Mandriva and Ubuntu (dropped 6.06 for Suse 10.1 with no regrets at all so far because couldn't even have an install screen on my ati X700, though from what I've seen this is still not fixed in 6.10). Also have checked the integrity of the CD. 

FTTB, will maybe try the Alternate CD install but rather from 6.06 than 6.10, while waiting for the final 6.10 release (unless someone can give a clue about this python script crash - I'm surprised there are so few with the same issue, was expecting to find easily a fix).

Obs.: I thought that one issue could be that on the normal (MBR) install I've asked grub to setup (hd0,3) instead of proposed (hd0) though it seems the install didn't reach that stage yet.

BR

---

### Post by mpbb77 on 2006-10-16
Just occurred to me that there is probably an issue with the install creating a 5th primary partition to swap, as I forgot to set it to the current swap common partition.  Will check later tonight.

BR

---

### Post by mpbb77 on 2006-10-16
BTW, mdubs, could be the same issue for you as the Thinkpads have got a standard backup partition so you've got win + backup and maybe another partition/OS (triple boot) ?

---

### Post by mpbb77 on 2006-10-19
Well, I was close to dropping forever Ubuntu, or at least for as long as I'll own my laptop, but finally on last try got it installed.

Tried everything: 

- burn and reburned 6.10 despite CD check ok, got the installer crash problem

- burned 6.06.1, got the same issue

- burned and reburned 6.06.1 alternate, got another issue with corrupted packages (xfsprogs and others) despite CD check ok

- burned 6.10.1 alternate , and got the same corrupt packages showstopper ! (needless to say CD check was ok)

- redownloaded and reburned 6.10 AND in a last ditch tried:
After the "usual" lousy x700 driver setup (sudo apt-get update; sudo apt-get install xorg-xserver-fglrx; edit xorg.conf to set fglrx), decided to launch sudo startx. Of course I would get in root home desktop but then launched install from my user home. It worked !

So I cannot say if it was a) a bad burn in my first 6.10 attempt despite CD check Ok and original iso md5 checksum Ok or b) my workaround to get the installer with root privileges (which could explain that the resizing python script would not work, maybe). 

Obs. 1: x700 install was not "usual" actually, I manages to be worse than 6.06 as you can't even get a console screen after the Xserver failure, as you get stuck in a shell in F7. So you need to Ctrl-Alt F1. And you cannot simply restart gdm, needs reboot.

Obs. 2: on the up side, I could confirm that setting grub install to (hd0,x) instead of (hd0) in the confirmation screen works, so no need to use the alternate CD to get grub not installed in the MBR. 8)   

Cheers

---

### Post by mpbb77 on 2006-10-30
Wow, this is worse than i ever thought possible.

Tried to install Edgy release and simply got stuck on a hanging screen. Same for safe graphics and even CD check...
Cannot even get any more a console to update the ati drivers. I cannot believe I'm alone in that, there are plenty of X700 around.

And I had succeeded to install 6.10 beta ! This time will not lose time on the alternate install. Already reburned twice my CD and I'm trying to redownload the iso, though checksum is ok. Will maybe take another CD to burn. If it doesn't work seems I will really have to wipe out Ubuntu from my machine. This time this seems really uninstallable, anyone has a guess, maybe interrupting install in the middle to get a console (ctrl-C ?) ?

Cheers

---

### Post by mpbb77 on 2006-10-30
Great. SOLVED the issue but what a hack. Seems like nobody got this issue, strange.

---

### Post by mpbb77 on 2006-10-31
Well, going on with probably the last chapter of my monologue, finally got my Edgy working fine. Still got a hang-on-logout issue after my install, but discovered it was a resolution issue. AND could install xgl and beryl is just working fine. Hope I'll be able to test Xen. After all, it's a fact, this is definitely not a mainstream release but is for "edgies" : no bash but dash, dpkg-architecture command won't work (couldn't update manually to the latest ATI driver while trying to solve the hang-on-logout issue because of that, despite redirecting sh to bash !) and I guess that's just the beginning.  Great. But they could have communicated it better. As such, I agree that this release is a PR debacle.

Cheers

---

