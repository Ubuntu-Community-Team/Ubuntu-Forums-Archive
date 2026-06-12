---
title: "How to install Ubuntu &amp; Xubuntu on same hard drive?"
date: 2013-06-07
forum: Installation &amp; Upgrades
---

### Post by gigenieks on 2013-06-07
Hello!

Few hours ago I successfully installed Ubuntu 13.04. Also want to install Xubuntu 13.04.
HDD's total size - 120GB; 2GB are used for swap, 25GB for Ubuntu (/), ~25GB are unallocated space, rest is for storing files (music, movies etc).

So what is correct way to install Xubuntu now? Just use all unallocated space for root partition (/), select it and start installation?

---

### Post by vadimkolchev on 2013-06-07
Actually you don't need to install xubuntu. Xubuntu uses the same repositories as ubuntu does, the difference is only in the fact it uses xfce desktop instead of ubuntu's unity desktop. Why not just install xfce within your existing ubuntu installation and be able to boot to xfce or to unity when log in?

---

### Post by ajgreeny on 2013-06-07
> **vadimkolchev said:**
> Actually you don't need to install xubuntu. Xubuntu uses the same repositories as ubuntu does, the difference is only in the fact it uses xfce desktop instead of ubuntu's unity desktop. Why not just install xfce within your existing ubuntu installation and be able to boot to xfce or to unity when log in?
+1
You can either install just the **xfce4** package for the DE alone, or can choose to add **xubuntu-desktop** package which will also bring in a lot of applications meaning you have duplicate apps, such as **gedit** and **leafpad** (or is it now **mousepad**?) as text editors, and both **thunar** and **nautilus** as file managers, along with many others.  This does not slow down the system as it might in Windows, it just takes space, but it can make your menus a bit cluttered.

Your choice; enjoy it!

---

### Post by vadimkolchev on 2013-06-07
If you still for some reason want to install it separately from Ubuntu, start Xubuntu installation, partition your spare space, make it a root partition for Xubuntu, choose swap to be the same partition as in Ubuntu and just make your /home partition show up under /etc/fstab in Xubuntu. To achieve this, choose this partition as /home when installing Xubuntu, but make sure to check and double check that you will not format it. During installation it should detect Ubuntu and place it into your new grub.cfg file. You will have to install grub once again during installation and overwrite Ubuntu one, but it should work.

---

### Post by ajgreeny on 2013-06-09
And again, if you install separately, you can use disk space more economically by simply making links from the main data folders in the /home of the first OS to those same data folders in /home of the second.  I used to do that all the time when I was testing newer versions of ubuntu but kept my main OS of Lucid 10.04.  At one point I had 5 separate OSs on the one machine all using the same data files in the /home of Lucid.

---

### Post by gigenieks on 2013-06-09
Update: Change of plans!

I decided there is no need for Xubuntu. [By reading this article]("http://lifehacker.com/5680453/build-a-killer-customized-arch-linux-installation-and-learn-all-about-linux-in-the-process") I decided to try ArchLinux. Why?

[LIST=1]
[*]For educational purposes
[*]> 
Since you start off with a minimal install and build up from there, you won't have any unnecessary packages bloating up your system.
You have complete control over everything that goes into your setup, and you can make it
as small and minimalistic or as big and powerful as you want&#8212;you essentially build your own, fast, stable, super-customized Linux distro from the ground up.
And who wouldn't love that?

[/LIST]

First step I want to achieve is preparation. Meaning, I want the *safest* way to start experimenting. It's probably a very bad idea to install Arch on the same HDD on which resides Ubuntu 13.04 and it's GRUB, right??
Well, I have 3 hard drives accessible for me:
[LIST]
[*]80 GB (Win8)
[*]120 GB (Ubuntu + GRUB)
[*]250 GB (no OS, just data)
[/LIST]
So the smartest way would be to back up all data from 250 GB HDD, use gParted LiveUSB to partion it and then install Arch, right?

I'm not sure, but when I do install Arch and it's bootloader it'll replace Ubuntu's bootloader, right? So there is possibility I mess something up and I can't login in Ubuntu?

Anyway, let's assume Arch is not usable yet, Ubuntu doesn't load up, still removing (or changing boot priority in BIOS) I would be save to at least load Win8, right?

I just want to start this project with some good precautionary to do's. And I need at least one OS functional at all times.

Please, any comments, recommendations before I start?

---

### Post by oldfred on 2013-06-09
I have not installed Arch. But if at all possible during install you want to install grub2's boot loader to the MBR of the ARch drive. With Ubuntu grub2 normally defaults to sda with any of the auto install options, you have to use manual install or Something Else to have an option on where to install grub2.

       [https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

---

