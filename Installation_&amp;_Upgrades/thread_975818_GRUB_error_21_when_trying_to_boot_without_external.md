---
title: "GRUB error 21 when trying to boot without external hdd plugged in"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by ChrisOShea on 2008-11-08
Hello everyone! my name is Christopher, and I'm new to the forums and Ubuntu!

I recently installed Ubuntu on my desktop through Wubi. I thought it was so great, i wanted it on my Eee pc as well.

I quickly found Ubuntu eee. I booted it up live from a USB drive and everything looked fine. But I was afraid that installing it to the main SSD drive would overwrite my Xandros installation (even if i don't like Xandros very much), which i wanted to keep because of some of the functions that only seemed to work through it (such as the webcam), and of course as a backup.

Well, the issue is, I decided to install Ubuntu to my external 300 gb harddrive, so my Xandros installation would remain untouched. I thought I could just plug my external drive every time I wanted to go Ubuntu, and keep it unplugged otherwise.

It installed fine, partitioned my drive through the setup guide, and booted up into Ubuntu.

Now the problem is, I can't boot up the computer without keeping the drive plugged. If I do try, the GRUB bootloader gives me an "GRUB error 21,"

As far as I've been able to read, this is related to the MSB?

How do I get everything back to normal?:(
Thanks in advance for any suggestions!!

Best regards, Christopher

---

### Post by caljohnsmith on 2008-11-09
Welcome to the forums, Christopher. :) Your situation is quite common; what happened is that if you accept the default boot loader options when installing Ubuntu, then Ubuntu installs Grub to the MBR (Master Boot Record) of (hd0), also known as /dev/sda, which is your internal drive. That way you can simply reboot, and Voila, you have a Grub menu where you can boot Ubuntu if all goes well. The problem with that is as you've found, disconnecting your external drive means you can't boot at all, because the files Grub needs to boot are on your external drive. 

A more ideal solution is if you can set your BIOS to boot the external drive, then you can install Grub to the MBR of the external drive, reinstall your Xandros boot loader to your internal drive (does Xandros use Grub or lilo?), and then your HDDs will be independent of each other. That way you can disconnect your external drive and boot your internal Xandros drive just fine. If that sounds good to you, then how about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
And we can work from there. :)

---

