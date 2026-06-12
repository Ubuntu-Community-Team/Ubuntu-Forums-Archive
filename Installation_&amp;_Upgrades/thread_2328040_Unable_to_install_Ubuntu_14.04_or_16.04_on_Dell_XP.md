---
title: "Unable to install Ubuntu 14.04 or 16.04 on Dell XPS 8900 in any fashion"
date: 2016-06-16
forum: Installation &amp; Upgrades
---

### Post by daniel.stolzberg on 2016-06-16
Hello Ubuntu Community,

I have been using Ubuntu for a few years now and have had a wonderful experience.

Recently, my office purchased a new computer based on my recommendation that would have Ubuntu 16.04 desktop installed.  I chose the Dell XPS 8900 because I had another XPS 8900 on which I easily installed a dual boot with Win 10 and Ubuntu 16.04 with no issues.  I did not want to build a custom rig and it is easy for us to buy from Dell.  Moving on...

I have been trying for two weeks to install Ubuntu and have been failing at every turn!  I followed instructions online: Disabled fast startup in Windows, made plenty of space (500 GB) for Ubuntu OS, booted into Ubuntu Live on USB stick (created using Penguin Pendrive utility).  Installation fails every time saying that my computer has 0 bytes remaining.  

I abandoned the dual boot option after much struggle and formated the hard disk.  I chose to erase the disk and do a fresh install Ubuntu 16.04 and I still get the same error!  I tried manually making partitions for swap space (16 GB), / (30GB), and /home (~1.8TB).... no luck, same error.

This was done off of a 4GB thumbdrive that I had used previously to install Ubuntu 16.04 with success.  I also tried downloading Ubuntu desktop from the website again and using another 16 GB USB thumbdrive... same errors.

I have also tried using 'legacy' boot mode with no luck.  I also tried Ubuntu 14.04 with the same result.  This makes me think it is my computer and not Ubuntu.

I 'examined' the drive when I received this error and it seems like the kern.log and syslog files are massive (each > 4 GB).  I'm not sure why this is happening or if it's related to the installation issue.  Again, this is a complete new system with no customization.  This should be straightforward.

I have no idea how to solve this!  Does anyone have any suggestions on how to solve this?

Thank you in advance,
Dan

---

### Post by ubfan1 on 2016-06-16
Does the machine use in Intel 67xx Skylake cpu?  Is the disk an nvme type disk?  Those have numerous problems. 16.04 a better bet on install. Below a random collection of boot parameters to try:

Skylake needs this (15.04...):
i915.preliminary_hw_support=1
noveau.blacklist=1 edd=on nolapic pcie_aspm=force tpm_tis.interrupts=0 
Maybe
intel_idle.max_cstate=1 nouveau.modeset=0

To slow SSDs to allow them to boot:
libata.force=noncq

---

### Post by eugandara on 2016-06-17
Similar problem here. From nothing i can't install the Ubuntu from usb drive. And yes the usb is good because i tried in other computers. ps. i didn't change any hardware. One week ago i could boot.

[http://ubuntuforums.org/showthread.php?t=2327982](http://ubuntuforums.org/showthread.php?t=2327982)

---

### Post by moosee3332 on 2016-07-28
Hi everyone,
  
     I just successfully installed Ubuntu 16.04 on my new Dell XPS 8900.  Starting from a bootable USB with 16.04, you can pretty follow this thread: [https://ubuntuforums.org/showthread.php?t=2303880&highlight=Dell+XPS+8900](https://ubuntuforums.org/showthread.php?t=2303880&highlight=Dell+XPS+8900) .  

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
NOTES FOR BEGINNERS

    If you are new to Ubuntu or are not too familiar with using the command line, I've provided some additional notes to help you along.  I'm assuming you know how to boot from the USB drive.  If not, please see [http://pcsupport.about.com/od/fixtheproblem/ss/bootorderchange.htm#step1](http://pcsupport.about.com/od/fixtheproblem/ss/bootorderchange.htm#step1) .

    From my experience with Ubuntu it can be a bit annoying to install (e.g. it is not unusual to find yourself constantly rebooting your system, finding different results each time).  Once Ubuntu is up and running though, it is super duper stable and you realize it was worth the struggle (plus you'll learn something new, which is always nice).  Sometimes when you boot Ubuntu from the USB drive you are taken nicely to a menu which reads (1) Try Ubuntu (2) Install (3) etc. .  Ubuntu was not so kind to me.  Instead, Ubuntu tried immediately to take me to the installer (which in a few clicks turned into a dead one) or Ubuntu decided to spit a bunch of jibberish out.  If you look closely at the jibberish, perhaps you'll notice the words "PCIe" and "error" flash up?  This error means Ubuntu 16.04 can't handle your (NVIDIA) video card -- generally, Ubuntu has a tough time with NVIDA video cards.  The culprit, as I understand it, is a program that manages the power use of the video card slots (it's called  Active-State Power Management or aspm for short).  So the strategy then is to turn off aspm.

     On my installs, the initial menu (i.e. (1) Try Ubuntu (2) Install (3) etc ) wouldn't show up, so I forced it to appear by pressing "Enter" when screen goes purple.  If you press it too many times you'll find yourself in the keyboard layout menu, just press Esc to get back to the menu.

     Ok, now for the tricky part.  We're going to install Ubuntu 16.04 by manually turning off aspm.  In the menu, highlight (2) Install and press F6 (I think its "More options" or something).  A menu with lots of options appears and, at the same time, a long command line appears.  Exit the menu by pressing Esc.  Notice that by pressing the left arrow key a cursor appears moving you through that long command.  Situate the cursor right after "quiet splash", add a space, and then add "pcie_aspm=off" (without the quotation marks).  There should also be a few hyphens to the right of what you entered, leave them there.  Hit Enter, wait for a while (~ 10 mins), then the installer should pop up.  Follow these instructions: [http://linux.about.com/od/LinuxNewbieDesktopGuide/ss/The-Ultimate-Windows-7-And-Ubuntu-Linux-Dual-Boot-Guide.htm#step9](http://linux.about.com/od/LinuxNewbieDesktopGuide/ss/The-Ultimate-Windows-7-And-Ubuntu-Linux-Dual-Boot-Guide.htm#step9) .

    The installation should go smoothly and Ubuntu will ask you to reboot, so do so.  When I clicked reboot the jibberish popped back up again, so I forced the computer to shut down, then turned it on again.  Which ever way you do it, make sure to take the USB drive out.  

    Ubuntu will now enter a purple 'grub' screen.  Basically, Ubuntu still doesn't remember that it needs to turn the aspm off, so we'll need to tell Ubuntu to turn it off again.  In the 'grub' menu highlight 'Ubuntu Advanced options' using the down arrow key and press Enter.  Place the selector over option 1 and press the key E to edit the grub boot command. On the third line just after quiet splash, add a space and the string pcie_aspm=off and press F10 to continue the boot. This will allow Ubuntu to boot properly.  This does work, but you'll have to do this trick every time you run Ubuntu...that's super lame.  Instead, let's just make Ubuntu remember to always add pcie_aspm=off after quick splash.

 Once inside Ubuntu open up the terminal (Ctrl+Alt+T).  Edit the grub file by issuing the command: sudo pico /etc/default/grub .  Enter your password and that should take you the editor.  Edit the line that starts GRUB_CMDLINE_LINUX_DEFAULT, so it reads GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=off"   (in this case, leave the quotation marks in).  Save by issuing Ctrl+O, then exit by issuing Ctrl+X.  FInalize the changes in the system by entering the command into the terminal: sudo update-grub .

Everything should work now!

---

