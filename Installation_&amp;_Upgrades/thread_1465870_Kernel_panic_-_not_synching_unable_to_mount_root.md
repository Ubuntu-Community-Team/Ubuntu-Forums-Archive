---
title: "Kernel panic - not synching: unable to mount root"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by Destro09 on 2010-04-29
Problems arose when I updated today, after not booting(updating) for a couple of days.  Message originally said "Kernel panic - not syncing: UFS: Unable to mount root fs on unknown-block(8, 1)"

I get the options to boot too:

2.6.31-21-generic
2.6.31-21-generic(recovery mode)
2.6.31-20-generic
2.6.31-20-generic(recovery mode)
2.6.31-14-generic
2.6.31-14-generic(recovery mode)

2.6.31-20 allows me to boot (normal, not recovery) as I am posting this now.

However, before posting this, I attempted to research and solve the problem by myself.

Attempted -> "sudo apt-get install --reinstall linux-image-2.6.31-21-generic"

This looked like everything installed correctly but no dice.  Same error as before.

Next advice I tried -> "sudo gedit /etc/default/grub"

Here I uncommented the line reading "GRUB_DISABLE_LINUX_UUID=true" (near the bottom of the text)

Finally, "update-grub" and reboot

Once again, looked like everything did its job, however, the error now reads "error: You need to load the kernel first"

Additional reading has since confused me and I now don't really understand what to do from here.  Any help would be GREATLY appreciated.


***Additional information:
Currently running Ubuntu 9.10

Other posts I've read continually ask for this info:

username@ubuntu:~$ dpkg -l|grep grub
ii  grub-common         1.97~beta4-1ubuntu4.1
     GRand Unified Bootloader, version 2 (common 
ii  grub-pc             1.97~beta4-1ubuntu4.1
     GRand Unified Bootloader, version 2 (PC/BIOS



PS - I really don't want to sound like a jerk BUT, please don't suggest upgrading to the new LTS version of ubuntu. :)  Thanks for the help in advance.

---

### Post by didkaticos on 2010-04-30
Hello there! I am a ***[COLOR=Red]newbie[/COLOR]*** (a REAL ONE). I have the same exact problem, plus I don't have any idea where to start fixing this issue. I wouldn't dare to do what Destro09 (above) did. Any suggestions for people like me? I love Ubuntu. I switched from Windows XP, and it had been working very well until now.

---

### Post by vincy on 2010-04-30
I am having similar problem' 

I left the upgrade to run overnight, when i try to restart today i get " [COLOR=#000000] [/COLOR][COLOR=#000000][B]Kernel panic - not syncing: VFS: Unable to mount root fs on unknown - block (0.0).

[/B][/COLOR]I have a separate boot and root partitions  [COLOR=#000000][/COLOR]
I followed a thread and did the root repair in terminal using the 9.10 live cd but still nothing sme message at start up
   	 	 	 	 	 	  [http://ubuntuforums.org/showthread.php?t=422523](http://ubuntuforums.org/showthread.php?t=422523)


   	 	 	 	 	 	  A little help please don't want to loose all the settings and everything else with a fresh install

---

### Post by Destro09 on 2010-05-03
For the other people reading/posting this thread, I found another one that might help you.  Keep in mind its version 10.4.  Some of the advice there might be helpful, not really sure.

[http://ubuntuforums.org/showthread.php?t=1460761](http://ubuntuforums.org/showthread.php?t=1460761)

---

### Post by Rayve on 2010-05-03
I had the same problem when I updated kernels in 9.10 at one point.  While GRUB is loading, you can press the SHIFT key multiple times to bring you to the menu where you can choose what kernel to load. 

However, if you can get into a working system (as you mentioned you can with .20), you can download startup-manager from Synaptic.  That will allow you to say which kernel you want to boot into by default.  Since .21 isn't working, click on System > Administration > StartUp-Manager and tell it to boot you into .20.

You can do this any time you'd like to get around a bad updated kernel.  Worked great for me.  :)  Hope this helps.

In fact, I have it booting into -20 as well, so -21 is probably what brought me to this point.  -21 loaded me into a kernel panic, and after *I* stopped panicking, I did some looking around and some kind forum user pointed me to startupmanager.  It's been great.

Just a note: if you download your video drivers and install manually, as I do for NVIDIA drivers, you'll have to reinstall them once you boot into a different kernel - you'll get the warning about "low-graphics mode", just choose "exit to terminal" and update as you do normally.

ETA: Vincy, startupmanager should help you, too.

---

### Post by Destro09 on 2010-05-06
All that will do is change my default boot kernel to an old version.  This is not what I had in mind.  I'm attempting to fix the new kernel that was downloaded as part of a system update.  If I am just going to keep booting into the old kernel version, it would be pointless to get updates.

---

### Post by guitarMan666 on 2010-07-01
I have never experienced the problem, however the prudent courses of action would be to roll back to the old kernel and upgrade your operating system to the latest release version. If your problem persists, or you cannot upgrade for whatever reason, then a fresh install, backing up all of the directories beginning with "." in your home folder(s) to preserve the settings is required.

This happens when the bootloader cannot properly read the filesystem.  The easiest solution has been described.

---

