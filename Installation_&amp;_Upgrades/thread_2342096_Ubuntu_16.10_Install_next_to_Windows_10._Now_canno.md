---
title: "Ubuntu 16.10 Install next to Windows 10. Now cannot find Windows 10!"
date: 2016-11-03
forum: Installation &amp; Upgrades
---

### Post by joecichocki on 2016-11-03
I followed the instructions to install Ubuntu 16.10 on my hard drive alongside Windows 10. It shows Ubuntu as using 267Gb disk space, meaning there is another 230Gb on the disk with my Windows 10 stuff. But I cannot find it, and it doesn't show up at startup. I only show Ubuntu boot options. 

I have used Ubuntu for about ten to fifteen years, but only because it is so easy to use out of the box, not because I am computer savvy or know how to use the terminal or commands, although I have done so a couple of times. But nothing complicated. 

I would be forever grateful if someone could point me in the right direction here so I might be able to retrieve my Windows 10 boot option or at least maybe my files...

Joe cichocki
[EMAIL="joecichjr@sbcglobal.net"]{removed email}[/EMAIL]


Thanking you so much, even if you just look...

---

### Post by ka55o5 on 2016-11-03
> **joecichocki said:**
> [..] instructions to install Ubuntu 16.10 on my hard drive alongside Windows 10.
All you have to do is provide EMPTY SPACE on a drive, it does **not** need to be a partition, there, even: the Ubuntu installer will automagically use the space to create the needed partition(s) and install - AND add your (existing!) Windows loader to its Grub2.

[color=gray]*****Just btw. :)[/color]

**Edit**: It SHOULD be, rather, simple to recover Windows, repair /restore the "[Windows 10 MBR]("https://www.google.com/search?q=fix+windows+10+bootloader")". Probably there's some built-in way, for Windows 10, whatever it may be - if you can /can't boot into it; BUT, the easiest way is to run some Command Prompt CMDs, from a Windows DVD /USB boot media... 

(Such as having had created a [Recovery Drive thingy]("http://www.howtogeek.com/131907/how-to-create-and-use-a-recovery-drive-or-system-repair-disc-in-windows-8/"))

Once you boot from USB, find a way to open the Command Prompt and run 2 CMDs, right (it **can** get *quite* complicated with uEFI BIOS, motherboards; hopefully it's NOT the case with your b0x); "We need to use the Bootrec.exe tool. Click on command prompt and type in the following commands, one after the other": 

[list][*]bootrec /fixMbr
[*]bootrec /fixboot[/list]
**+** "bootrec /RebuildBcd", previously, as in: **[http://www.thewindowsclub.com/repair-master-boot-record-mbr-windows](http://www.thewindowsclub.com/repair-master-boot-record-mbr-windows)**

**Reference**, [https://support.microsoft.com/en-us/kb/927392](https://support.microsoft.com/en-us/kb/927392) ("Use Bootrec.exe in the Windows RE to troubleshoot startup issues")

P.S.
"**Solution 2**: Rebild MBR in Windows 10 with AOMEI Partition Assistant"```
http://www.disk-partition.com/windows-10/fix-mbr-windows-10-0708.html
```(If you're finding it difficult to do manually :))

---

### Post by ka55o5 on 2016-11-03
Just a few moar links, didn't mean to make the answer above so complicated (& jumbled!), it's late over here - sorry about that! xD

[list][*][http://pureinfotech.com/repair-master-boot-record-mbr-windows-10/](http://pureinfotech.com/repair-master-boot-record-mbr-windows-10/)
[*][http://www.digitalcitizen.life/command-prompt-fix-issues-your-boot-records](http://www.digitalcitizen.life/command-prompt-fix-issues-your-boot-records)
[*][https://neosmart.net/wiki/fix-mbr/](https://neosmart.net/wiki/fix-mbr/)[/list]

**++** THE link /answer from my previous post, above, which *should* work is, again @```
http://www.thewindowsclub.com/repair-master-boot-record-mbr-windows
```

**Edit**: Forgot to add, AGAIN, there's no need to get into panic mode and think about recovering files, or whatever - you SHOULD be able to, just repair the Windows bootloader and get the PC working normally again - just the same as before having installed Linux! :) 

(Afterwards, you can take a look at what partitions - or, whatever - the installation had created and start taking care of that, through Computer Management and/or using a partition editor /program software)

P.S. However, there **IS** a possibility that you might've over-written, deleted, your Windows partition (or, *something*) & then you're -really- in for it; just, btw! xD

[color=gray]^^ You'll know, if there's no way to repair /recover the bootloader.[/color]

Edit #33, if your C:\Windows is really gone (which, HOPEFULLY it isn't), then it's gonna be a LONG road, to get anything back... The MOST IMPORTANT thing in this case is to keep your computer **OFF**. You don't want anything writing to the disk, in this case!..

---

### Post by ubfan1 on 2016-11-03
In what mode is Windows installed (UEFI or legacy)?  Ubuntu needs to be installed in the same mode, if not, maybe that explains what you are seeing.  The Ubuntu install media can boot both ways, so it's up to your settings and machine how it boots. If Windows 10 came on your machine, it's probably UEFI.  Look in /sys/firmware and if there is an efi or efivars directory, Ubuntu is in UEFI mode, otherwise, legacy.  A UEFI installation does not even use an MBR, so first determine how things are installed.

---

### Post by joecichocki on 2016-11-03
I did gain access to my Windows 10 partition by depressing f8 while booting. Everything is there and working. However, that whole process seems to be divorced from my Ubuntu partition, where only Ubuntu alternatives are listed during startup.

---

### Post by oldfred on 2016-11-04
Removed email. You would gets lots of spam as forum is regularly scanned all the time.

You would seem to have installed Ubuntu in BIOS boot and have Windows in UEFI boot mode. The two modes are not compatible and once you start booting in one you cannot switch. Or you cannot dual boot from grub menu but only from UEFI one time boot key. Some systems may require you to turn on/off UEFI or CSM/legacy/BIOS boot settings.

If drive is gpt, Boot-Repair's advanced mode can convert a BIOS Ubuntu install to UEFI boot. It un-installs grub-pc (BIOS) and installs grub-efi-amd64 (UEFI).

How you boot install media and repair media UEFI or BIOS is then how it installs. Best to always boot in UEFI mode.
UEFI will give two boot modes for Ubuntu flash drive, UEFI:flash and flash (BIOS) where flash is brand, name, or label of flash drive you are using.

       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

