---
title: "Three MS-Win : how to boot each one ?"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by tompravi on 2010-10-19
I have three installation of Windows :

/dev/sda1    Windows 7
/dev/sda2    Windows 7
/dev/sda3    Windows XP

Before the “new” grub I could boot a Windows partition hiding the other two Win_partitions.
I've searched, I found few solutions and I've created a 40_custom file in /etc/grub.d with the following settings :

#!/bin/sh

echo "Adding 40_custom menu entries." >&2

exec tail -n +3 $0

# This file provides an easy way to add custom menu entries.  Simply type the

# menu entries you want to add after this comment.  Be careful not to change

# the 'exec tail' line above.



menuentry "Yiannis" {

insmod chain

insmod ntfs

parttool (hd0,1) hidden-

parttool (hd0,2) hidden+

parttool (hd0,3) hidden+

parttool (hd0,1) boot+

set root='(hd0,1)'

search --no-floppy

chainloader +1

}


menuentry "Alla" {

insmod chain

insmod ntfs

parttool (hd0,2) hidden-

parttool (hd0,1) hidden+

parttool (hd0,3) hidden+

set root='(hd0,2)'

parttool (hd0,2) boot+

search --no-floppy

chainloader +1

}



menuentry "Windows XP" {

insmod chain

insmod ntfs

parttool (hd0,3) hidden-

parttool (hd0,1) hidden+

parttool (hd0,2) hidden+

parttool (hd0,2) boot+

set root= (hd0,3)

search --no-floppy

chainloader +1

}

I try to boot Win on /dev/sda1 – (hd0,1) and I have the following messages :

setting partition type 0x17
setting partition type 0x17
setting partition type 0x17
partition 0 is active now
error : no argument specified
error : no device is set



If I'll remove the entry "search --no-floppy" I have only the second error message ( no device set ). 

I've tried searching but I could not find any solution.

---

### Post by oldfred on 2010-10-19
Have you installed each windows separately so each partition still has its boot files? If so grub2 should find & let you boot each. But if they are combined grub will only boot the windows with the boot flag as windows has moved all the boot files to that partition.

To see where everything is at:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by tommcd on 2010-10-19
Here is my custom boot file in /etc/grub.d/ for booting WindowsXP. I named the file 33_WindowsXP (so it would show up last in the grub menu on bootup, since I have a 31_Slackware and a 32_Salix custom boot file).
```

echo "Adding WindowsXP on /dev/sda1" >&2
cat << EOF
menuentry "WindowsXP on /dev/sda1" {
        set root=(hd0,1)
        chainloader +1
}
EOF

```
See this guide for custom boot entries for grub2:
[https://wiki.ubuntu.com/Grub2#User-defined%20Entries](https://wiki.ubuntu.com/Grub2#User-defined%20Entries)
Be sure to make any custom boot file executable, and then run: "*sudo update-grub*" to update your /boot/grub/grub.cfg file

---

### Post by ottosykora on 2010-10-20
the problem is, that when more windows partitions are present, grub will find them but as windows will be instaled in primary partitions, they need to be hidden except for one. I f you just boot to the single partitons, confusion will start when some functions are on other partition for example. 
So far I managed this with the old grub only, grub2 has mechanism for that, but it seems not to work well.

I ended up with creating special partiton for grub, installing old grub into it and run the hide unhide process from there.

---

