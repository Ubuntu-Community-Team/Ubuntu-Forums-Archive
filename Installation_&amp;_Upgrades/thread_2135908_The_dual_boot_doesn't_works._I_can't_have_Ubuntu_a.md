---
title: "The dual boot doesn't works. I can't have Ubuntu and Windows"
date: 2013-04-15
forum: Installation &amp; Upgrades
---

### Post by augustom on 2013-04-15
Hello!

I have Windows 7 installed.

I install Ubuntu, so, I have the GRUB, but just works if I choose Ubuntu.

If I choose Windows 7 appears the message "BOOTMGR is missing".

If I fix the Windows 7 boot using the Windows CD, the GRUB disappear (of course).

If I fix the GRUB using the Ubuntu Live CD, the GRUB get back, but if I choose Windows... "BOOTMGR is missing".

What the way?

Thanks.

---

### Post by oldfred on 2013-04-15
Did you install grub to the Windows NTFS PBR - partition boot sector. Windows in the MBR tries to boot the Windows PBR which must have Windows boot code even for NTFS data partitions.

Best to see details.
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by augustom on 2013-04-15
oldfred,

I installed the GRUB on my Linux partition.

I followed those instructions:

[COLOR=#333333]*$ sudo fdisk -l *[/COLOR]

[COLOR=#333333]*$ sudo mount -t ext4 /dev/*[/COLOR][COLOR=#ff0000]*sda6*[/COLOR][COLOR=#333333]* /mnt *[/COLOR]

[COLOR=#333333]*$ sudo grub-install --root-directory=/mnt /dev/sda*[/COLOR]

"[COLOR=#ff0000]sda6[/COLOR]" is my Linux partition.

Ok, I will use Boot-Info to show the boot parameters here.

Thanks.

---

### Post by augustom on 2013-04-15
oldfred,

Here I am, after run Boot-Info.

The URL >> [http://paste.ubuntu.com/5711929/](http://paste.ubuntu.com/5711929/)

Ok, I`m seeing that my Linux partition is the [COLOR=#ff0000]sda7[/COLOR].

I`m not crazy, it was [COLOR=#ff0000]sda6[/COLOR] a couple of days ago.

I used [COLOR=#333333]*sudo fdisk -l*[/COLOR] in the terminal and confirmed [COLOR=#ff0000]sda7[/COLOR] as the Linux partition.

How can I fix my boot (get back my dual boot)?

Does [COLOR=#333333]*sudo grub-install --root-directory=/mnt /dev/sda*[/COLOR] work?

Thanks.

---

### Post by nerdtron on 2013-04-15
May I ask what command did you use when you install GRUB using the live environment?

Hmmm...If I were to do this dual boot, as I always do, I would install GRUB in the /dev/sda partition itself. That would remove the windows bootloader and let GRUB takeover everything on boot.

You could try and if it doesn't work, use the Win7 DVD again to repair boot and proceed with other solutions.

---

### Post by oldfred on 2013-04-15
Boot-Repair will reinstall grub automatically. Or you can do it manually:

       #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda7 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda7 if not correct:
sudo fdisk -l
#confirm that linux is sda7
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub


 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2
Grub2 info & full chroot version - also METHOD 3 - CHROOT:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by augustom on 2013-04-24
oldfred, thanks!

Sorry for my late. I did today the procedure.

Well...

**Boot-Repair** saved me! It's solved!

I loved this program.

Boot-Repair
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

oldfred, thanks again!

nerdtron, thanks!

:D

---

