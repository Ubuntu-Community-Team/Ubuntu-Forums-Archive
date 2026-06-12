---
title: "UBUNTU 9.10, Black Screen after UPDATES"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by uprise on 2009-12-07
[FONT=Arial Black][SIZE=2]**Hi**[/SIZE][/FONT][SIZE=2]![/SIZE] I am new to ubuntu and linux and I have win7 on my computer. I installed linux 9.10 to another partition. I was using both os with grub. And i had 5 choices in the grub screen:
[FONT=Comic Sans MS][I]Ubuntu 9.10 build ....
Ubuntu 9.10 ....(recovery mode)
Mem test...
Mem test...
Windows 7[/I][/FONT]



I installed _startupmanager _and changed boot default in it, and boot win7 and ubuntu with *no problems.*
 

After that, i changed some boot settings in startupmanager, like resolution and some other stuff i cant remember(that was like a week ago), while doing that I was installing all the updates. it asked me about the grub version, if wanted to change it or keep it, giving 5 choices, i chose *"show me my version*" to see and than choose, but _it just continued installing updates!? _Anyway, after that update i rebooted, and saw that grub screen was changed to:
[FONT=Comic Sans MS][I]Ubuntu 9.10 build ....
Ubuntu 9.10 build ....(recovery mode)
Ubuntu 9.10 some other build ....
Ubuntu 9.10 some other build....(recovery mode)
Mem test...
Mem test...
Windows 7[/I][/FONT]
 
**i tried booting both builds, neither worked!**
** I just get a BLACK SCREEN!**
But i have no problems with booting Win7.
 So, is it about startupmanager, grub, other updates, doing startupmanager and grub thing at the same time, or smthng else?
What can i do about that?
I am pretty new to linux and ubuntu, i have almost no ideas about the console commands right now, just trying to learn and figure out the system, can i do smthng with some commands in the recovery mode? Or other solutions?
 ***THANX FOR UR HELP!***

---

### Post by dstew on 2009-12-07
From what I can see about startupmanager, it is a Windows program that can change how Windows boots, but I don't think it is a boot loader. That is, I don't think it would change the MBR, or the  boot sector of a partition. But, perhaps it does, I don't know much about it.

Probably, you answered the wrong way about grub when you got the updates. I think the default answer is usually the correct one. You might have ended up with a mis-configured grub.

You should probably re-install grub from a Live CD. The technique for re-installing grub 2 is [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD").

---

### Post by darkod on 2009-12-07
> **dstew said:**
> From what I can see about startupmanager, it is a Windows program that can change how Windows boots, but I don't think it is a boot loader. That is, I don't think it would change the MBR, or the  boot sector of a partition. But, perhaps it does, I don't know much about it.


Slight correction. I think the OP is talking about the startupmanager package which you can install in Ubuntu and offers GUI for changing grub2 like default OS, timeout, etc, instead of editing the config files. Having said that, some issues have been reported between startupmanager and grub2, it seems it's fine tuned for grub1 but not so much for grub2.
Anyway, how often do you do grub menu changes? For me editing the config files (not grub.cfg) is enough.

---

### Post by jaylsi on 2009-12-07
Could you see anything if you go with the recovery mode? If yes, you can then select "drop to root shell", run "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak", and finally "sudo reboot". These steps make the system use default video driver if somehow the latest system upgrades conflict with current driver. If you don't see xorg.conf, then it is not the problem.

---

### Post by uprise on 2009-12-07
> **jaylsi said:**
> Could you see anything if you go with the recovery mode? If yes, you can then select "drop to root shell", run "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak", and finally "sudo reboot". These steps make the system use default video driver if somehow the latest system upgrades conflict with current driver. If you don't see xorg.conf, then it is not the problem.
Thanx, but i dont think it is about that, because i had already installed the drivers before the update, and booted properly. I'll try to reinstall grub via the live cd...:D

---

### Post by uprise on 2009-12-08
Well, i tried reinstalling grub, it didnt work. i dont have the grub2 in the grub screen actually. it is the previous 1,... one. i have no problems with getting the grub screen opened, and win7 booted. But whenever i try to reach ubuntu or recovery mode, i get a black screen!:?

---

### Post by dstew on 2009-12-08
Can you confirm for me that your grub menu at the top says grub 0.97 (that is grub legacy, or "grub 1") and not grub 1.97 (which is grub 2)?

---

### Post by uprise on 2009-12-08
> **dstew said:**
> Can you confirm for me that your grub menu at the top says grub 0.97 (that is grub legacy, or "grub 1") and not grub 1.97 (which is grub 2)?
sorry:redface: i didnt know 1.97 was grub2, yes than it is grub2...

---

### Post by dstew on 2009-12-08
If the Windows entry boots, then grub is installed correctly. Since the other menu entries do not boot, it must be a problem with the grub configuration.

To take a look at what grub is trying to do when you select one of the Ubuntu menu items, at the menu, highlight the first Ubuntu item and press 'e'. That should display the commands that grub will try to execute if you had pressed 'enter' instead of 'e'. Post the list of commands to the forum. Maybe we can tell what the configuration issue is. If it looks funny, we can change the commands and see if we can get Ubuntu to boot.

---

### Post by jaylsi on 2009-12-08
Here are the steps I use for restoring Grub loader after XP overwrote my MBR. If you find it useful, you may try it.

1) Boot with 9.10 live CD without hard drive change
2) In a shell window, type 'sudo -i'
3) Run 'mkdir /media/root'
4) Run 'mount /dev/sda5 /media/root'
5) Run 'sudo grub-install --root-directory=/media/root /dev/sda --recheck'
6) reboot without live CD

