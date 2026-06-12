---
title: "Windows 10 November Update Killed my UEFI Grub install.   Help?"
date: 2015-11-14
forum: Installation &amp; Upgrades
---

### Post by mattlach on 2015-11-14
Hi all,

So it turns out that Microsoft in their wisdom automatically download and install the Windows 10 November update / Threshold 2 thing.

When it installs - Going from the June initial release of Windows 10, to the November Threshold 2 release it doesn't just install like an update, but rather like a full OS upgrade.

As a user, you have no input to prevent this.  IF Windows is left to idle on its own, it will download the November update to version 1511, and after a while reboot and install itself (3am for most people)

When it did this it somehow messes with the EFI partition resulting in this:

[img]https://c1.staticflickr.com/1/705/23027080981_c6dd6dbd35_n.jpg[/img]

I'm relatively new to UEFI, having done traditional BIOS type booting in the past, so I assumed it would just be a matter of booting from my handy Ubuntu Live USB stick, chrooting into my linux install, and re-running update-grub.

Except, this had no effect.   The command output looked like it found everything, and updated grub, but rebooting took me to this same screen.

The Windows EFI entry is still intact, so I can manually choose to boot from it in my BIOS, but during the Windows 10 update, but when I choose my Ubuntu entry, I just get the output above again.

Any suggestions on how to repair this would be greatly appreciated.

Right now I'm guessing I'll have to boot in Windows rescue mode, go into the command line and delete the Ubuntu EFI entry, and then reboot back to my trust Ubuntu USB live stick, chroot into my install and issue a command something like this:

```
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy --debug
```

All this is horribly obnoxious. If I am going to have to do this ever few months when Microsoft decides to issue another "upgrade" it's going to drive me absolutely insane...

Any help appreciated!

---

### Post by mattlach on 2015-11-14
Alright, my suspected solution above did the trick.

I had to boot from an ubuntu live disk, chroot into my linux partition, and then use efibootmgr to delete the Ubuntu EFI entry.

After that I had to reinstall grub into an EFI entry with grub-install.  Now everything works.

Still going to be a huge pain in the ass if I'm going to have to do this every single time Microsoft comes out with an update.

With their new "Windows as a Service" approach they have promised that these updates will come more often, as often as every few months. :mad:

Really is making me take another look at whether or not I want to keep Windows installed at all.   I keep it for the few programs I want to run that don't work in Linux, and for games, but there are always work-a-likes in Linux that I could use and now that I am older, I really don't play games that often anymore.

I could probably get rid of Windows all together and never have to deal with this crap again...

---

### Post by oldfred on 2015-11-14
Windows may have/probably just reset UEFI to have Windows as first entry in UEFI or UEFI default boot.
And reinstalling grub just had grub set ubuntu as first in UEFI boot menu.

You can check boot order and use efibootmgr to change boot order.
Most UEFI should let you change boot order in UEFI boot tab.

sudo efibootmgr -v

 You would first type sudo efibootmgr -v to get a list of boot options. Note the number associated with the Ubuntu entry -- for instance, it might be Boot0005. You'd then type sudo efibootmgr -o 5 to make "Ubuntu" (actually GRUB) the default boot loader. (You can specify a set of boot loaders to be tried in order, as in sudo efibootmgr -o 5,1,2 to use 5, then 1 if that fails, then 2 if both 5 and 1 fail.)
Some require all four digits, others accept just the one or two.


 [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

### Post by mattlach on 2015-11-15
> **oldfred said:**
> Windows may have/probably just reset UEFI to have Windows as first entry in UEFI or UEFI default boot.
And reinstalling grub just had grub set ubuntu as first in UEFI boot menu.

Nope.   That's not what happened at all.

The order was the same, and it was still set up to load Ubuntu's EFI entry on boot.   Somehow the Windows update corrupted the Ubuntu EFI entry.

This is actually rather odd, as I would have expected it to just be ignorant to the existence of Grub and just overwrite it completely, and boot from Windows next reboot, but this is not what happened.

It was still booting from the Grub based EFI entry, but that EFI entry had become corrupted.

---

