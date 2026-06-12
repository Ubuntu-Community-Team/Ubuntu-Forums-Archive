---
title: "Ubuntu as Second OS"
date: 2013-06-06
forum: Installation &amp; Upgrades
---

### Post by Lilium816 on 2013-06-06
A while ago I made a thread to confirm that Ubuntu could in fact be installed on a Windows 8 64bit machine. In one of the replies a user mentioned that I should come back here before actually installing Ubuntu because there are some special steps: ( here is the original thread: [http://ubuntuforums.org/showthread.php?t=2150390&p=12672373#post12672373](http://ubuntuforums.org/showthread.php?t=2150390&p=12672373#post12672373))
 
" Yes, that laptop should work with Ubuntu as second OS. Once you get that new machine get back to the forums with a new thread before you set up Ubuntu-Windows dual boot. You will need some special instructions before you proceed. "
[COLOR=#000000]
I am now here for those "special instructions"





[/COLOR]

---

### Post by oldfred on 2013-06-06
Some other threads.
 Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

You can review my general instructions & links. See my signature. Then if you have specific questions or issues ask those or post BootInfo report after install.

---

### Post by ShadowVegan on 2013-06-06
Installing Ubuntu second is pretty risk free. You'll still want to back up your Windows files, with partitioning and installing an OS you can never guarantee something won't go wrong. However, if you just boot from the Ubuntu CD it will give you an option to install alongside the existing OS and ask you how much HDD space you want for each and it does everything else automatically, you shouldn't have much trouble with it.

---

### Post by fantab on 2013-06-07
+1 for the Backup suggestion.

Read the 'complete Backup' instructions here: [http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710) (specially Mark Phelp's post)
The tool Mark recommends can be found here: [http://www.macrium.com/reflectfree.aspx](http://www.macrium.com/reflectfree.aspx)

If you have any doubts do clarify before you start.

Good Luck...

---

### Post by Mark Phelps on 2013-06-07
> **ShadowVegan said:**
> ... if you just boot from the Ubuntu CD it will give you an option to install alongside the existing OS and ask you how much HDD space you want for each and it does everything else automatically, you shouldn't have much trouble with it.

That is, until you try to boot Back into Win8 and find that it won't boot anymore because your using the Slider caused the boot loader to become corrupted ...

This is a really bad idea for installing Ubuntu in a Win7/Win8 environment.  Windows doesn't take kindly to having its partitions messed with from outside, and when that goes badly, as it sometimes does, you end up with an unbootable copy of Windows.

---

