---
title: "Dual Boot, two identical windows partitions, sda2 sda2"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by Jconfusion on 2011-03-26
Hi,

I just successfully installed ubuntu 10.10 Meerkat Maverik parallel to manufacturer installed Windows 7 Professional on a newly bought ThinkPad t410. All works find just that on the boot screen instead of 1 Windows partition (usually something like "Windows 7 loader on sda1") I find two Windows partitions.  

Now, I know that Thinkpads have a recovery partition. Funny is though that both "Windows 7 loader on sda1/2" login to what seems the identical Windows (not one of them the "normal" and the other some form of a recovery).

Has anyone got a comment on this?

cheers

---

### Post by garvinrick4 on 2011-03-26
It is normal in 7's menu entry as per below. sda1 and sda2
```
rick@rick-HP:~$ grep menuentry /boot/grub/grub.cfg
menuentry 'Ubuntu, with Linux 2.6.38-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.38-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.38-6-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.38-6-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
menuentry "Ubuntu, with Linux 2.6.32-30-generic-pae (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.32-30-generic-pae (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.32-29-generic-pae (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.32-29-generic-pae (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.38-7-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.38-7-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.38-6-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.38-6-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda13)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-26-generic (on /dev/sda13)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-26-generic (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
menuentry "Ubuntu, with Linux 2.6.32-29-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
rick@rick-HP:~$ 

```
Just for the heck of it run this and post to this thread:
```
sudo parted -l
``` (lower case L)

---

