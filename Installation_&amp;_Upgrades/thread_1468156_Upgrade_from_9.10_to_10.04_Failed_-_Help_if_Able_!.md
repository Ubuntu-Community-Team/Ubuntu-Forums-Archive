---
title: "Upgrade from 9.10 to 10.04 Failed - Help if Able !"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Johnny M! on 2010-05-01
Saturday 1-May  09:00hr US Eastern Daylight Savings Time
-----------------------------------------------------------------------

Dear Fellow Ubuntu'ers,

Decided yesterday to allow Upgrade Manager to proceed with upgrading my Ubuntu 9.10 Build to 10.04.   Bad idea - all circuits were busy.  The normal 2 hour download (at DSL 90KB/sec download speeds) took 13 hours.    I promise (again) to wait a few weeks after a new release before attempting Upgrading.

I am a semi-experienced Ubuntu User; having computed with builds since 8.04.  I've noticed that the last couple upgrades have been more problematic for me than the first few.  That said: here is my story (and I'm sticking to it!):

Other than the 13 hours to download; all went well until the wee hours of the morning when the download finally finished.   Then the install/setup process prompted me for the following user input:

- There were about 3 windows asking if I want to replace or keep my current Menu.lst (Kernel boot options):  I just clicked the "Forward" button keeping my current Grub Boot options.  (I like to manually edit Menu.lst to the latest Kernel myself to prevent dual boot with Windows problems previously encountered: Windows not recognized).   I didn't want the new GRUB-2 at this time and I didn't want to see 20 different Kernel Boot Options at Start-up!.

- There was a window that asked about keeping a configuration file (was too sleepy to remember exact wording); but I again - kept my current configuration.  I thought I was just playing it Safe - Maybe a bad Choice here?????

- Another final prompt asked if I wanted to cleanup old obsolete software - that I gave my blessing to and let her clean away!   I noticed a lot of old Kernels being deleted (maybe the one I was booting 9.10 with: 2.6.31-20-generic was deleted ??).

Now the system asked me to finish the entire Upgrade Process by Rebooting the Machine.  OK - Here we Go !

Grub comes up with my previous Boot options - I select Ubuntu 9.10 (which I intend to manually rename in Menu.lst later when I edit the boot kernel).

Here is where things get funky:

On the boot screen appears some new text (error warnings) that I haven't seen before):

- "Mount: mounting none on /dev failed: No such device a43499....." (my machine code)

- "chroot: cannot execute /etc/apparmor/initramfs: No such device or directory"

Not sure what they both mean - but whatever it is: it doesn't sound good !

After a brief pause - my system continues to boot.    All seems to go well.   
I get my login screen: Machine and User Account all A-OK!
Login accepts my password and I get the welcome music and the 10.04 default desktop wallpaper picture and a Mouse Pointer;
BUT - I get NO Menus or Task Bars !!!!!!!!!!!

