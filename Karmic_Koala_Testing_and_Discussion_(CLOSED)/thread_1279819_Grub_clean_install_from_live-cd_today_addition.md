---
title: "Grub clean install from live-cd today addition?"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jhawk on 2009-10-01
Since menu.lst is no longer in /boot/grub and ref is made to /etc/grub.d/40_custom perhaps we need to provide correct syntax example in that file:

I edited it as below:

# This file provides an easy way to add custom menu entries.Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Fedora 11 x86 (on /dev/sda3)" {
	set root=(hd0,3)
	chainloader +1
}

However, this fails to be added to menu. Syntax must be wrong.

Can anyone advise on correct synatx?

---

### Post by VMC on 2009-10-01
> **jhawk said:**
> Since menu.lst is no longer in /boot/grub and ref is made to /etc/grub.d/40_custom perhaps we need to provide correct syntax example in that file:

I edited it as below:

# This file provides an easy way to add custom menu entries.Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Fedora 11 x86 (on /dev/sda3)" {
	set root=(hd0,3)
	chainloader +1
}

However, this fails to be added to menu. Syntax must be wrong.

Can anyone advise on correct synatx?

Did you do a "sudo update-grub"

---

### Post by ranch hand on 2009-10-01
My working custom entry for Mandriva looks like this;
```

echo "Adding Mandriva2009-1-Gnome on sda12" >&2
cat << EOF
menuentry "Mandriva 2009 Gnome sda12" {
linux (hd0,12)/boot/vmlinuz
initrd (hd0,12)/boot/initrd.img
}
EOF

```Your menu entry for Fedora may be the way to go but I would plug it into this format.

You will need to run update grub for the new /boot/grub/grub.cfg to be generated.  That is where the menu you see on booting comes from.

When it is generated the things entered on it are in the order of the file (script) names in /etc/grub.d.  Thias means that your custom entries from 40_custom are at the bottom of the menu.

You can create another file and put it between 05_debian-theme and 10_linux (name it, say 07_custom) and use the same type thing as you did in 40_custom.

Here is the start of my 08_custom file;
```

#!/bin/sh 
# This file is an example on how to add custom entries 

echo "Adding Kinky1.1A4 on sda16 (2.6.31-11-generic)" >&2 
cat << EOF
menuentry "Kinky1.1A4 on sda16 2.6.31-11-generic" {
    set quiet=1
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set e62bedbe-f9d8-43a1-a39a-32e651a233c0
    linux    /boot/vmlinuz-2.6.31-11-generic root=UUID=e62bedbe-f9d8-43a1-a39a-32e651a233c0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-11-generic
}
EOF

echo "Adding JauntyA6 on sda17 (2.6.31-11-generic)" >&2 
cat << EOF
menuentry "JauntyA6 on sda17 2.6.31-11-generic" {
        set root=(hd0,17)
        linux /vmlinuz root=/dev/sda17 so quiet splash
        initrd /initrd.img
}
EOF

```Note that the second entry is for Jaunty updated to A6 and does not look like the entry above it.

It is kind of a generic entry that does not define the kernal.  It will work for right through updates with no editing.

Edit
When you are editing this (I use gedit) with your favorite editor it is important to go to Preferences and set it so that there isno "line wrapping".  Will not work if any of your lines wrap.

I realize that this should not be the case with your entries.  There are some other entry options for some interesting stuff that may have long lines.

I have not gotten it to work with anything I want to use it for but you are supposed to be able to boot .iso files directly from grub2.  Acouple folks have done this with a rescue disk .iso.  I want to boot an Ubuntu LiveCD.  Haven't figured out the right boot path.

Grub2 IS going to be GREAT.  And FUN.

---

### Post by jhawk on 2009-10-01
Thanks All

I have Fedora working but Windows is another issue, I need to sit down with the manual "RTFM". Grub can't figure out why I have Windows 7 x86 RTM, Windows 7 amd64 bit RTM and Windows 7 amd64 bit RC. All entries map to x86 32 bit.

jhawk

---

### Post by ranch hand on 2009-10-01
If you have Fedora working you had to run update-grub.  That really should have picked up your Winwhatever.

You have not changed 30_os-prober so that it is not executable have you?

