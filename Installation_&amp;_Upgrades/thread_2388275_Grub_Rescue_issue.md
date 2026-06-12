---
title: "Grub Rescue issue"
date: 2018-03-30
forum: Installation &amp; Upgrades
---

### Post by lowellg on 2018-03-30
Hi there,

First off... I know little to nothing about computers. I setup a dual boot on my hard drive years ago. It has Linux and Windows 10.  I never found the time to mess with Linux.  I recently tried updating windows...tried 3 times. It kept failing. I found a forum thread that said the dual system was the issue.  Since I didn't want Linux anymore and just wanted to update windows I deleted the Linux partition...agter backing up all my data ofcourse.  When I turn on the computer it now just says Grub Rescue.  I guess I deleted the boot software?  I'm guessing the computer is trying to boot Linux or Grub but it isn't there anymore?

Anywho my apologies for my ignorance.  I just want to boot my computer back into Windows permanently.  I do not have a windows install disc or iso.  So I would really like to fix this without a clean install if possible.

I have a Mac computer I can use to create usb thumb drives if need be.

Thanks in advance!!

---

### Post by hrsetrdr on 2018-03-30
By deleting your Linux install you kind of "orphaned" your remaining Windows system, because[ grub]("https://en.wikipedia.org/wiki/GNU_GRUB") was handling OS booting.    There are a couple options, one is to reinstall a Linux distro, that way you'll have a functioning grub boot menu to select you Windows install from.

The other strategy that comes to mind is to download a Win 10 .iso that your license is for, and create a USB installer for Windows 10.   That way you can do a fresh install, and wipe the remains of your Linux installation, if that is your desire.

---

### Post by yancek on 2018-03-30
>  I recently tried updating windows...tried 3 times. It kept failing.

Some details on exactly what happened would be useful.  There is no reason having a Linux system on your computer/drive should interfere with your windows system.  They are on separate partitions.
Do you know if this is/was an EFI system as windows 10 pre-installed almost certainly was.  If it was EFI, you should be able to access the windows EFI file from the BIOS regardless of whether Ubuntu Grub is available.  If you have or can create a bootable Ubuntu flash drive, go to the site below and download and run the boot repair software per instructions on the page and select the option to Create BootInfo Summary and post the link you are given here.  Do NOT try to make any changes.

Another option, you should be able to download at least some type of repair iso of windows 10.  You would need to get the exact same release and version of windows you have installed.

---

### Post by ajgreeny on 2018-03-31
I don't use Windows any more but I believe that you can use **Boot-Repair** (from my signature below), go to Advanced, and from there repair Windows boot system files.

You can run Boot-Repair from a live Ubuntu system, so it must be worth a try.

---

### Post by lowellg on 2018-04-01
Thanks for the reply.  Will I be able to install Linux if I download it to my Mac and put on a thumb drive to then install on the Microsoft?  Also will I then be able to do what I initially set out to do and convert the pc to solely windows?  If not then I'll just do a clean install.

---

### Post by oldfred on 2018-04-01
Did you try directly booting Windows from UEFI boot menu?

---

### Post by lowellg on 2018-04-01
I don't see that option.  Could you please explain how to do that?  I only see

+Hard drive
CD
Removable devices
Network
Diagnostics

---

### Post by oldfred on 2018-04-02
+Hard drive 

Then under the + should be more options?

---

### Post by lowellg on 2018-04-02
There is a long line of numbers and letters under that. Selected it and booted...went straight to grub rescue. Appreciate the assistance.

I got a 16gb thumb drive today.  What exactly do I need to put on it to boot the computer? A linux ISO?  And is it the installation file or a full installed OS?

---

### Post by oldfred on 2018-04-02
If you only want Windows, you should have a Windows repair disk.
       [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive](http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive)

Many Windows repairs cannot be done from Linux.

If you just need a Windows type boot loader in MBR, just about any Linux distribution can install the syslinux or lilo boot loaders (boot loader in MBR, not entire boot loader).

Or from Ubuntu live installer, you can add Boot-Repair.
       
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[URL="http://www.ubuntu.com/download"]http://www.ubuntu.com/download

[/URL]
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

[URL="http://www.ubuntu.com/download"]
[/URL]

---

### Post by lowellg on 2018-04-03
I found this [Create a bootable USB stick on Windows | Ubuntu tutorials]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=12&cad=rja&uact=8&ved=0ahUKEwiz_Jzq3Z7aAhUHnlkKHQKaAyQQFghiMAs&url=https%3A%2F%2Ftutorials.ubuntu.com%2Ftutorial%2Ftutorial-create-a-usb-stick-on-windows&usg=AOvVaw3ykui8dL17kqTtiKWhapsM") and followed the instructions, except I used Etcher because I had to use Mac OSX to create the drive.  It worked and my computer boots now.  I still have to select Windows or Linux when booting though.  I'm kinda digging the look of Ubuntu though and may keep it... it will depend on whether or not I can update Windows 10.  Thanks for all the replies.

---