I have a pretty picture (that's all) and a moving mouse pointer but nothing to click on ???????

-------------------------------------------------------------------------------------------------

I suspect a Kernel Problem !

Help - can someone tell me what Kernel the upgrade to 10.04 should be using (2.6.32-X or other ????).   Thank you!

Must I let the upgrade process automatically update my GRUB Menu.lst ????
I was hoping to do this manually because I'm afraid of Dual Boot Problems (last time I allowed Windows went inoperable) !


Any and All Help Appreciated !

BVR
Johnny M!


PS:  Thank God I have an Acronis True Image of my good Ubuntu 9.10 Build to fall back on !

---

### Post by Johnny M! on 2010-05-01
Please - Help if Able (Many Thanks in Advance) !
---------------------------------------------------------

Fix for wrong 10.04 Kernel:

I dual boot with Windows XP, but Windows doesn't even see Ext3  Partitions.   I'm looking for a way to fix my 10.04 Upgrade without  having to reinstall the 9.10 Image and start all over again !

Does anyone know if I could use an older version Ubuntu CD (9.04) to boot from into Ubuntu; Then modify the "Menu.lst" file on my Hard Drive 10.04 Build with an Updated Linux Kernel ?

I suspect no dice - I know you need proper account credentials and SUDO to edit one's GRUB/Menu.lst file.   Just want to see if anyone has aver fixed this problem and how ?


Many Thanks!
BVR
Johnny M!

---

### Post by P4man on 2010-05-01
ive seen a few similar posts recently with 9.10 -> 10.04 upgrades not working and ending up in a mixed environment with 9.10 kernels (you are correct  they should be 2.6.32 and I take it this machine has 2.6.31 kernels only?)

Ive not managed to solve the problem for the others suffering the same issue. If you know what you are doing you could boot a livecd and chroot in to the install and run the update again, but i really have no idea whats going wrong. Im vaguely thinking it has something to do with grub..

---

### Post by Johnny M! on 2010-05-01
I solved the Problem:

The Problem:  Ubuntu Upgrade from 9.10 to 10.4 resulted in an inoperable Ubuntu OS (see above post for details).

The Problem's Cause:  During Set-up/Install phase (after Upgrade download) By clicking "Forward" Button to keep current Boot/Grub/Menu.lst file; Ubuntu 10.04 was trying to boot with my Ubuntu 9.10 Kernel (2.6.31-20).    But that was incompatible !     Ubuntu 10.04 needed Kernel 2.6.32-20/21.

Note: I don't like to accept the Upgrade automatically updating my Menu.lst file because last time I let it do its own thing:  it trashed Windows dual boot option (9.04 tp 9.10 Upgrade) and put 20 Kernal options on the Grub Boot Start-up Screen.    I prefer to manually edit the Menu.lst file myself (after Upgrade); but that requires the new Ubuntu Version to at least boot with the previous Kernel!

The Solution:   Use a Ubuntu Live CD to edit your real Menu.lst File !

1. Boot with a Ubuntu CD into the Live CD Mode (Your First Option: No Install - No Changes to Computer)

2. Go to Places Menu and Mount (open) the Hard Disk Drive Partition where the Real Ubuntu Lives.   Note: It will have some generic name (not the same as when you are in your real Ubuntu Build).

2. Open Terminal Window (Applications - Accessories - Terminal).   Type the following Command:

sudo gedit /boot/grub/menu.lst

3.  Now it gets tricky!    You'll have to fish around looking for the Real (on your Hard Drive) Ubuntu Location.   It will have a generic name, "Disk".   It won't be called the same (File System) as when you view it in your real Ubuntu Build.    But once you find it - follow the same pathway:   /Boot/Grub/Menue.lst.
Before navigating there (to menu.lst); verify that the upgrade did in fact load the latest kernels in /Boot.

4.  Open the real Menu.lst file and overwrite the old Ubuntu Version Name and kernel names with the new, in my case (2.6.32-21); Example:

itle          Ubuntu 10.04
uuid        1f74fa33-b019-4fe7-ab93-44a43499c08a
kernel     /boot/vmlinuz-2.6.32-21-generic root=UUID=1f74fa33-b019-4fe7-ab93-44a43499c08a ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

5.  Save !    Now Ubuntu will yap about not being able to save, etc.. etc.   But I did it a few time and it actually accepted the changes in the Real Ubuntu menu.lst file.

6. Re-Boot and Wham !!!!!!!!!!!!   Right into a fully operable Ubuntu 10.04 Build !

How lovely is that !!!!!!!!!

---------------------------------------------------------------------------------------------------------------------------

I think this is a wonderful solution to recent Ubuntu Upgrade Problems - I hope my discovery can help others with similar Upgrade Problems.   

Maybe this is already in Help files somewhere; but if not - I hope someone can add it in.   It is really a very nice trick up your sleeve !    It saved me countless hours of reinstalling my old Ubuntu Image and starting the Upgrade all over Again.

BOL2U
BVR
Johnny M!

---

### Post by distortedecho on 2010-05-03
Cursed Kernels and defective GRUB!!! Ugh

Thanks for this solution. Will jump right to it.

---

