---
title: "Can't boot into windows 8 anymore..."
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by RawrX32 on 2013-02-24
Hi guys, Linux newbie here and I'm having problems booting into windows 8.

I successfully managed to dual booting Kubuntu with Windows 8 by using boot-repair. But then I got the sudden urge to install Ubuntu so I deleted the kubuntu partitions to use for Ubuntu. I did all this in the windows 8 partition manager. which was a bad Idea apparently because after that I couldn't boot back into windows. I had gotten the no OS detected error.  

I didn't think much about it at the time because I had already burned Ubuntu 12.04 Lts to my usb. I figured I'd just use boot repair to fix it but...things didn't go down like that...

I was able to boot up Ubuntu just fine but when I boot into Windows 8 I get this \Efi\Microsoft\boot\bcd 0x000000f Error thingy. I tried Boot repair again and It still didn't work. And now I'm out of Ideas. I haven't had this computer over a month and it feel like I already broke it. Dell didn't give me any sort of recovery media..and I didn't bother to make one..  Any help would be Appreciated 
Link:[http://paste.ubuntu.com/5562935/](http://paste.ubuntu.com/5562935/)

---

### Post by RawrX32 on 2013-02-24
I'm gonna bump this.
Can anyone help? Or am I "S.O.L"

---

### Post by QIII on 2013-02-24
&#65279;Welcome to the forums!

Everyone's issues are very important to them and we certainly understand that. Let me assure you that you are not being ignored.
 
This is a volunteer community of users from all around the world. Not everyone here can answer every question immediately. The person with just the right answer may live in Kolkata and be asleep at the time you post, or in Geneva having dinner with his/her family or Des Moines at work. Sometimes it takes a bit for us to get to the forums and answer questions.
 
So please do not take it as a snub if you question is not answered immediately.
 
Give it 24 hours to make the rounds before bumping. Sometimes an odd bump at 36 hours or something might catch other people in a different time zone at their computers.

With this particular problem, I am sure someone will be along fairly quickly.  Since you already ran the boot info script, they should be able to hit the ground running.

Thanks.

---

### Post by RawrX32 on 2013-02-24
> **QIII said:**
> &#65279;Welcome to the forums!

Everyone's issues are very important to them and we certainly understand that. Let me assure you that you are not being ignored.
 
This is a volunteer community of users from all around the world. Not everyone here can answer every question immediately. The person with just the right answer may live in Kolkata and be asleep at the time you post, or in Geneva having dinner with his/her family or Des Moines at work. Sometimes it takes a bit for us to get to the forums and answer questions.
 
So please do not take it as a snub if you question is not answered immediately.
 
Give it 24 hours to make the rounds before bumping. Sometimes an odd bump at 36 hours or something might catch other people in a different time zone at their computers.

With this particular problem, I am sure someone will be along fairly quickly.  Since you already ran the boot info script, they should be able to hit the ground running.

Thanks.
Noted. Thanks for the reply

---

### Post by oldfred on 2013-02-24
Welcome to the forums.

It looks like a Windows error and with Windows 8 we do not know much. You have a Windows recovery in sda4, but I do not know if that is the Windows repair partition or a Vendor recovery that rewrites the system to as purchased.

But I think you need a working Windows.
       Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

    
Maybe you only can get to repair from the Windows boot menu. But it looks like Boot-Repair has renamed your Windows boot file. Some systems only will boot Windows so Boot-Repair renames the grub shim file that has the Microsoft secure boot key to be the Windows boot file and then boots Windows from the backup.  
If you rename files back with Boot-Repair and directly boot Windows from UEFI menu, you may get same error but be able to use whatever key Windows now uses (it used to be f8) to get into the repair console? Or maybe f8 works from grub entry. With BIOS some have said you have to be real quick or try multiple times as from grub to Windows is very quick.

       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

---

### Post by RawrX32 on 2013-02-24
> **oldfred said:**
> Welcome to the forums.

It looks like a Windows error and with Windows 8 we do not know much. You have a Windows recovery in sda4, but I do not know if that is the Windows repair partition or a Vendor recovery that rewrites the system to as purchased.

But I think you need a working Windows.
       Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

    
Maybe you only can get to repair from the Windows boot menu. But it looks like Boot-Repair has renamed your Windows boot file. Some systems only will boot Windows so Boot-Repair renames the grub shim file that has the Microsoft secure boot key to be the Windows boot file and then boots Windows from the backup.  
If you rename files back with Boot-Repair and directly boot Windows from UEFI menu, you may get same error but be able to use whatever key Windows now uses (it used to be f8) to get into the repair console? Or maybe f8 works from grub entry. With BIOS some have said you have to be real quick or try multiple times as from grub to Windows is very quick.

       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.
I'm sorry, I'm not quite sure of what you're asking me to.

---

### Post by JKyleOKC on 2013-02-24
Tell us the make and model of your machine and we can be more specific in the recommendations. The message from OldFred was extremely generic, because different manufacturers have set up Win8 differently and what works for some can be fatal for others. When we know exactly what you have we can trim the recommendations down!

---

### Post by RawrX32 on 2013-02-24
> **JKyleOKC said:**
> Tell us the make and model of your machine and we can be more specific in the recommendations. The message from OldFred was extremely generic, because different manufacturers have set up Win8 differently and what works for some can be fatal for others. When we know exactly what you have we can trim the recommendations down!
I'm using a Dell Inspiron 660. Anything else I need to provide?

---

### Post by RawrX32 on 2013-02-25
I got into it guys!

I  just messed around with Gparted and Ubuntu's build n partition manager

My OS wasn't Mounted. I think that's what the problem was. once I finished fix that I restarted my computer and went into
/EFI/Dell/Boot/bootmgfw.efi  and went to auto repair. I'm currently making a recovery drive.

---

### Post by aurora72 on 2013-02-25
Hello

In situations where another OS next to Ubuntu is present, it's better to make the last modification related to boot loader by using Ubuntu.

I also have a computer with FreeBSD & Ubuntu and I managed to make it dual boot by installing Ubuntu later.  In my case, both OS'es must have their own separate boot sections.  Having a proper dual boot system often requires several trial and error, reinstallation and occasional repartitioning.

---

