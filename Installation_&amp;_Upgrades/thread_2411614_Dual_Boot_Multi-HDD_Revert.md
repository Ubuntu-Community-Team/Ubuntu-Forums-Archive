---
title: "Dual Boot Multi-HDD Revert"
date: 2019-02-01
forum: Installation &amp; Upgrades
---

### Post by apexdestroyer on 2019-02-01
I'm new to Linux and I have read through but I can't find what I'm looking for.
Yes, another question about dual booting/partitioning. Sorry.

I have a Windows 10 headless machine with a 250 GB HDD. I wiped it and installed Linux Mint. [sda]
Then I added an additional 500 GB HDD and installed Ubuntu Budgie on that HDD. [sdb]

I can go to the boot screen and select either one but the default is always Mint [sda]

I removed the Mint HDD and tried to boot and all I get is a black screen.

I moved the physical HDDs around to se if I could swap [sda] and that worked but still no boot.

Now I have Budgie [sda] and Mint [sdb] but the Mint HDD must stay in for boot.

I want to just run/boot Budgie and wipe Mint. How can I do this?
Screenshots of gparted attached.

[ATTACH=CONFIG]282369[/ATTACH][ATTACH=CONFIG]282370[/ATTACH]

---

### Post by oldfred on 2019-02-01
Do not know LVM nor encryption. Are both installs LVM?

But issue with UEFI is that grub only installs into one ESP or first drive seen, often sda (even if flash drive installer is promoted to sda) for first NVMe drive for those with very new SSDs.
I think Mint also used /EFI/ubuntu in ESP - efi system partition. It may (and should) have changed. But then you only have one UEFI boot entry and the one ESP on sda.
I normally install an ESP on sdb or any additional drive, but it normally is not used. I use it more for backup, but then drive could easily be reconfigured to be UEFI bootable, just by adding correct UEFI boot entry for that ESP.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Dennis N on 2019-02-01
Biggest problem:
In your pictures, boot loader files are on sdb (originally sda) so Budgie can't boot unless sdb (originally sda) is attached.
> I want to just run/boot Budgie and wipe Mint. How can I do this?
Easiest solution here: Reinstall Budgie without the Mint disk connected.

---

### Post by apexdestroyer on 2019-02-02
Thanks for the help guys. I used boot-repair and it worked. I know have the mint drive fully disconnected. However, my boot time for Budgie has increased drastically.

---

