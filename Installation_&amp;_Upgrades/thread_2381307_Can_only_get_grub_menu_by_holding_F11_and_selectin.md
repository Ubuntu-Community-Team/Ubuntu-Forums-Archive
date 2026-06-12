---
title: "Can only get grub menu by holding F11 and selecting HDD to boot"
date: 2017-12-29
forum: Installation &amp; Upgrades
---

### Post by gazialankus on 2017-12-29
I have Windows 10 in the first drive (/dev/sda) and Ubuntu 16.04 in a partition in the second drive (/dev/sdb). I can't get the grub boot menu unless I hold F11 during boot and tell BIOS to use the second drive (/dev/sdb) from the menu. If I set the second drive as the drive to boot from in BIOS settings (MSI Click Bios 5), it boots into the grub command line (the one that says "minimal bash-like editing is supported...").

Here is my Boot Repair logs: [https://paste.ubuntu.com/26278407/](https://paste.ubuntu.com/26278407/) 

Boot Repair with various options or update-grub did not fix it. 

Here is a list of trials and their logs with Boot Repair: 
[http://paste.ubuntu.com/26277894/](http://paste.ubuntu.com/26277894/)
[http://paste.ubuntu.com/26278089/](http://paste.ubuntu.com/26278089/)
[http://paste.ubuntu.com/26278202/](http://paste.ubuntu.com/26278202/) (this one said an error occured during the repair, I think I purged etc. in this one)
[http://paste.ubuntu.com/26278407/](http://paste.ubuntu.com/26278407/)


I would be very happy if someone can take a look at the pastebin and tell me how to fix this situation.

Also, here is the Ask Ubuntu question that I had posted before about the same situation: [https://askubuntu.com/questions/985253/grub-with-windows-10-and-ubuntu?noredirect=1#comment1585982_985253](https://askubuntu.com/questions/985253/grub-with-windows-10-and-ubuntu?noredirect=1#comment1585982_985253)

---

### Post by ajgreeny on 2017-12-29
I think you have installed Ubuntu in legacy BIOS mode but Windows is in UEFI mode, hence the problem; the two OSs must both be installed in the same mode, either BIOS or UEFI if you want them to boot from a single boot process.

If this is a new install of Ubuntu you may want to reinstall using UEFI, or you could try the repair suggested by the Boot-info output.
Wait for more replies before jumping in as I am no great expert in this problem, and you can at present use both OSs, even if not as you would wish to.

---

### Post by oldfred on 2017-12-29
What brand/model system?
Some will only let you manually boot (your f11) unless you do a work around. As posted on AskUbuntu. [https://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](https://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Same work arounds are also posted in the link in my signature below.

Grub only installs in UEFI mode to ESP - efi system partition on drive seen as sda. 

But you managed to install in UEFI mode on a MBR(msdos) drive. That works in your case as booting is thru the ESP on the gpt partitioned drive sda.

I suggest converting sdb to gpt, but that is not the issue.
UEFI standard suggests gpt, but Ubuntu installer does use MBR (in some configurations), so it can be booted in either UEFI or BIOS boot mode.
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 
    If you do convert, be sure to back up all data first.

---

### Post by gazialankus on 2018-01-02
Here's my system details: [http://www.sanalmarketim.com/Urun/EXPER-XCELLERATOR-XP870-Gaming-Core-i7-6700-Z170-16GB-240GB-SSD--2TB-GTX1080-Wi-Fi-Win-10-700W-Full-Tower/615](http://www.sanalmarketim.com/Urun/EXPER-XCELLERATOR-XP870-Gaming-Core-i7-6700-Z170-16GB-240GB-SSD--2TB-GTX1080-Wi-Fi-Win-10-700W-Full-Tower/615) 

So, I converted sdb to GPT using EaseUS free version. Then I ran boot repair with suggested settings in Ubuntu. The first time it gave an error in grub-install. I ran that line manually later, which did not help. I ran boot repair one more time, this time without an error. It directly boots into Windows. 

I changed settings in BIOS to boot from sdb. After a full shutdown, that booted into grub command line... Then I set it back to sda.

I did the bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi in Windows as boot repair suggested. Still boots into Windows. 



Here are the logs of the two boot repair executions: 

[https://paste.ubuntu.com/26305047/](https://paste.ubuntu.com/26305047/) (after this it said "An error occurred during the repair."). In logs I saw that the error was related to [COLOR=#000000]grub-install. I ran it manually without errors, but did not help. 
[/COLOR][https://paste.ubuntu.com/26305132/](https://paste.ubuntu.com/26305132/) (this is the second time. no errors, but did not help)

I appreciate all the help. I wish I had time to learn all about EFI and stuff. Should I try various options in the Ubuntu boot repair tool? Any help will be appreciated.

**Edit:** should I just reinstall Ubuntu in UEFI mode? What's the easiest and surest way to get this done?

---

### Post by oldfred on 2018-01-02
If you go into UEFI boot menu  - f11, do you see these two options and can you then boot Ubuntu entry?

```
efibootmgr -v
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0000
Boot0000* Windows Boot Manager	HD(1,GPT,f5c3047b-6bd8-435b-968c-4fbcadd766c6,0x800,0x32000)/File(EFIMICROSOFTBOOTBOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* ubuntu	HD(1,GPT,f5c3047b-6bd8-435b-968c-4fbcadd766c6,0x800,0x32000)/File(EFIubuntushimx64.efi)

```

And then with efibootmgr change boot order?
       Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok. or 0000,0001
sudo efibootmgr -o 1,0
Then has order changed?
sudo efibootmgr -v
see also 
man efibootmgr

---

### Post by gazialankus on 2018-01-03
ATM I'm not in front of this computer but I'll do my best to answer now and will add later when I'm in front of it. 

Yes, when I hit F11 I see these two entries (so that menu lives in the HDD and not my BIOS? I don't get EFI...) Selecting ubuntu opens up the grub menu, from which I can boot into ubuntu (or Windows if I wanted to).

HOWEVER, after some of these boot repair tries, the two entries in this menu both say the same thing: Windows Boot Manager (I think it's the case ATM). Still, selecting one of them boots Windows and selecting the other opens up the Grub menu. It went back and forth between saying both Windows and one Windows and one Ubuntu as I messed with boot repair. 

I will play with efibootmgr when I'm in front of the computer and will let you know. Thank you!

---

