---
title: "GRUB issues in dual boot Windows/10.04 systems"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by thenudehamster on 2010-11-15
To begin with, I'm not a core level expert, just a halfway competent user; I *like* Linux as an OS and anything that reduces my dependence on Micro$oft can't be all bad...

I currently have three systems dual-booting to Windows or Ubuntu 10.04; they are a Packard Bell desktop under Vista, an HP laptop under Vista, and a homebrew desktop under XP-Pro. The two Vista machines were initially set up with 9.04 and upgraded using recommended updates from the Update Manager. The XP machine was a direct install of 10.04.

I have three small (to me) issues, all with the boot-up routines.

Problem 1: On all three machines, when the GRUB screen appears with the OS options, there is a long list of every Linux kernel version (and its recovery option) that's ever been installed, as well as the version of Windows available. It's unnecessary and I'd like to reduce it to one, the latest version.

Problem 2: The two Vista machines have the infamous 'recovery partition', and GRUB identifies this partition and the 'live' Windows partition in the wrong order. I can live with it - I'm used to it by now - but it is likely to cause problems as I want to loan one machine to my non-techie sister while I have the joy of trying to repair her Windows box, and I can see her unintentionally 'restoring' Windows and destroying not only her data but mine and the Linux partition also. 

Problem 3: On the XP machine I installed Ubuntu using the Windows Installer package just to see how it was different; now when it boots up I get the GRUB loader screen, then if I select the Windows XP option, I get dropped into the Windows OS option screen with the choice of XP or Linux to load - which is great if you are prone to making errors in selection, but...

So. How do I (can I, even?) change the GRUB configuration file so that it only gives me the option of the current update of Ubuntu, or Windows - and how do I persuade it to display the Windows options in the correct order?

Sorry if this is a little long, but it's all related, and I believe in giving as much information as possible.
Thanks in advance.

---

### Post by Quackers on 2010-11-15
This will be a good place for you to start :-)

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by thenudehamster on 2010-11-16
Thank you, quackers - or as they would say in Nottingham, "Ta, me duck,"! 
I did try searching before I made the post, but it's difficult sometimes to know just what parameters to insert into the engine; the ones I tried either brought up thousands of results (or it looked like it) or none. Sometimes the human search routines are far more efficient than the silicon ones.

I have had a look through the tweaks and modifications in the thread, and it does look as if I will be able to achieve most of what I want to do. I'm not, as I have said, a 'core level' geek (for that I'd need my late wife, a code genius) but I have printed the main post so that I have a hard copy to hand when I start playing with code, just in case. All being well, I'll get back to you guys with a successful outcome - just don't expect it to happen too quickly...

---

### Post by Quackers on 2010-11-16
No problem. Just take your time and above all check that you are in the file you should be! It is always good practise to make a backup of any file before you make changes, so that things can be returned to how they were previously.
(Copy/paste will do just fine :-) )

---

### Post by oldfred on 2010-11-16
the link that quackers provided to drs305 is my main reference also. 
But this is what I did, which is a little more brute force in copying the windows entries to 40_custom and editing rather than modifying the script.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

Once you confirm new entries work you can stop the old entries from appearing. If you ever what to update you can turn it back on.
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

