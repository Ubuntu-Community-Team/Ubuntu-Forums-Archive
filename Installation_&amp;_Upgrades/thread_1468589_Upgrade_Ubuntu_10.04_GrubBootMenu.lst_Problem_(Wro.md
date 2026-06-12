---
title: "Upgrade Ubuntu 10.04: Grub/Boot/Menu.lst Problem (Wrong Linux Kernel) Solved !"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Johnny M! on 2010-05-01
Upgrade Ubuntu 10.04: Grub/Boot/Menu.lst Problem (Wrong Linux Kernel) Solved !:P

Hope the below experience can help Grub/Boot/Menu.lst Upgrade Problems with Incorrect Kernels!

BVR
Johnny M!
-----------------------------------------------------------------------------------------------------------

See Thread:  [http://ubuntuforums.org/showthread.php?t=1468156](http://ubuntuforums.org/showthread.php?t=1468156)

------------------------------------------------------------------------------------------------------------

 Upgrade from 9.10 to 10.04 Failed - Help if Able !
Saturday 1-May 09:00hr US Eastern Daylight Savings Time
-----------------------------------------------------------------------

Dear Fellow Ubuntu'ers,

Decided yesterday to allow Upgrade Manager to proceed with upgrading my Ubuntu 9.10 Build to 10.04. Bad idea - all circuits were busy. The normal 2 hour download (at DSL 90KB/sec download speeds) took 13 hours. I promise (again) to wait a few weeks after a new release before attempting Upgrading.

I am a semi-experienced Ubuntu User; having computed with builds since 8.04. I've noticed that the last couple upgrades have been more problematic for me than the first few. That said: here is my story (and I'm sticking to it!):

Other than the 13 hours to download; all went well until the wee hours of the morning when the download finally finished. Then the install/setup process prompted me for the following user input:

- There were about 3 windows asking if I want to replace or keep my current Menu.lst (Kernel boot options): I just clicked the "Forward" button keeping my current Grub Boot options. (I like to manually edit Menu.lst to the latest Kernel myself to prevent dual boot with Windows problems previously encountered: Windows not recognized). I didn't want the new GRUB-2 at this time and I didn't want to see 20 different Kernel Boot Options at Start-up!.

- There was a window that asked about keeping a configuration file (was too sleepy to remember exact wording); but I again - kept my current configuration. I thought I was just playing it Safe - Maybe a bad Choice here?????

- Another final prompt asked if I wanted to cleanup old obsolete software - that I gave my blessing to and let her clean away! I noticed a lot of old Kernels being deleted (maybe the one I was booting 9.10 with: 2.6.31-20-generic was deleted ??).

Now the system asked me to finish the entire Upgrade Process by Rebooting the Machine. OK - Here we Go !

Grub comes up with my previous Boot options - I select Ubuntu 9.10 (which I intend to manually rename in Menu.lst later when I edit the boot kernel).

Here is where things get funky:

On the boot screen appears some new text (error warnings) that I haven't seen before):

- "Mount: mounting none on /dev failed: No such device a43499....." (my machine code)

- "chroot: cannot execute /etc/apparmor/initramfs: No such device or directory"

Not sure what they both mean - but whatever it is: it doesn't sound good !

After a brief pause - my system continues to boot. All seems to go well.
I get my login screen: Machine and User Account all A-OK!
Login accepts my password and I get the welcome music and the 10.04 default desktop wallpaper picture and a Mouse Pointer;
BUT - I get NO Menus or Task Bars !!!!!!!!!!!

I have a pretty picture (that's all) and a moving mouse pointer but nothing to click on ???????

-------------------------------------------------------------------------------------------------

I suspect a Kernel Problem !

Help - can someone tell me what Kernel the upgrade to 10.04 should be using (2.6.32-X or other ????). Thank you!

Must I let the upgrade process automatically update my GRUB Menu.lst ????
I was hoping to do this manually because I'm afraid of Dual Boot Problems (last time I allowed Windows went inoperable) !


Any and All Help Appreciated !

BVR
Johnny M!



PS: Thank God I have an Acronis True Image of my good Ubuntu 9.10 Build to fall back on !

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Johnny M! Wrote:
    
Re: Upgrade from 9.10 to 10.04 Failed - Help if Able !
Please - Help if Able (Many Thanks in Advance) !
---------------------------------------------------------

Fix for wrong 10.04 Kernel:

I dual boot with Windows XP, but Windows doesn't even see Ext3 Partitions. I'm looking for a way to fix my 10.04 Upgrade without having to reinstall the 9.10 Image and start all over again !

Does anyone know if I could use an older version Ubuntu CD (9.04) to boot from into Ubuntu; Then modify the "Menu.lst" file on my Hard Drive 10.04 Build with an Updated Linux Kernel ?

I suspect no dice - I know you need proper account credentials and SUDO to edit one's GRUB/Menu.lst file. Just want to see if anyone has aver fixed this problem and how ?


Many Thanks!
BVR
Johnny M!

-------------------------------------------------------------------------------------------------------------------------------------------------------------
 
P4man's Avatar Wrote



Re: Upgrade from 9.10 to 10.04 Failed - Help if Able !
ive seen a few similar posts recently with 9.10 -> 10.04 upgrades not working and ending up in a mixed environment with 9.10 kernels (you are correct they should be 2.6.32 and I take it this machine has 2.6.31 kernels only?)

Ive not managed to solve the problem for the others suffering the same issue. If you know what you are doing you could boot a livecd and chroot in to the install and run the update again, but i really have no idea whats going wrong. Im vaguely thinking it has something to do with grub..
P4man is offline Report Post       Reply With Quote Multi-Quote This Message Quick reply to this message
P4man


-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Johnny M!Wrote: 

    
IMPORTANT - SOLVED ! Upgrade from 9.10 to 10.04 Failed - Help if Able !
I solved the Problem:

The Problem: Ubuntu Upgrade from 9.10 to 10.4 resulted in an inoperable Ubuntu OS (see above post for details).

The Problem's Cause: During Set-up/Install phase (after Upgrade download) By clicking "Forward" Button to keep current Boot/Grub/Menu.lst file; Ubuntu 10.04 was trying to boot with my Ubuntu 9.10 Kernel (2.6.31-20). But that was incompatible ! Ubuntu 10.04 needed Kernel 2.6.32-20/21.

Note: I don't like to accept the Upgrade automatically updating my Menu.lst file because last time I let it do its own thing: it trashed Windows dual boot option (9.04 tp 9.10 Upgrade) and put 20 Kernal options on the Grub Boot Start-up Screen. I prefer to manually edit the Menu.lst file myself (after Upgrade); but that requires the new Ubuntu Version to at least boot with the previous Kernel!

The Solution: Use a Ubuntu Live CD to edit your real Menu.lst File !

1. Boot with a Ubuntu CD into the Live CD Mode (Your First Option: No Install - No Changes to Computer)

2. Go to Places Menu and Mount (open) the Hard Disk Drive Partition where the Real Ubuntu Lives. Note: It will have some generic name (not the same as when you are in your real Ubuntu Build).

2. Open Terminal Window (Applications - Accessories - Terminal). Type the following Command:

sudo gedit /boot/grub/menu.lst

3. Now it gets tricky! You'll have to fish around looking for the Real (on your Hard Drive) Ubuntu Location. It will have a generic name, "Disk". It won't be called the same (File System) as when you view it in your real Ubuntu Build. But once you find it - follow the same pathway: /Boot/Grub/Menue.lst.
Before navigating there (to menu.lst); verify that the upgrade did in fact load the latest kernels in /Boot.

4. Open the real Menu.lst file and overwrite the old Ubuntu Version Name and kernel names with the new, in my case (2.6.32-21); Example:

itle Ubuntu 10.04
uuid 1f74fa33-b019-4fe7-ab93-44a43499c08a
kernel /boot/vmlinuz-2.6.32-21-generic root=UUID=1f74fa33-b019-4fe7-ab93-44a43499c08a ro quiet splash
initrd /boot/initrd.img-2.6.32-21-generic
quiet

5. Save ! Now Ubuntu will yap about not being able to save, etc.. etc. But I did it a few time and it actually accepted the changes in the Real Ubuntu menu.lst file.

6. Re-Boot and Wham !!!!!!!!!!!! Right into a fully operable Ubuntu 10.04 Build !

How lovely is that !!!!!!!!!

---------------------------------------------------------------------------------------------------------------------------

I think this is a wonderful solution to recent Ubuntu Upgrade Problems - I hope my discovery can help others with similar Upgrade Problems.

Maybe this is already in Help files somewhere; but if not - I hope someone can add it in. It is really a very nice trick up your sleeve ! It saved me countless hours of reinstalling my old Ubuntu Image and starting the Upgrade all over Again.

BOL2U
BVR
Johnny M!
:guitar:    :lolflag:

---

### Post by markofealing on 2010-05-03
You are an absolute star, excellent advice.

In my case I thought my fstab was broken in Kubuntu 10.04, so did a non destructive re-install, no change except my mouse stopped working!

Doing a **[B]uname -**a[/B] confirmed the kernel was indeed the wrong version.

Following your fix got rid of the error message and restored the mouse:)
[COLOR="Red"]
**1/10 to the Ubuntu team for letting this bug slip under the radar.**[/COLOR]

---

### Post by mnavasuk on 2010-05-05
thanks for posting your findings, this is driving me mad. My boot up process takes ages, longer to get to the login screen as with the previous release.
I also upgraded from 09.10 to 10.04, which means I'm on grub legacy since my machine has been upgraded, not installed clean, since 08.10.
My update choices are the same as yours, forward, keep my boot.lst. I ended up with loads of kernel options, but the "wrongly named" ones work, loading a different kernel version, and if I select the new entry for 10.04, I just get a blinking cursor over a blank background. The booting process gets stuck there.
I've removed the "old" kernel entries from menu.lst, but then the system becomes unusable, since the names are wrong but are the only working kernel, but using the wrong kernel.
I'll keep searching for a way to clean up this mess. Any pointers will be great.

uname -a:
Linux mars 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

contents of currently in use menu.lst
default 0
timeout 5
color white/black light-blue/black

title Ubuntu 9.10, kernel 2.6.31-20-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.31-20-generic root=UUID=23fd88e0-180f-4557-8668-190a51f33d6d ro quiet splash vga=795
initrd /boot/initrd.img-2.6.31-20-generic
quiet

title Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.31-20-generic root=UUID=23fd88e0-180f-4557-8668-190a51f33d6d ro  single
initrd /boot/initrd.img-2.6.31-20-generic

title Ubuntu 9.10, kernel 2.6.31-19-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.31-19-generic root=UUID=23fd88e0-180f-4557-8668-190a51f33d6d ro quiet splash vga=795
initrd /boot/initrd.img-2.6.31-19-generic
quiet

title Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.31-19-generic root=UUID=23fd88e0-180f-4557-8668-190a51f33d6d ro  single
initrd /boot/initrd.img-2.6.31-19-generic

title Ubuntu 9.10, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Windows Vista/Longhorn (loader)
root (hd1,0)
chainloader +1
savedefault
makeactive
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=23fd88e0-180f-4557-8668-190a51f33d6d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=23fd88e0-180f-4557-8668-190a51f33d6d

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid		23fd88e0-180f-4557-8668-190a51f33d6d
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=23fd88e0-180f-4557-8668-190a51f33d6d ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		23fd88e0-180f-4557-8668-190a51f33d6d
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=23fd88e0-180f-4557-8668-190a51f33d6d ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-20-generic
uuid		23fd88e0-180f-4557-8668-190a51f33d6d
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=23fd88e0-180f-4557-8668-190a51f33d6d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-20-generic (recovery mode)
uuid		23fd88e0-180f-4557-8668-190a51f33d6d
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=23fd88e0-180f-4557-8668-190a51f33d6d ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		23fd88e0-180f-4557-8668-190a51f33d6d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Sundark on 2010-05-08
maybe you should look at this file /boot/grub/grub.cfg and then change all that you need. I had a problem where menu.lst was clean, when I install ubuntu 10.04. So, if you have a problem, just look at that file that I said.

byeeeee!:popcorn:

---

### Post by mnavasuk on 2010-05-08
thanks Sundark. I could't use your suggestion because that file doesn't exist in that path in my installation. I think it's due to me being on legacy grub, not grub2.
I've resolved the mess in the list by simply editing my menu.lst after I had removed some old kernels using synaptic, which takes out those entries of the removed kernels.
By boot time is slower than I was expecting with 10.4, but I can live with that.
Thanks.

In case is of use to anyone looking where to make the modifications, what worked for me is to have it looking like this now:
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=23fd88e0-180f-4557-8668-190a51f33d6d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=23fd88e0-180f-4557-8668-190a51f33d6d

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##
default 0
timeout 5
color white/black light-blue/black

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid		23fd88e0-180f-4557-8668-190a51f33d6d
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=23fd88e0-180f-4557-8668-190a51f33d6d ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		23fd88e0-180f-4557-8668-190a51f33d6d
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=23fd88e0-180f-4557-8668-190a51f33d6d ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid		23fd88e0-180f-4557-8668-190a51f33d6d
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=23fd88e0-180f-4557-8668-190a51f33d6d ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		23fd88e0-180f-4557-8668-190a51f33d6d
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=23fd88e0-180f-4557-8668-190a51f33d6d ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		23fd88e0-180f-4557-8668-190a51f33d6d
kernel		/boot/memtest86+.bin
quiet
title Other operating systems:
root 

title Windows Vista/Longhorn (loader)
root (hd1,0)
chainloader +1
savedefault
makeactive
### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Johnny M! on 2010-05-11
To prevent Wrong Kernel Problems after an Ubuntu Update/Upgrade (to new/next version); try this:

----------------------------------------------------------------------------------------------------------------------

- During the Install Portion of your Update procedure (at the end), you'll be asked if you want to keep or replace your /boot/grub/menu.lst file

- If you are like me, and Click "Forward" at the Prompt to keep the existing Menu.lst; be CAREFUL - because your new Ubuntu build is still associated with a Previous Linux Kernel (the New Version of Ubuntu might require a New Kernel to Boot Properly).

Note: I edit this file manually to prevent problems with Dual Boot GRUB  Systems (with Windows) and massive Clutter on the Boot Menu Screen.

- At the end of a successful Update/Upgrade (download); the system will Prompt you to Re-Boot so the changes can take effect.

- DON'T !!!!!!!!!!!!!!!!!!!!!    Don't Re-Boot Yet !

- Now is the time to manually edit your Menu.lst file with the new Linux Kernel.

- Check: (Places - Computer - File System - boot) for the latest Linux Kernel designations (write down the most current - highest number). 

- Open a Terminal Window (Applications - Accessories - Terminal) and use the command:

sudo gedit /boot/grub/menu.lst

- Manually change (edit) the text to change or add the latest kernel options. SAVE !!!!!!!!!!!

EXAMPLE: 

title        Ubuntu 10.04
uuid        1f74fa33-b019-4fe7-ab93-44a43.......................
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=1f74fa33-b019-4fe7-ab93-44a43499c08a ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

- NOW you can Re-Boot with Confidence!  Your New Ubuntu Version will be associated with the latest (and correct) Kernel !!

-----------------------------------------------------------

BVR
Johnny M!
:guitar:

---

### Post by mnavasuk on 2010-05-11
useful tip, thanks.

---

### Post by rfincher on 2010-05-12
I had the same problem also. My computer has dual-boot set up for Ubuntu and Vista. At start-up after installing the 10.04 upgrade, the GRUB menu appeared, showing the former system as Ubuntu 9.04, kernel 2.6.28-13-generic etc. Highlighting the first line on the menu (ie the one describing the version and kernel numbers as above), I then pressed 'e' to edit the command. On the next screen I edited all the old kernel numbers to the new 2.6.32-22-generic, then pressed 'b' to boot and Ubuntu 10.04 started up perfectly. (BTW to discover that the update I had just downloaded was kernel 2.6.32-22, I first booted from the old Ubuntu 9.04 CD, opened the drive where 9.04 was installed, and found the new kernel 2.6.32-22 files had also been saved there).
After 10.04 was running, I entered Terminal and changed the grub/menu.lst file to reflect the version and kernel changes, and now everything works as expected.
:P:P

---

