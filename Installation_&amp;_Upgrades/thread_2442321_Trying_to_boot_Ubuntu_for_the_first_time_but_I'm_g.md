---
title: "Trying to boot Ubuntu for the first time but I'm getting stuck at the loading screen"
date: 2020-05-02
forum: Installation &amp; Upgrades
---

### Post by professor-butchwell on 2020-05-02
[COLOR=#242729][FONT=Arial]I am trying to boot Ubuntu (20.04 LTS) for the first time on a HP ENVY laptop to replace Windows 10. I followed Ubuntu&#8217;s instructions to create a bootable USB using Rufus and selecting the USB from the boot manager. However, whenever I do so, it scans the file system successfully and thereafter I get stuck on the Ubuntu loading screen (image atached) and nothing happens except the loading circle spins. I have tried it multiple times and even left it for over 12 [/FONT][/COLOR][COLOR=#242729][FONT=Arial]hours, but to no avail.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thank for any help in advance.
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]
[ATTACH=CONFIG]285711[/ATTACH][/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-05-02
What option have you selected in Rufus?

---

### Post by professor-butchwell on 2020-05-02
Boot selection: FreeDOS (then I select the .iso file and it changes to "ubuntu-20.04-desktop-amd64.iso")

Partition scheme: MBR

Target system: BIOS (or UEFI-CSM)

File system: FAT32 (Default)

Cluster size: 16 kilobytes (Default)

---

### Post by CelticWarrior on 2020-05-02
Those options are likely the problem.
FreeDOS isn't to be used and the rest makes it bootable only in BIOS/Legacy, exactly the option you don't want.
You need UEFI/GPT or use the DD option -or- use something else altogether like Balena Etcher for Windows to avoid such problems.

Also of note that isn't a good idea to remove Windows but if you want to do that then first use it to update UEFI and SSD's firmware if applicable as they are usually provided as Windows executable files.

---

### Post by professor-butchwell on 2020-05-02
I tried both your suggestions, but unfortunately now the USB isn&#8217;t showing in the boot manager so the only option is to boot to Windows.

I also tried using Universal USB Installer which got me to the loading screen once again, but it&#8217;s stuck there again.

---

### Post by CelticWarrior on 2020-05-02
You're doing something wrong then.
You have Legacy/CSM enabled in UEFI ("BIOS"), the default even with Windows 10 installed in UEFI mode (and we know it is because you booted a "BIOS"/Legacy only USB, with a properly made USB media, you'd now see 2 entries to boot from, one with just the USB's name and other preceded by "UEFI:"

So, in summary, first of all try my suggestion about updating UEFI and SSD's firmware. Then there are other settings in UEFI that will probably need to be changed (Secure Boot OFF, Fast Boot OFF and SATA mode should be AHCI). Then the next step is assuring you have a properly made USB installation media. HP in general and the Envy line in particular do not need that many changes, ESC > F9 should show the one-time boot menu with all the correct options including external media.

---

### Post by professor-butchwell on 2020-05-02
Yes I have updated UEFI Firmware and created the USB boot media (this time using the DD option) which *is *showing up in the boot manager, but unfortunately it is getting stuck at the same screen again.

.[ATTACH=CONFIG]285721[/ATTACH]

---

### Post by CelticWarrior on 2020-05-02
> Then there are other settings in UEFI that will probably need to be  changed (Secure Boot OFF, Fast Boot OFF and SATA mode should be AHCI)

Also, in order to assure it's booting in UEFI mode (A bit-by-bit copy with DD boots in either mode), open UEFI settings and disable Legacy/CSM.

---

### Post by professor-butchwell on 2020-05-02
Yes Legacy/CSM is disabled. Secure boot is off, fast boot is off.

---

### Post by CelticWarrior on 2020-05-02
So next thing to try is the option to boot with safe graphics or use 'nomodeset'. Does it have a Nvidia Graphics?

---

### Post by professor-butchwell on 2020-05-02
No it has a AMD A10 8700P APU with Radeon integrated graphics.

I have also tried the Safe Graphics boot and it gets stuck at the same screen.

---

### Post by CelticWarrior on 2020-05-02
OK, then same initial procedure - safe graphics or 'nomodeset' - for booting the live session and installation applies.
AMD APUs are well supported but there's always the odd one out.

---

### Post by professor-butchwell on 2020-05-02
Unfortunately stuck at the same screen :(

---

### Post by CelticWarrior on 2020-05-02
> **professor-butchwell said:**
> Unfortunately stuck at the same screen :(

And that is weird and unexpected. I haven't mentioned it before because such errors are very rare but now it's in order. Have you checked the downloaded ISO? It looks like it's corrupt. 

[http://releases.ubuntu.com/focal/SHA1SUMS](http://releases.ubuntu.com/focal/SHA1SUMS)
Instructions: [https://www.howtogeek.com/246332/how-to-verify-a-downloaded-linux-iso-file-wasnt-tampered-with/](https://www.howtogeek.com/246332/how-to-verify-a-downloaded-linux-iso-file-wasnt-tampered-with/)

---

### Post by professor-butchwell on 2020-05-02
I followed the instructions and created a checksum file for my iso, but the txt checksum file it created was blank, 0kb?

Edit: I have also now tried creating a USB for Ubuntu 18.04 and 19.10 and the same thing happened on both of them, they all just get stuck on the loading screen.

---

