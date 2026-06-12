---
title: "Installation of grub fails"
date: 2012-02-19
forum: Installation &amp; Upgrades
---

### Post by Deepfriedice on 2012-02-19
Hello all.

I've recently been trying to shift back into Ubuntu after leaving Debian Squeeze, but I have been having some troubles with installation.

I downloaded Xubuntu 11.10 AMD desktop and wrote it to a USB drive. Xubuntu will boot to the live desktop fine (that's what I'm typing this from) but any attempt to install the OS the my hard drive will fail with an error message. The error message claims the the installation of grub failed and asks for a alternate location to install grub, upon closing the dialog the installer crashes.

I am running a Toshiba NB300 laptop and have a GPT partition table (but no EFI). What do I need to do to get grub to install successfully?

Possibly relevant info:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=409073](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=409073)
[http://ubuntuforums.org/showthread.php?t=1773665&highlight=Installation+grub+fails]("http://ubuntuforums.org/showthread.php?t=1773665&highlight=Installation+grub+fails&page=2")

---

### Post by Deepfriedice on 2012-02-20
UPDATE

I just successfully installed Xubuntu 10.10 to a spare external hard drive.
The only major difference I can think of between the situation there and on my main HD is that the external drive is using a MSDOS partition table.
 
Obviously changing my laptops partition table from GUID to MSDOS isn't a guaranteed fix, but I will give it a try tomorrow.

Any thoughts or similar cases will be greatly appreciated.

---

### Post by oldfred on 2012-02-20
I use gpt with BIOS and do not have any issues, since early on in chainbooting to a MBR Windows drive.

But you need a bios_grub partition for grub to install correctly. While efi partitions have to be first a bios_grub can be anywhere on drive.

If using gpt with BIOS create a 1MB bios_grub partition. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.


GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

---

### Post by Deepfriedice on 2012-02-20
Thanks for that oldfred, that looks like it will work.
Just to make sure I understand: I need to create a small partition, give it the BIOS_GRUB flag, then tell the installer to install the boot-loader to it; correct?

Thank you very much.


For future reference:
[http://en.wikipedia.org/wiki/BIOS_Boot_partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition)

---

### Post by oldfred on 2012-02-20
When installing with gpt you still install the grub2 boot loader to the MBR of the drive or sda. The extra bios_grub partition is automatically found and used to hold the core.img file for grub2. 

With MBR partitioning the core.img is just in the sectors after the MBR and before the first partition.

---

### Post by Deepfriedice on 2012-02-20
Well, I missed your last message and tried installing the boot loader to the biosgrub partition, which produced some interesting failures. But I got it right the second time round and the new OS is running great.

Thank you very much for you help.
:)

---

### Post by oldfred on 2012-02-21
Glad you got it working.

---

