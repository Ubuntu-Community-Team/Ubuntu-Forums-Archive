---
title: "Dual Boot Gone Wrong! Please Help!"
date: 2022-03-23
forum: Installation &amp; Upgrades
---

### Post by nicholsct on 2022-03-23
[https://pastebin.ubuntu.com/p/rfHx4wwVnx/](https://pastebin.ubuntu.com/p/rfHx4wwVnx/)

Hi,

I’ve tried to install ubuntu 18.04 on my dell inspiron 7590 laptop. I created an empty space on a nvme ssd, ~180gb and installed from a usb. First problem I ran into was that my drives weren’t showing up. Fixed this using these instructions, changing away from raid.

[https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on](https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on)

Okay, problem solved. I then went to do a custom install, and allocated 21 gb for root, 6 gb for swap, and the rest for home. I wasn’t sure what to select for the device to install the boot loader to, but found some links that to choose the one with the windows booter (don’t know the correct name) on it.

Everything seemed to work. Booted to grub, was able to select ubuntu, and use ubuntu just fine. Only problem now, is that I can’t boot into windows. When i try, it gives me the auto-resolving /repairing, and then goes to the blue troubleshooting screen where I can choose to continue to windows, or try other troubleshooting like resetting windows or ‘advanced options’. Continuing to windows normally just puts me into my windows os when this shows up, but now it reboots and goes back to grub, where the cycle repeats.

My suspicion is that I installed the boot loader to the wrong device, and do not know how to fix. I tried the reset windows option, doesn’t do anything, and the boot repair, which pastebin is linked above, but it didn’t fix. Please help!

---

### Post by tea for one on 2022-03-23
You have two disks in your PC and each OS is on a separate disk.
[COLOR="#0000FF"]Line 244[/COLOR] - OS#1:   Ubuntu 18.04.6 LTS on [COLOR="#0000FF"]nvme1[/COLOR]n1p7
[COLOR="#0000FF"]Line 245[/COLOR] - OS#2:   Windows 8 or 10 on [COLOR="#0000FF"]nvme0[/COLOR]n1p3

Have you tried to boot Windows from the one-time boot menu?

Also, nine partitions on nvme1 and six partitions on nvme0 seems very complicated.
Are these partitions something to do with the previous RAID and are now not required?

Assuming that you want to continue dual booting, it may be worth thinking about your partition requirements for the future.

---

### Post by nicholsct on 2022-03-23
Ah I can get in through the one time boot menu! Thanks a ton!! I selected windows boot manager from there, and it got me in. Is there a way I can get it so that I can boot to windows from grub?

In all honesty I don&#8217;t know why the partitions were there, they were created by default by windows. I don&#8217;t know why/if they&#8217;re needed.

---

### Post by tea for one on 2022-03-23
After you have finished your Windows session, power off the PC and make sure Windows is not hibernating, snoozing, having a siesta etc.
Also, check that it is not encrypted.
Secure boot disabled in the UEFI firmware.

Boot into Ubuntu, open a terminal and enter
```
sudo update-grub
```
Hopefully, grub will add the Windows Boot manager to the menu.

I asked the question about the partitions because it looks over-complicated for a dual boot.
I suspect that it was a RAID arrangement when you purchased the PC.

Each OS on a separate disk is ideal.
Install in UEFI mode with GPT

Ubuntu would need minimum two partitions (ESP and combined system & home)
Many users, including myself, have three partitions (ESP, system and separate home) 

Windows usually has four partitions (ESP, C: partition, Windows recovery and Windows restore)

Fewer partitions = easier to manage
ESP on each drive = fewer boot problems and if one drive fails, the other is not affected.

If you are going to re-think your partitions, please always have data backups (both Windows and Ubuntu)

---

