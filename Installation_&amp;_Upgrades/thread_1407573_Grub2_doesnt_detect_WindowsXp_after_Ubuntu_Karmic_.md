---
title: "Grub2 doesnt detect WindowsXp after Ubuntu Karmic Install"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by sunds on 2010-02-15
Hi

I installed Ubuntu9.10 on a USB hard drive attached to my laptop. Laptop has pre-installed XP in the in-built hard-drive. Point to be noted is that my hard-drive is protected via encryption software called Pointsec.

The installation of Ubuntu on the USB hard drive went through fine and I'm able to boot Ubuntu from it.

But now the problem is, GRUB2 fails to detect the Windows XP installation. 

Can someone tell me how I can force GRUB2 to boot Windows XP from hd0,0?

The GRUB1 way of configuring /etc/grub/menu.lst does NOT seem to work with GRUB2.

Thanks in advance for the help

Regards,
Sundar

---

### Post by darkod on 2010-02-15
You should investigate further whether you can force it at all to go trough Pointsec. I guess that is why it didn't detect it automatically.
Otherwise, for grub2 custom menu entries are made in /etc/grub.d/40_custom and read more about the syntax of the entries here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by sunds on 2010-02-15
Thank Darko. The link proved very useful in understanding how GRUB2 works.

I just have one doubt. My Windows XP is installed in (hd0,0). I saw the below example for manual windows entry.

How can I modify this to make Grub boot from (hd0,0) for WindowsXP?

**Manual Windows Entry** (with /etc/grub.d/30_os-prober made unexecutable)
     Quote:
                                                 #! /bin/sh -e

echo "Adding Windows 43_custom" >&2
menuentry "Windows Vista 43_custom" {
insmod chain
insmod ntfs
search --fs-uuid --set CFFCFF9EECFF7F49
chainloader +1
}

---

### Post by darkod on 2010-02-15
Usually you would have:

set root=(hd0,1)

before the search..... line (grub2 is counting partition starting from 1, not 0 like in grub1).
Also in the search line the CFFCFF... string is the UUID of the windows partition. You need to use the UUID of your windows partition. You can get UUIDs of partitions with:

sudo blkid

---

### Post by oldfred on 2010-02-15
Grub2 is smarter than old grub and wants to load drivers to see the partition before chainloading so it will not crash if the chainload does not work. but it may not be able to read your  encryption.

You can still do a barebones chainboot to the MBR of the harddrive which is all the BIOS does (unless the BIOS is part of the encryption).
I would add this to 40_custom as that file is all setup to work.

 menuentry “Drive sda = hd0 by chainloader”  {
chainloader  (hd0)+1
}

example from:
[http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0)

---

### Post by sunds on 2010-02-16
Thanks. I updated the grub.cfg with the menuentry you mentioned by using the update-grub command.

However, the menuentry doesnt show up in the GRUB menu during start up. Please note that i had to press ESC key continuously to bring up the GRUB menu, otherwise it was always going into Ubuntu by default.

Should I have to run grub-install /dev/sda to update the MBR with the modifications to GRUB?

Thanks
Sundar

---

### Post by oldfred on 2010-02-16
With grub2 it is the shift key to get the grub.cfg menu. You should not have to reinstall grub, you are just updating the grub.cfg file.

Did you turn off the executable flag on 40_custom? Not sure if 30_custom has to run to get 40 loaded.

Grub2 settings:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by darkod on 2010-02-16
> **oldfred said:**
> 
Did you turn off the executable flag on 40_custom? Not sure if 30_custom has to run to get 40 loaded.


You mean 30_os-prober right? No, it doesn't have to run. In fact, the recommendation is when using 40_custom to make your own entries, to disable the executable flag for 30_os-prober so it doesn't add any OS potentially.

PS. I think the Pointsec is making all the issues here, but I have no clue about it so I'm not jumping in. :)
Do you have only one grub? Are you sure you are not booting another grub (from your internal for example) so you're not seeing the menu item you added?

---

### Post by mountney on 2011-01-14
I had to [COLOR="Red"]modify[/COLOR] /etc/grub.d/11_Windows to boot WinXP...

#! /bin/sh -e
echo "Adding Windows XP" >&2
cat << EOF
menuentry "Windows XP" {
[COLOR="Red"]insmod ntfs[/COLOR]
set root=(hd1,1)
[COLOR="Red"]drivemap -s (hd0) \${root}[/COLOR]
chainloader +1
}
EOF

Then of course run update-grub and reboot...

Dell Optiplex GX520
2GB Ram
500GB Sata - Ubuntu 9.10 (/dev/sda)
250GB Sata - WinXP Professional (/dev/sdb)

Found that os-prober and thus 30_os-prober were NOT working so WinXP was not detected. Still researching why os-prober isn't detecting WinXP. I have three other systems, Debian 5 (64bit)/Win7 Ultimate (ASUS P6T), Ubuntu 10.04/WinXP (EPOX EP-4PLMI) and Ubuntu 9.10/WinXP (HP Pavilion dv8000 laptop) and on these os-prober/30_os-prober work fine.

Hope this helps some...

---

### Post by Quackers on 2011-01-14
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

