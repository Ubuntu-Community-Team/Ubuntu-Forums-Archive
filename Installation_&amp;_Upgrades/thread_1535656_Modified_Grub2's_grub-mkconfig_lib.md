---
title: "Modified Grub2's grub-mkconfig_lib"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by slickvguy on 2010-07-21
WARNING: Don't mess around with this unless you understand it fully or you can/will have serious problems with your booting. 

Something had been bothering me about Grub2's grub.cfg file. When you look at the file, you see entries like this:

```
menuentry 'Ubuntu, with Linux 2.6.34-020634-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
        set root='(hd0,3)'
	search --no-floppy --fs-uuid --set da29e52f-274d-4064-b152-7357d3dcd2bd
	linux	/boot/vmlinuz-2.6.34-020634-generic root=UUID=da29e52f-274d-4064-b152-7357d3dcd2bd ro   quiet splash
	initrd	/boot/initrd.img-2.6.34-020634-generic
}
```

The "set root=" and the "search... --set" (which uses the UUID) are redundant. One can easily edit the grub.cfg file and take out one or the other lines that set the root variable, but I was interested in finding a better/automatic way otherwise my edits would be replaced each time update-grub runs. 

I looked into all the configurable files, but the code that generates those two specific lines was not in the /etc/grub.d directory (or the other obvious directories/files). Hmmm...where were those lines coming from? 

I downloaded the source code for Grub2, did some tracing, and found the file that contained the code responsible for writing those lines in grub.cfg. The file is /usr/lib/grub/grub-mkconfig_lib. 

```
  # If there's a filesystem UUID that GRUB is capable of identifying, use it;
  # otherwise set root as per value in device.map.
  echo "set root='`${grub_probe} --device ${device} --target=drive`'"
  if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
    echo "search --no-floppy --fs-uuid --set ${fs_uuid}" --target=drive`'"
  fi
```

See? Even the comment suggests it should be one or the other, but not both. I made a small change to the script. Make sure you make a backup copy before saving any changes!

```
  # If there's a filesystem UUID that GRUB is capable of identifying, use it;
  # otherwise set root as per value in device.map.
  # svg mod: One method/format or the other - not BOTH!
  if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
    echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
  else
    echo "set root='`${grub_probe} --device ${device} --target=drive`'"
  fi
```

When you run update-grub2, the entries in grub.cfg (if your partitions in question have UUIDs) now look like this:

```
menuentry 'Ubuntu, with Linux 2.6.34-020634-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	search --no-floppy --fs-uuid --set da29e52f-274d-4064-b152-7357d3dcd2bd
	echo	'Loading Linux 2.6.34-020634-generic ...'
	linux	/boot/vmlinuz-2.6.34-020634-generic root=UUID=da29e52f-274d-4064-b152-7357d3dcd2bd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.34-020634-generic
}
```

Much better! :)

Anyways...just thought I'd share it with those who might be interested.

---

