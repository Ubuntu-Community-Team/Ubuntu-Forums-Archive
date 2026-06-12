---
title: "Possible to change partition layout in ubiquity (12.10) with full disk encryption?"
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by latestversion on 2012-12-23
I'd like to use LVM and full disk encryption with Ubuntu 12.10, but I'd also like to specify additional partitions (like /home, /tmp, etc), but I can't seem to do that when selecting "Encrypt the new Ubuntu installation for security" and "Use LVM with the new Ubuntu installation".

The ability to manually review and change the partition layout is only possible if I select "Something else".

Am I missing something in the installer, or is it not possible to manually review/change the layout if I select full disk encryption? If it's not possible, how and when could I set up these extra LVM partitions?

---

### Post by dwewer on 2013-02-08
Greetings! ):P

I found this thread with no answers via search results. I'll add my  questions here, since they're virtually identical. I'm interested in  setting up xubuntu with full disk encryption using LUKS+LVM. There  should be 2 partitions on the HDD, first one is for /boot and second one  is for dm-crypt. Ontop of the LUKS device I'd like to setup LVM and use  it to create separate partitions for i.e. /home, /var, /var/log, swap,  etc.

The xubuntu installer does not seem to offer any advanced  configuration options. There are a few checkboxes, but the manual  partitioner doesn't seem to allow me to setup more than one partition  inside the LUKS device. In fact I think it doesn't use LVM at all -  pvscan, vgscan, lvscan don't show any results.

How can I setup  xubuntu with a custom HDD encryption/partition setup? I've seen some  people suggest to use an alternate CD or a miniCD. Will I get the same  xfce desktop as with xubuntu, if I use the miniCD? If not, what steps  are needed to get an XFCE desktop? How can I get a plymouth splash  screen asking me for PW at boot?

Best regards!


EDIT: I've just tried the miniCD image. It's a network installation media. The operating system is currently installing/downloading, and the setup allowed me to customize the partitions the way I wanted to - the LUKS/LVM was totally configurable unlike in ubiquity! I'll see if I can get the desktop going.

EDIT2: Got it. XFCE is running just fine, but there are some minor bugs I'll have to address.

**ADDITIONALLY:** Forum bug report: This forum doesn't seem to allow me to preview my post, if I block access or javascript to "yahooapis.com". It errors out and tells me that the message I entered is too short. For security/safety reasons I block requests and javascript by default using browser addons like NoScript and RequestPolicy.

---

### Post by Herman on 2013-02-08
Another way to do it would be to:
1. Partition a disk with a small  /boot partition and a larger partition for encryption and in which to base the logical volumes. You can use GParted in the 12.10 LiveCD for partitioning.
2. Encrypt the larger partition using command line tools.
3.. Set up your LVM using command line tools or enabled the universe repository and install system-config-lvm, (Logical Volume Manager), which is a GUI application similar to GParted, but for managing LVM.
4. Run the 12.10 installer and choose 'manual partitioning', although the 12.10 CD's installer lacks the ability to do everything with encrypted LVM, at least it can recognize logical volumes when they have already been created and you get the installer to assign mount points for them and install into them, you can have your operating system split up into as many volumes as you have prepared.
5. Make the new operating system bootable by chrooting into it and doing the following,
(a) add an /etc/crypttab file 
(b) edit /etc/initramfs-tools/modules
(c) create a new initrd.img

Useful links: 
 '[EncryptedFilesystemsViaUbiquity]("https://help.ubuntu.com/community/EncryptedFilesystemsViaUbiquity")' - Ubuntu Community Docs, 
'[Encrypted Filesystem LVM How-to]("https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto")' - Ubuntu Community Docs, see especially this part: [final preparation]("https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto#Final_preparation"). 
' [how to chroot, simple and fast]("http://ubuntuforums.org/showthread.php?t=1156240")', by taavikko - Ubuntu Web Forums
[How to Resize a LUKS Encrypted File System]("http://ubuntuforums.org/showthread.php?p=4530641") - bodhi.zazen - Ubuntu Web Forums

---

