---
title: "Yet another dual-boot/GRUB issue"
date: 2006-03-30
forum: Installation &amp; Upgrades
---

### Post by Roger Mudd on 2006-03-30
Hello All,

I am having some issues with a dual-boot XP/Ubuntu 5.10 machine and I'm in need of some assistance.
XP is the native OS. I am attempting to install Ubuntu within a 20GB partition (sda3) located on a 160GB SATA drive which also houses my XP installation.
I was able to format a root partition as well as a swap partition using the Ubuntu install disc. The initial stages of the install apparently went well (including GRUB setup) and Ubuntu asked me to reboot. After removing the install disc and rebooting, however, I cannot even get to GRUB. My machine simply runs through the traditional diagnostics and stops before calling GRUB.
I've done a bit of reading and have checked into editing /boot/grub/menu.lst. I attempted to do this last night using a Knoppix Live CD but was unable to get root access to actually alter the file. I was able to open it, just couldn't edit it and I wasn't confident that I would enter the right settings if I attempted.
I also looked into rescuing GRUB using the the Ubuntu install disc, however, I have a Bluetooth keyboard and mouse and it won't connect (they worked during the initial install and functions perfectly when running the Knoppix Live CD).
So there you have it. As you can see, I'm stuck halfway through the installation process and have neither a functional Windows or Linux system. I could probably just insert the XP install disc and do a "fixmbr," but I wanted to check here first and see if I could find a solution.

Thanks for taking the time to read this and I appreciate any advice you can offer.

Roger

---

### Post by nerderello on 2006-04-02
see if this guys suggestions work :-

[http://www.ubuntuforums.org/showthread.php?t=76652](http://www.ubuntuforums.org/showthread.php?t=76652)

Nerderello

---

### Post by mrhelpman on 2006-04-02
I had a similar thing happen when I installed for the first time. In my case Grub just gave an error 2 on the screen and nothing else happened. I was on the verge of running fixmbr but in the end I just ran the ubunbtu installation again. The second time I ran through the installation it complained about the root volume not being assigned, fixed the problem and then completed sucessfully.

John T

---

