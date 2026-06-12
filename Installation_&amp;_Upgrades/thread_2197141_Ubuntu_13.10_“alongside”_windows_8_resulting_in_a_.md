---
title: "Ubuntu 13.10 “alongside” windows 8 resulting in a grub 2 issue"
date: 2014-01-02
forum: Installation &amp; Upgrades
---

### Post by MisesEnForce on 2014-01-02
[COLOR=#000000][FONT=Arial]Hi all,

Some time ago, I have installed ubuntu 12.10 64bits alongside windows 8 bits on a samsung series 7 chronos laptop, using the usb universal installer with ubuntu's 12.10 iso image. I am not an expert, but everything went fine, grub was functioning well. Then I had a bios update, which resulting in messing grub somehow etc... So I erased all ubuntu related partitions, and extending the win 8 one, returning thereby to my starting point.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Now I am back on track and need to work under ubuntu for some project, and having had a very recent bios update, I decided to reinstalled ubuntu on this laptop. I have opted for ubuntu 13.10 64 bits. I used the usb universal installer again, and boot of the ubuntu usb key, creating an ext4 (with mounting point /) following the win 8 partition, and created a swap partition following this ext4 partition after.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Every went fine, except that grub 2 (on dev/sda2) is not working properly : in the grub menu I have 1) Ubuntu 2) advanced options for ubuntu 3) windows boot manager UEFI 4) system setup (the bios menu in fact). When I want, from ubuntu, to boot on windows, I choose 3, the windows boot manager UEFI, I have the following error message :
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/EndEntire file path : ACPI(a034d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(2,fa800,96000,c5a85a4e9cd697b,b6,f6)/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi)/EndEntire
error : cannot load image
Press any key to continue...
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]When I press a key, I am brought back to grub's menu. The only thing I can do is to choose 4, then change boot order putting ubuntu under win8, save this an reboot, and then here come win 8. Same of course if I want to boot from win 8 to ubuntu, I must go to the bios menu, put ubuntu above win8 etc.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Of course, this is fine, I could do like this if I am not using ubuntu on a regular basis but... I tend to use it on a frequent basis, so I would like to solve this issue.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]In any case case I put a screenshot of partitions I have on my laptop

[ATTACH=CONFIG]249117[/ATTACH]

Any help would be greatly appreciated.

Thx in advance[/FONT][/COLOR]

---

### Post by oldfred on 2014-01-02
Post BootInfo report. Do not say yes to Boot-Repair's suggested 'buggy' UEFI fix if you can now boot ubuntu entry from UEFI. That is only for some systems that hard code UEFI to only boot Windows UEFI entry. But Boot-
Repair often suggests fix if you run it more than once.
Also do not reinstall Ubuntu before reading link in my signature if thinking about reinstall. Some have erased drive.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by MisesEnForce on 2014-01-02
Here is the BootInfo report :

[http://paste.ubuntu.com/6679677/](http://paste.ubuntu.com/6679677/)

When I have lauched boot-repair I was told in a pop-up window that windows UEFI was detected, nothing else.

---

### Post by oldfred on 2014-01-02
Boot-Repair has this:

       EFI detected. Please check the options.
Please disable SecureBoot in the BIOS. Then try again.Do you want to continue?    

And with 13.10 there is this bug where grub will not boot Windows when secure boot is on.
       Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

---

### Post by ubfan1 on 2014-01-02
You can add yourself to the bug [https://bugs.launchpad.net/ubuntu/+s...2/+bug/1091464]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464") and mention if you have experienced anything different than what has been reported.  I get around the problem by using the efi boot menu to boot windows, and grub to boot just Ubuntu.

---

### Post by MisesEnForce on 2014-01-02
Ok, I disabled the secure boot in the bios menu, been brought back to grub's menu where [FONT=Arial][COLOR=#000000]I opted for the 3rd option, windows boot manager. Then, I did not have the former errors I had : I succeeded in booting win 8, but through a very bizarre phase, that I have recorded and uploaded on my youtube here :

[/COLOR][/FONT][http://www.youtube.com/watch?v=IhLELw3LlNw&feature=youtu.be](http://www.youtube.com/watch?v=IhLELw3LlNw&feature=youtu.be)[FONT=Arial][COLOR=#000000]

I really don't know what is happening here... Is it normal to have such a buggy boot ?...[/COLOR][/FONT]

---

### Post by ubfan1 on 2014-01-03
Your video looked like a normal grub booting windows sequence.  With secure boot enabled, if you were able to make the error come and go by rearranging the UEFI Settings boot order that would be a very interesting observation to add to the bug.

---

### Post by MisesEnForce on 2014-01-05
I guess that it depends on how you define "being normal". For me, what the video shows (samsung rotating icon on its proper color, surrounded by purple ubuntu color, extremely buggy) is not normal at all, and by the way, this wasn't happening before, on my very first ubuntu 12.04 64 bits install, alongside win8 (64 of course). Anyway.

For the booting, as I told, even with secure boot enabled, I was able to boot on the os I wanted by simply putting the os I wanted to boot on on the top of the list of bootable drives in the bios menu.

Other question : when the previous os booted on is ubuntu, when I reboot, grub shows up. When the previous os booted on is win8, when I reboot, grub does not show up. As I am not an expert, I would like to know if this is normal or not. Thx.

---

### Post by oldfred on 2014-01-05
With Windows 8 it would update to be first in boot order anytime you did system changes or updates. But with 8.1 it seems that it always updates. 
It does try to sync UEFI and BCD, so when ubuntu gets added it then is out of sync and updates?

 Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

### Post by johnvantran6592 on 2014-01-08
I have a similar problem as [**[COLOR=#000000]MisesEnForce[/COLOR]**]("http://ubuntuforums.org/member.php?u=1895369") when I try dual booting with Ubuntu 13.10, and the result of the video is exactly the same as when I try to boot to Windows 8.1. I also have a Samsung laptop (series 5 instead of series 7), so this can't be a coincidence.

---

