---
title: "Ubuntu boot loader never starts"
date: 2018-04-17
forum: Installation &amp; Upgrades
---

### Post by jonnan on 2018-04-17
After a long hiatus, Windows 10 had reduced my lenovo 110s with 10 of 32 GB available to 2 Gig of space being continually cleaned. Googling indicated Ubuntu worked so I created a USB installer.

Works fine from USB. Won't boot. Goes to a 'Boot Menu' with two options, both of which just cycle. BIOS is setup to match recommendations, I've tried separate boot partitions, I've left space behind the MBR, I've reinstalled GRUB from Terminal, I've installed and run boot-repair, I've even tried to install lilo (liloconfig refuses to run from the USB, trying to restore MBR from there it just errors out.)

Frankly, I've been unemployed for awhile and I just lost my access to a slew of things I need. I really need this machine to work.

(Apologies, on a phone and it submitted without being quite ready and isn't letting me fix tags.)

Solution for those finding this in Google.
UEFI expects the USB Dongle to be formatted in FAT32; The USB creation tools will happily let you format in NTFS and say it's UEFI Compatible but things just don't work.

Hopefully this saves someone pain.

---

### Post by oldfred on 2018-04-17
This thread may help.
 Lenovo 110s  Experience Installing and Using Linux on my Lenovo 110s UEFI settings better support than 100
[https://ubuntuforums.org/showthread.php?t=2350394](https://ubuntuforums.org/showthread.php?t=2350394)

---

### Post by yancek on 2018-04-18
Are you trying to do an MBR or UEFI install?  Is windows still on the computer or are you trying to overwrite it?
  
> BIOS is setup to match recommendations, 

What recommendations?  From where/who?

---

### Post by jonnan on 2018-04-18
Actually, the recommendations from the previous thread; I have the exact same model 110s-11IBR. Windows 10 is gone entirely, I repartitioned and reformatted the drives entirely. I've tried just a primary and a swap, I've tried four primaries, I've rearranged the boot order, no matter what I do, grub never initiates, boot repair acts like it will work but makes no difference, reinstalling grub from the terminal acts like it works, no difference, attempts to install lilo just error out, yet Ubuntu starts up fine from the USB disk.

If I don't get a solution by tonight I'll be spamming this thread with screenshots from the USB version and the boot-repair info text. I was just too tired to get into that last night on top of getting my login here to work again.

---

### Post by oldfred on 2018-04-18
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by jonnan on 2018-04-18
Did another reinstall, left 512 mb at the beginning of the drive to ensure I wasn't somehow 'crowding' grub'
Boot repair seems to be properly detecting mmcblk0p1 as the bootable OS, 
Bootinfo Summary: (before doing anything) [http://paste.ubuntu.com/p/68sz2xMCnh/](http://paste.ubuntu.com/p/68sz2xMCnh/)
Bootrepair Summary: [http://paste.ubuntu.com/p/2XkZ3jhVr8/](http://paste.ubuntu.com/p/2XkZ3jhVr8/)

Now submitting and rebooting because I would love for it to just work this time. I could live with the embarrassment,

---

### Post by jonnan on 2018-04-18
Survey says: [X][X][X]

And I took photos of the bios screens, but don't see a way to upload them from my phone.

---

### Post by jonnan on 2018-04-18
But for some reason the USB grub just quit working. I can probably recreate it but I've no idea why it quit no too.

'I can only assume I'm repaying karma at a vastly accelerated rate.' - Commander Ivanovna

---

### Post by oldfred on 2018-04-18
Are you sure you have UEFI in BIOS/CSM/Legacy boot mode. And to have that on, you must have UEFI Secure Boot off.
You cannot boot an UEFI system in BIOS boot mode with Secure boot on. 
And some systems you have to specifically allow USB boot and BIOS boot with even more settings.

Do not know about phone, but from a PC or live installer you can use Forum's advanced mode and the paperclip icon to attach screenshots or photos. Make sure photo are not large, not sure if uploading automatically shrinks them or not.

---

### Post by jonnan on 2018-04-19
Well, it *says* it's in legacy mode in the BIOS. It just never goes anywhere. I'll try and get the screenshots uploaded but honestly it's a much simpler interface than a lot of the old BIOS menu's used to be, not much to misread.

---

### Post by oldfred on 2018-04-19
The link I posted in 2nd post, the user did use UEFI and it worked.

---

### Post by jonnan on 2018-04-19
> **oldfred said:**
> The link I posted in 2nd post, the user did use UEFI and it worked.

[https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295) ?

Honestly, I'm having a hard time making heads or tails of that thread. It references a whole bunch of options I've never seen before and aren't in the 16.04 iso I downloaded.

I suppose I can try it with 17.x but I was hoping to get back in with an LTS release.

---

### Post by jonnan on 2018-04-19
Okay, I tried with 17.10.1 as mentioned in that thread and
A- I'm not getting these UEFI options the thread seems to think are there, and
B- it makes no difference. Exact same results, UEFI selected or legacy.
Boot Menu
1. Windows Boot Manager
2. eMMC Disk: SanDisk iNAND 32GB

---

### Post by jonnan on 2018-04-19
[ATTACH=CONFIG]279360[/ATTACH][ATTACH=CONFIG]279361[/ATTACH][ATTACH=CONFIG]279362[/ATTACH][ATTACH=CONFIG]279363[/ATTACH][ATTACH=CONFIG]279364[/ATTACH]

---

### Post by oldfred on 2018-04-19
If you change boot priority from legacy first to UEFI, can you not then boot Ubuntu USB flash drive in UEFI mode?

---

### Post by jonnan on 2018-04-19
I am waiting to see if this install works, but the preliminary looks good.

If so, I think it may be worth noting that UEFI installs require the USB drive be formatted in FAT32 format. Why UEFI would require an obsoletevfilesystem from 1996, I do not know.

But the USB was recognized in UEFI mode now, and seems to have mounted the efi partition to /boot/efi during install, so I think it's going to work.

---

### Post by jonnan on 2018-04-19
That was it. I was using NTFS on the USB key and UEFI expects FAT32.

---

