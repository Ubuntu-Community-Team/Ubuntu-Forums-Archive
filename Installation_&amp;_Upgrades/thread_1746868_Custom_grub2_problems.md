---
title: "Custom grub2 problems"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by markyb73 on 2011-05-02
Hi,

I did a clean install of Natty and as per Maverick etc i like to set up grub to point to other bootloaders on other partitions, which used to work fine but now i get an error. I have several partitions on a second hard drive which run other distros and windows 7.

What i do is in /etc/grub.d is make 30_os-prober non executable so it doesn't look for other operating systems.

```
sudo chmod -x /etc/grub.d/30_os-prober 
```

Then i edit /etc/grub.d/40_custom and add the following to the bottom of the file.

```
#! /bin/sh -e
echo "Adding Windows 7" >&2
cat << EOF
menuentry "/dev/sda3 Windows 7 Enterprise OX" {
set root=(hd0,3)
chainloader +1
}
EOF

#! /bin/sh -e
echo "Adding /dev/sdb2" >&2
cat << EOF
menuentry "/dev/sdb2 Natty Test-Partition" {
set root=(hd1,2)
chainloader +1
}
EOF

#! /bin/sh -e
echo "Adding /dev/sdb3" >&2
cat << EOF
menuentry "/dev/sdb3 Kubuntu" {
set root=(hd1,3)
chainloader +1
}
EOF

#! /bin/sh -e
echo "Adding /dev/sdb5" >&2
cat << EOF
menuentry "/dev/sdb5 Fedora" {
set root=(hd1,5)
chainloader +1
}
EOF

#! /bin/sh -e
echo "Adding /dev/sdb6" >&2
cat << EOF
menuentry "/dev/sdb6 Arch Linux" {
set root=(hd1,6)
chainloader +1
}
EOF

#! /bin/sh -e
echo "Adding /dev/sdb7" >&2
cat << EOF
menuentry "/dev/sdb7 Spare" {
set root=(hd1,7)
chainloader +1
}
EOF
```

Finally i run ```
sudo update-grub
```

Then i can normally boot and see the kernels in my primary os and select another bootloader on another partion.

When i run sudo update-grub i get:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-8-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 143
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done

```

Line 143 in /boot/grub/grub.cfg shows the following:

```
### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```

I am a bit stuck as this used to work fine on Maverick and Lucid, just wondering whether something has changed and i need to modify something.

Any advice would help :D

Thanks!

---

### Post by markyb73 on 2011-05-04
any grub experts?

---

### Post by satanselbow on 2011-05-04
You have got a bit ahead of yourself ;)

Set the execute bit back (+x) on the os_prober and rerun: 

```
sudo update-grub
```

That will regenerate complete grub.cfg file with all your OS possibilities listed. You then want to cut n paste the required entries into your 40_custom file before removing the execute bit from the os_prober - I usually do the same for the memtest file ;)

To edit grub.cfg stick this in a terminal:

```
gksu gedit /boot/grub/grub.cfg
```

You can then pick and choose, customise or remove which menu entries you wish to include by pasting the complete entry into 40_custom - which you have obviously found already ;)  (a complete entry looks something like the example below)

```
menuentry "Ubuntu 11.04 (11.04 NUTTY) (TESTING ONLY)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 912bc06d-8394-4284-b06b-a7f7ce222cc5
    linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda10
    initrd /boot/initrd.img-2.6.38-8-generic
}
```

You can also tweak screen resolution of of the menu, timeouts and a couple of other bits n bobs VERY CAREFULLY! by editing:

```
gksu gedit /etc/default/grub
```

Happy tweaking ;)

---

### Post by markyb73 on 2011-05-04
thanks for the info :)

But the way i want it to work (and it used to in Lucid and Maverick) is that each of those other distro's have their own bootloaders on their root partitions, and as a  new kernel is added i don't need to modify the 40_custom file each time. It used to work fine until i installed Natty, now i get an error. Very frustrating. Any other ideas? :confused:

---

### Post by oldfred on 2011-05-04
I also have a 40_custom that I use. I had not used it in Natty yet, so I added it to my Natty install and got similar errors. But after further checking I had a missing } in one of my stanzas. The line number of the error was just the end of the file and not the location of the typo. After I fixed that typo then it worked just fine.

I do not see anything in what you posted. I do not have the echo, cat, EOF lines. Just the first standard lines and then all my boot stanzas.

You did not delete the exec tail line at the top?

#!/bin/sh
exec tail -n +3 $0

Did you edit /etc/default/grub at all? Check for  a typo there also.

I just reran it with the error on Maverick. I get no errors, and it copies it to the grub.cfg with the missing }.

Second update:
Maverick also reboots ok with the error, but I had not noticed the missing boot stanza as it is for an old version that I do not use anymore.

---

### Post by markyb73 on 2011-05-04
thanks....i will try what you suggested and report back.

---

### Post by markyb73 on 2011-05-05
Its all working now :D

As you suggested in the /etc/grub.d/40_custom file i removed the echo, cat and EOF lines except for the last EOF to look like this.

```
#! /bin/sh -e
menuentry "/dev/sda3 Windows 7 Enterprise OX" {
set root=(hd0,3)
chainloader +1
}

#! /bin/sh -e
menuentry "/dev/sdb2 Natty Test-Partition" {
set root=(hd1,2)
chainloader +1
}

#! /bin/sh -e
menuentry "/dev/sdb3 Kubuntu" {
set root=(hd1,3)
chainloader +1
}

#! /bin/sh -e
menuentry "/dev/sdb5 Fedora" {
set root=(hd1,5)
chainloader +1
}

#! /bin/sh -e
menuentry "/dev/sdb6 Arch Linux" {
set root=(hd1,6)
chainloader +1
}

#! /bin/sh -e
menuentry "/dev/sdb7 Spare" {
set root=(hd1,7)
chainloader +1
}
EOF

```

Ran sudo update-grub and all is good.

Thanks!!!

---

### Post by oldfred on 2011-05-05
Glad it worked.

I do not even have the last EOF in mine. But I have heard that it used to be sensitive to extra characters (even blanks) at end or end of lines.

---

### Post by markyb73 on 2011-05-05
Just removed the EOF and it still updates grub fine.

---

### Post by drs305 on 2011-05-05
I'm curious if you see either of these errors when you boot from Grub 1.99 (Natty). It doesn't stop the boot, it's just displayed:
> Error: No Argument Specified
Error: Invalid Signature

When Grub 1.99 originally came out, if you used the following it would generate them:
> search --no-floppy --fs-uuid **--set** 912bc06d-8394-4284-b06b-a7f7ce222cc5

The solution was to use the following (which is what is auto-generated with update-grub but wouldn't be in place with a custom file you created or copied from an older Grub2 menuentry):
> search --no-floppy --fs-uuid **--set-root** 912bc06d-8394-4284-b06b-a7f7ce222cc5

---

### Post by oldfred on 2011-05-05
With the typos, it would not even convert the file to grub.cfg. It just created /boot/grub/grub.cfg.new.

I do not have any search lines as I know the drive, partition I want. But have had issues on flash drives with drive changing, but I just manually edit. 

Also my chain load to another MBR change. Boot drive is always hd0 and I normally boot sdb, so to chain to the MBR of sda I have to use hd1. I only use the chain entries when I forget to use f12 and want to use MBR rather than a specific entry or do not have specify entry in the version I am booting. (It is confusing to me too, but I prefer how I have it.) I have not tested all this with Natty yet.

---

