---
title: "Ubuntu-Studio 24.04 won't re-boot without significant coaxing"
date: 2024-06-29
forum: Installation &amp; Upgrades
---

### Post by dondidge on 2024-06-29
Greetings,

I recently installed Ubuntu-Studio 24.04 on my Lenovo Flex 7i bought last October, 2023, using an Ubuntu_Studio Live USB drive. (The computer had Win 11 on it originally, but when I installed Ubuntu-Studio, I had the installation wipe the drive.)

 So my situation is odd. After installing 24.04, it works quite well, but I can’t boot it up a second time almost ever.  
 If I just ‘turn it on’ it won’t boot. (I presume this is obviously because I don’t know what I’m doing here yet, and that's why I’m asking for help. :-)  

 I did notice that if I hit certain keys, it would boot once in awhile. I tried to figure out a pattern, and realized that I should hit the left shift key numerous times when it first powers up, stopping when the screen backlight goes off. 

 Then almost as soon as the backlight goes off, if I then hit Fn + F2 several times before the screen backlight goes on again, the majority of the time, the computer will boot and act like a normal computer within ten seconds or so. How this works, or why it works, is beyond me, but at least I can still usually get into the machine easily.  

 I invoked LVM for partition management during the install, and downloaded extra codecs, and the drive is a 1TB SSD.  

 I downloaded, and ran boot-repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) and got that printout and attached it below.  

 I thank you in advance for your help. I am very appreciative of getting into Linux after having been a computer user since the late seventies. It kind of makes this all new again, and I like that a lot. 

Here's my Boot-Info_20240629_1728.txt link [ATTACH]293927[/ATTACH].  

 Thanks,
 Don
 
 
 Operating System: Ubuntu Studio 24.04
 KDE Plasma Version: 5.27.11
 KDE Frameworks Version: 5.115.0
 Qt Version: 5.15.13
 Kernel Version: 6.8.0-36-lowlatency (64-bit)
 Graphics Platform: X11
 
 
 Processors: 12 × 13th Gen Intel® Core™ i7-1355U
 Memory: 15.2 GiB of RAM
 Graphics Processor: Mesa Intel® Graphics
 Manufacturer: LENOVO
 Product Name: 82Y2
 System Version: Lenovo Flex 7 14IRU8

---

### Post by tea for one on 2024-06-30
Some Lenovo devices have other security options in the UEFI settings.
Perhaps, have a look around to see if you can disable something to eliminate "significant coaxing"

Double check the following (if present):-
TPM (Trusted Platform Module)
PTT (Platform Trust Technology)
FTPM (Firmware Trusted Platform Module)
TPT (Trust Platform Technology)
Device Guard (some Lenovo devices)
OS Optimised Defaults (some Lenovo devices)
Lock UEFI BIOS Settings
Boot Order Lock
Enable Microsoft 3rd Party UEFI CA 

Secondly, with reference to the boot-repair report, this comment was a surprise:-
Line 228 - The default repair of the Boot-Repair utility would not act on the boot

Finally, the info from /etc/default/grub was missing in the report.

Anyway, I would suggest that you examine your UEFI settings first, because your PC does boot intermittently with gentle persuasion.

---

### Post by dondidge on 2024-06-30
Greetings,

Thanks for your quick reply. 
I found that PTT Platform Trust Technology was enabled, and I disabled it. It didn't seem to matter. 
I found that Device Guard was enabled, and I disabled it. It didn't seem to matter.
I found that Secure Boot was enabled, I disabled it, things seemed to get worse, although I can't describe how at this point, so I re-enabled it, and that's how it is now. 
Intel Virtualization is enabled. Intel VT-d is also enabled (also part of virtualization) 
I can still get it to boot most of the time. I can't honestly tell if it's gotten easier, more difficult, or is unchanged in how easily I can get into it. 

> "Finally the info from /etc/default/grub was missing." Sorry about that. I guess I don't know where to find or how to generate that info. 

This may not matter at all, but there was a brief point in time when this machine had both Ubuntu-Studio and Windows 11 on it. I selected the option to erase the hard drive when re-installing Ubuntu-Studio a couple of times since then. It is possible that installer left something behind that it shouldn't have? (Pure conjecture, I admit) 

Anyway, thanks again for your help. We haven't found it yet. 
Don

---

