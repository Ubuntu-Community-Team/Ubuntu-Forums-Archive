---
title: "GRUB Problems after Editing Partitions"
date: 2011-11-02
forum: Installation &amp; Upgrades
---

### Post by GreenRaccoon on 2011-11-02
I fixed my problem, but I figured I'd explain how I fixed it in case anyone else has this issue.

While I was adding Macbuntu 10.10 alongside my Ubuntu 11.04 Natty Narwhal and Windows 7 OS's, I saw that I had an extra linux-swap partition.  My 10.10 Live USB used one swap and my 11.04 used the other, but the one that I needed to remove was being used by the Live USB.  (In hindsight, I could have probably avoided this mess by just unmounting it, but that would have been the smart thing to do.)  So I tried to remove one of the partitions using Windows 7, but it removed both of the linux-swap partitions instead.  I created a new linux-swap partition using GParted with my 10.10 Live USB, but, after rebooting, GRUB came up looking weird and I couldn't even use the arrow keys.  If I selected the default kernel, it read:
```
error: invalid extent
error: symbol not found: 'grub_os_area_addr'
error: symbol not found: 'grub_os_area_addr'

Press any key to continue.
```
I found the solution here: [http://ubuntuforums.org/showthread.php?t=1719857]("http://ubuntuforums.org/showthread.php?t=1719857").  I booted from the Live USB and opened up GParted to check the location of my main Ubuntu partition ("/dev/sda5") and the location of the hard disk ("/dev/sda").  The Ubuntu partition was an ext4 file system and the hard disk is found in the top right corner.  I opened up Terminal and typed this (replace "dev/sda5" and "dev/sda" with what you found in GParted):
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
However, my system still would not automatically mount my linux-swap partition.  I found the solution here: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637").  First, I checked the location of my linux-swap partition in GParted.  Then I ran this in Terminal (replace "sda7" with what you found in GParted):
```
sudo mkswap /dev/sda7
sudo swapon /dev/sda7
free
```
BUT, two files need to be updated after this.  Update the UUID in these two files to the UUID listed from the previous set of Terminal commands (you can also find the new UUID in GParted by right-clicking the linux-swap partition and selecting "information"):
```
sudo gedit /etc/fstab
sudo gedit /etc/initramfs-tools/conf.d/resume
```
Update the UUID in these two files to the UUID listed from the previous set of Terminal commands (you can also find the new UUID in GParted by right-clicking the linux-swap partition and selecting "information").  Finally do this:
```
sudo update-initramfs -u
```
While I'm at it, I'll throw in this other fix that I found.  When I installed 10.10, my MBR (Master Boot Record) was overwritten, so all of my GRUB customizations were removed.  Linux likes to be customized though, and I eventually found out how to bring it back.  I booted up my original 11.04 system and ran this in Terminal ("/dev/sda" should be replaced with the location of your hard disk):
```
sudo grub-setup /dev/sda
```
That's it (although a "sudo update-grub" wouldn't hurt either).

---

### Post by Rubi1200 on 2011-11-02
Thanks for sharing this with us GreenRaccoon :)

This type of helpful and informative post adds much value to the forums, helping both new and more experienced users.

---

### Post by GreenRaccoon on 2011-11-02
> **Rubi1200 said:**
> Thanks for sharing this with us GreenRaccoon :)

This type of helpful and informative post adds much value to the forums, helping both new and more experienced users.

Thanks! :biggrin: I try to make my posts easy for newbies to understand, cause I remember being so overwhelmed when I first started on Linux.

---

