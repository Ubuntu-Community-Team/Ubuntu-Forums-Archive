---
title: "Installed Ubuntu 12.04 64 bit on SSD - Trim Enabled?"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by biosol on 2012-05-05
Hi,
Just installed a fresh 12.04 64bit version on my new SSD from a USB thumb drive.  Took 5-7 minutes.  It's fast.  Wanted to ask about Trim.  This is my first SSD and have seen mention of this Trim feature/command wonder if it's enabled by default/supported in Ubuntu?

Any info/advice?

Thanks

---

### Post by oldfred on 2012-05-06
You need to change some settings in fstab.

You need to add noatime & discard like this:
Typical fstab entry:
UUID=d65e4ad3-6315-4838-97a1-ec574cb8575f / ext4 [COLOR=DarkRed]noatime,discard[/COLOR],errors=remount-ro   0       1

I had not updated my fstab right away and did this:
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

You should have partitioned ok by default, the new standard is to start at 2048 and use 1K boundaries.

Some of these links may be getting older, I have not recently reviewed them.

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

How to Tweak Your SSD in Ubuntu for Better Performance
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)
See comment: There’s no reason to use BOTH noatime and nodiratime, using noatime implies nodiratime.
[http://techgage.com/print/enabling_and_testing_ssd_trim_support_under_linux](http://techgage.com/print/enabling_and_testing_ssd_trim_support_under_linux)

You normally want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1

No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center

After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

---

