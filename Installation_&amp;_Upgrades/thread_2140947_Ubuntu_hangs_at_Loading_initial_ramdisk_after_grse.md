---
title: "Ubuntu hangs at Loading initial ramdisk after grsecurity kernel patch"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by RinkeB on 2013-05-01
Hej fellow Ubuntu fans,

I am trying to patch my Ubuntu version with [grsecurity]("http://grsecurity.net/"). 
I'm working with Ubuntu Server 12 32bit inside a Windows 7 virtual machine.
Windows 7 is running VirtualBox.
For patching I used [this]("http://en.wikibooks.org/wiki/Grsecurity/Configuring_and_Installing_grsecurity") tutorial, which is the official for grsecurity.
In addition, I compiled and install the debian files with [this]("http://www.howtoforge.com/kernel_compilation_ubuntu") tutorial.
Now when I try to boot Ubuntu, it hangs at the following point:
[ATTACH=CONFIG]242035[/ATTACH]

Also I can't use recovery mode anymore, because I am unable to select anything. 
The ‘[[B’ character sequence appears when I press the down button.
[ATTACH=CONFIG]242036[/ATTACH]
I really have no clue what to do.
I googled around a lot for the error but I couldn't find a working solution.

Some information about my system:

```
rinke@ubuntuserver:~$ lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
00:03.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 01)
00:06.0 USB controller: Apple Inc. KeyLargo/Intrepid USB
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0b.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
00:0d.0 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 02)

```

Please help me get past this annoying screen! ;)
If you need more information please tell me, I am out of options.
I know my way around Linux, but I wouldn't call myself an advanced user.

---

### Post by RinkeB on 2013-05-02
After hours of tweaking and with some help I was finally able to boot into the kernel patched with grsecurity.
The kernel is Linux 3.2.44 and grsecurity is of the corresponding version.
Now I run into this error:

[IMG]http://s4.postimg.org/sbysecudp/kernel_panic.jpg[/IMG]

I googled around a lot to find an answer, but so far without any results.
Can you give me some advice or tips on how to fix this error?

---