### Post by tea for one on 2024-07-01
> **dondidge said:**
> I found that Secure Boot was enabled, I disabled it, things seemed to get worse, although I can't describe how at this point, so I re-enabled it, and that's how it is now.
Line 59 - Your boot-repair report stated that Secure Boot was disabled
> **dondidge said:**
> I can still get it to boot most of the time. I can't honestly tell if it's gotten easier, more difficult, or is unchanged in how easily I can get into it.
Yes, sometimes, it is very difficult to tell if a UEFI setting is a help or hindrance.
> **dondidge said:**
>  Sorry about that. I guess I don't know where to find or how to generate that info.
You do not generate the /etc/grub/default independently, boot-repair report does it for you.
The fact that the info was missing is the surprise i.e. why did boot-repair produce an incomplete report?
> **dondidge said:**
> This may not matter at all, but there was a brief point in time when this machine had both Ubuntu-Studio and Windows 11 on it. I selected the option to erase the hard drive when re-installing Ubuntu-Studio a couple of times since then. It is possible that installer left something behind that it shouldn't have? (Pure conjecture, I admit)
Very unlikely, if the disk was erased.
Creating a new partition table (GPT) is often a useful solution to remove everything
> **dondidge said:**
> Anyway, thanks again for your help. We haven't found it yet.
Not yet, still cogitating

I have the germ of an idea in my tiny brain box.
Firstly, does your PC always successfully boot to a live "Try Ubuntu" session? (i.e. without coaxing)

---

### Post by dondidge on 2024-07-01
Greetings,

> **tea for one said:**
> 
Firstly, does your PC always successfully boot to a live "Try Ubuntu" session? (i.e. without coaxing)

That's a good question. Basically no. 
It found and booted from the Live USB once by itself that I'm aware of, but mostly I have to do the Fn + F12 thing to get it to come up with a boot menu. (In the BIOS, 'Boot from USB' is enabled, but I guess it doesn't think it's bootable.) 
When the boot menu appears, the alternatives are Ubuntu, which doesn't work, (being the thing I'm trying to get fixed, I presume), Hynix (the hard drive) which also doesn't work, and lastly the 'Live' USB drive itself, (identified by USB drive manufacturer's brand name). 
When I select the USB drive manually, it will boot to the 'Try' or 'Install' 'Live' menu. 
It seems like sometimes from there, it somehow ends up in the installed version of Linux on the hard drive. (I think that's the case anyway, otherwise I don't think Firefox would remember any of my tabs, nor would the system remember my mouse preferences. Does that make sense?)

Thank you,
Don

---

### Post by oldfred on 2024-07-01
While report on boot order line 62 shows Ubuntu as first in boot order, I wonder if it still is trying to boot Windows.
Some systems, HP typically, require you to change boot order in UEFI settings, not from UEFI one time boot menu.

Some older systems would also only boot "Windows Boot Manager" in UEFI. But they did not check actual boot file, so we created a new "Window" boot entry that booted using Ubuntu/grub's shimx64.efi for UEFI boot. Shim works if Secure boot on or off.

You can delete 0000 entry for Windows and create a new one.
Check that 0000 is correct entry to delete.
Noted that new version of efibootmgr -v seems to output much more detail where old efibootmgr only entry only showed names. But new efibootmgr only shows details of partUUID/GUID so we know which ESP your are using to boot.
sudo efibootmgr 
or 
sudo efibootmgr -v
Delete
sudo efibootmgr -b XXXX -B #where XXXX is entry you want to delete.

See also
man efibootmgr

To add a Windows entry to boot Ubuntu.
The efibootmgr assumes default of sda1 for ESP, so you have to specify if any other location for ESP.
Create new Windows entry that boots shim.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1

UEFI uses partUUID to know ESP to use. You can see the partuuid is different in old Windows entry & ubuntu entry. So we can see you created new ESP for UEFI boot files. Or old Windows entry has no use now.

---

### Post by dondidge on 2024-07-01
Greetings, 

> sudo efibootmgr -v

sudo efibootmgr -b 0000 -B 

sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1

