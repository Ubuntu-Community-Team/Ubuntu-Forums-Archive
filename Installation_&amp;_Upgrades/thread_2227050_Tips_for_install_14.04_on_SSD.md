---
title: "Tips for install 14.04 on SSD"
date: 2014-05-30
forum: Installation &amp; Upgrades
---

### Post by jamesdcarroll on 2014-05-30
Just got an SSD and installed 14.04 onto it but with the /home on a existing regular non-SSD hard drive.   Everything is working great and I followed the tips at [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd) to help my SSD last longer.  

The only suggested tips that I didn't do are the ones related to Firefox/Chrome/Java.  I suspect that cache, temporary internet files, and things like that would be written to /home so I was wondering if I should still do those.

Thanks,


James

---

### Post by sudodus on 2014-05-30
I think you are right about that, and what is not written to the SSD won't wear it :-)

---

### Post by oldfred on 2014-05-30
If /home is on hard drive then Firefox is on hard drive.

I keep /home inside / on SSD, but have Firefox on hard drive, so I can share it with my several other test installs on the hard drive.
I use ext4 but do turn journal off. Partition is small and just system. So not need journal to recover quickly or can easily totally reinstalled if SSD not totally destroyed.
I use a daily cron task for trim.

Some also suggest /tmp in RAM, but I only have 4GB and use DVDs to write some backup folders to save a copy. That is 4GB and would fill /tmp.
Some now say the newest SSDs have lives comparable to hard drives, so no special settings even required.

---

### Post by ubfan1 on 2014-05-30
You are right, (speaking for firefox only), those caches are written into your home directory.  What you can consider is moving them to ram for increased performance.  A simple link from the Firefox cache to /tmp/Cache-username works for me.  Downside it you always start with an empty cache at boot, but I don't even notice that.

---

### Post by ubfan1 on 2014-05-30
Oops, forgot to say my /tmp was already in ram. Don't do what I said above, or it'd just put it back onto the SSD.

---

### Post by jamesdcarroll on 2014-06-03
Thanks for all the tips!

---

