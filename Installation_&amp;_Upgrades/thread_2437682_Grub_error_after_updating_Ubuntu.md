---
title: "Grub error after updating Ubuntu"
date: 2020-02-27
forum: Installation &amp; Upgrades
---

### Post by amitamb on 2020-02-27
I am not able to boot into Ubuntu after upgrading packages. Following is boot-repair output

[http://paste.ubuntu.com/p/TPkmWGMfzp/](http://paste.ubuntu.com/p/TPkmWGMfzp/)

I am dual booting with Windows 10.

---

### Post by CelticWarrior on 2020-02-27
You should be booting from the drive identified as 'sdb', the 1TB HDD? This is irrespective of location of the system partitions. It's because this one seems to have the proper EFI partition with bootloaders for Windows and Ubuntu. The 120GB SDD? has only entries for Ubuntu.

This is likely a problem with UEFI ("BIOS") settings and nothing to do with updates (but please describe what those updates were anyway).

Please check the boot order in UEFI > Boot (or equivalent menu). Most vendors use separated settings for drive order - determines which EFI will be read in your case - and OS selection. Change the drive priority in the first settings making sure the 1TB drive is the first one; then at the OS selection make sure "Ubuntu" is selected so you can use Grub to boot Ubuntu and Windows.

---

### Post by amitamb on 2020-02-28
Thank you very much for your response. You were right and after changing boot priority, it worked. Surprising thing though is that it stopped working suddenly. I did not mess around boot order. Just restarted the PC after doing some updates and got the grub prompt.

I was targetting sda1 while doing manual boot repair. Would have never guessed that order of drive was messed up.

---

### Post by CelticWarrior on 2020-02-28
Great :popcorn:
You can mark this one solved with the thread tools.

More about this... The updates may have included firmware updates and it reset the UEFI. Or it lost the configuration that used to work for some other reason.

---

