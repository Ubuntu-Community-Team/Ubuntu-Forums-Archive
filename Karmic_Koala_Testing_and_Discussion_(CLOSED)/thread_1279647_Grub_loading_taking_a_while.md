---
title: "Grub loading taking a while?"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mmcmonster on 2009-10-01
Just installed Alpha 6 and updated to current.

When booting up, there's actually a delay while Grub2 is loading (It says "Grub loading...", or something ike that).

Is that normal?  I remember when I was using 9.04 with Grub (not Grub2), the grub menu never had to tell me it was loading.

Also, after I picked the Ubuntu 9.10 item, it starts booting in text mode (telling about the different services being started), before going into graphical mode.

I guess I'll reinstall when 9.10 final comes out, but is this normal behavior now?  It seems like a step back from 9.04.

---

### Post by xzero1 on 2009-10-01
I have the same problem. My guess is the more grub2 entries the slower. Is there a way to speed it up with many grub2 entries? Will it matter how fast Ubuntu boots if so much time is wasted just getting to a boot menu? Hopefully, this can be remedied.

---

### Post by seamuso on 2009-10-01
is grub installed to the mbr of the same drive that your /boot is installed to?

---

### Post by xzero1 on 2009-10-01
> **seamuso said:**
> is grub installed to the mbr of the same drive that your /boot is installed to?

Probably not. What is the easiest way to check that? I have 2 physical drives. Before installing Karmic, each had their own independent grub. Since grub 2 was installed, it scanned all partitions from both drives into the menu. The bios is set to boot from the non Karmic drive though.

---

### Post by seamuso on 2009-10-01
When it happened to me, I thought it was something else until I told my system to load from what should have been both the bios selected boot drive as well as my win7 drive .. grub came up .. slow

Then booted from my known karmic installed drive and grub came up quickly.

Most recent systems should offer you an option to enter a boot device choice menu .. I have to hit esc when I'm booting .. then you can try each drive in turn to see if grub2 wrote to both MBRs ..


[http://ubuntuforums.org/showpost.php?p=8001667&postcount=1](http://ubuntuforums.org/showpost.php?p=8001667&postcount=1)

---

### Post by drs305 on 2009-10-01
There is another thread on the same thing here:
[looooooong time until xsplash appears ]("http://ubuntuforums.org/showthread.php?t=1278573")

---

### Post by dino99 on 2009-10-01
remember some time ago with a1 / a2 , everybody was so happy: karmic was booting faster than Jaunty.

At that time, grub legacy was at work. Since, grub2 take place, but now it's still a young child and cant walk or run fast.

For sure, it's not powered by Usain Bolt :(

---

### Post by xzero1 on 2009-10-01
> **seamuso said:**
> When it happened to me, I thought it was something else until I told my system to load from what should have been both the bios selected boot drive as well as my win7 drive .. grub came up .. slow

Then booted from my known karmic installed drive and grub came up quickly.

Most recent systems should offer you an option to enter a boot device choice menu .. I have to hit esc when I'm booting .. then you can try each drive in turn to see if grub2 wrote to both MBRs ..


[http://ubuntuforums.org/showpost.php?p=8001667&postcount=1](http://ubuntuforums.org/showpost.php?p=8001667&postcount=1)

Thanks, changing the bios boot drive to the grub2 drive does seem to speed things up quite a bit.:)

---

