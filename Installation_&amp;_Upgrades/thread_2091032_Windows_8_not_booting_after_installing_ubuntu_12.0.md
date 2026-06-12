---
title: "Windows 8 not booting after installing ubuntu 12.04"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by 681ankit on 2012-12-04
I have installed Ubuntu after installing windows 8.Now I can not boot into windows8.
how to do.I have searched all over forum.but nothing find helpful to fix that problem.I don't want to loose GRUB .How to make grub to boot windows8..My windows 8 is installed into logical drive and ubuntu is in primary drive.

:(

---

### Post by slickymaster on 2012-12-04
You can fix your problem just by installing Boot-Repair and run it.

First open a terminal window and type:
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
```

Hit Enter and then type:
```
sudo apt-get install -y boot-repair && boot-repair
```

Hit Enter again and run the program.

---

### Post by 681ankit on 2012-12-04
Unwanted post

---

### Post by 681ankit on 2012-12-04
> **slickymaster said:**
> You can fix your problem just by installing Boot-Repair and run it.............


First of all thank you very much for the reply.
Boot Repair adds new entry "WINDOWS" in boot menu ..
But when I click it..I get the following error..

[FONT=Courier New]error:no such device: /EFI/Microsoft/Boot/bootmgew.ef
error:file not found

press any key to continue

[FONT=Arial]My windows 8 is on:  dev/sda5

[/FONT][/FONT]

---

### Post by darkod on 2012-12-04
You seem to have win8 installed in uefi mode.

Did you install ubuntu in uefi mode too, or in legacy bios mode?

---

### Post by oldfred on 2012-12-04
From Boot-Repair post the link it creates when you run BootInfo.

If you installed Windows 8 in sda5 in MBR it will not work unless you have another install of Windows in a primary partition. Or did you and then delete it (and Windows 8's boot files)? Windows only boots from a primary partition, NTFS format with boot flag. Grub does not need boot flag, but Windows boot files are all in that primary partition.

---

### Post by YannBuntu on 2012-12-05
Hello

> **681ankit said:**
> First of all thank you very much for the reply.
Boot Repair adds new entry "WINDOWS" in boot menu ..
But when I click it..I get the following error..

[FONT=Courier New]error:no such device: /EFI/Microsoft/Boot/bootmgew.ef
error:file not found

press any key to continue[/FONT]

I'm sorry there was a bug in the Boot-Repair version you used.
Please :
1) wait that all packages have a green check in this page: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)
2) then update and retry Boot-Repair

---

### Post by conradin on 2013-01-24
> **slickymaster said:**
> You can fix your problem just by installing Boot-Repair and run it.

First open a terminal window and type:
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
```

Hit Enter and then type:
```
sudo apt-get install -y boot-repair && boot-repair
```

Hit Enter again and run the program.

>>This post fixed my problems hallelujah!

---

### Post by guy1a on 2013-02-03
Hello

this fix did nt work for me

is there another ?

thank you !

---

### Post by darkod on 2013-02-03
> **guy1a said:**
> Hello

this fix did nt work for me

is there another ?

thank you !

Did you install ubuntu in uefi mode if your win8 is also in uefi mode?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by guy1a on 2013-02-03
> **darkod said:**
> Did you install ubuntu in uefi mode if your win8 is also in uefi mode?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


i am not sure about the windows 8
it wasn't installed by me...

thank you i will check the link above.

---

### Post by darkod on 2013-02-03
> **guy1a said:**
> i am not sure about the windows 8
it wasn't installed by me...

thank you i will check the link above.

Run boot-repair again but only to create the bootinfo results and post the link it gives you. It will show us more details what is where.

---

### Post by shimonna on 2013-02-10
tnx

---

### Post by shimonna on 2013-02-16
Hi.
I have the same problem.
I did everything listed but nothing gets better.
you can see info abut my system at [http://paste.ubuntu.com/1662038/](http://paste.ubuntu.com/1662038/)
Thanks

---

### Post by shimonna on 2013-02-16
Hi.
I have the same problem.
I did everything listed but nothing gets better.
you can see info abut my system at [http://paste.ubuntu.com/1662038/](http://paste.ubuntu.com/1662038/)
Thanks

---

### Post by darkod on 2013-02-16
> **shimonna said:**
> Hi.
I have the same problem.
I did everything listed but nothing gets better.
you can see info abut my system at [http://paste.ubuntu.com/1662038/](http://paste.ubuntu.com/1662038/)
Thanks

1. Do you still have both XP and win8?

2. You seem to have a wubi Kubuntu installation boot files, but not the installation itself. Are these left overs from earlier when you had wubi? In that case you can delete sda1/wubildr and sda1/wubildr.mbr. They might get in the way of the booting process.

Everything else looks fine, if it can't boot something is broken in the windows boot process, not grub2/ubuntu.

---

### Post by Rahil Bhavsar on 2013-06-06
[HR][/HR]Please help me ... I have the same problems.. even when I try the Windows Bootloader I get this error.. 

file: \BCD
Status: 0xc00000098

I did boot-repair..
Here is my log file after Boot-Repair... [http://paste.ubuntu.com/5739884/](http://paste.ubuntu.com/5739884/)

In the advance options of Boot-Repair in other options, I can't click on 'Repair Windows Boot Files'

Just so that You know, I made a new partition in the Windows 8 of 30 GB and I have installed ubuntu on that! My Windows still exists and I can see it in the drives... PLEASE HELP ME GET BACK TO IT! I SWEAR, I"LL NEVER MESS UP IN SUCH A WAY! 
I had a pre-installed Windows 8 and I removed the Secure Boot and all to get the Ubuntu Installed and now I can't go back to WINDOWS 8 which is really a disaster! 

PLEASE, JUST PLEASE REPLY SOON!

---

### Post by oldfred on 2013-06-06
Did you turn off fast boot before installing Ubuntu?
 Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

You may be able to boot a recovery or repair directly from UEFI? Otherwise you need a Windows 8 repair flash drive.


[http://answers.microsoft.com/en-us/windows/forum/system/windows-8-consumer-preview-boot-bcd-0xc0000098/3fa65d2a-70c6-43c1-9f0a-fcbf993173db?msgId=7a44e2ca-bed5-4a57-b91a-4ce1b26ee75e](http://answers.microsoft.com/en-us/windows/forum/system/windows-8-consumer-preview-boot-bcd-0xc0000098/3fa65d2a-70c6-43c1-9f0a-fcbf993173db?msgId=7a44e2ca-bed5-4a57-b91a-4ce1b26ee75e)

 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

