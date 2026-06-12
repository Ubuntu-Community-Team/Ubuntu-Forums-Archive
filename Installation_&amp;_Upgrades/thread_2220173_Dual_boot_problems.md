---
title: "Dual boot problems"
date: 2014-04-27
forum: Installation &amp; Upgrades
---

### Post by dylan18 on 2014-04-27
I have Kubuntu 14.04 and Windows 7 dual booting on a 24GB SSD and a 750GB HDD with Linux installed on the 24gig and Windows installed on the 750gig drive. I'm going to buy another mSATA SSD and replace my 24gig drive with a 240. I want to just re-install both Linux and Windows from scratch after I upgrade since there are some strange quirks to the way it's set-up now. For instance with GRUB II set as my bootloader, I have 2 entries for Windows 7 (SDB1 and SDB2) however SDB2 is my 500gig storage partition that is not bootable. Also Windows 7 does not have any OS entries for msconfig when you boot with GRUB. I had to use the boot menu in my BIOS and boot Windows directly from my 750GB drive to install Service Pack 2 because if I boot from GRUB it fails to install. Also Windwows takes ***FOREVER*** to boot while using GRUB for some reason. The other weird thing is that when I upgraded from Kubuntu 13.10 to 14.04 the upgrade says everthing went fine, however GRUB was left unbootable and just went into the recovery console. 

[IMG]http://img.techpowerup.org/110612/Capture029151.jpg[/IMG]

I want to know if there is an easy way to restore all of the widgets and layout for KDE along with the custom global hotkeys and such so I don't have to configure all of that manually. It'd also be nice to save a list of my repositories and packages that are installed. Is there a way to move all of those settings over to the new install? When I get the new drive I'm going to have both Linux and Windows on the same drive so I won't be able to use the boot menu trick to install SP2 on Windows. Does anyone know why msconfig has no entries when using GRUB? That is going to be a major problem fro me. Thanks for the help!

---

### Post by oldfred on 2014-04-28
Grub is just chainloading to the Windows PBR or partition boot sector, and that is all a Windows boot loader in the MBR actually does. But grub seems to only boot working Windows and any Windows maintenance requires a separate Windows repair CD or flash drive or temporary reinstall of the Windows boot loader to directly boot Windows.

Your /home should have all your configurations and if you back that up and copy it to new install then you should have all your settings. Most are in hidden files in /home.
You can export a list of installed apps and use that list to reinstall.
       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

This still is what I do, but with some updates in links below.

 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
      
 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

---

