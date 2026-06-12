---
title: "How to re-install Xubuntu"
date: 2015-02-01
forum: Installation &amp; Upgrades
---

### Post by gordon99 on 2015-02-01
My HP laptop came with Windows 7 and I have added Xubuntu 14.04 as a dual boot OS. Recently I have been finding that the system freezes or crashes for no apparent reason. I know, for example, that if I try to open the /proc file the system freezes every time and I have to switch off to get things up and running again. I have no particular reason to enter the /proc file but the problem it causes if I try together with the other freezes at random times leads me to believe the OS is bugged or corrupted.  
I am minded to remove the existing and re-install a fresh version of Xubuntu. How should I best go about this please, if possible without disturbing my other files, programs and settings?.

---

### Post by nerdtron on 2015-02-01
> **gordon99 said:**
> 
I am minded to remove the existing and re-install a fresh version of Xubuntu. How should I best go about this please, if possible without disturbing my other files, programs and settings?.

Boot into a Live CD and start the reinstall. (but backup all your files in Xubuntu first).
Do NOT choose"Remove Existing *" on the Xubuntu installer - This option will wipe your hard drive partitions along with Windows 7.

The only safe way to do this is to choose the "Something Else" option. Now before we proceed, a reinstall of Xubuntu will probably erase your files on the Xubuntu partition. You may want to copy them first on the windows 7 partition (or another computer) just to be safe.

Now upon choosing "Something Else" option, you will be presented with the manual partitioning screen. You will see there the Windows 7 partition and two linux partitions. You can post a screen shot here for us to see.

Now click the Linux partition (the larger one), and click Change and set the mount point of as "/" and format ext4. Then click the smaller linux partition, click change and set format/type as "swap area".

On the lower part of the partitioner, you'll see the bootloader option. It should be pointed to /dev/sda or /dev/sdb depending on which is your hard drive.

Before you you click on proceed. Post your screen shot here so that we can see that you did it correctly.

---

### Post by mörgæs on 2015-02-01
Would be worth a shot to install 14.10 this time.

---

### Post by ajgreeny on 2015-02-01
> **mörgæs said:**
> Would be worth a shot to install 14.10 this time.
But only if you are prepared to do it all over again in 6 months time when 14.10 loses support.

If not stick with 14.04, supported until April 2017.

Why do you want to open the /proc folder in the filesystem?

All files and folders in there with one exception in my case (kcore) are merely virtual files; you can't open them to see properly in a GUI application, eg mousepad, where** /proc/cpuinfo** will show you an empty file, whereas **cat /proc/cpuinfo** in terminal will give you lots of content.

What are you wanting to do in /proc?

---

### Post by gordon99 on 2015-02-02
Thanks for the responses. When I first tried to open the /proc file out of interest, just to see what was in it, the system froze, that's to say the keyboard and mouse would not function. I have tried to open /proc a few times since with the same result. Each time I have to resort to a forced shut down i.e switching off the laptop. Also, on two or three occasions recently the system has frozen for no apparent reason. I am not that interested in looking into /proc, but I am concerned that the system gums up if I try. I am just suspicious that the OS may not be working as well as it should and that's why I am considering doing a re-install.

I have downloaded xubuntu 14.04.1 using torrents as this seems to be the recommended method. I hope I have have done this correctly as I seem to have two files;one titled 'xubuntu-14.04.1-desktop-amd64.iso.torrent', the other is 'xubuntu-14.04.1-desktop-amd64.iso.' The latter file is described in 'Properties' as a 'raw CD image' so I assume it is this one only I will need to burn onto a CD.

I attach a copy of my present partitions. You will see that for Xubuntu I have an extended partition sda4 containing sda5; 6 & 7. Any backup I do would be to an external HDD
.[ATTACH=CONFIG]259667[/ATTACH]

---

### Post by nerdtron on 2015-02-03
You can proceed with the re-installation but be sure to set the correct mount points as you are seeing on the the gparted screen. 
Run the Xubuntu installer and choose "Something Else" set /dev/sda5 (70GB) as the ext4 and mount point as /. Be sure to check the box for format this partition to wiped the old Xubuntu. Then set /dev/sda6 (3GB) as swap area. If you want to keep the contents of /dev/sda7 (40GB), set the mount point of it as /data but DO NOT CHECK the format option. As for the /dev/sda1 and /dev/sda2, don't touch them on the installer they are probably where windows is installed and double check that they are not formatted.

On the lower part of the installer, you have the option on where to install the bootloader. Be sure to choose /dev/sda.
Assuming you setup correctly, you can now clicked Proceed on the installation screen.

If you are still in doubt you can post the screenshot of your installer screen.

---

### Post by gordon99 on 2015-02-06
Thank you for the re-installation guide nerdtron which I have followed with success.

---

