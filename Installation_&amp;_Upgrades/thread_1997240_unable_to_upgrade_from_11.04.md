---
title: "unable to upgrade from 11.04"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by Carnendil on 2012-06-04
I think this has not been asked elsewhere in the forums.

I'm running Lubuntu 11.04 on a Dell Inspiron 1200; 1.40 GHz Intel Celeron & 241 MB.

I tried to upgrade with ```
sudo do-release-upgrade -d
```the plan being to upgrade consecutively to end up with Lubuntu 12.04.

However, while it was already downloading Oneiric packages (specifically, linux-image-3.0.0-20-generic), it showed the following messages:
```

Error in function pulse


Ha ocurrido un error fatal

Informe de este fallo e incluya los archivos
/var/log/dist-upgrade/main.log y /var/log/dist-upgrade/apt.log en el
informe. La actualización ha sido cancelada.
Su archivo sources.list original se guardó en
/etc/apt/sources.list.distUpgrade.

Traceback (most recent call last):

File "/tmp/update-manager-uqsWZC/DistUpgradeViewText.py", line 41, in
pulse
apt.progress.text.AcquireProgress.pulse(self, owner)

File "/usr/lib/python2.7/dist-packages/apt/progress/text.py", line
166, in pulse
apt_pkg.time_to_str(eta))

OverflowError: Python int too large to convert to C long
```I had no problem changing back the repositories to Natty, but I really would like to upgrade to a newer Lubuntu.

I'm afraid that a fresh install in this laptop, apart from being more cumbersome than just upgrading, might not work: I tried last year to install Lubuntu 11.04 but failed, and had to go back to Lubuntu 10.04 and then upgrade from the command line.

I have attached both log files. Any help will be very welcomed.

---

### Post by Bucky Ball on 2012-06-04
Too late now but LTS upgrades to LTS (eg, you can go from 10.04 LTS directly to the next LTS release, 12.04 LTS).

Just a point, although I can't really help with your specific problem. An upgrade needs some 'overhead' or 'headroom' to store things while it is updating (some of which will later be removed). So, if you have 11.04 just crammed in to a 10Gb partition, for instance, with very little spare space to move (less than a Gb, say), your upgrade will probably fail. I was wondering if this issue has something to do with this:

```
OverflowError: Python int too large to convert to C long
```

Solution? Expand the 11.04 partition (make it bigger) and try again.

I could be miles away but just a thought. I had this problem when trying to upgrade a machine myself (8.04 LTS to 10.04 LTS).

Good luck.

---

### Post by Carnendil on 2012-06-05
Thank you for your reply. I do have over 24 GiB free of harddisk, so I wonder if it has to do with something else.

RAM is 241 MiB, plus 692 MiB swap partition and an additional 2GiB swapfile I created when I realized that the default swap partition size was that small.

Again, thank you.

---

