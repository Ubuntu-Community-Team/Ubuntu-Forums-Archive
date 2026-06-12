---
title: "Install Lucid without installing GRUB"
date: 2009-11-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by SalvoMaltese on 2009-11-18
Hi,

I want to try Lucid in a separate partiction I have, near Karmic, but without re-installing GRUB2, as it detects my existent OSs very badly, and ends messing up my startup configuration.

It's possible?

---

### Post by philinux on 2009-11-18
At the last phase choose advanced and install grub to the partition and not the mbr. It will complain about having to use blocklists but will install ok.
 Then on your main install edit your /etc/grub.d/40_custom to look similar to this. Just change the partitino to match your install.

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Grub on sdb1" {

      set root=(hd1,1)

      chainloader +1

      }
```

---

### Post by SalvoMaltese on 2009-11-18
Hi Phil,

In the last phase, if I select the same partition where I'm going to install Lucid, the "OK" button gets grayed, so I can't continue.

Can I uncheck totally "Install boot loader" and use my existing (karmic) grub 2?

---

### Post by kappa962 on 2009-11-19
Yes. You should have no need to install grub at all if your OS on your other partition is running grub 2. Just remember to "sudo update-grub" in your original OS. That should add your Lucid install into the boot menu. Also, if you do it this way, you shouldn't need to edit any of the grub configuration files.

---

### Post by kansasnoob on 2009-11-19
I have, a number of times, installed Karmic and selected advanced, then selected not to install grub at all.

What you must understand is: 

(1) If you're using grub2 on another OS it may or may not recognize the change when you run "update-grub".

(2) If you're using legacy grub you'll have to manually add that new OS to the menu.lst!

But if you know how to add the new OS to your existing grub (or other boot-loader) knock yourself out!

You must also actually remove the grub-pc package from the new OS after you're done or it'll bite you in that downside :D

---

### Post by SalvoMaltese on 2009-11-20
> **kansasnoob said:**
> 
(1) If you're using grub2 on another OS it may or may not recognize the change when you run "update-grub".


How can I know if it will or will NOT recognize?

What happened is that the "NEW" Grub2 associated all my kernels (the existent from karmic, and the new for lucid) to the Lucid partition, so I was only able to start lucid.

How can I modify grub2 config files to prevent that?

thanks.

---

### Post by VMC on 2009-11-20
> **SalvoMaltese said:**
> How can I know if it will or will NOT recognize?
From a terminal type this

```
sudo grub-mkconfig
```

It will display the grub.cfg output on your screen, without destroying your "/boot/grub/grub.cfg" file

---

### Post by kansasnoob on 2009-11-20
Something you might be interested in:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/485457](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/485457)

I filed that yesterday. Discussion here:

[http://ubuntuforums.org/showthread.php?t=1327491](http://ubuntuforums.org/showthread.php?t=1327491)

**IMHO** in your position I'd just let Lucid install grub2, if it's a mess then boot into Karmic and run:

```
sudo grub-install /dev/sda

```(replace /dev/sda with your proper destination)

and:

```
sudo update-grub
```

That should hand grub back to Karmic.

Or you could boot back into Lucid and try those new packages as I described here:

[http://ubuntuforums.org/showpost.php?p=8349028&postcount=15](http://ubuntuforums.org/showpost.php?p=8349028&postcount=15)

Best performance I've seen yet from grub2 :D

---

