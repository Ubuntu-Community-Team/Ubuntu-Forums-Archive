---
title: "No bootable device -- insert boot disk and press any key"
date: 2017-10-16
forum: Installation &amp; Upgrades
---

### Post by perplexedgecko on 2017-10-16
So I installed Lubuntu 17.04 yesterday. I succeeded, then I shut it  down. Earlier this morning, I wanted to use my freshly installed Linux  on my laptop but when it was booting, this notification showed up:
> No bootable device -- insert boot disk and press any key

  Booting from flash drive worked, but I couldn't reinstall Lubuntu because the installer crashed.
  I tried several methods from the internet, but none worked. My laptop  is Acer Aspire One 522, AMD Dual-Core processor C-50 1 GHz, 1 GB DDR3  memory, and 320 GB HDD (quite old, I know).

  Here is the log: [URL="http://paste.ubuntu.com/25752978"]http://paste.ubuntu.com/25752978
[/URL]
  Any help would be appreciated.

---

### Post by oldfred on 2017-10-16
You are only showing your sda, your 8GB flash drive.
No hard drive at all.

Does BIOS show hard drive. Unless BIOS can see drive (and write that to drive), then operating system will never see it.

If in BIOS then try Disks and in upper right corner icon is Smart Status. What does it say about drive?

---

### Post by perplexedgecko on 2017-10-16
Thank you for your response.

I don't think I have the "Disks" tab nor Smart Status icon in BIOS, but I looked for the HDD informations in BIOS. In the HDD part, it says "none" in the model name, and nothing in the serial number. I have a pic but I don't know how to post it here.

---

### Post by oldfred on 2017-10-17
Gnome Disks is in your Ubuntu live installer. It may not be in Lubuntu, but then you can easily install it from repository into live installer.

---

### Post by perplexedgecko on 2017-10-19
I tried and it said "gnome-disk-utility is already in the newest version (3.24.0-0ubuntul)"
Then what should I do?
[IMG]https://mail.google.com/mail/u/0/#inbox/15f34ac93677422c?projector=1[/IMG][ATTACH=CONFIG]277170[/ATTACH]

---

### Post by oldfred on 2017-10-19
Then you have Disks.
Do not know Lubuntu and where to find it.

You may be able to run from command line.

This worked for me, but I am using 16.04 Unity with Flashback.
gnome-disks

---

### Post by leunam12 on 2017-10-20
the first thing that you have to do is find a small screw driver and flip your laptop and remove the HDD door and make sure that the hard disk is firmly seated in its connector, may even pull it out and re-seat it. Then boot the live USB and open disks utility, I think the command from the terminal is gnome-disks. Then check the SMART section and look for uncorrectable errors, reallocated sectors, sectors pending reallocation, read error rate, raw read error rate. The raw value for those fields should be 0; if it's not, then your disk has problems.

---

### Post by perplexedgecko on 2017-11-05
> **oldfred said:**
> Then you have Disks.
Do not know Lubuntu and where to find it.

You may be able to run from command line.

This worked for me, but I am using 16.04 Unity with Flashback.
gnome-disks

> **leunam12 said:**
> the first thing that you have to do is find a small screwdriver and flip your laptop and remove the HDD door and make sure that the hard disk is firmly seated in its connector, may even pull it out and re-seat it. Then boot the live USB and open disks utility, I think the command from the terminal is gnome-disks. Then check the SMART section and look for uncorrectable errors, reallocated sectors, sectors pending reallocation, read error rate, raw read error rate. The raw value for those fields should be 0; if it's not, then your disk has problems.
I apologize for the really late reply.

It turned out that my hard disk was loose and thus couldn't be recognized. I have fixed the problem by pulling it out then putting it back in again just like leunam12 said.
Thank you for your responses and advice!

---

