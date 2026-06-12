---
title: "My experience in upgrading Two Laptops to 17.10.1"
date: 2018-02-07
forum: Installation &amp; Upgrades
---

### Post by irv on 2018-02-07
My experience in upgrading Two Laptops.
I am posting this to maybe help others. I ran into a few things that would have helped me if I knew them ahead of time.
The first laptop, which was a Dell 3000 11" 2 in 1, when well except for the fact that I found I had trouble installing some of my programs and some didn't even run. After doing some research, I found the problem was Wayland, or maybe I should say the programs that didn't work with it. After going back to Xorg, they worked just fine.
On the second laptop which was an Asus Q500, with an i7 processor, 8 gigs of RAM and a 250 gig SSD running Ubuntu 17.04 and Windows 10. This one gave me a headache. 
First I made a 17.10.1 boot USB to upgrade the 17.04 because it was not supported any longer. I tried to install in UEFI because I had Windows on this laptop. For some reason, it would not install the grub at the end of the install. I think I tried the install about six times at that point. The last time I tried, I deleted all the partitions formatted the drive, and it would still not install the grub. 
I booted with a super grub boot USB, and I could get into the OS. I tried running a Boot Repair and had some issues with that. After hours of trying everything, I could think of I ended up installing an LTS version of Ubuntu. 16.04 once I had it installed I follow these instructions.
> Steps to Upgrade from 16.04 LTS to 17.10
As upgrading Ubuntu from 17.04 to 17.10, upgrading from 16.04 to 17.10 is as easy as any other regular package, but it involves a couple of extra steps, but it’s nothing fearsome like typing assembly codes with just the notepad. As usual make sure the system is up-to-date by using both apt-get update, and apt-get dist-upgrade. The purpose of the dist-upgrade is to make sure there won’t be any conflicts among packages, as it intelligently handles them, then Ubuntu update-manager-core package has to be installed, which is used to upgrade the core Ubuntu files, meaning the operating system.

Once the package is installed, configure the release upgrade file to make sure Ubuntu is upgraded to the next successive version. It provides one single parameter name which is Prompt=<option>, and 3 options; never, normal, and lts. Never option is to ignore the upgrade, it’s useful to make sure nobody performs the upgrade. Normal parameter value is to instruct do-release-upgrade to upgrade existing version of Ubuntu to the next successive version, for instance if the current version is 16.04, it upgrades Ubuntu itself to 17.04 instead of 17.10, but then again following 17.04 to 17.10 upgrade segment makes Ubuntu to upgrade to 17.10 from 17.04. Finally execute do-release-upgrade to actually perform the upgrade. While it’s being upgraded, follow the on screen instructions to continue the upgrade. After upgrade is completed, restart the computer with “shutdown –r now” command. Here r denotes the restart, and now denotes the immediate restart.

apt-get update
apt-get dist-upgrade
apt-get install update-manager-core
nano /etc/update-manager/release-upgrades
do-release-upgrade
shutdown -r now

Once I had 17.10.1 up and running, I installed all the programs I use. Again I ran into problems again. I found gparted and UNbootin were two that would not run. I started installing some of my gnome-shell extensions, and I ran into problems again. When I loaded EasyScreenCast, it locked up the OS. Seeing it did boot after this I tried fixing it by booting into recovery mode and trying to fix it at a shell prompt. I ended up fixing it by booting the live USB and deleting the directory in /home/.local/share/gnome-shell/extensions/EasyScreenCast@iacopodeenose. And all it files. I had to change the read-only on the directory to delete them.
After all this, I found out that all I would have to do was to boot in Xorg and not Wayland. I was as easy as doing this. At the login screen, I clicked on "not listed" even though my name was the only one in the list. I then just put in my login name and click on the little gear below my name and selected Xorg and not the Wayland server. Using Xorg fixed all my problems with programs that would not run. I reinstalled the EasyScreenCast, and it worked as well.
I believe this was the most extensive upgrade I ever did. Over 15 hours.
I am not sure what the problem was with the grub-install, so I filed a bug report. All I know is I could not get it to install even after deleting the entire SSD and starting fresh. The only thing I could think of was the problem with the installer. Why would 16.04 work the first time and 17.10.1 not?
I hope this post will help others who are trying to install 17.10.1. Hopefully, 18.04 will go much smoother. 

Here are the links I followed.
[https://linuxhint.com/upgrade-ubuntu-17-10-from-17-04-or-16-04/]("https://linuxhint.com/upgrade-ubuntu-17-10-from-17-04-or-16-04/")
[https://itsfoss.com/switch-xorg-wayland/]("https://itsfoss.com/switch-xorg-wayland/")

---

### Post by TheFu on 2018-02-07
18.04 will default to using Xorg/X11.

---

### Post by irv on 2018-02-07
> **TheFu said:**
> 18.04 will default to using Xorg/X11.

This is good to know.

---

