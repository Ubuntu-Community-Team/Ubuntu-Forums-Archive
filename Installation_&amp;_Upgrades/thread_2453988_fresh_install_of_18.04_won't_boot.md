---
title: "fresh install of 18.04 won't boot"
date: 2020-11-20
forum: Installation &amp; Upgrades
---

### Post by frankdn01 on 2020-11-20
Due to user error I had to reinstall 18.04.  All went well, taking default choices, on my amd64 Thinkcentre, until the reboot after completion.  I did choose to reformat the disk, wiping all files.  Then this:

Error: no such partition
Entering rescue mode
grub rescue>

There was no indication during system install that grub would have a problem.  Thanks for your thoughts!

---

### Post by Bashing-om on 2020-11-20
frankdn01; Hello

Let's have a look at what we are working with.

From the liveUSB (installer) booted in "try ubuntu" mode;
post back the result of terminal command:
```

sudo fdisk -lu

```
see here the partitioning - that maybe this is EFI and you are booting legacy or vise-versa.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by frankdn01 on 2020-11-20
Thank you!

I'm seeing 3 partitions: Linux swap, Linux filesystem, and the first (/dev/sda1) is EFI.  Thing is, I don't know what that means.

---

### Post by Bashing-om on 2020-11-20
frankdn01; Well -

that sda1 partition contains the boot code(s).
We can "assume" - yukkie- that this is a EFI system.

Have you set in the boot-manager (bios) to boot EFI ?
OR do we need to mount that partition and have a look at what it contains ?

[INDENT]still the process. the process
[/INDENT]

---

### Post by frankdn01 on 2020-11-20
OK, before continuing, I followed your 'popularpages' link and screwed things up further.  Now, on a 2nd attempt, I get this... which is progress of a sort :-)...

dpkg: error processing grub-efi-amd64-signed (--configure)
installed grub-efi-amd64-signed post-installation script subprocess returned error exit status 1
/usr/bin/dpkg error code 1

and now, fdisk -lu shows only 2 partitions, and the first (smaller, 512 mb) is 'EFI system'

I have not touched the bios.

BTW I should add that this box booted 18.04 and 16.04 before it, no problems.  I don't recall any trouble installing 16.04 on this machine years ago,

I mounted the EFI fs and the first directory is EFI.  It contains BOOT and ubuntu.

---

### Post by Bashing-om on 2020-11-20
frankdn01; Ouch!

At this point - considering this is a new install - Me thinks you are best served with a new install attempt.
Will be much quicker and avoid further errors.
You did verify the downloaded .ISO file, yes ?

This time insure for sure for sure that you boot the installer in EFI mode; >> erase disk and install ubuntu.

[INDENT]2nd time the charm?
[/INDENT]

---

### Post by frankdn01 on 2020-11-21
Thank you Bashing-om, for your help (and patience!)

I did do a fresh install, wiping all files and reformatting the disk, which is how I ended up with this: (Oh and I did verify the dvd, it checked OK.)

>sudo fdisk -lu
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 883D862F-BDB6-49AC-AB6C-D4026A2F531B

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624 488396799 487346176 232.4G Linux filesystem

The box now boots to the grub rescue prompt.  I searched for help with grub rescue without effective result.  One page, linuxhint/grub_rescue_ubuntu_1804 looked promising, but several commands he uses don't exist on my grub.  Example:
'grub rescue> linux' returns 'unknown command' or words to that effect.

I should add that searching through my BIOS, the words 'EFI' and 'UEFI' are not there.  This box originally came with Windows 7 installed and when I first tried to install Linux in dual-boot mode, that failed.  I don't remember how I managed to install Linux, but this has been a Linux-only box since then.

---

### Post by frankdn01 on 2020-11-21
I spent some time dealing with grub rescue.  Watching [https://www.youtube.com/watch?v=OJTGpvZO8Oc](https://www.youtube.com/watch?v=OJTGpvZO8Oc), at 4:16 he enters: 'insmod normal'.  This fails for me: grub appears to be not finding the file <mumble>/i386-pc/normal.mod.  There is a normal.mod in /boot/grub/x86_64-efi however.  Would it help if I posted my /boot/grub/grub.cfg?

I should add that I did finally find a UEFI setting in the BIOS.  It was set to 'auto'.  I set it to UEFI (meaning only, apparently) and on bootup I did not fall into grub rescue.  Instead I learned that no OS could be found.  Another data point?

---

### Post by Bashing-om on 2020-11-21
frankdn01; Hummm ----

Perplexing - to say the least. as you are installing from a DVD then the boot code location should install correctly (USB install sometimes can install the coot code to the wrong device).

In any event, now let's explore why the boot does not find the operating system.

Boot to the grub prompt and execute grub command:
```

ls

```
that is an ell and s - to see that the partitions are known and how we are to address them in further discovery. Directly we will look for the system's boot directive file.

[INDENT][INDENT]we follow the path[/INDENT][/INDENT]

---

### Post by oldfred on 2020-11-21
What brand/model system?
Some like Acer need you to set "trust" on ubuntu UEFI boot entry.
Some like HP do only like "Windows Boot Manager" as boot entry. 

Have you updated UEFI/BIOS to latest available from vendor. 
Spectre virus, repoline
Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching.

---

### Post by frankdn01 on 2020-11-22
Solved!  ...well not really.

Thank you both for helping me through this!  I don't really know why it worked, but here's what I did:
First,  as I reported above, after booting the DVD in 'try linux' mode, I ran fdisk  -lu on the hard disk I've been trying to install to:

root@pc:/home/self# fdisk -ls
[B]Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624 488396799 487346176 232.4G Linux filesystem

[/B]Grub rescue> ls produced:
**(hd0) (hd0,gpt2) (hd0,gpt1)**

where gpt2 was sda2.

This AM I rebooted the DVD in 'try' mode again, and ran gparted on /dev/sda.   I *deleted both partitions* and then executed 'install'.  Result:
root@pc:/home/self# fdisk -lu
[B]Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1  *     2048 488396799 488394752 232.9G 83 Linux[/B]

Restarting, Ubuntu 18.04 booted on /dev/sda and is running as I type this.  If anyone can explain why this worked I'd be grateful for the education.  But as of now I'm a happy camper. 

Incidentally this all started when I upgraded to 20.04, to discover that an app I use a lot (gourmet) isn't supported.  Naive me trying to work around that broke 20.04 and here I finally am.

---

### Post by oldfred on 2020-11-22
Since now you do not have an ESP - efi system partition, it looks like you reinstalled in BIOS boot mode.

How you boot live installer UEFI or BIOS, is then how it installs. 
With UEFI hardware usually better to use UEFI, but some early UEFI have had issues and BIOS then often was easier.

---

