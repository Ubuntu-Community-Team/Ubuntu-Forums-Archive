---
title: "GRUB in other then MBR"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by kapetr on 2011-02-08
Hello,

in past times I every time had install GRUB in MBR and also in partition with root (/) (containing also /boot).

The reason was: if GRUB in MBR was corrupted - e.g. by install of other OS, then I had only to run some GRUB and in command line chain my backup GRUB installation in root partition - without get crazy by adding kernel parms, initrd names, ...


So now I have installed new Ubuntu 10.10 with GRUB to MBR.

But I can not install GRUB also in /dev/sda3 (root).
I get:

> 
$ sudo grub-install /dev/sda3
[sudo] password for gogo: 
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
$


So ?

1. Why is that BAD idea ?
2. By install to MBR is not used blocklist to load stage 1/2 or what ?!
3. Should I use --force ? What could go wrong ?

--kapetr

---

### Post by oldfred on 2011-02-08
With grub2 in the MBR and if that is all that is messed up then this will work:

grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

Grub2, in trying to accommodate all the new types of systems is larger. Blocklists are just addresses of the files. If you move the file then it will not boot. Even a fsck could move a file and then you cannot boot without a grub2 reinstall. If you can live with that then you can install grub2 to the partition.

---

### Post by kapetr on 2011-02-09
Thank You for good answer.
I will do that so.

Note: I have find excellent explanation, how GRUB2 works - exactly that, what I could not find in standard docu.

See: [http://people.apache.org/~skitching/MineOfInformation/linux/Booting_Linux_on_x86_with_Grub2.html]("http://people.apache.org/~skitching/MineOfInformation/linux/Booting_Linux_on_x86_with_Grub2.html")

So - only difference between installing GRUB2 in "MBR" and in partition is:

1. MBR - core.img is in sectors 2-63 == outside of any filesystem
2. partition -  core.img is in some filesystem (could by problematic)

But the boot process, boot code in boot record, ... is the same.

BTW - do not NTLDR the region after MBR too ?

--kapetr

---

### Post by oldfred on 2011-02-09
windows has part of its code in the MBR, but all that does is then call more code in the PBR, partition boot sector. Then then calls ntldr and loads boot.ini.

Lots of detail, pictures worth reviewing. Discusses Vista & dual boot, but applies to all MBR (msdos) based systems.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

