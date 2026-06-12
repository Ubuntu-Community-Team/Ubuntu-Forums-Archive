---
title: "Making permanent change to grub boot menuentry?"
date: 2019-01-22
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2019-01-22
I dual boot with VeraCrypted Windows, and after I made some change to the Windows 10 grub menuentry in the beginning this has been working fine, i.e. changing the menuentry to point from *EFI\Microsoft\Boot\Bootmgfw.efi* to instead *EFI\VeraCrypt\DcsBoot.efi*.

Something, I am guessing an update, has reverted this back to how it was initially, so that the same entry that was working now makes Windows attempt repairs. Thankfully I can still boot Windows 10 by hitting F12 on boot to bring up the boot menu and selecting VeraCrypt boot loader.

I am not sure how I edited the menuentry in the beginning, but I have been trying to use Grub Customiser this time, and I have edited and saved the Windows entry as:

[ATTACH=CONFIG]282272[/ATTACH]

And I can see this is reflected in /boot/grub/grub.cfg as:

```
menuentry "Windows Boot Manager (on /dev/sda1)" --class windows --class os $menuentry_id_option 'osprober-efi-E625-C979' {
	insmod part_gpt
	insmod fat
	set root='hd0,gpt1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  E625-C979
	else
	  search --no-floppy --fs-uuid --set=root E625-C979
	fi
	chainloader \EFI\VeraCrypt\DcsBoot.efi
}

```

Still when I boot, when I select that menu entry Windows starts attemtping repairs, and if I select 'e' on the menuentry, I can see it is still set to try and boot *EFI\Microsoft\Boot\Bootmgfw.efi. *I rebooted and input sudo update-grub, but this did not change anything.

How can I make the changes I made be reflected in the actual menuentry, and better yet, how can I make it so that this is a last changing, even through future updates?

---