I believe I followed through on this correctly. Here is a console printout of what happened. 

                        [FONT=monospace][COLOR=#54ff54]**didge@didge-Lenovo-Flex-7-14IRU8**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo efibootmgr -v [/COLOR]
[sudo] password for didge:  
BootCurrent: 0000 
Timeout: 0 seconds 
BootOrder: 0000,0001,0013,0014,0015,0016,0017 
Boot0000* Windows Boot Manager  HD(1,GPT,4a550efe-8ca1-4e80-a22c-4cd585abc4a4,0x800,0x219800)/File(\EFI\ubuntu\shimx64.efi) 
     dp: 04 01 2a 00 01 00 00 00 00 08 00 00 00 00 00 00 00 98 21 00 00 00 00 00 fe 0e 55 4a a1 8c 80 4e a2 2c 4c d5 85 ab c4 a4 02 02 
/ 04 04 34 00 5c 00 45 00 46 00 49 00 5c 00 75 00 62 00 75 00 6e 00 74 00 75 00 5c 00 73 00 68 00 69 00 6d 00 78 00 36 00 34 00 2e 00 65
00 66 00 69 00 00 00 / 7f ff 04 00 
Boot0001* Ubuntu        HD(1,GPT,4a550efe-8ca1-4e80-a22c-4cd585abc4a4,0x800,0x219800)/File(\EFI\ubuntu\shimx64.efi) 
     dp: 04 01 2a 00 01 00 00 00 00 08 00 00 00 00 00 00 00 98 21 00 00 00 00 00 fe 0e 55 4a a1 8c 80 4e a2 2c 4c d5 85 ab c4 a4 02 02 
/ 04 04 34 00 5c 00 45 00 46 00 49 00 5c 00 75 00 62 00 75 00 6e 00 74 00 75 00 5c 00 73 00 68 00 69 00 6d 00 78 00 36 00 34 00 2e 00 65
00 66 00 69 00 00 00 / 7f ff 04 00 
Boot0010  Setup FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9) 
     dp: 04 06 14 00 66 8b 1c 72 6c 42 86 4e 8e 99 34 57 c4 6a b0 b9 / 7f ff 04 00 
Boot0011  Boot Menu     FvFile(86488440-41bb-42c7-93ac-450fbf7766bf) 
     dp: 04 06 14 00 40 84 48 86 bb 41 c7 42 93 ac 45 0f bf 77 66 bf / 7f ff 04 00 
Boot0012  UEFI Diagnostics      FvFile(f8397897-e203-4a62-b977-9e7e5d94d91b) 
     dp: 04 06 14 00 97 78 39 f8 03 e2 62 4a b9 77 9e 7e 5d 94 d9 1b / 7f ff 04 00 
Boot0013* NVMe: VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a4) 
     dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 00 1c 19 99 32 d9 4c 4e ae 9a a0 b6 e9 8e b8 a4 / 7f ff 04 00 
Boot0014* USB FDD:      VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49) 
     dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 6f f0 15 a2 88 30 b5 43 a8 b8 64 10 09 46 1e 49 / 7f ff 04 00 
Boot0015* USB HDD:      VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803) 
     dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 33 e8 21 aa af 33 bc 47 89 bd 41 9f 88 c5 08 03 / 7f ff 04 00 
Boot0016* USB CD:       VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55) 
     dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b 86 70 12 96 aa 5a 78 48 b6 6c d4 9d d3 ba 6a 55 / 7f ff 04 00 
Boot0017* USB LAN:      VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,e854bca4cae7704ca322b00da0376322) 
     dp: 03 0a 24 00 d2 38 78 bc 82 0f 60 4d 83 16 c0 68 ee 79 d2 5b e8 54 bc a4 ca e7 70 4c a3 22 b0 0d a0 37 63 22 / 7f ff 04 00[/FONT]

  

So that happened. I then checked to see if it could boot on its own, and it did so, once. 
I can still get it to boot using the 'shift' and 'Fn + F2' keys like I'd previously mentioned, but other than that, no operational change. 

Thank you,
Don

---

### Post by oldfred on 2024-07-01
The efibootmgr list is just to see what entries you have.
You still show 0000 as Windows entry.

---

### Post by dondidge on 2024-07-01
Greetings,

I apparently misunderstood the purpose of this quoted  part. I thought it would create the '0000' entry new, and I thought it  did so. 

> To add a Windows entry to boot Ubuntu.
The efibootmgr assumes default of sda1 for ESP, so you have to specify if any other location for ESP.
Create new Windows entry that boots shim.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1

Those parameters looked good to me so I ran them that way. 
I'm sorry I thought that's what you were asking me to do. 
I entered those lines and ran them, which gave me a different printout than I'd had before.  

