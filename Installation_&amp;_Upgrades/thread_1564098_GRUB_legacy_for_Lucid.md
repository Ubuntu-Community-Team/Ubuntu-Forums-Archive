---
title: "GRUB legacy for Lucid"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by vikrang on 2010-08-30
I have a dual boot win 7 and win XP...I installed 7 and NTLDR of win 7 created a boot entry for XP,,,I installed Mint 9 and was using GRUB2 Menu chainloading NTLDR...Now I want to uninstall Mint 9 and since GRUB2 is installed by Linux, I want to be careful in not deleting the partition and rendering the MBR unbootable he screwing up GRUB2..I hit upon EasyBCD and installed it ...Now I have re-written with NTLDR and GRUB2 is gone..In Easy BCD itself there is an option to add Linux in the boot menu...This would be the best solution for me...Though my personal pref is using GRUB2 as the primary boot loader...I have been warned by my wife not to mess up Win ..So a safer option would be not to touch Win and related boot loader and experiment with Distros by adding or deleting in NTLDR...
 
I noticed that there is an option called neobootloader (which installs a Boot menu within NTLDR) ..I think this uses the old GRUB ...My question is - how do you reference it to the Linux distro in my (hd0,7) ..On selecting GRUB2 in neo bootloader, it drops me to a Grub Prompt
I tried the following:
 
Set root=(hd0,7)
Linux /boot/vmlinuz-2.62.32-21-generic
Initrd /boot/initrd.img-2.6.32-21-generic
boot
 
Result : Kernel not syncing ...Kernel Panic...My numlock and certain other keys started blinking in the keyboard
 
There is one more option in EASyBCD whuch uses the legacy Grub...On selecting this , it drops to the grub prompt
 
I tried legacy grub's menu entries
 
root (hd0,6)
Kernel /boot/vmlinuz-2.62.32-21-generic
initrd /boot/initrd.img-2.6.32-21-generic
boot
 
The command is executed , but on boot , same error as above
 
I read in some forum that kernel should refer to config-2.62.32-21-generic...
 
Then I ran Initrd and loaded all the files (system Map,abi etc) ending with generic and gave boot ...Still Kernel Panic not syncing
 
I have shortlisted on 4 methods but need ur advice
 
Method 1USE GRUB legacy in Easy BCD 2.01 to jumpstart a Linux distro which by default uses GRUB2 (or)
 
Method 2:Retain GRUB2 installed by a distro but able to  delink the linux distro from the menu and delete that partition without rendering the system unbootable
 
Method 3:To look for a MAster boot loader which is independent of the OS , so that I can add and delete without tampering MBR,...Maybe a dedicated partition for this which links to all the distros on a modular basis so that addition / deletion is not a hitch....
 
Method 4 : USE a freeware Boot loader which loads all the OS independent of each other ...Advantage is you can have same OS of different versions or any OS...But the main problem is they are independent and file sharing is not possible..Each OS is hidden from the other...It is like having stand alone OS with separate use which I do not want...
 
Can some Guru pl explain me the best way for all the 4 ....I need detailed commands for 1 and 2 if possible
 
Is there any open source application exactlyh like EasyBCD ...That is a very golod piece of software...But sadly to be used only in MS..Anything which automates GRUB menu manipulations would be superb without the user struggling with the commands
 
I am a noob but I am too impressed with Linux and cant restrain myself from trying it out....

---

### Post by vikrang on 2010-08-30
I was able to boot from Easy BCD Neosmart Linux option by executing the command

configfile /boot/grub/grub.cfg and my Distro loaded

If I want to load the kernel directly, what is to be done?

---

