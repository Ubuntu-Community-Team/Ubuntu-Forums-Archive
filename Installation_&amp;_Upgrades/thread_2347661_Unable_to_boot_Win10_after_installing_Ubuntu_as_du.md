---
title: "Unable to boot Win10 after installing Ubuntu as dual boot"
date: 2016-12-27
forum: Installation &amp; Upgrades
---

### Post by icebryanchan on 2016-12-27
[FONT=arial]Hi all,[/FONT][FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I am having a problem of not able to boot my Windows 10 after installing Ubuntu as a dual boot environment.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]My PC: Lenovo Y500 Ideapad[/FONT]
[FONT=arial]Storage: 120GB SSD + 1TB HDD[/FONT]
[FONT=arial]I have my Win10 installed on my SSD as primary storage, with HDD as a secondary storage.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]in order for my SSD to work with my HDD I have my BIOS setting to legacy.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Then I went on and installed Ubuntu on my HDD.[/FONT]
[FONT=arial]When asked for boot loader installation path, I chose /sda/ which is my SSD.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]After that, I can boot Ubuntu without any problem, from the Grub during startup.[/FONT]
[FONT=arial]My default OS on Grub is Ubuntu.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]However, when I chose to boot Win10 from Grub, the screen just turns purple and stucks there forever.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I have ran boot-repair on my Ubuntu.[/FONT]
[FONT=arial]Every time there will be a pop up asking whether my HDD is a removable or not.[/FONT]
[FONT=arial]I tried answering both yes and no and attempted to boot Win10, but still no luck.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Here is my URL from boot-repair.[/FONT]
[FONT=arial][http://paste2.org/cf0Wvg9C](http://paste2.org/cf0Wvg9C)
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I am really looking forwards for your reply as soon as possible, since I wish to retrieve my important files from Win10 and I can't access to my Win10 drives from Ubuntu. [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Thanks in advance. Really need a big help here.[/FONT]

---

### Post by oldfred on 2016-12-27
I would keep Windows boot loader on sda and have grub2's boot loader on sdb. And set BIOS to default boot sdb. Then you can choose Windows or Ubuntu in grub. But when Windows does its thing and makes grub not boot Windows you can directly boot Windows from BIOS on sda.

Windows 8 or later uses fast start up or always on hibernation. The Linux NTFS driver will not mount nor see hibernated NTFS partitions. And then grub cannot boot Windows. And Windows hibernation keeps all NTFS partitions mounted or hibernated. And if you try to force mount NTFS, you may then get issues in Windows with that NTFS partition. Best just to turn off the fast start up. And Windows on updates will probably turn it back on.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)
More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by icebryanchan on 2016-12-27
Hi oldfred,

Thanks for the prompt reply. 

Do you mean all my problems, i.e. not able to boot Win10 + not able to mount drives from Linux, are all caused by the fast startup or always on hibernation of Win10?
Is my understanding correct?

I have read all the links given, guess I have to make a Win10 bootable thumbdrive to access to command prompt to turn off the hibernation.


Thanks alot!

---

### Post by oldfred on 2016-12-27
You can install a Windows boot loader from Linux. But it is better to have & keep a Windows repair/recovery drive.

If it is hibernated, not sure if Boot-Repair will install the syslinux boot loader which is a Windows type boot loader or not. It likes to see that you have Windows & with hibernation on, it will not "see" it.

Lilo (boot loader to MBR only not full install of boot loader) and syslinux are Windows type boot loaders. They look for boot flag on a partition and jump to that partition to continue boot process.
       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Windows screenshots:
[URL="http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on"]http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on

      [/URL]
 sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda 
    [URL="http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on"]
[/URL]

---

