---
title: "Boot from CD/DVD : error: no such device"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by bananabob on 2010-07-12
I installed 10.04 onto a new HDD the install went perfectly.
When I cold booted (boot after a power off) this morning I got the
following message
"Boot from CD/DVD :
error: no such device: (long string identifying the UUID)
grub rescue >"

I booted up again with the Live CD and used the restart option. Allowing,
what I will call a, warm boot.
This time the system booted up perfectly.

Using our friend Google I did some searches and found the following

[http://ubuntuforums.org/showthread.php?t=1481733&highlight=grub2+error%3A+device](http://ubuntuforums.org/showthread.php?t=1481733&highlight=grub2+error%3A+device)

This tells me to edit /etc/default/grub and remove the comments from:

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to
Linux

#GRUB_DISABLE_LINUX_UUID=true


Which I did.

It didn't work from a cold boot. Warm boot was OK after using the Live CD.

More searching revealed

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

Which told me to place comments in the following
/usr/lib/grub/grub-mkconfig_lib to remove the search line in grub.cfg

thus:

 # If there's a filesystem UUID that GRUB is capable of identifying, use it;
    # otherwise set root as per value in device.map.
    echo "set root=`${grub_probe} --device ${device} --target=drive`"
    # if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
    # echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
    # fi

This didn't work from a cold boot either. I looked at the resulting
grub.cfg and the entries for 10.04 did not have any mention of the  UUID.

Is there someone who can point me in the right direction to obtain a
solution to this problem?

This is a dual boot system with 8.04 on the other HDD. Booting back into
8.04 was achieved by changing the order of the SATA cables allowing the
system to boot using Grub (from 8.04 install) not Grub2 (from the 10.04
install). I can not get access to the 10.04 HDD from 8.04 because the
filesystem is EXT4.

Thanks
James

---

