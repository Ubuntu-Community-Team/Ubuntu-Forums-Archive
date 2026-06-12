---
title: "Cannot boot into ubuntu server install after reinstallation"
date: 2022-01-24
forum: Installation &amp; Upgrades
---

### Post by disruptis on 2022-01-24
I have done a lot of work troubleshooting this issue. Here's what I have so far.

**The Problem**
 I have an old lenovo desktop PC that I'm trying to run an ubuntu  server on. It has worked fine using server in the past, so I reinstalled  it on a new WD Sata SSD I have. It originally worked flawlessly until I  decided I didn't like the fact that I chose to encrypt the OS with LUKS  when I installed, so I booted from my install USB and reinstalled  over the same SSD without the encryption enabled. After a reboot, the bios won't boot the  drive anymore despite seeing that it exists.

 [B]
Specs[/B]

 My PC is a Lenovo Thinkcentre m91p. [Sticker info here]("https://i.stack.imgur.com/yk4oG.jpg"). I haven't changed out any of the hardware except for adding a 500GB WD Blue SATA SSD (WDS500G2B0A) that can be found [here]("https://www.westerndigital.com/en-ca/products/internal-drives/wd-blue-sata-2-5-ssd#WDS500G2B0A"). I'm using a [Cable Matters 90 Degree Right-Angle SATA III Cable]("https://www.cablematters.com/pc-188-156-cable-matters-3-pack-90-degree-right-angle-60-gbps-sata-iii-cable-18-inches.aspx")  to connect it to the motherboard. I have it plugged into slot HD1 on  the motherboard, which is a Sata III interface as far as I can see.
 My Ubuntu version is ubuntu-20.04.3-live-server-amd64


 **What I've Tried**
 The most important thing to note is that the drive still works. If I  install windows 10 pro onto it, overwriting my server install, it will  boot into the windows drive perfectly. The problem only occurs with  either an ubuntu desktop or ubuntu server install. Neither of those will  boot even when the boot order is correct and everything.
 I have the original 500GB hard-drive that the desktop came with. When  I plug it into the other SATA III port HD0, it has the exact same  problems as my SSD. Windows works, but Ubuntu does not.
 I have tried wiping and reinstalling both ubuntu and windows on these drives multiple times and the effects are consistent.
 Now let's talk BIOS. A lot of answers surrounding my issue ask to  either disable Secure Boot or enable CSM. Only issue is that as far as I  can see, my BIOS doesn't have either feature. I have tried resetting to  its default settings, resetting it with CMOS jumpers, and even trying  to flash it with the [most recent update]("https://support.lenovo.com/ca/en/downloads/ds018245-flash-bios-update-thinkcentre-m81-m91-m91p-thinkstation-e30")  to the 7033-A25 motherboards provided by Lenovo. I installed FreeDOS  onto a USB using RUFUS and executed the program, which seemed to  complete though when I rebooted and checked the bios, the version number  hadn't changed to the update I installed. I don't believe it actually  updated. None of these options worked.
 I tried to repair the bootloader in case that was the issue somehow  even though it was a fresh install, but that didn't seem to work either.  Here is the [boot-repair summary]("https://pastebin.com/CiwvE50T").
 [B]
Conclusion[/B] I'm pretty sure this is a problem with the way LUKS encryption works  with Ubuntu doing something strange to my motherboard, but I just don't  know enough about it to understand what went wrong. If anybody could  help point me in the right direction that would be incredibly  appreciated.

---

### Post by oldfred on 2022-01-24
Bit surprised it is UEFI as 2011 system.
Microsoft started requiring vendors to install Windows 8 in UEFI boot mode to gpt partitioned drives in 2012.
Some vendors did start conversion from old BIOS to newer UEFI and even installed Windows 7 in UEFI boot mode.

You show UEFI boot of LVM install on sda, but also have a LVM install on sdb?

And UEFI (before repair?) shows booting from sdb.
But it looks like Boot-Repair updated based on install in sda?

Not sure which install is encrypted or which is newer.
Best to only use Boot-Repair's advanced mode with multiple drives or multiple installs, so you can choose an install and choose which drive to install boot loader into.

---

### Post by disruptis on 2022-01-24
Do you have a suggestion on how I can fix this or at least move forward? Is there more diagnostic information somewhere that may be helpful?

---

### Post by MAFoElffen on 2022-01-24
I see two drives, with EFI partitions on each... Which is the drive that is et in BIOS to boot from?

What is on the second drive? It says it is Linux... Was it disconnected when you re-installed? When you tried to repair? Did you delete the system partitons before you reinstalled?

What was your original plan for this? You said Server, but have it as Dual boot between two Linux OS'es. So I'm assuming you will not need the Server services 24x7x365.

It was two fresh installs... (on the SSD) so there may be not much there, right? Do you have a good backup of data and config files, if there is?

---

### Post by disruptis on 2022-01-26
> **MAFoElffen said:**
> I see two drives, with EFI partitions on each... Which is the drive that is et in BIOS to boot from?

What is on the second drive? It says it is Linux... Was it disconnected when you re-installed? When you tried to repair? Did you delete the system partitons before you reinstalled?

What was your original plan for this? You said Server, but have it as Dual boot between two Linux OS'es. So I'm assuming you will not need the Server services 24x7x365.

It was two fresh installs... (on the SSD) so there may be not much there, right? Do you have a good backup of data and config files, if there is?

When I was attempting a boot repair, I had the hard drive plugged in with an ubuntu server install of its own because I was testing to see if it was just my SSD that was faulty. Didn't unplug it while I was doing it. My plan is to only hold one single install of ubuntu server and nothing more. I'm trying to host a 24x7x365 web server on it. Right now there is no important data on it so I'm fine with wiping it and reinstalling again, which I've already done a lot to no avail. What "data and config files" would be helpful to see?

---

### Post by oldfred on 2022-01-26
On my system an external drive gets promoted to first or sda and other drives all change up one letter.
Which drive is your internal?

---

### Post by disruptis on 2022-01-28
> **oldfred said:**
> On my system an external drive gets promoted to first or sda and other drives all change up one letter.
Which drive is your internal?

Both of them are internal devices plugged directly into the SATA on my motherboard.

---

### Post by oldfred on 2022-01-28
Do not know LVM installs.
But with two drives & two installs, when running Boot-Repair you have to only use Advanced mode where you can choose which install and then which drive to reinstall grub. Be sure LVM is mounted especially if encrypted, & /boot. But, it should mount /boot & ESP without issue.
And you do have UEFI boot, so need to boot live installer to make repairs in UEFI.
Since early UEFI, it may not have Secure Boot setting, but it also may be called "Windows" or "Other" as my motherboard uses.

Shows advanced mode screens.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by disruptis on 2022-02-01
Today I reinstalled ubuntu server for the 7th time again using the exact same settings I've always done and it just worked. My sincere condolences to anyone who is having a similar issue to me. Thanks for the help you guys.

---