Here is the previous printout:
[SIZE=1][FONT=courier new]
[/FONT][/SIZE][SIZE=2][SIZE=1][FONT=courier new] [COLOR=#54ff54]didge@didge-Lenovo-Flex-7-14IRU8[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]~[/COLOR][COLOR=#000000]$ sudo efibootmgr[/COLOR]
[sudo] password for didge:  

BootCurrent: 0001 

Timeout: 0 seconds 

BootOrder: 0001,0013,0014,0015,0016,0017 

Boot0001* Ubuntu        HD(1,GPT,4a550efe-8ca1-4e80-a22c-4cd585abc4a4,0x800,0x219800)/

File(\EFI\ubuntu\shimx64.efi) 

Boot0010  Setup FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9) 

Boot0011  Boot Menu     FvFile(86488440-41bb-42c7-93ac-450fbf7766bf) 

Boot0012  UEFI Diagnostics      FvFile(f8397897-e203-4a62-b977-9e7e5d94d91b) 

Boot0013* NVMe: VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a4) 

Boot0014* USB FDD:      VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49) 

Boot0015* USB HDD:      VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803) 

Boot0016* USB CD:       VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55) 

Boot0017* USB LAN:      VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,e854bca4cae7704ca322b00da0376322)
[/FONT][/SIZE]

 [/SIZE]
I apologize if I got confused and did the wrong thing here. 

Here is the new printout:
[FONT=monospace][COLOR=#54ff54]**didge@didge-Lenovo-Flex-7-14IRU8**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ efibootmgr [/COLOR]
BootCurrent: 0000 
Timeout: 0 seconds 
BootOrder: 0000,0001,0013,0014,0015,0016,0017 
Boot0000* Windows Boot Manager  HD(1,GPT,4a550efe-8ca1-4e80-a22c-4cd585abc4a4,0x800,0x219800)/File(\EFI\ubuntu\shimx64.efi) 
Boot0001* Ubuntu        HD(1,GPT,4a550efe-8ca1-4e80-a22c-4cd585abc4a4,0x800,0x219800)/File(\EFI\ubuntu\shimx64.efi) 
Boot0010  Setup FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9) 
Boot0011  Boot Menu     FvFile(86488440-41bb-42c7-93ac-450fbf7766bf) 
Boot0012  UEFI Diagnostics      FvFile(f8397897-e203-4a62-b977-9e7e5d94d91b) 
Boot0013* NVMe: VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a4) 
Boot0014* USB FDD:      VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49) 
Boot0015* USB HDD:      VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803) 
Boot0016* USB CD:       VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55) 
Boot0017* USB LAN:      VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,e854bca4cae7704ca322b00da0376322)

Thanks again. 
Don
[/FONT]

---

### Post by oldfred on 2024-07-01
Even though descriptions are different, both the ubuntu & Windows boot entries are using the same shimx64.efi.

Do you get any difference in booting between the two?
If so, it is something in UEFI, that you may not be able to change or a UEFI setting that can be changed.

---

### Post by dondidge on 2024-07-01
Greetings,

I have not been booting between the two. I do not have that option. I never see a menu about choice when booting, (a GRUB menu?), (I presume that is what would give me a choice). 
When I turn on the machine, nothing is displayed on the screen. I (normally) hit the left 'Shift' key a dozen times or so, then when the backlight goes out on the display, (in seven or eight seconds I suppose), I pause a couple of seconds and then hit Fn +F2  repeatedly just before and after the backlight comes back on, and it will generally boot by itself from there. 
As far as I know, nothing operationally has changed for me since I made the last change I'm talking about here. 
I'm sorry if I'm being confusing. I don't mean to be.
Thanks again,
Don

---

### Post by oldfred on 2024-07-01
There are two menus.
One is UEFI one time menu, same as you use to boot USB flash drive/live installer.
And other is grub menu.

UEFI menu requires you to press the correct key often f12, but Lenovo seems to not always be consistent. Check manual.
With one install, grub normally does not show as it assumes you just want to boot that install.

With UEFI, you can press Escape key just after UEFI/BIOS screen but before grub menu would normally appear. Often have to try more than once.
And if UEFI fast boot is on, that assumes you have made no system changes and immediately boots. Then no time to press any key.

Best to have UEFI fast boot off, when making changes. But once configuration finalized you can turn it back on.
You can get back into UEFI settings from grub, command line or total cold boot (full power down). Warm reboot uses fast startup.

---

### Post by dondidge on 2024-07-02
Greetings oldfred,

> **oldfred said:**
> There are two menus.
One is UEFI one time menu, same as you use to boot USB flash drive/live installer.
And other is grub menu.

