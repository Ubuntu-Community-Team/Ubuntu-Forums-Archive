---
title: "Restore grub with mbr on SATA, NOT on IDE drive"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by radinator on 2006-12-28
I have three HDs on my system:

1. 13 GB IDE (slow, data only...not a boot device)
2. 400 GB SATA  (contains XP and is the boot device)
3. 80 GB SATA (contains Ubuntu 6.06)

When originally set up this system I was able, after several days of hail-pulling, to get things set up perfectly wrt grub.  Grub really wanted to put an mbr on the IDE disk, and I finally dissuaded it from doing that.

However, I had to recently re-install XP, which overwrote the MBR on disk #2 as it installed.  I can still get to my linux setup with my Super Grub disk.

So now I want to reestablish grub working properly.  What I don't want is for grub to do the clumsy thing it wants to do and turn the IDE drove into a boot device.  The order in which grub sees the disks makes this unwanted outcome likely:

hellmouth:~$ cat /boot/grub/device.map
(hd0)   /dev/hdc    (#1 above)
(hd1)   /dev/sda    (#2 above)
(hd2)   /dev/sdb    (#3 above)

The linux partition (containing /boot) is on /dev/sdb5 (hd2,4) and all of the required grub files are there, so all I need is to replace the mbr portion on drive #2 (hd1), without grub automatically putting it on drive #1 (hd0).

I've been reading all the man pages, and feel I know just enough to confidently screw things up and turn hd0 into a boot device again. ;)

How exactly do I tell grub to do:
grub-install  <put mbr on (hd1)>  <point to grub files on (hd2,4)>

Thanks,
Ray

---

### Post by shane2peru on 2006-12-28
Ray,

  Here are my thoughts.  Theoretically if your run this command in a terminal ```
sudo grub-install /dev/sda 
``` it should have to install on your Windows Boot sata disk.  However to be on the safe side you can disconnect your IDE hard drive, (just pull the plug on the power cable of it while the computer is off;).)  Let me know if this works for you.

Shane

---

### Post by radinator on 2006-12-29
Yes, that worked.  I was very uncertain about trying it since I had such a bad experience last time, but, once running ubuntu, it assumed that I wanted to point to the grub files in /boot and placed the 'mbr' portion right where I asked.  I tried it right after posting the question, and it worked great.

Of course, something else went wrong and I couldn't log onto the forums to post a 'solved it' message until now.  For some reason I currently can't log in to post with firefox (version 2 and 1.5) on my several machines (XP or Ubuntu) and am currently only able to login/post with Internet Explorer.  Go figure.

Thanks,
Ray

---

