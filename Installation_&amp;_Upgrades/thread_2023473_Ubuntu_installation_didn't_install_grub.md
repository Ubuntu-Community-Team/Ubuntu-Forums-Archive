---
title: "Ubuntu installation didn't install grub"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by Soulcrusher on 2012-07-12
I have a laptop with a 64 gb ssd and an 640 gb hd. I have windows 7 installed on the ssd and wanted to install ubuntu on a partition on the second hd. I did the following steps:

- I created a partition 150 gb big on the end of the hd (149 gb ext4 and 1 gb swap). After installation the system restarted and it just booted windows, no sign of grub at all.
- I tried to reinstall ubuntu a couple of times, trying different things with the boot drive setting (install grub on 1st hd, sda1 windows loader and sda2 the windows partition itself).
- I've put the live cd on a usb drive, but I dont have an option to restore grub. If i boot into the live cd, I cant install grub or change it's settings.
- I tried installing easyBCD on windows and added grub2 as an entry, and when I then boot up it shows the windows and grub entries. But when I select grub, I get a commandline interface with "Grub: ".

I think my bios is set to uefi but I'm not sure.
How do I proceed?

---

### Post by oldfred on 2012-07-12
If you have UEFI, you should install Ubuntu in the same UEFI way as Windows. Best to see all details of both installs which the BootInfo report that this creates will give us. Just post link to report that it gives.

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary - uses standard bootinfoscript but adds some extra info
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by Soulcrusher on 2012-07-12
Thank you, boot-repair fixed the problem. I couldn't get to run it earlier, when I tried installing grub or boot-repair via terminal it failed. That would probably have been a network issue (I'm not that familiar with terminals yet).

---

