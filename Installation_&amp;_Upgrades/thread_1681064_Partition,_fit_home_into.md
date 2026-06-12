---
title: "Partition, fit /home into /"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by apostra on 2011-02-03
Hello there,

I have partitioned my HDD as /,/home,swap,

last week i screw up with my system and format it, installed kubuntu, didnt like it and reinstalled ubuntu once again.

Unfortunately as proper damp, forgot to set the /home folder at installation, did only the root one.

Now my pc, reads the previous /home folderas separate disk (sda2), which i have to mount every time i login and created a separate /home folder inside the root partition as meant to be. 

Is there a way to fit the old /home into the new /  or the only way is to format all over again?

PrintScreen here,
[http://postimage.org/image/1kxbm2g2s/](http://postimage.org/image/1kxbm2g2s/)


Kinda noobie here. thanks in advance.

Apo



P.S. I know could work fine as it is, but i want the /home to be inside root so I can run programs from wine etc, without any lagging issues and same time keep them safe from crashes and sadden formats.

---

### Post by kansasnoob on 2011-02-03
It's possible to do what you're asking but it's complicated. If this is a fresh install of Ubuntu (as it sounds) then I'd suggest just reinstalling.

Be sure to use the "Manual/Advanced" option, then select /dev/sda1, accept the default size, where it says "Use as" select Ext4, where it says Format be sure and check that, and set the Mountpoint as /.

Next select /dev/sda5. **[COLOR="Red"]Pay attention here![/COLOR]** This time you'll still accept the default size, and "Use as" will still be Ext4, **[COLOR="Red"]but DO NOT check the box to format[/COLOR]**, then select the mount point "/home"!

No change to SWAP is needed.

The caveat is that you'll likely still have some KDE configuration files that may mess with you but I'm fairly sure you/we can deal with that.

In the future if you want to fiddle with different DE's look at the Playing Around section here:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by oldfred on 2011-02-03
Reinstall may be easier if you are not comfortable with editing fstab.
But all you have to do is part of any of the how to's on moving /home to a new partition. You in effect have already moved it, but just have to add it to fstab.

You any one or review each to see which makes more sense to you, they are all essentially the same using different copy commands which you do not need.
To move /home uses rsync  (create mount may be missinig)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by apostra on 2011-02-03
Hm, if its complicated to do it as it is now, gonna follow your advice and just reinstall.

I know what you're saying for the installation part, its my stupid rushing mood sometimes that create me the problems, can handle it proper this time.

Thanks for the link as well. Gonna check it out.

-----

Oh thanks. I'm gonna reinstall it but definitely will look out the links for the other work around. Sounds something new and interesting to learn here for me, hehe.

---

