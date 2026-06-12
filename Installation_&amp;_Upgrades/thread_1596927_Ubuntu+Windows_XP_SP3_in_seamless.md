---
title: "Ubuntu+Windows XP SP3 in seamless?"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by Kizamime on 2010-10-14
Here's my issue. I've got terrible hardware, and I'm running Windows 7. I really have gotten used to it, and I love it. But it doesn't run like it should my my rig. Specs:

Intel Celeron (D?) 2.4GHz
Integrated Intel 82865G Graphics
2Gb DDR RAM
40GB OS drive
20GB Storage drive

I'm really used to 7, but it just doesn't run right. So my theory was that, if I could install Ubuntu, I know it would run better. But what about compatibility? I figured I could just install Windows XP SP3 in a virtual machine, and put it in seamless mode. Would this work?

---

### Post by rjs987 on 2010-10-14
> **Kizamime said:**
> Here's my issue. I've got terrible hardware, and I'm running Windows 7. I really have gotten used to it, and I love it. But it doesn't run like it should my my rig. Specs:

Intel Celeron (D?) 2.4GHz
Integrated Intel 82865G Graphics
2Gb DDR RAM
40GB OS drive
20GB Storage drive

I'm really used to 7, but it just doesn't run right. So my theory was that, if I could install Ubuntu, I know it would run better. But what about compatibility? I figured I could just install Windows XP SP3 in a virtual machine, and put it in seamless mode. Would this work?

My work computer is running Kubuntu and I have Windows 7 running in a vbox vm in seamless mode all day everyday. No problems doing that. It will run as well or better than a native install of Windows. I also have a Windows XP sp3 vm running in seamless mode on my home computer with Kubuntu host OS. No problems there either. Windows XP definitely runs better as a vm on a Linux OS.The seamless mode puts the task bar just on top of any Ubuntu/Kubuntu task bar you have at the bottom (or top if you configure it that way). Only the task bar shows and not the desktop unless you click on the Show Desktop button. One of the things I do for both my vm desktops is to add the Desktop toolbar on the task bar. That way any icons on the desktop will be available without having to take it out of seamless mode or clicking on the Show Desktop button. It makes your desktop a popup menu that you can navigate just like the Ubuntu menus. Been running this way on both computers for almost 2 years now.

My first test of this set up was on an old HP laptop (zt1230) with a 1.1GHz Celeron CPU and 512MB RAM and a 20GB hard disk. Windows XP ran so much better as a vm in Linux than the original install on the laptop. Almost as if I doubled the RAM and CPU speed!

Make sure you set the disk size to be enough for the Windows vm and make it dynamic. Otherwise your setup looks fine for running this way. Just be careful about your space usage and chose carefully on which disk you put the vm.

---

