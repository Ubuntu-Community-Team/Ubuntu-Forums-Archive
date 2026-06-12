---
title: "need help with: grub-install warning"
date: 2023-10-07
forum: Installation &amp; Upgrades
---

### Post by diablo2222 on 2023-10-07
Hi everyone,

I just did the update then the upgrade and got this message:

> Setting up grub-efi-amd64-signed (1.187.6+2.06-2ubuntu14.4) ...Trying to migrate /boot/efi into esp config
Installing grub to /boot/efi.
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.

OK, that's nice. But how do I do that??? I'm on Xubuntu 22.04.3

Thanks for helping me!

---

### Post by oldfred on 2023-10-07
What brand/model system?
Do  you have latest UEFI firmware for your system?
Have you checked UEFI settings. 
Some brands have settings like Lenovo's locked boot order or HP's locked NVRAM settings.
Review UEFI settings, you may need to download manual as descriptions in UEFI often very limited.

---

### Post by diablo2222 on 2023-10-07
It's an old TOSHIBA 
Satellite  C650D - 005 
Model PSC0YC-005003

I did numerous update/upgrade in the last months and never got that message before.

I don't think UEFI can work on this laptop since it's an old one. And I just checked: I don't have /sys/firmware/efi.
I only have /sys/firmware/acpi, /sys/firmware/dmi, and /sys/firmware/memmap

I used efibootmgr just to make sure, and "EFI variables are not supported on this system."

---

### Post by yancek on 2023-10-08
>  I just did the update then the upgrade and got this message:


"the" update?  What update/upgrade are you referring to?  Also, define "old", preferably in years if possible, year of manufacture.

The message you report as well as the information provided would indicate you have a Legacy machine not capable of installing UEFI.  What were you doing when you got the message about installing grub efi?  If you run: sudo fdisk -l, the output will show if you have an EFI partition as well as if you are using a gpt or msdos drive.  Useful information.  And exactly which release of Ubuntu are you using?

---

### Post by diablo2222 on 2023-10-08
I did the sudo apt-get update, then the sudo apt-get upgrade. And got the above message at that moment.
It's an old laptop and there's no year printed anywhere. I bought it used and it had Windows 7 on it. The HDD is new so there's no trace of any other OS.
As for your other questions it's already answered in my previous posts. Xubuntu 22.04.03 (1st post) And no EFI (checked two ways) (reply to oldfred)
Thanks!

---

### Post by oldfred on 2023-10-08
It does look like an older BIOS system, but I do not know AMD versions to know.
I would not think you would get the Installing for x86_64-efi platform unless you booted in UEFI mode.
It installs in the boot mode that you boot live installer.

Also with only 4GB of RAM per default specs, better not to use Ubuntu but a lighter weight flavor.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

I have an old 2006 Toshiba BIOS only with only 1.5GB of RAM. Last used with 12.04 until it expired. Pulled it out of closet just to see if I could install 20.04. Ubuntu would not install, server installed with lighter weight fallback gui then added. I use Kubuntu on my desktops and tried it and was surprised it worked as it is more a middleweight flavor. Put back in closet.

Not a fan of laptops but planning some travel so purchased new laptop. Just before trip, new laptop died & had to be sent in for repairs. Pulled old 2006 Toahiba laptop out. I have an external SSD with UEFI install. But was able to put grub and a boot stanza on laptops old HDD, and boot Kubuntu 22.04 on SSD. That actually worked well as long as I only loaded one larger app like Firefox and smaller app like Zim which is my normal use anyhow. If I did click on too much, it used swap, but swap on SSD was tolerable. when I used to use system on old slow HDD and it went to swap I would have a 2 second blank screen.

---

### Post by yancek on 2023-10-08
Can you boot your installed Xubuntu?  If so, just run:  sudo update-grub.  If you can't boot it, use the install USB with which you installed Xubuntu originally and use a command similar to below:  Create a mount point, run the grub-install after getting the proper drive (the example below is sda)

> sudo mount /dev/sdXY /mnt # Example: sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdX # Example: sudo grub-install --boot-directory=/mnt/boot /dev/sda 

---

### Post by diablo2222 on 2023-10-09
Hi Oldfred,  I have installed **X**buntu

---

### Post by diablo2222 on 2023-10-09
> [COLOR=#000000]Can you boot your installed Xubuntu?[/COLOR]
Thankfully, Yes!

---

### Post by diablo2222 on 2023-10-09
OK guys,  I'm going to write everything again because I'm being asked questions that were already answered in my post. And also told things that "seems" irrelevant. Please read carefully this time. And a BIG thanks for your kind help all! :)

I just did the update then the upgrade and got this message:
> Setting up grub-efi-amd64-signed (1.187.6+2.06-2ubuntu14.4) ...Trying to migrate /boot/efi into esp configInstalling grub to /boot/efi.
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.

a) I am on _**X**_ubuntu 22.04.3
b) I was very afraid that it wouldn't reboot. **But it did reboot okay**.
c) I didn't specified at first what I updated and upgraded. It is: **sudo apt-update and sudo apt-upgrade**
d) I checked the folder /sys/firmware/ and:
- the folder /sys/firmware/**efi is not there**. I only have /acpi, /dmi, and /memmap
- based on what I've read on the web, if /efi is not present, it means UEFI cannot run on this laptop. I don't know if true or not.
e) I ran **efibootmgr** to double check, and got this message:[B] "EFI variables are not supported on this system."
[/B]f) **when I boot**, I first have to enter a password since my HDD is encrypted.
g) **after booting**, I have to enter a password since my Xubuntu is **not** set on auto-login.

**Additional info:**
**After** that update and upgrade:
a) I add to re-enter my user and password for Goggle/YouTube. It seems that it was somehow deleted by the update/upgrade.
b) I entered again my user and password for Google/YouTube and it's working fine now.
c) I play 0.A.D. and all my saved game have disappeared following the update/upgrade (I don't mind, that's ok. But still weird...)
d) I had Foxit reader (for PDF) and now it's gone!?? Opening a .pdf is now using Document Viewer
e) I check in "All Applications" and Foxit is nowhere to bee seen!

In short, the update/upgrade:
- gave me an error message concerning the UEFI, but I'm still able to boot ok.
- disconnected me from Google/YouTube and I had to re-enter my user/password.
- deleted all my saved games from 0.A.D.
- deleted Foxit reader and now using Dcument viewr to open .pdf.

**Is it possible the error message is automatic whether you have UEFI or not. And if you don't have UEFI just to discard that message?**

**I ran sudo update-grub as told. This is the result:**
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.19.0-32-generic
Found initrd image: /boot/initrd.img-5.19.0-32-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
done
[/QUOTE]

Again, BIG thanks!

---