This assumes linux partition is on /dev/sda5 of course. Replace it with what you have.

---

### Post by gonzoop on 2009-12-08
i'm having this problem too but this is a display driver problem i think. i'm using ATI HD4670. i'm sorry i'm also a newbie on ubuntu

---

### Post by uprise on 2009-12-08
> **dstew said:**
> If the Windows entry boots, then grub is installed correctly. Since the other menu entries do not boot, it must be a problem with the grub configuration.

To take a look at what grub is trying to do when you select one of the Ubuntu menu items, at the menu, highlight the first Ubuntu item and press 'e'. That should display the commands that grub will try to execute if you had pressed 'enter' instead of 'e'. Post the list of commands to the forum. Maybe we can tell what the configuration issue is. If it looks funny, we can change the commands and see if we can get Ubuntu to boot.
Here it is:

```
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd0,8)
search --no-floppy --fs-uuid --set 931ad8d5-a3d8-42c6-b851-7b1ed...
linux /boot/vmlinuz-2.6.31-15-generic root=UUID=931ad8d5-a3d8-42...... ro splash vga=794 quiet splas\
h
initrd /boot/initrd.img-2.6.31-15-generic
```well, it is grub 1,97 beta4...
thanx:::

---

### Post by uprise on 2009-12-08
> **gonzoop said:**
> i'm having this problem too but this is a display driver problem i think. i'm using ATI HD4670. i'm sorry i'm also a newbie on ubuntu
could my problem be similar to that, a driver problem, i have an ATI HD3450 in my laptop... but i had the driver installed before the update 
???????

---

### Post by jaylsi on 2009-12-08
There are so many people having driver working but broken after system upgrade. Do a search you will find out. So don't assume it is not driver problem.

---

### Post by dstew on 2009-12-09
Thanks for posting your menu information. Some things to check:

Is ```
(hd0,8)
``` really the partition where your /boot directory is? Also, do you have a separate /boot partition?

Do you have an ext2-formatted partition? I notice an **insmod ext2** line in the menu entry.

Check to be sure that the UUID for the linux kernel root argument is correct. You can boot a Live CD, and from the Live CD command line, do```
sudo fdisk -l
```That should list all the partitions on all your hard disks. You can look at UUIDs with the **blkid** command also.

If there is some doubt that the UUIDs in the menu entry are correct, try replacing them with linux-style partition names:```
linux /boot/vmlinuz-2.6.31-15-generic **root=/dev/sda8** ro splash vga=794 quiet splash
```Do the same for the initrd command argument. You edit the lines by highlighting one, pressing 'e' again. Then edit, press 'enter' to save your edit. When done, press 'b' to boot. At least I think that is how you do it. Your edits will not hold to another boot, but by experimenting this way you might be able to find out what the problem is. Then we can work out a permanent solution by editing the proper files in /etc/grub.d/ or by editing the /etc/default/grub file.

I also see "splash" in there twice, you might try removing one of them. Also, vga=794 is high-color resolution. If you think this might be causing some problem with your graphics card, try vga=775, or get rid of the vga statement altogether.

If you remove the **quiet splash** parameters, you might be able to see what errors are being generated when you try to boot your Ubuntu system. That might also help us.

---

### Post by uprise on 2009-12-10
there is sth i just realised after me hitting enter, it says on the black screen for a very short time:
vga=775 (or 794 for default, whatever i enter) [B][SIZE=2]depreciated...........
[/SIZE][/B][SIZE=2]*a graphics card driver problem ???*
[/SIZE]

---

### Post by dstew on 2009-12-11
Yes, perhaps. Try completely eliminating the **vga** parameter from the linux line and see if that changes anything. Also, try removing the **quiet splash** parameters so we can see the errors.

---

### Post by uprise on 2009-12-15
yes, i deleted it and booted! thank you!
i changed some resolution stuff from startup manager, now it is booting w/out any editing. but still seeing the vga=*** depreciated row?

---

