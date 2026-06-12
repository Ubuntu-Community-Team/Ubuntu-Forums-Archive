---
title: "grub-install mysterious message &quot;source_dir doesn't exist&quot;"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by kornelix on 2013-05-02
I have multiple distros installed and wanted to move grub to the newest one: ubuntu 13.04
I did what I always did but it no longer works.

$ sudo update-grub
This runs OK and puts grub.cfg at /boot/grub

$ sudo grub-install /dev/sda
This produces the following error:
"source_dir doesn't exist. Please specify --target or --directory"

The info page for grub-install is useless. It tell me to do what I did.
The information regarding --target and --directory is incomprehensible. 

update-grub seems to be looking for "modinfo.sh" which I cannot find.

---

### Post by fantab on 2013-05-03
> **kornelix said:**
> I have multiple distros installed and wanted to move grub to the newest one: ubuntu 13.04
I did what I always did but it no longer works.

What did you do exactly? How did you "move grub to the newest"? and Why? What distro was handling the Grub before you "moved' grub?

---

### Post by kornelix on 2013-05-03
How did I move grub?
1. Put custom menu in /etc/grub.d
2. Update /etc/default/grub - which grub to pre-select
3. $ sudo update-grub
4. $ sudo grub-install /dev/sda  (failed)

Why did I do this?
I generally use grub from the newest install so grub is up to date.

Beforehand Ubuntu 12.10 was the grub source.

This turns out to be a known problem. The new Ubuntu install used grub-uefi instead of grub-pc. I found this with a google search using the search terms "grub" and "source_dir doesn't exist". Searching the Ubuntu forums returned hundreds of irrelevant posts. 

I fixed the problem with $ sudo apt-get install grub-pc

---

### Post by fantab on 2013-05-03
> **kornelix said:**
> This turns out to be a known problem. The new Ubuntu install used grub-uefi instead of grub-pc.

This wouldn't have happened unless there is GPT partition-table, efi partition Fat32, and UEFI enabled in your BIOS, and you install using 'uefi' install... can you confirm any of this? Is there any Windows in the picture booting with Uefi anywhere?

I am glad, however that you have figured out the cause and fixed it.

---

### Post by kornelix on 2013-05-03
1. There were no changes in partitions or BIOS since my prior grub install (via Ubuntu 12.10).
2. BIOS pages do not mention UEFI
3. There is a Windows 7 partition on the disk.
4. I used the 13.04 64-bit CD image from the Ubuntu web site, labeled "for newer machines".

I just now looked at the files on the CD and it seems to have grub-uefi and not grub-pc.
If I should have used some other CD image, where is it ???

Thanks for looking into this.

---

### Post by oldfred on 2013-05-03
I installed 13.04 in my sdc MBR drive and ran sudo update-grub and reinstall to sda with out any errors.
I do have a couple of gpt drives booting with BIOS, but have not installed 13.04 to them yet. I did not yet add my 40_custom to that install yet.

Many new systems have both UEFI & BIOS boot capabilities. And how you boot installer either UEFI or BIOS is how it installs. It should not install grub-efi or grub-efi-signed if in BIOS mode as that uses grub-pc.

I have had issues with typos in 40_custom. I had a typo since the beginning of grub2 (missing end } ) and one boot stanza for an old install was missing. I never noticed. With grub 1.99 it stopped updating grub until I fixed the typo.

---

