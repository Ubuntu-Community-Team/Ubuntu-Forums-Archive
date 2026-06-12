---
title: "Fresh install won't boot, HELP!!"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by mlalich on 2006-09-24
I am trying to install Ubuntu 6.06.1 Desktop on a spare computer. I can get Ubuntu to completely install with the LiveCD version and the alternate version. Once the system reboots it'll get to where it's searching for a bootable drive and it says, "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER". It was suggested to me to use gparted LiveCD as the partitioning portion of the Ubuntu LiveCD might be the problem. So I used gparted and partitioned the only hard drive in the computer as such.

/dev/hda1 ext3 boot flag is on
/dev/hda2 extended
/dev/hda5 linux-swap

Now I am totally new to Linux so please excuse my probably idiotic questions. I know standard windows partitioning pretty well, but have no idea how Linux partitioning works. So can anyone please give me a walkthrough, tip, or suggestion on how to get Ubuntu to boot up for me? Oh I did successfully install Ubuntu on VMWare and it works fine, so I know the CDs I'm installing from are fine. I also have tried several hard drives and all same results, so the hard drives are also okay.

I've heard about an app called GRUB being needed to boot. From wha I take from various conversaions is GRUB is for dual booting right? Like having a choice at bootup to boot WinXP or Ubuntu.

I have manually paritioned the hard drive and chose the Format entire drive option on the Ubuntu LiveCD. All avenues have lead me to the same result, the DISK BOOT FAILURE message. I've made sure my BIOS is looking for a bootable partition on the only hard drive in the computer. My boot sequence is setup as such:

CDROM
Hard Drive

Please help! Thanks!

---

### Post by Ocxic on 2006-09-25
grub is for booting any OS not just for dual booting you need it or else your computer will never boot (or some other boot manager) grub should have been installed automatically, you could try re-installing grub from the live cd. I'v never had to do it myself so i can't tell you how off hand but there is a how-to try searching for "install grub" in the forums.

---

