---
title: "Win 8 problems"
date: 2013-01-04
forum: Installation &amp; Upgrades
---

### Post by bill-lancaster on 2013-01-04
I have read several posts on this item but am getting nowhere.

I have a new Compaq with win 8 pre-installed and wish to install Ubuntu along side it.

I've tried installing Ubuntu 12.10 (64 bit) from a DVD and get the 'Windows Boot Manager - Windows failed to start' message in the dual boot screen. 

I see the use of a flash card or usb is mentioned - would it be different from a dvd?  If so, can any one advise how to do it?

---

### Post by dino99 on 2013-01-04
i suppose you have a UEFI install; so all depend on how grub (the ubuntu boot loader) have been installed

[https://encrypted.google.com/search?hl=en&q=anki&sei=udDmUJj-Aqal0AXSjoCIDw&gbv=2#hl=en&safe=off&tbo=d&gbv=2&sclient=psy-ab&q=windows+8+ubuntu+dual+boot+uefi&oq=windows+8+ubuntu+dual+boot&gs_l=serp.1.1.0l4.0.0.2.3861.0.0.0.0.0.0.0.0..0.0.les%3B..0.0...1c.c4EPJsWQHks&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&bvm=bv.1355534169,d.d2k&fp=fbc027b25070be38&bpcl=40096503&biw=1680&bih=804](https://encrypted.google.com/search?hl=en&q=anki&sei=udDmUJj-Aqal0AXSjoCIDw&gbv=2#hl=en&safe=off&tbo=d&gbv=2&sclient=psy-ab&q=windows+8+ubuntu+dual+boot+uefi&oq=windows+8+ubuntu+dual+boot&gs_l=serp.1.1.0l4.0.0.2.3861.0.0.0.0.0.0.0.0..0.0.les%3B..0.0...1c.c4EPJsWQHks&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&bvm=bv.1355534169,d.d2k&fp=fbc027b25070be38&bpcl=40096503&biw=1680&bih=804)

---

### Post by Fahim Abdun-Nur on 2013-01-04
Maybe try this using wubi? [http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

---

### Post by bill-lancaster on 2013-01-04
Thanks for the suggestions.

Downloaded the installer and followed the instructions.

Exactly the same problem, on reboot I have a choice of Windows or Ubuntu.  The Ubuntu choice gives me the Windows Boot Manager screen saying that Windows failed to start etc

---

### Post by bill-lancaster on 2013-01-04
Also read elsewhere to hit ESC when booting the dvd then F9.  This set the dvd drive spinning plus a blue screen - that's it.

I've installed Ubuntu many times on older systems but Win8 seems to be a real problem

---

### Post by hali66 on 2013-01-04
I am having similar problems trying to get dual loading, but I am trying to boot Ubuntu off of a USB. I followed the instructions outlined here:
 
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
 
  but when I change the boot order settings in BIOS to load off of CD/DVD/USB, windows 8 simply restarts instead of booting off the USB.

---

### Post by oldfred on 2013-01-05
wubi does not work with gpt partitions. Since all Windows 8 systems preinstalled have UEFI and gpt you will not be able to use wubi.

Grub2's os-prober has a bug.
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

    
You can manually add correct entries as discussed as work arounds in the bug report or use Boot-Repair.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by bill-lancaster on 2013-01-09
Thanks oldfred,
Trouble is that I can't get the 'try ubutnu' installed.
I already have Ubuntu as an alternate os - it doesn't work as mentioned above.

I did, by chance, get rid of the Ubuntu choice - (so back to no coice of o/s) but have no record of what I did.

In Windows Boot Manager I have:-
   UEFI hp CDDVDW SH-216....
   UEFI IPv4
   UEFI IPv6
  Legacy Boot Source

Choosing  UEFI hp I get to a terminal type window with choice of Try Ubuntu (CD busy for a bit then nothing), Install Ubuntu, etc.

Just don't know where to go from here

---

### Post by oldfred on 2013-01-09
Do you have secure boot off? And fast boot off?

Then the UEFI/BIOS menu should give you the option to boot liveDVD or flash if configured as bootable devices and not just the ISO copied to it.

the newest versions are all too large for CD, do you have to use DVD or flash drive.

       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by bill-lancaster on 2013-01-10
Thanks, have now turned off secure boot and fast boot.

I'm using Ubuntu 12.10 AMD64 bit on a DVD.

My processor is an Intel Core i3, presumably the version of Ubuntu is correct (despite the reference to AMD).

I still get to the same point (choose 'try Ubuntu' then nothing.

I'm going to try to reinstall Win8 and then begin from fresh.

---

### Post by oldfred on 2013-01-10
Then it can be video issues.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
All 64 bit versions are AMD as they were first with the standard 64 bit design. A bit of interesting technical/legal history on why. Some on link below.
       The binaries for AMD64 will also work on processors that implement the Intel 64 architecture (formerly EM64T), i.e. the architecture that Microsoft calls x64, and AMD called x86-64 before calling it AMD64. They will not work on Intel Itanium Processors (formerly IA-64).
Mostly technical info:
[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

### Post by bill-lancaster on 2013-01-10
OK, clean install.  Then checked secure boot off and fast boot off.
Reboot PC with Ubuntu DVD in.  F9 for Boot Select, select DVD drive and thene select 'Try Ubuntu'.  Screen goes blank and nothing happens.

---

### Post by oldfred on 2013-01-10
If you press e at try Ubuntu can you add nomodeset? As detailed in links on nomodeset above?

---

### Post by bill-lancaster on 2013-01-17
Progress, but not quite there!
After reinstalling Win 8,F10 during boot gave me the HP Setup Utility, under Security, Secure Boot Config:-
Legacy Support - Enabled
Secure Boot - Disabled
Fast Boot - Disabled.
Reboot with Ubuntu 12.10 64 bit DVD in.
ESC brings up "Please selevt Boot Device"  I now have Legacy/ATAP DVD/SATA1 which brings up the Install Ubuntu option.
Ubuntu Installed (partitioned HD 50:50)- no problems.

Reboot, no options but straight into Win 8.  A further reboot produced a Win or HP error detected on HD, auto repair then into win 8 again.

Any ideas?

---

### Post by bill-lancaster on 2013-01-17
Ran the HP Setup, booted from Legacy Boot Sources/HD/SATA0
Somehow got the Ubuntu offer to install CD Boot Helper m(from Ubuntu DVD).
Now everything is fine, I get two choices at boot time.
Thanks for all the help.

---

### Post by oldfred on 2013-01-17
Are you directly booting from UEFI menu?

Boot-Repair can convert a BIOS install to UEFI install and add correct chain load entries to allow you to boot Ubuntu and then chain back to the Windows efi entry.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

---

### Post by bill-lancaster on 2013-01-17
Good question, second time around I didn't get the dual o/s option
I'll work at it and report

---

### Post by rishabh sachan on 2013-01-18
while installing the ubuntu and windows 1st u install the ubuntu in ur system because its works properly and i think ubuntu is gd if u have any problen in our operating system

---

### Post by Elfy on 2013-01-18
> **rishabh sachan said:**
> while installing the ubuntu and windows 1st u install the ubuntu in ur system because its works properly and i think ubuntu is gd if u have any problen in our operating system

Then once you have installed windows you'll have to reinstall grub - install windows THEN other things.

---

### Post by mörgæs on 2013-01-18
@rishabh sachan:

No, if you are installing both Windows (as opposed to working on a pre-installed system) and Ubuntu in a dual boot, Windows should be installed first.

By the way, this was not original poster's problem, so let's stop it here.

---

