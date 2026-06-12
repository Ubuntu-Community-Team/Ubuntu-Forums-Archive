---
title: "Help required installing Ubuntu by new user"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by Rosmary16 on 2011-01-21
**Help required by a new user.**
 
Installed a brand new hard drive in my Compaq NX9010 laptop.
 
On the second attempt installing Unbuntu the screen said 100% installed and restarted. However when it did, Ubuntu did not start but gave me the option to start in normal mode, safe mode or check the memory.
 
When I try to start in normal or safe mode I get the following message:
[SIZE=3][FONT=Calibri]“Error: no such device: 83f3432b-8ea4-4b7a-91f5-5fab0634c71b[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Failed to boot default entries”[/FONT][/SIZE]
I am unable to do anything at all with my laptop now.
 
[SIZE=4]Please can someone help me (in simple terms!)??[/SIZE]
:cry:

---

### Post by dino99 on 2011-01-21
here is how to install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by sikander3786 on 2011-01-21
Welcome to the forums :-)

The error you posted gives a hint of some problem with some disk mount problems. Instead of troubleshooting, you can just try a re-install as that would be a lot easier and quicker than troubleshooting it.

If you've got any queries regarding the install, feel free to ask.

If the error persists even after a re-install, we'll need to diagnose it. And then, you'll need to boot an Ubuntu Live CD/USB in 'Try' mode and post the output of bootinfoscript as per instructions here, in order to let us see what is going wrong.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

### Post by Rosmary16 on 2011-01-22
Can you please advise how I actually format the hard drive so I can reinstall Ubuntu?
 
Hope that you can help.
Rosmary

---

### Post by oldfred on 2011-01-22
Sometimes grub just does not install correctly. Most do not seem to have issues and often a reinstall of grub works.


For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

If you still have issues review these threads and post the boot script results suggested by sikander3786.
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
Solutions to many boot issues - meierfra.:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)

---

