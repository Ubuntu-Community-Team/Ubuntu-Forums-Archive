---
title: "Boot Issues - grub rescue"
date: 2013-08-05
forum: Installation &amp; Upgrades
---

### Post by tyler7 on 2013-08-05
i have a toshiba sattilite laptop and it was duel booted with windows 7 and ubuntu 12.04 i tried to uninstall Ubuntu so i deleted what i thought was the Ubuntu partition and no when i turn on my laptop it goes to a black terminal like screen and it sais error no such partition then under it it sais grub rescue> i have a windows 7 recovery disc and the ubuntu 12.04 disc but i dont no how to boot into them becaus it just goes to this screen[ATTACH=CONFIG]245102[/ATTACH]

---

### Post by Tom 6 on 2013-08-05
Hi :)
How about creating a small boot-partition?  No need to install the full OS ;)

It might have been possible to create a tiny partition at the end of you drive or safely tucked out of the way elsewhere.  It could be on almost any device that can read&write.  Usb-stick is just one good option but there are many others.  I'm not sure how much space grub2 takes up but 200Mb would probably be far more than it needs.  

Then just install Grun2, grub-legacy or Lilo (ie any of the gnu&linux bootloaders) to that.  Grub2 might be the easiest one because
1.  more people are familiar with it nowadays.  Lilo is a bit specialist
2.  it usually finds Windows on it's own without any need to edit anything.  
[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

Once you have booted into Windows you might be able to 'fix' (as in horse racing) the Windows boot-loader and get rid of the Gnu&Linux one.  However i've heard that a lot of people keep a Gnu&Linux boot-loader even on Windows-only systems because it's more robust, easier to configure and less flaky than the Windows ones.  

Regards from 
Tom :)

---

### Post by Tom 6 on 2013-08-05
Hi Tyler :)
Waaay before you get to that screen, when you first switch on the machine a splash-screen appears saying to press F2, or Del, or F8 or F12 to get into the bios.  Usually it's either del or F2 so i tend to press those 2 quite a few times just after starting up the machine.  

Once you are in the bios change the boot-order (maybe in advanced cmos options?) to put the cd/dvd-drives and anything similar higher up the list than the hard-drive.  Then save and exit.  

The LiveCd or Windows Cd should boot-up now.  The Windows one probably has a repair option that should help you fix your Windows boot-loader.  
Regards from 
Tom :)

---

### Post by tyler7 on 2013-08-05
[COLOR=#000000]i have a toshiba sattilite laptop and it was duel booted with windows 7 and ubuntu 12.04 i tried to uninstall Ubuntu so i deleted what i thought was the Ubuntu partition and no when i turn on my laptop it goes to a black terminal like screen and it sais error no such partition then under it it sais grub rescue> i have a windows 7 recovery disc and the ubuntu 12.04 disc but i dont no how to boot into them becaus it just goes to this screen[/COLOR][COLOR=#000000][IMG]http://ubuntuforums.org/attachment.php?attachmentid=245102&d=1375726471[/IMG][/COLOR]

---

### Post by oldfred on 2013-08-05
Moved to your own thread as you were in an older one and your issues are now different.

---

### Post by Tom 6 on 2013-08-05
Hi :)
Only my 2nd post was aimed at Tyler.  The first one belonged to the other thread
Apols and regards from 
Tom :)

[edit] the last thread kept getting posts from other people saying "me too" and such so i wanted to give an alternative. However i do think you are right and that Tyler is going to need both my answers in this thread unless soemone else gives one of the alternatives to my 1st.

---

### Post by grahammechanical on 2013-08-05
Do you understand what you did? When we install Ubuntu it puts Grub  boot loader into the MBR (Master Boot Record) of the hard drive. Then when we boot Grub will look for its configuration files in /boot/grub on the Ubuntu partition. By deleting the Ubuntu partition you also deleted the Grub configuration files but Grub is still in the MBR and it cannot find its configuration files or a Linux OS to boot so it goes to a Rescue prompt.

You now need to restore a Windows boot loader or boot manager to the MBR. As I do not use Windows I cannot tell you how to do that.

Regards.

---

### Post by tyler7 on 2013-08-05
[COLOR=#000000]i have a toshiba sattilite laptop and it was duel booted with windows 7 and ubuntu 12.04 i tried to uninstall Ubuntu so i deleted what i thought was the Ubuntu partition and no when i turn on my laptop it goes to a black terminal like screen and it sais error no such partition then under it it sais grub rescue> i have a windows 7 recovery disc and the ubuntu 12.04 disc but i dont no how to boot into them becaus it just goes to this screen[/COLOR][ATTACH=CONFIG]245108[/ATTACH]

---

### Post by tyler7 on 2013-08-05
thanks i tried doing that but every method required me booting into the recovery disc and idk know how to do that

---

### Post by bapoumba on 2013-08-05
Threads merged. Please do not start multiple threads in multiple forums, thanks.

---

### Post by oldfred on 2013-08-05
You have to have your Windows repairCD or flash or boot a Linux repairCD and install the Windows boot loader to the MBR of the drive.

How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by ubfan1 on 2013-08-05
Or if your recovery media is just the vendor junk, with no way to get to a Recovery Console, you might try installing the grub config files in a boot directory sitting on a FAT Windows recovery partition.  (The eventual link found in the above ...7Bootloader for an XP recovery iso is dead, apparently killed by Microsoft).

---

### Post by tyler7 on 2013-08-07
> **Tom 6 said:**
> Hi Tyler :)
Waaay before you get to that screen, when you first switch on the machine a splash-screen appears saying to press F2, or Del, or F8 or F12 to get into the bios.  Usually it's either del or F2 so i tend to press those 2 quite a few times just after starting up the machine.  

Once you are in the bios change the boot-order (maybe in advanced cmos options?) to put the cd/dvd-drives and anything similar higher up the list than the hard-drive.  Then save and exit.  

The LiveCd or Windows Cd should boot-up now.  The Windows one probably has a repair option that should help you fix your Windows boot-loader.  
Regards from 
Tom :)

see i wish that was the case i dont get anything before that so i have no idea what to do

---

### Post by ubfan1 on 2013-08-07
Turn machine on, and immediately start repeatedly typing F2 rapidly.  If that does not get you into the BIOS, turn machine off, and repeat trying F12, F10, ESC, DEL.  One of those should work.  When in the BIOS, find the delay time for boot, and increase it from 0 to 5 or 10 seconds so doing this in the future is not such a challenge.

---

### Post by tyler7 on 2013-08-10
thers not anything before that screen

---

### Post by oldfred on 2013-08-10
You have to boot from a working repairCD  or flash drive to fix your system. And that repair disk has to be correctly configured as a bootable device or it will not boot.

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)


 [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

      
 [URL="http://www.sevenforums.com/"]http://www.sevenforums.com/

[/URL]
 [http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

[URL="http://www.sevenforums.com/"]
[/URL]

---

### Post by tyler7 on 2013-08-11
there is no screen before that

---

### Post by tyler7 on 2013-08-11
i no how to use hotkeys its just i dont have a way to type them in i turn on the computer and thers that screen nothin before it

---

### Post by oldfred on 2013-08-11
Some computers that get rebooted too many times without a full power down seem to get lost.

You can try totally shutting down, removing battery and hold power switch (without battery) so deplete any remaining power in system. Then wait overnight and try again to boot to BIOS with correct keys for your system.

---

