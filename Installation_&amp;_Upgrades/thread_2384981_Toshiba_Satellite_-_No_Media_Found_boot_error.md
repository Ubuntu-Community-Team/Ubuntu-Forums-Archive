---
title: "Toshiba Satellite - No Media Found boot error"
date: 2018-02-14
forum: Installation &amp; Upgrades
---

### Post by cdegroot2 on 2018-02-14
Hello,

I have installed Ubuntu on my Toshiba Satellite L50-A-1EH, the installation went flawlessly without any issues. I installed it using a USB pendrive and it is a single boot (the HDD has been completely formatted by the Ubuntu installation).
Booting the system fails, resulting in a No Media Found message from the system.

I have run the boot-repair tool from the "Try Ubuntu" live version from the pendrive, and it gave me the following pastebin: [http://paste.ubuntu.com/p/4jbNMdNt8Y/]("http://paste.ubuntu.com/p/4jbNMdNt8Y")
I have tried to run the system using UEFI/CMS with Secure Boot On/Off, but nothing works.

The UEFI ends in the "Checking Media...No Media Present" screen and the CMS/AHCI boot ends in a loop of searching for something bootable from my network card.

I'm quite new to this process, and I had hoped it would work "Out of the Box". Any help would be greatly appreciated, I'm excited to get into Ubuntu!

PS: I have searched these forums and haven't found topics describing the same problem, so I'm posting my own.

---

### Post by strixtux on 2018-02-15
It might help to enter setup during boot and rearrange boot options.

---

### Post by cdegroot2 on 2018-02-15
> **strixtux said:**
> It might help to enter setup during boot and rearrange boot options.

I have, the boot options are rearranged so the HDD is on top, I removed the USB pendrive so it wouldn't boot from that one.

---

### Post by strixtux on 2018-02-16
Looks like hardware damage. Pull the HDD and check it in another computer as an external HDD via USB. Might give a clue or two.
Could be a mainboard trouble as well, possibly a loose plug.

---

### Post by cdegroot2 on 2018-02-17
I tested the HDD and there's absolutely nothing wrong with it, it passed all tests from DiskCheckup. I think it has something to do with the BIOS setting, but I can't figure it out.
I've heard that Toshiba's are generally not that receptive to Ubuntu, but I'd really like to get it to work.

To summarize: I installed Ubuntu, turned off secured boot, tried with both UEFI and CMS boot and with various boot orders, but it won't boot.

I'd be very grateful if anyone has any suggestions.

---

