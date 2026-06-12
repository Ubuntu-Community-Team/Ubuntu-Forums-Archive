---
title: "Unable to dual boot Windows after installing 14.04LTS (UEFI / Legacy)"
date: 2015-10-29
forum: Installation &amp; Upgrades
---

### Post by haffer on 2015-10-29
Hi guys,


Once upon a time, I had a computer(Thinkpad Edge 530) with pre-installed Windows 8. Then I foolishly wanted a dual boot with Windows 10 for games, and Ubuntu for school/work. Now I have Windows 10 installed in UEFI mode, and Ubuntu 14.04 in Legacy mode. It boots directly into Ubuntu, and I cannot access my BIOS by interrupting start-up(splash-screen says "Press Enter").


Here is the story.. 


1. Upgraded from win8 to win10.
1.1 Formatted harddrive to get a clean win10. Came with warning: Not able to get back to win8. Proceeded anyway.
1.2 Created a restore point. 


2. Created a boot-able USB with Ubuntu 14.04.


3. Computer did not recognize this USB, even though I had changed the boot-up order. It still booted directly into win10.
3.1 Changed, in BIOS, to Legacy mode, instead of UEFI. To do this, I had to disable safe boot. Did not disable fast boot. 


4. Computer did still not recognize USB, and was now stuck in infinite loop with "Media test failure" and "Exiting PXE ROM"
4.1 Splash screen said "Press Enter to interrupt start", but was - and still are - not able to do so. Tried multiple key-combinations.
4.1.1 Tried unplugging AC and battery, hold fn+r, insert AC and power up. This made the computer now beep 8 times on start, and had black screen(F***, I bricked it...)
4.1.2 Tried fn+b combo and came back to infinite loop, as in point 4. 
4.2 Tried to insert internet-cable at school, and it booted some winPE school version. So it was not bricked (wuuhu!)


5. Inserted an other boot-able USB, with Ubuntu 14.04, which worked on my old computer.
5.1 This one worked, and I could install Ubuntu. But in Legacy mode. During install, it could not recognize my windows OS. 


I have tried boot-repair, but it replies with an error:
"The current session is in Legacy mode. Please reboot the computer, and use this software in an EFI session. This will enable this feature. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd](www.sourceforge.net/p/boot-repair-cd)), after making sure your BIOS is set up to boot USB in EFI mode."
	But, I cannot access my BIOS... 


The boot-info comes with following output: [http://paste2.org/YOHBEeL9](http://paste2.org/YOHBEeL9)


And I can even see my Windows files from Ubuntu. I called Lenovo support about getting into BIOS, but she wasn't of much help - "If it says "Press Enter", then press Enter. Otherwise I don't know what you can do" .. 


How do I get some bootloader(grub?) to manage both Windows and Ubuntu, so I can actual use both systems? OR somehow get into BIOS and change to UEFI mode. Do I have to unplug my harddrive, which some threads suggests? 


If I somehow can boot into Windows then I'll happily reinstall my Ubuntu using UEFI.. Any suggestions?

---

### Post by oldfred on 2015-10-29
Microsoft requires Windows to boot quickly.
So vendors have set UEFI to use a fast boot setting which does not scan system for changes, but assumes no hardware changes. And since that is usually the case it works for many. And Windows seems faster even though it is not really Windows but UEFI/BIOS.
But if full boot required, you can usually do that thru Windows, but if Windows not working then a major problem.
Some will do the full UEFI boot so you have time to get into UEFI, if you do a cold boot or boot from total power down. If laptop, you also need to remove battery. Hold power switch for 10 sec or so to drain all power. Then boot and immediately press correct key(s) to get into UEFI.
Some have a tiny reset hole/switch at bottom of system, others have to open case (usually desktops) and jumper pins on motherboard for a full reset.

Someone with a Lenovo post this, not sure if in other links users posted details or not:
 Lenovo Laptops there is NOVO button on left side

 > Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.

       
 T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

If you can boot live installer in UEFI mode, Boot-Repair can convert a BIOS install to UEFI.
But all it really is doing is uninstalling grub-pc and installing grub-efi-amd64. But I would not do that unless you can get into UEFI as often you need that to change other settings as well.

---

### Post by haffer on 2015-10-29
Thanks for the reply!

> **oldfred said:**
> Microsoft requires Windows to boot quickly.
So vendors have set UEFI to use a fast boot setting which does not scan system for changes, but assumes no hardware changes. And since that is usually the case it works for many. And Windows seems faster even though it is not really Windows but UEFI/BIOS.
But if full boot required, you can usually do that thru Windows, but if Windows not working then a major problem.
Some will do the full UEFI boot so you have time to get into UEFI, if you do a cold boot or boot from total power down. If laptop, you also need to remove battery. Hold power switch for 10 sec or so to drain all power. Then boot and immediately press correct key(s) to get into UEFI.
Some have a tiny reset hole/switch at bottom of system, others have to open case (usually desktops) and jumper pins on motherboard for a full reset.


I'm on a laptop, so I'll try the cold boot thing a couple of times. 

> **oldfred said:**
> 
If you can boot live installer in UEFI mode, Boot-Repair can convert a BIOS install to UEFI.
But all it really is doing is uninstalling grub-pc and installing grub-efi-amd64. But I would not do that unless you can get into UEFI as often you need that to change other settings as well.

So if I convert my Ubuntu into UEFI, then I might not be able to boot any of them? If I can, then this will be a solution I guess..? Haven't been in BIOS before installing Ubuntu, and if both work - I see no reason to change stuff in there.

---

### Post by oldfred on 2015-10-29
Many brands have modified UEFI to use description as part of boot. And of course only description allowed is "Windows". Use of description is specifically not allowed in UEFI standard. Since so many vendors now are doing this I assume a major vendor of operating systems has suggested it.

We have many work arounds for systems that make it difficult. But best to have access to UEFI, but most changes are in using live installer to edit efi partition or UEFI entries.
One of links above used the rename of bootx64.efi as a work around on his Lenovo. Not sure if all Lenovos need that or not.

---

### Post by haffer on 2015-10-30
I've tried cold booting without any results... 

I've also tried editing /etc/grub.d/40_custom and adding:
```

menuentry "Windows" {
set root=(hd0,4)
chainloader +1
}
```
And running both ```
 sudo update-grub 
``` and ```
 sudo update-grub2 
```

Because this is where Gparted states that my Windows partition is. And I've also tried (hd0,x) , x = 1,2,3,4 without any luck.. 
[ATTACH=CONFIG]265270[/ATTACH]

The error at sda3 reads:

Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/sda3 is missing



Am I on the right track by editing something in grub??

---

### Post by oldfred on 2015-10-30
With UEFI you do not boot the Windows partition from grub, but chain load the the Windows efi boot file in the ESP.

But grub will find the Windows boot entry with:
sudo update-grub

But if hibernated or its fast boot is on, then it cannot find it as it will not mount hibernated or NTFS needing chkdsk. Also entry below will not work as grub only boots working Windows.

Typical entry should be:

But you have to have your efi partition sda1 or 2 as [COLOR=#ff0000]hd0,gpt2[/COLOR] and your [COLOR=#ff0000]UUID[/COLOR] for the ESP.
```
 menuentry "Windows 8 UEFI" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='(hd0,[COLOR=#ff0000]gpt2[/COLOR])'
  search --fs-uuid --no-floppy --set=root [COLOR=#ff0000]4f84-ee2e[/COLOR]
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}


```

---