UEFI menu requires you to press the correct key often f12, but Lenovo seems to not always be consistent. Check manual.
With one install, grub normally does not show as it assumes you just want to boot that install.

With UEFI, you can press Escape key just after UEFI/BIOS screen but before grub menu would normally appear. Often have to try more than once.
And if UEFI fast boot is on, that assumes you have made no system changes and immediately boots. Then no time to press any key.

OK, thank you for making it clear to me what to call which menu, that makes it easier to talk about this stuff. 
So I'll start over in describing my 'problem'.  
When I turn on the laptop, I can tell that the power is on *only* because the keyboard backlight lights up, and the screen backlight lights up, but there is no information displayed on the screen (usually), no logo for Lenovo or Ubuntu. Not even a mouse cursor. 
(I say 'usually' because on the extremely rare occurrence that I wait for it, and my waiting is prompted by my having run some command of some kind like even '**grub-install -V**', sometimes it then boots by itself, but then it won't do that again a second time.) 
When it does boot by itself, I usually do get all three of the computer logo, Ubuntu logo, and even a mouse cursor, but only for a couple of tenths of a second.)

Typically when I'm just waiting to see if it will boot, the screen backlight will go off for a few seconds after several, maybe ten seconds, and then come back on, but nothing else will happen. 
So I started intervening to see if I could 'trick' it into booting. That's when I discovered the left shift key, and then the Fn + F2 sequences to let me in. That still mostly works. Sometimes it takes two or three times to get booted up, but once in awhile, it'll boot up completely by itself, (if I just wait for it. Mostly though it's just waiting for Godot, (the man who never comes)). 
I'm lost. I don't know what makes a computer do one thing one time only and then (virtually) never come back to that sequence. 

Thank you,
Don

---

### Post by tea for one on 2024-07-02
How about a bit of an adventure?
> **dondidge said:**
> and lastly the 'Live' USB drive itself, (identified by USB drive manufacturer's brand name)
When I select the USB drive manually, it will boot to the 'Try' or 'Install' 'Live' menu
You should be able to set this option as default i.e. always boot external usb device first
(if a usb is not attached, then your PC firmware will try the second priority e.g. an nvme disk)

If you manage to set USB device as first boot priority, you can create a bootable usb containing rEFInd. 
Nothing will be altered on your internal disk unless you install rEFInd later.
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html) > A USB Flash Drive Image File
A USB with rEFInd for emergency use may help to find and boot an OS (if Grub is damaged/not responding)

Options include:-
(a) Boot the kernel directly
e.g. Boot boot\vmlinuz-6.8.0-36-lowlatency

(b) Find and boot the grub efi file
e.g. Boot EFI\ubuntu\grubx64.efi from 510 MiB FAT volume

(c) Start an EFI shell
The boot instructions are similar to this:-
Identify your Efi System Partition e.g. FSO
Type FSO: i.e. FSO and colon symbol (press enter)
Then type \EFI\ubuntu\grubx64.efi (and hit enter)

Try Option (a) first - screenshot attached

---

### Post by oldfred on 2024-07-02
+1 tea for one's post on rEFInd.

I have an old USB flash drive that was too small for anything. 256MB.
But rEFInd fit on that, so I have that flash drive with rEFInd as one of my emergency boot flash drives. Although now using mostly SSDs as external boot devices.
The rEFInd flash drive saved me several times when my older UEFI system did not like too many drives with UEFI boot. It would lock up and not boot anything. And rEFInd then was the only bootable device.

---

### Post by dondidge on 2024-07-02
Greetings,

I discovered that even if I don't have anything plugged into a USB port, hitting Fn + F12 (slightly furiously) after the screen backlight goes out that first time, (after five to seven seconds?), the machine will boot and land me in the installed version of Ubuntu-Studio 24.04. 
I can deal with that little detour. 
Things work. 
I thank you for your help in moving this along, but I think I'm going to leave it here for now. 
I somehow thought this was going to be trivial to fix. 
Where it is at now though is simple to deal with and I can live with it working this way. 
Maybe it'll sort itself out in August when the first update comes out. I can wait until then, and revisit it if it doesn't get fixed automatically then. 
Thank you for helping me. 
You've been much more responsive than other OS providers! 
Best to all,
Don

---

### Post by osirisgothra on 2024-10-22
same issue, My setup is very similar to yours also. I can log in once, but not twice, although I haven't been able to "coax" mine as you did. Hope your info helps me :) I know this is reverse as usual just shouting out saying your not alone.

---

