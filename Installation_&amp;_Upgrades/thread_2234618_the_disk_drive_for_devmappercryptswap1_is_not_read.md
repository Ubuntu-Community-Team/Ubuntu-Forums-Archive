---
title: "the disk drive for /dev/mapper/cryptswap1 is not ready yet or not present"
date: 2014-07-15
forum: Installation &amp; Upgrades
---

### Post by Mar Komus on 2014-07-15
The solutions found [here]("http://askubuntu.com/questions/341979/what-to-do-about-the-disk-drive-for-dev-mapper-cryptswap1-is-not-ready-yet-or") and [here]("http://punygeek.blogspot.com/2012/10/ubuntu-1204-how-to-solve-disk-drive-for.html") are helpful, but don't solve the current problem.

I installed 14.04 server (along with the Unity GUI; long story) for my home based server. I also installed 14.04 Desktop on my laptop. In both cases I decided to try LVM and encrypt the home folder (as I recall). I don't remember if the error message, as stated in the title, was present from the get go, but it exists now.

I found, at least, a work around for the laptop (not sure if the swap space is encrypted or not). But for the server, no dice. Here's what's going on:

On the laptop, I found the swap space that was set up during installation, except it was unallocated space (or was it supposed to be like that?). Simple work around fix: I formatted it as a swap file, made changes to /etc/fstab and /etc/crypttab such that the swap space is now identified in /etc/fstab via UUID rather than the proxy /dev/mapper/cryptswap1. I tried to encrypt this using the terminal, but it returned the same error, so I changed it back. This same solution, however, won't work on the server. I don't see a swap space at all and I couldn't make one because I don't know how to shrink the pv in gparted. I looked for that, but everything says it's a risky move! Now, when I access the *Disks* application, I have, under *Devices > Disk Drives*, the following: 640 GB Hard Disk, Floppy Drive (Yes, I have one; don't judge), CD/DVD Drive, and the USB drives associated with a card reader. Under that, in *Other Devices*, I have 636 GB Block Device on /dev/server-1/root and 4.3 GB Block Device on /dev/server-1/swap_1. Such a thing as *Other Devices* doesn't exist on my laptop.

So, two part question:

1) How can I create a swap space in LVM2 PV?
2) How can I restore the swap in such a way as to be sure the swap files are encrypted (i.e., so that I can change /etc/fstab and /etc/crypttab back to their configurations)?

Ultimate goal here: have my swap files encrypted without error message.

---

### Post by Mar Komus on 2014-07-16
bump :)

---

### Post by oldfred on 2014-07-16
I do not know how to recreate an encrypted swap. 
When you install it creates an encrypted swap and then partition tools do not see it as it is unformatted and encrypted space.

To create a swap with LVM you have to use LVM tools. Standard partition tools like gparted do not work with LVM.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

    
 Repair gpt & encryption
[http://ubuntuforums.org/showthread.php?t=2197301](http://ubuntuforums.org/showthread.php?t=2197301)
The Performance Impact Of Linux Disk Encryption On Ubuntu 14.04 LTS - std vs. full disk LVM or encrypted /home
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1404_encryption&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1404_encryption&num=1)
[http://www.truecrypt.org/docs/truecrypt-portable](http://www.truecrypt.org/docs/truecrypt-portable).
14.04 Encrypt LVM install with dual boot Windows 8 UEFI/gpt- dusf
[http://ubuntuforums.org/showthread.php?t=2218477](http://ubuntuforums.org/showthread.php?t=2218477)
13.10 LVM install - Herman
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)
man cryptsetup
[http://linux.die.net/man/8/cryptsetup](http://linux.die.net/man/8/cryptsetup)
LUKS is designed for fast and secure wiping by just overwriting header and key-slot area.

---

