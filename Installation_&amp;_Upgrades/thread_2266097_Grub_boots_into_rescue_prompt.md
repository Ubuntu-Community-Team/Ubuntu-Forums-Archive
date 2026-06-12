---
title: "Grub boots into rescue prompt"
date: 2015-02-19
forum: Installation &amp; Upgrades
---

### Post by Thimoteus on 2015-02-19
Before I describe anything, here's my summary from boot-repair: [paste.ubuntu.com/10316177]("http://paste.ubuntu.com/10316177/")

I originally installed Ubuntu under CSM mode. I can get into Ubuntu just fine using what the OP in [this thread]("http://ubuntuforums.org/showthread.php?t=2192777") used. I'm on a Samsung (not sure if that's relevant but [this guy seems to think so]("https://bbs.archlinux.org/viewtopic.php?pid=1242611#p1242611")). I'm wary of trying anything, because before today I was using grub to get into my system's BIOS/EFI menu (it doesn't accept key presses for whatever reason, nor will it load live usbs unless from the grub command line).

I'd rather not have to do the set root, set prefix, ..., boot dance each time, but I don't want to make things worse either.

EDIT: The problem seems to be fixed. I guess it took boot-repair an extra restart or something? Anyway, to the people of the future: Sorry, I didn't do anything specific except run boot-repair.

HOWEVER, now my grub menu is populated with a bunch of .efi items, probably left by old distrohopping habits. I wouldn't mind getting rid of those if someone could tell me how to do so safely?

---

### Post by oldfred on 2015-02-21
Backup efi partition.

Remove any folders from efi partition that are not for current installs.

Then with efibootmgr remove entries in UEFI.

       sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

