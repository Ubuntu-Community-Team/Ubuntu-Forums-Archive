---
title: "No wifi on 12.04 upgrade; other problems with eee netbook"
date: 2012-06-30
forum: Installation &amp; Upgrades
---

### Post by pbewig on 2012-06-30
I have an Asus Eee PC 1000H Netbook. It has been running Ubuntu 10.04, and yesterday I upgraded it to Ubuntu 12.04 using a bootable USB drive. I had much trouble with the upgrade. I could not use the option to upgrade directly from 10.04 to 12.04 and had to make a clean install. The partition manager could not handle the existing partition and I had to use cfdisk to write a usable partition table (neither the graphical partition tool in the installer nor fdisk was able to write a usable partition table). With that done, I was able to complete the install, upgrade all packages, and begin loading software. I was working at my office, and wifi worked fine.

Last night when I got home wifi failed to work. I noticed that wifi was disabled in the BIOS, and enabled it in setup before the computer booted. But still there is no wifi. Clicking on the network tool in system settings shows only the possibility of a wired network, and tells me that none is available, which is correct, as I have no network cable connected to the machine.

1) How do I get wifi working?

2) How do I get rid of this new interface? I was perfectly happy with the old one. Reading an upgrade guide I installed the old gnome-panel, but how do I connect my login identity to it?

3) I used to have a package called eee-control that let me manage the netbook. Now I can't find it. How do I get it?

Thanks for your help,

Phil

---

### Post by pbewig on 2012-06-30
I've had no replies. Can anyone help?

Many thanks,

Phil

---

### Post by Rex Bouwense on 2012-06-30
Hi Phil.  I too have an ASUS EeePC 1000h on which I am currently running Lubuntu 12.04.  I have run Ubuntu from 9.04 thru 10.04 and then dual booted with Lubuntu (11.04 and 11.10).  I tried the Unity desktop and didn't like it.  Of couse the ASUS ,as you know, can handle it.
1.  I found that WIFI works out of the box but some folks have had to reinstall the network manager to get it working.  Have you done that?  Also ensure that the Wireless is enabled in the network manager.  Does your network manager see your network?
2.  If you want a different desktop you can install the Lubuntu desktop (LXDE) or Xubuntu desktop (XFCE).  They both should be in the repository.
3.  When you installed over your old OS you lost the EeePC control package.  You will have to reinstall it if you want it.  I have never felt a need for it.
By the way it is customary to wait 24 hours before bumping your thread.  As you may or may not know.  Everyone on these forums is a volunteer and most have jobs to put food on the table.  They do this because they love Linux and want to help others.

---

### Post by pbewig on 2012-07-02
I am still unable to get wifi working. But I have more information that may help.

Wifi was working previously. I am certain of that.

I notice that now when I boot the computer that the wireless network adapter is disabled in the BIOS Setup screen.

If I re-enable the wireless network adapter and boot from the USB startup system, wireless is enabled and I can make a connection.

But if I shutdown and then reboot from the internal hard drive, I cannot make a wireless connection, and wireless is disabled in the BIOS.

Obviously what has happened is that as I was installing packages, something either uninstalled the wireless networking package or installed an incompatible upgrade. I don't know what package that was.

The question now is how to recover. How can I install the wireless network package? I don't know what to install, and remember that I can only make a connection when booted from the USB stick.

Can I somehow boot from the internal hard drive and use the USB stick as a repository from which to fetch the wireless network package?

Or is there some other way to do what I need?

Many thanks,

Phil

---

### Post by Rex Bouwense on 2012-07-03
Not exactly sure what you are doing.  You can boot from your hard drive but the WIFI is disabled in the BIOS.  Can't you simply enable it, save the changes, and then boot?
Is this the only OS on your disk?

When you choose run from your menu and type in network manager, what shows up?

---

### Post by pbewig on 2012-07-03
This is the only OS on the disk.

I can enable Wireless LAN in the BIOS, save settings and boot. That works fine. But then when I choose Network from the System Settings menu, it only offers me a wired network (which of course doesn't exist) but no wireless network. I can only see the option for a wireless network when booting from the USB stick.

So how do I get the wireless network to work when booting from the internal hard drive?

---