I do not have MS on my box but most folks seem to be getting MS to come up by running update-grub.  There are some reports of it identifying Win7 as Vista.

I don't have links to them because I don't use MS, but there are threads in this forum that have covered the entry you need quite well.  I think it  is very like the one you used for Fedora.

---

### Post by jhawk on 2009-10-02
The documentation is definitely a work in progress. Here is what I have gleamed so far.

```

#!/bin/sh
# /etc/grub.d/25_hawk
# required for save_default_entry to work
prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib

echo "Adding Fedora 11 x86 (on /dev/sda3)" >&2
cat << EOF
menuentry "Fedora 11 x86 (on /dev/sda3)" {
EOF
save_default_entry | sed -e "s/^/\t/"
cat << EOF
	set root=(hd0,3)
	chainloader +1
}
EOF

echo "Adding Windows 7 32 bit RTM (loader on /dev/sda1)" >&2
cat << EOF
menuentry "Windows 7 32 bit RTM (loader on /dev/sda1)" {
EOF
save_default_entry | sed -e "s/^/\t/"
cat << EOF
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 964c56634c563de5
	chainloader +1
}
EOF

echo "Adding Windows 7 64 bit RC (loader on /dev/sdb1)" >&2
cat << EOF
menuentry "Windows 7 64 bit RC (loader on /dev/sdb1)" {
EOF
save_default_entry | sed -e "s/^/\t/"
cat << EOF
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 67af6e2808c752ac
	chainloader +1
}
EOF

echo "Adding Windows 7 64 bit RTM (loader on /dev/sdb2)" >&2
cat << EOF
menuentry "Windows 7 64 bit RTM (loader on /dev/sdb2)" {
EOF
save_default_entry | sed -e "s/^/\t/"
cat << EOF
	insmod ntfs
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 7115061167664bcc
	chainloader +1
}
EOF

```

What works? 
[LIST]
[*]Save default
[*]Fedora 11 x86
[*]Windows 7 32 bit RTM (loader on /dev/sda1)
[*]Added graphics package
[/LIST]
What Fails?
[LIST]
[*]Windows 7 64 bit RC  (loader on /dev/sdb1) 
[*]   Windows 7 64 bit RTM (loader on /dev/sdb2)
[*]   In both instances Windows 7 32 bit RTM (loader on /dev/sda1) is started
[/LIST]
May require disk mapping?

This like all things will be resolved by patience and perseverance.

jhawk

Update: I have used the bcd work around and edited Windows bootmgr to accomplish the task required.
However, this is only a workaround and I will resolve this issue with grub2 not working, but at least
I have a working system for now.

---

### Post by ranch hand on 2009-10-02
You really need to copy all the entries that work and put them in an .odt document. 

Save that bugger somewhere handy (a directory titled Grub2 maybe) so that you can cut/paste for posts when the common horde gets the release and has a collective fit over grub2.

If you think about the possibilities, rather than the problems we are having, grub2 looks better all the time.  With generic entries in a custom file there is no need to ever update the buggers.  When you have your drive set up you can "turn off" 10_linux, 20_memtest, 30_os-prober and nothing can ever screw with your menu.

I changed one of my 9.10 installs yesterday and went to edit my custom files.  It was a generic entry.  I had done a clean install of the daily build to test the .iso and the custom file is in the OS that I have always used as Boot/root.

I stopped myself from changing it and tried it.  Worked great.  It was pointed at the right partition for root and it just booted as well as it had in the OS that was formatted out.  I think that this is just really great.

That said, save your notes, this may currently be the only documentation of this problem.  to put it another way, folks think I am nuts for having a bunch of Linux distros on my box, why, by all that is sacred, would someone have 3 installs of MS products?  What on earth did your poor box do to you?

Your experience will be greatly needed come release time and through the release of 10.04.  Write it down, keep it safe, share it.

I don't even allow MS stuff on here.  Won't have wine on here.  I am really interested in what you get done.  I will be following this closely.  Keep us up to date. I think this is the thread that I will be keeping for grub2 and Win Jerry Lewis Pro (or whatever they are selling now).

If you think about what os-prober has to do, it has come a long way since A2.  Then you come along.  Good job, keep it up.  HAVE FUN

---

