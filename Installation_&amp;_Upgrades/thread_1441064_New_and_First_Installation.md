---
title: "New and First Installation"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by aqualion on 2010-03-28
Installed Ubuntu 9.10 on a two hard drive machine (dual boot WinXP/Ubuntu) using Wubi (Installing Ubuntu from within Windows.)  When I boot and select Ubuntu at the boot manager, I am confronted with a command line which I don't want and don't know what to do with.  The heading is "GNU GRUB version 1.97~beta4" and the command line is "sh:grub>".  I would like to be able to boot into a username/password screen followed by a desktop.  I've searched Ubuntu documentation but haven't found an answer as to what to do.  Suggestions?

---

### Post by debianmike on 2010-03-28
If I read that right, your grub boot loader can't find your Ubuntu install...i suggest you wubi install it again, though I am no expert on that kind of setup.

You could probably fix it with grub commands if you can wait for a better answer than mine.

---

### Post by Mark Phelps on 2010-03-28
Main suggestion is that since you are running a 2-drive system, you would do much better with each OS on its own drive.  You could then disconnect the Windows drive, install Ubuntu to the other drive, reconnect the Ubuntu drive, boot from it, and once in Ubuntu, open a terminal and enter "sudo update-grub".  That will create a GRUB menu containing an entry for your MS Window OS such that the next time you boot, you will be able to select either OS.

That's a lot less work than messing around trying to get Wubi to work.

---

### Post by aqualion on 2010-03-28
> **Mark Phelps said:**
> Main suggestion is that since you are running a 2-drive system, you would do much better with each OS on its own drive.  You could then disconnect the Windows drive, install Ubuntu to the other drive, reconnect the Ubuntu drive, boot from it, and once in Ubuntu, open a terminal and enter "sudo update-grub".

I did install Ubuntu to its own drive (F:) using Wubi but I don't know enough about disconnecting/reconnecting drives or about terminals that I would want to try a procedure like that.  If the installation program in Ubuntu can't install the OS itself, I won't be able to install Ubuntu with my limited computer knowledge.  May I please ask for simpler suggestions?  Also, I noticed that the installer did not ask me to format the drive prior to installing the OS.  Isn't the correct file format for linux ext3 (wikipedia, I think) and what do I need to do to make sure that is the file format that I have?  Lastly, Wubi had an option to select "Installation Size".  The drive I installed to was over 70GB but the maximum size I could select using this option was 30GB.  I could not find any documentation explaining the "Installation Size" option in Wubi.  Thank you for helping.

---

### Post by presence1960 on 2010-03-28
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

P.S. Even though you are unfamiliar with terminal do not fear it. People in here will walk you through it. Terminal is a powerful tool and because it involves commands is a lot simpler than saying click on this, at this screen do this, then do that, especially since everyone's GUI may not be exactly the same. But the terminal commands are the same regardless of your GUI.

---

### Post by aqualion on 2010-03-30
?

---

### Post by presence1960 on 2010-03-31
> **aqualion said:**
> ?

> I did install Ubuntu to its own drive (F using Wubi but I don't know enough about disconnecting/reconnecting drives or **_about terminals_** that I would want to try a procedure like that.

Did you not say this? That is why I posted what I did about terminal.

---

### Post by ern on 2010-03-31
Aqualion: I'm having exactly the same problem as you. I'm installing Ubuntu 10.4 beta 64-bit from Windows 7 64-bit, using Wubi from a Daemon Tools mounted Ubuntu-ISO.
Have you found an answer yet?

---

### Post by theozzlives on 2010-03-31
Don't bother with WUBI Beta 1 don't work off the live CD. Just backup your second HD and boot off the live CD. During install, choose "whole disk" for sdb. Uninstall Ubuntu from "programs and features" first. you should be fine after the install is done.

---

### Post by MCVenom on 2010-03-31
Disconnecting drives? No. Nononono. :P

Assuming you burned an Ubuntu LiveCD, (if you didn't and you don't know how, just ask), go ahead and boot from that. You can choose 'try without installing', which will deposit you onto the Ubuntu desktop (you can run the installer from there), or choose the 'Install Ubuntu' option, which will deposit you directly into the installer. Either way, get into the installer and continue until it asks you toset up space for Ubuntu; there should be a drop down box so you can choose the hard drive you want to install it on. If you already have files or other data you want to keep on there, make sure you choose the 'Install sided by side option'. Then follow the rest of the installer, install Ubuntu, and then reboot, you should have a full-featured dual boot :D

Also, about the terminal, what was said is right; all that using the terminal will usually ever require of you is that you copy and paste a command, and watch your problems disappear. It is the most universal and versatile tool in Linux, don't be afraid of it ;)

Windows cmd.exe = :|
Linux/Ubuntu Bash = ;)

---

### Post by aqualion on 2010-04-02
> **BlackOtaku said:**
> Disconnecting drives? No. Nononono. :P
Assuming you burned an Ubuntu LiveCD, 

1. Two hard drives, XP on one, trying to put linux on the second
2. Yes, burned the Ubuntu liveCD
3. Gave up on WUBI (or whatever it was.)
4. Trying to install Ubuntu on second disk and confronted with mounting points and swap files.  Didn't have to do that for WinXP and glad I didn't because I don't know about mounting points and can't find them explained in the documentation so I go to wikipedia but that information isn't specific enough either.  As to swap files, WinXP takes care of that (called virtual memory I believe.)  So I ask on the forums about ext3 and about installation size options: silence.  There has to be a better way for someone sick of Windows to change OSes.  To my eternal shame, I used to be an electronic technician but if I don't have the information to do an installation, it doesn't matter if I'm the Pope because not even divine intervention will allow me to guess what I'm supposed to do with a concept that isn't explained sufficiently for me to do an installation.  Where to mount?  What to mount?  Where to put a swap file?  What size?  Why not let the OS take care of it like Windows?  Not interested in opening the computer case to play with the drives.  Not interested in anything but a graphical user interface that explains the options.  I don't want to be a mechanic anymore.  I want to get in the car and drive.  Period.  Is there a distribution that does all the technical stuff that I don't want to do and thoroughly explains what I do want to do?  I hope so because I tried Windows 7 and I'm not going to pay $200 for that stuff and I'm not going to spend weeks trying to install an OS.  Not to upset anyone but Ubuntu is not ready for prime time.  Thanks to those that responded but I'm going to try a different distribution.

---

