---
title: "Ubuntu 10.10 Boot Stops"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by rinishak on 2010-10-13
Hello,

I've just upgraded to Ubuntu Maverick 10.10 yesterday from Lucid 10.04. After the completion of the upgrade, I rebooted the machine to login to the desktop.

After selecting the new version from the GRUB menu, the screen goes to the usual black screen where it says, "Starting...".

After a while, the plymouth purple boot screen flashes for a split second, as if it failed to initialized, and it reverts back to the black screen. Then, a **ttyl prompt** appears and the boot just stops there.

If I press Ctrl+Alt+F7, I see another black screen, with text showing the progress of the startup, where it usually ends (but not all the time) after Starting Winbind, or something along those lines.

I've also tried to load the other kernel versions from the GRUB menu, but the booting stops as well, all **without any error messages**. I'd really like to get this fixed as soon as possible.

Before this, I have not had boot problems with 10.04 and everything has worked well until now. Any help would be greatly appreciated. Thanks in advance.

---

### Post by mörgæs on 2010-10-13
There seems to be quite a few problems on this machine. Rather than trying to fix them, have you considered a fresh install?

---

### Post by rinishak on 2010-10-13
Well, I have. Although, I prefer not to do a fresh install because it would be a lot of work and time to backup my files, as well as re-install and reconfigure my applications and so on. I was hoping there was a fix for this.

---

### Post by rinishak on 2010-10-15
Hello, people. Just a little update. I decided to reformat and start from scratch like mörgæs suggested. After installation everything works fine, I think this problem is somehow related to Nvidia drivers for 10.10.

In fact, after installation, I used the Additional Drivers dialog to search for drivers for my Nvidia graphics card, but the search did not yield any results. I tried to download it manually using the command nvidia-xconfig to get the driver started, and rebooted the machine.

During boot, the same problem occured. So I assume the problem is caused by the absence of proper Nvidia drivers, which explains why I experienced the problem right after updating from 10.04 to 10.10. The system already had Nvidia config settings written into the /etc/X11/xorg.conf file.

So, I got rid of the problem by simply removing the /etc/X11/xorg.conf file. I'm not sure if this step is safe, though. I assumed it was for me, because before I ran nvidia-xconfig command, it was non-existent.

There are a couple of workarounds around the web. I followed a short guide and had mine run on the Mesa driver temporarily for 3D acceleration. Unfortunately, I've lost the link to the guide. So if any of you are in need of a workaround, you may need to do a bit of Googling. It's not perfect, but it works, at least until the Nvidia drivers kick in.

Hope this helps.

---

### Post by oldfred on 2010-10-15
Have you tried nomodeset.

On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Then I installed the hardware driver suggested for nvidia.

---

### Post by rinishak on 2010-10-18
> **oldfred said:**
> Have you tried nomodeset.

On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Then I installed the hardware driver suggested for nvidia.

This uses the original Nvidia drivers, I presume? Does it work for the 96 drivers? I've read a blog post that suggests something similar [here]("http://www.socialblogr.com/2010/10/how-to-install-nvidia-graphic-card-driver-on-ubuntu-10-10.html"). Is it the same?

Just curious, is this safe and stable? Because the last time I tried to install Nvidia drivers manually from the site, it screwed up my desktop.

---

### Post by aixroot on 2010-10-18
> **rinishak said:**
> Hello, people. Just a little update. I decided to reformat and start from scratch like mörgæs suggested. After installation everything works fine, I think this problem is somehow related to Nvidia drivers for 10.10.

In fact, after installation, I used the Additional Drivers dialog to search for drivers for my Nvidia graphics card, but the search did not yield any results. I tried to download it manually using the command nvidia-xconfig to get the driver started, and rebooted the machine.

During boot, the same problem occured. So I assume the problem is caused by the absence of proper Nvidia drivers, which explains why I experienced the problem right after updating from 10.04 to 10.10. The system already had Nvidia config settings written into the /etc/X11/xorg.conf file.

So, I got rid of the problem by simply removing the /etc/X11/xorg.conf file. I'm not sure if this step is safe, though. I assumed it was for me, because before I ran nvidia-xconfig command, it was non-existent.

There are a couple of workarounds around the web. I followed a short guide and had mine run on the Mesa driver temporarily for 3D acceleration. Unfortunately, I've lost the link to the guide. So if any of you are in need of a workaround, you may need to do a bit of Googling. It's not perfect, but it works, at least until the Nvidia drivers kick in.

Hope this helps.
I changed the driver name NVIDIA in NV in xorg.conf
 
That worked for one of my machines.
Netbook is still not working

---

### Post by oldfred on 2010-10-18
Way back (7.04 or 7.10) I installed the nvidia drivers from the nvidia site and had huge issues trying to get them to work. I ended up finding out I had to totally purge everything related to nvidia including some files it would not normally delete and install the Ubuntu version. Since then I have only installed the version supplied with/by Ubuntu and that has worked well for me. I originally had a 7600gs and now have 9600gt. When I changed from the 7600 to the 9600 I did not have to make any changes to my system, it just booted & ran.

For whatever reason some seem to have success with the version directly from Nvidia.

---

### Post by rinishak on 2010-10-20
I see, Alright then. Thanks, guys, for your help. I'll just give the drivers from the site a shot. Hopefully it works.

---

### Post by rinishak on 2010-10-24
Okay, I've tried the drivers off the site, but came unsuccessful. Instead, I found a better solution off another thread on this forum. It involves downgrading xorg to the old Lucid version. This is the **best** temporary fix I've found so far. Basically **downgrading xorg** allows you to install the old **Nvidia drivers for Lucid**.

[Here]("http://ubuntuforums.org/showpost.php?p=10005160&postcount=7")'s the link to the step-by-step post by **beew**. Credit to him for coming up with the solution.

You might notice that marking xserver-xorg for uninstallation will also mark ubuntu-desktop. Simply unmark ubuntu-desktop manually.

---

