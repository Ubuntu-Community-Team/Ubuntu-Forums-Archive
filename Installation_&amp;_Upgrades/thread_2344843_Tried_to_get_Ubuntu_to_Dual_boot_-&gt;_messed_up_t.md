---
title: "Tried to get Ubuntu to Dual boot -&gt; messed up the system"
date: 2016-11-28
forum: Installation &amp; Upgrades
---

### Post by 2meoverhere on 2016-11-28
Hi! I&#8217;m having major problems when trying to install Windows to dual boot with Ubuntu. So my schools computer (HP Elitebook 820 G3) came with Ubuntu pre installed and my plan is to install Windows 10 to run alongside. First I booted the computer to Gparted in order to make the needed partition for Windows. See my attached photos where I recreated what I did with the partitions (in case it is something I did wrong when making the partitions). I was able to make a partition and install Windows 10 on it and the Windows installation was working without any problems. However I wasn&#8217;t able to boot to Ubuntu anymore,because the computer directly booted to Windows always. The Ubuntu partitions wouldn&#8217;t show up in Windows file explorer, however you could see that they are there from Windows Disk Manager. Tried fixing the problem with several instructions I found on the internet without succeeding in fixing the problem and even tried with boot repair disk, but that was not able to connect to the internet so it was no use. Next I deleted the created Windows partition with Gparted in order to make it boot to Ubuntu again. This caused the computer only to go to a Windows repair screen. With Gparted I however see that my Ubuntu installation seems to be ok. Is there a way to fix the Ubuntu to boot again and install Windows alongside. Right now my situation is rather embarrassing thinking that I study computer science in University =/.

---

### Post by oldfred on 2016-11-28
It looks like computer is UEFI, but Ubuntu is installed in BIOS/MBR configuration.
FAT16 is unusual on a internal hard drive. It was/is allowed for UEFI external drive boot, but usually even then FAT32 is used.

If drive is MBR(msdos) then your Windows would have to be installed in BIOS boot mode to a primary NTFS partition with the boot flag. You show mostly logical partitions inside the extended partition.

You can manually reinstall grub by mounting / (root) (and /boot if separate which it does not look like you have) and then install grub.
But usually easier to use Boot-Repair but Internet is required. And often live installer works only or best with hard wired connection. Too many different wireless drivers to include all in live installer.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System

[/URL]
```
 sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda 


```

---

### Post by 2meoverhere on 2016-11-28
Thanks for the answer! Do you have any tips on how to get the Boot-repair to connect the internet. Tried to connect an ethernet cable but nothing happens. After connecting the ethernet cable I added new "ethernet connection" from network settings but that didn't seem to help either.
While waiting for an answer I reinstalled Windows 10 same way I installed it in the first place, is Boot-repair able to help me still or do I need to do something for the partitions? Or did I understand it correctly so that the partition I'm installing Windows to should not be logical but primary? For that I probably need to format the partition(?) so I need to install Windows again.

---

### Post by oldfred on 2016-11-28
If you are having Internet connection issues best to post that in a new thread with that in title.
Since wired usually works, those that know wireless want you to post a script with lots of detail.
[https://help.ubuntu.com/stable/ubuntu-help/net-wireless-connect.html](https://help.ubuntu.com/stable/ubuntu-help/net-wireless-connect.html)

Windows does not have to be on a primary partition, but you have to boot Windows from a primary NTFS partition with boot flag. Windows 7 or later default install normally uses two primary partition one Boot and one as main install. 
       Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by 2meoverhere on 2016-11-30
So actually took my laptop to our schools IT-department to see if they would be able to make it boot. Well couple of our IT-specialists worked for an hour on it and actually got it to work so that now i can dual boot both systems (thousand thanks to them). But there is a very minor problem still. After the fix there is no splash screen on boot, only plain text (there used to be this really cool tux whose eyes where rolling while loading =P). The IT-guy mentioned that it is fixable but I didn't wan't to bother him more. So now I ask if you know how get splash screen back on boot (IT-guy mentioned something about a file that he possibly accidentally renamed while fixing the system and this might be the cause of this).

---

### Post by oldfred on 2016-11-30
I have not changed splash screen.
Is splash setting still on in grub?
You can quick check in grub menu when booting by looking at linux line.
And here:
 cat /etc/default/grub 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Then you have to have a file in correct place.
Cavsfan says .png work best, although .jpg should work.

[https://ubuntuforums.org/showthread.php?t=2076205&p=13525580#post13525580](https://ubuntuforums.org/showthread.php?t=2076205&p=13525580#post13525580)

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by 2meoverhere on 2016-12-01
Maybe the problem was caused by the fact that there doesn't seem to be a grub file in /etc/default/... I created one with nano and added "[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" line there but it was no use, the splash screen does not come up while booting, only the "text lines". On an unrelated note while trying to search for a fix, I came across that it is plausible to change the grub wallpaper, did that and now it looks awesome =D. [/COLOR]

---

### Post by oldfred on 2016-12-01
If you are totally missing /etc/default/grub then you may want to reinstall grub. Boot-Repair in advanced options makes that relatively easy. But you can just run the command or use synaptic.

But note that any changes like the ones you just did may get undone. That is why one of the backups I do is to include any manual changes I make in /etc as a copy in /home so my normal backup of /home includes those changes. Some suggest backing up all of /etc, but if for example in your case you totally restored it, then you may restore the incorrect grub.

---

