---
title: "Frustrating installation"
date: 2017-08-24
forum: Installation &amp; Upgrades
---

### Post by Phil S on 2017-08-24
Hello
I resurrected an Asus motherboard and i7 CPU and eventually got a semi-working computer going, albeit at the BIOS only.
I downloaded Ubuntu 16 (latest release) and put it on a brand new USB stick.
After some faffing around (memory etc.) I got it to boot and run from the USB. Great (thank you Pete/Rufus).
Then I went to install on a new WD Blue 1TB HDD. After two days of all sorts of errors, reformatting USB drives, HDD, nothing was happening. I pulled out cables, memory sticks.
It would partially get through the installation, then at the name, password box, it just crashed every time with error #5, blaming dirty, hot CD.
At the last chance, as soon as the name etc. box came up, I started entering text. No crash so far. Carried on and installation completed.
All I can deduce from all this, is that at some point in the installation, something times out and it just crashes. I am not talking about 30-minutes, but 5 - 10 seconds at the most, just time to read what was needed.
 I cannot believe that all this wasted time was down to something so simple. It might be a coincidence, but I spent hours on the internet, followed all the tutorials (mainly Ubuntu).
There were suggestions that the installation was expecting a CD and that the name of the volume (added by Rufus) was too long. Not a bit of it.
If anyone can offer an explanation, I would like to hear.
I have installed Ubuntu 12 from a Canonical CD which was trouble free, but I know very little about Linux in general. Not an enjoyable experience, but only glad that it now works, of sorts.
Firefox crashes and only just managed to download Chrome. The old 12 installation works well and has never been a problem. The only plus side of all this is that I know a lot more about BIOS and making bootable USB sticks.
This was to be an attempt to get away from Apple and Microsoft and I am grateful for all the effort that goes into Ubuntu.

---

### Post by oldfred on 2017-08-24
I have an Asus Z97 with Intel i5.
And in Asus UEFI settings I must have had 10 different settings in UEFI to change, some were required and others just to make boot a tiny bit better.
But I had to have fast boot off, UEFI Secure Boot off which was really the "Other" setting than the "Windows" setting. 
Also to boot flash drive in UEFI mode, the UEFI and BIOS/Legacy setting would not boot in UEFI mode, but the UEFI only setting on USB boot was the only one that work. I think there was also a setting on turning allow USB boot in UEFI mode.

If installing in BIOS mode then many of those setting may just default to something that works?

---

### Post by Phil S on 2017-08-25
Many thanks oldfred. I need to digest all of this. If you are lucky, the 12-step tutorial installation might work, otherwise life is not so simple.
At least I'm not looking at a collection of hardware wondering if it had been better spent on something else.
I will revisit the BIOS again. The Asus came out of a new Win 7 Pro PC that kept doing BSOD. It took a change of MB and a downgrade to i5 to fix the problem. So if the PC builder (not me) had optimised the BIOS etc. for Win, it might explain some of the problems.
I still find it strange that the installation failed at the same point. The only thing I can think of is that all the earlier setup boxes like location don't take much time to do, but name etc. is the first bit where you have to ponder a bit.
All the Ubuntu PC will be doing is running Arduino IDE, the object being to keep my dodgy wiring away from the main PC that runs Win 10 Pro.
As an aside, Win 10 isn't half bad and though I moan about stuff like forced updates and poor network support, some of my main applications are Win only.

---

### Post by oldfred on 2017-08-25
If Windows 7, that is normally installed in BIOS boot mode even to newer UEFI systems.
The Windows 7 DVD is BIOS boot only and how Windows (and Ubuntu) boots installer is then how it installs. But Windows DVD if 64 bit version, can be relatively easily copied to flash drive and a couple of files moved around/renamed to make it UEFI bootable. UEFI only boots flash drives from /EFI/Boot/bootx64.efi, so that is the file that is needed, but with Windows is really a copy of its boot file.

If Windows is BIOS, often then better to install Ubuntu in BIOS mode, unless you want to reinstall Windows to UEFI mode. The conversions of Windows once installed is possible but not particularly easy. 
Windows only boots in BIOS mode from MBR(msdos) partitioned drives and only in UEFI mode from gpt partitioned drives.
Ubuntu can boot in UEFI or BIOS boot mode from gpt partitioned drives if an additional supporting partition is added. All UEFI require an ESP - efi system partition (FAT32), and grub2 boot loader in BIOS boot mode on gpt needs a bios_grub partition.

Post this:
sudo parted -l

---

