---
title: "Moving from Sid to Edgy?"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by horst on 2006-10-15
Hi,

I am an long time Debian Sid user (using the same but of course updated installation from 2001). I have used GNOME for an amount of time and switched to KDE about a year ago. I use the packages from the Debian repository and the debian-mutlimedia repository for things like mplayer an ffmpeg.

I still use lilo and do compile the kernel. I also have a Nvidia graphic card and use the installer that bypassed Debian's package management. I get annoyed by the following procedure: download kernel, compile kernel, install kernel, update lilo.conf, reboot, reinstall nvidia drives. And I also get annoyed be Debian licence policy in case of cdrecord and Mozilla apps.

Though my knowledge in Linux, I want a Linux installtion that works out of the box and is not that old. I guess that the (K)Ubuntu way with the 6 month release cycle and improvements for laptops and so on is a rather good way.

But before I make my descision for the released Edgy (I would choose the 32bit-Kubunto DVD) I have some questions:

1. The hardware installation seems to be very good during the installtion. But what is to do if you plug in a webcam after some month? Is there a kind of hardware installation assistant?

2. I have a AMD K8 CPU running in 32bit mode. Which kernel image is automatically choosen or which one is the most appropriate to be installed manually: *-K8 (real one but maybe for 64bit?), *-K7 (AMD and 32bit), *-686 (though for Intel CPUs but the also have the SSE2 commands).

3. How easy is the installtion/upgrade of the propriate Nvidia-drivers: Is updating nvidia-glx sufficent since it will also update the linux-restricted-modules?

4. What is the defaul bootmanager? Lilo or Grub? Are Lilo or Grub automatically updated if a new kernel from the repository is installed?

Thanks in advance.

---

### Post by taurus on 2006-10-15
1.  If it works once, it would work a year later.

2.  If you want to use the 32bit, then you can either use the k7 or i686 kernel.  The default from installation gives you a i386 so upgrade the kernel as soon as you finish installing.

3.  It takes only one command and you don't even have to shutdown X before you install nVidia driver for your graphic card.  

4.  Ubuntu uses GRUB although you can pick LILO if you wish...  And each time you upgrade your kernel by using aptitude, it would automatically update your /boot/grub/menu.lst.

5.  Wait, there is no 5...

     If you like KDE, then Kubuntu is what you want.  Edgy will be out on October 26 so you can play around with Dapper right now to get used to things in Ubuntu and when Edgy comes out, do a fresh install and you have to latest version of Ubuntu.

---

### Post by Kateikyoushi on 2006-10-15
1. I plugged in my webcam and no assistant started so I guess you have to find assitance here on the forum. ^^;

2. As far as I know edgy uses i686 kernels, it is running i686 on my K7 as well.

3. I didn't bother with the nvidia drivers yet.

4. It is using grub and the new entries are automagically created during updates.

---

### Post by lamego on 2006-10-15
> 1. The hardware installation seems to be very good during the installtion. But what is to do if you plug in a webcam after some month? Is there a kind of hardware installation assistant?

If the webcam you are plugin is supported and recognized by the kernel you will be using it will just be automatically configured, you just need to configure whatever program you use with it.

> 2. I have a AMD K8 CPU running in 32bit mode. Which kernel image is automatically choosen or which one is the most appropriate to be installed manually: *-K8 (real one but maybe for 64bit?), *-K7 (AMD and 32bit), *-686 (though for Intel CPUs but the also have the SSE2 commands).

You best match is linux-image-k7

> 3. How easy is the installtion/upgrade of the propriate Nvidia-drivers: Is updating nvidia-glx sufficent since it will also update the linux-restricted-modules?

If you use the repository based drivers, you don't need to care about it, you will just need to click the upgrade button when there are updates available.

> 4. What is the defaul bootmanager? Lilo or Grub? Are Lilo or Grub automatically updated if a new kernel from the repository is installed?

The default is grub, grub menu doest get updated at each kernel install.

---

