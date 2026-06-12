---
title: "grub rescue on every boot - how to solve"
date: 2021-12-14
forum: Installation &amp; Upgrades
---

### Post by josephmmorgan on 2021-12-14
I picked up a use Dell Precision M6500 laptop.  It came, of course, with Windows, so I popped in a live CD and did a complete erase install of Ubuntu 20.04.

The computer has 2 drives, one is a 128GB SSD, and the other a 500GB normal Toshiba drive.  I opted to install the OS on the SSD.

Every time I restart the computer, however, I end up at the grub rescue prompt.   This is easy enough to solve through the following commands:

[COLOR=#000000][FONT=&quot]ls 
     Which strangely lists 18 partitions, only one of which has a filesystem (ext2) on it.  That one is (hd1/msdos5)  Even when I examine the disks from the live boot using the disks utility, I see, on the /dev/sdb drive, 3 partitions.  One is the boot, and the other 2 seem to overlap with 119GB each.  One says parition 1, and the other says partition 5 (ext4).   Not sure if that has anything at all to do with the problem, so mentioning it.    However, I in no way see 18 partions.  The 500GB shows only 2.  I have no idea where the others are coming from.

Any way, if I then do this:
[/FONT][/COLOR]

 [COLOR=#000000][FONT=&quot]ls (hd1,msdos5)
    It displays it having an ext2 file system on it.  OK.. maybe.  So I proceed:
[/FONT][/COLOR]

 [COLOR=#000000][FONT=&quot]set boot=(hd1,msdos5)[/FONT][/COLOR]

 [COLOR=#000000][FONT=&quot]set prefix=(hd1,msdos5)/boot/grub[/FONT][/COLOR]

 [COLOR=#000000][FONT=&quot]insmod normal[/FONT][/COLOR]

 [COLOR=#000000][FONT=&quot]normal[/FONT][/COLOR]

And it starts up.  This is great.  Running just fine.  However, if I restart the computer, I end up right back at the grub rescue prompt, where I repeat the above and I'm back in.

How can I make the grub settings permanent so I don't have to do that every single time?

---

### Post by #&amp;thj^% on 2021-12-14
If you  changed their layout/locations on disk and Grub hasn't yet been updated to see their new locations. This can be manually fixed using:

```
sudo update-grub
```
Please paste back the return from the terminal.

This should update the configuration files. Sometimes when making significant changes to the partition layout (usually when adding or removing an entire disk) you may need to also run this command:

```
sudo grub-install some_device_name
```

---

### Post by josephmmorgan on 2021-12-14
Sourcing file '/etc/default/grub'
Sourcing file '/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image:  /boot/vmlinuz-5.11.0-41-generic
Found initrd image:  /boot/initrd.img-5.11.0-41-generic
Found linux image:  /boot/vmlinuz-5.11.0-27-generic
Found initrd image:  /boot/initrd.img-5.11.0-27-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done.

And.. that didn't seem to work.
Restarted... and back at the grub-rescue... but the commands I posted boot it right up.
Another note (just because I'm a dummy), while it was up, and before issuing the 'sudo update-grub' command above, I installed one small app just to ensure I'm seeing the same image and all is saving normally.  That is, the thing works.  Just gotta slap grub around every time.

P.S.  I really don't mind starting completely over if needed.  Should I try the 2nd command to sdb?

---

### Post by #&amp;thj^% on 2021-12-14
> **josephmmorgan said:**
> 

  Should I try the 2nd command to sdb?

Please do. And post back the return again.

---

### Post by josephmmorgan on 2021-12-14
OK.. so.. it seemed to need something else.  Hard to fully explain.. but, for whatever reason, my BIOS would not keep the SSD above the 500GB as a boot device.  I've set it over and over during this process, but the 500GB kept coming back on top.  However, on a hunch, I changed BIOS boot order again, and this time it seems to have "stuck".  Now it is behaving normally.

I can only suspect that the BIOS wasn't seeing the GRUB on the SSD before the first command was executed, and was switching back to the other??? I don't know.  But for now, the problem is solved.

---

### Post by #&amp;thj^% on 2021-12-14
> **josephmmorgan said:**
> OK.. so.. it seemed to need something else.  Hard to fully explain.. but, for whatever reason, my BIOS would not keep the SSD above the 500GB as a boot device.  I've set it over and over during this process, but the 500GB kept coming back on top.  However, on a hunch, I changed BIOS boot order again, and this time it seems to have "stuck".  Now it is behaving normally.

I can only suspect that the BIOS wasn't seeing the GRUB on the SSD before the first command was executed, and was switching back to the other??? I don't know.  But for now, the problem is solved.

Great.
I've forgotten to hit <f10> to save the bios change a time or two. ;)

---

### Post by josephmmorgan on 2021-12-14
You're the best!  Thanks.

---

