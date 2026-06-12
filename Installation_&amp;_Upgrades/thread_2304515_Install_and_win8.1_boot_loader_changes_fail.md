---
title: "Install and win8.1 boot loader changes fail"
date: 2015-11-27
forum: Installation &amp; Upgrades
---

### Post by FerryGnu on 2015-11-27
Using this excellent video...
[https://www.youtube.com/watch?v=rPUVIc-W13s](https://www.youtube.com/watch?v=rPUVIc-W13s)

I have an SSD with win8.1 installed.
I shrunk the C-drive and made a 40G partition for Ubuntu
I installed as instructed and followed the instructions for the ubuntu.bin file.
Shut down Ubuntu and rebooted to windows.
Started the BCDEdit process with Admin-level, but the first line 
***bcdedit /create /d "Ubuntu" /application bootsector***
returns 
[B][I]The entry {f53b4f14...} was successfully created.
The parameter is incorrect.
[/I][/B]
I have tried everything I can think of and researched the bcdedit commands and cannot get rid of that error.
If I ignore it I cannot use the /set options so I need help figuring out what is wrong.

Another issue that concerns me is the ***ubuntu.bin*** file placed in the root of drive C: during the Ubuntu-Install, is filled with zeroes using a Hex file viewer.
Shouldn't that contain some details as to where to boot Ubuntu?

I have now spent allmost two days and probably 20+ installs to get this working. As well as the above video, I have followed through many of the step-by-step instructions on this site but nothing is working. As soon as I try the bcdedit stuff it fails with the "***parameter is incorrect.***" issue.

Can someone please help me with this as I am trying to make Ubuntu my main start up as I wean off windows. :)

I am currently having to use F12 boot menu and select Ubuntu from that, but including Ubuntu as the default in the windows boot manager would be a better option.

Thanks

---

### Post by ubfan1 on 2015-11-27
Don't know what the ubuntu.bin file is, probably a copy of the empty MBR (on a UEFI machine).  I use efibootmgr on the Ubuntu side to change the default boot order of the OSes.

---

### Post by yancek on 2015-11-27
Take a look at the link below discussing 'bin' files on Ubuntu/Linux.

[http://howtoubuntu.org/how-to-execute-a-run-or-bin-file-in-ubuntu](http://howtoubuntu.org/how-to-execute-a-run-or-bin-file-in-ubuntu)

I've never see a bin file on my system so I'm not sure what it is.  From what I've read, they are generally used to install something.  Not sure why it would be on the windows partition or if it should be.  Is your windows 8.1 a pre-installed system using UEFI and did you install Ubuntu UEFI?   I would think that since your problem is not being able to modify the windows boot file you would have better luck at a windows forum.

---

### Post by oldfred on 2015-11-27
The bin file method is a very old way to install grub to MBR, and use a copy of that in Windows to boot. That is only for BIOS boot and not recommended even back then. Last saw it used with some XP installs.

With UEFI, you can only boot with your f12 method if you installed Ubuntu in BIOS boot mode, not UEFI boot mode.
If both Windows & Ubuntu are UEFI you can dual boot from grub menu or from Windows BCD. But BCD method is really a one time UEFI reboot into another system, so you have to boot into Windows to boot Ubuntu.
UEFI & BIOS are not compatible, and once you start booting in one mode you cannot change to the other mode without rebooting.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

    
Boot-Repair can also convert an Ubuntu/grub BIOS install on gpt partitioned drive to UEFI boot if ESP - efi system partition exists. If you have Windows in UEFI boot mode you already have the ESP.

We typically suggest using grub to dual boot, but you can use BCD.
 Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

### Post by FerryGnu on 2015-11-27
Thanks to all who responded so quickly.
@olfred:
I thought I had covered everything about the install, but -- and ain't there always a but, DUH! Slapping my forehead! Yup, I installed using UEFI+Secure boot for win+Ubuntu and the F12 menu works, but it is a pain to use.

I'll wade my way through your suggestions, but I suspect I am not as smart as you think I am. LOL I am most certainly a newbie to Ubuntu (any Linux actually)

---

### Post by yancek on 2015-11-27
If you are having trouble with it, go to the link for the boot repair download posted above in the post by oldfred and as sugggested, do not try to repair but select the option to Create BootInfo Summary and post the link here.  Someone should be able to give you more detailed instructions.

---

