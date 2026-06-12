---
title: "No option to choose on dual boot"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by Jedwinjim on 2013-04-28
Hi guys,

Running Ubuntu 12.04LTS like a dream for a year, no issues there. Thought I'd give 13.04 a trial so ran it from live USB & like what I see so wanted to install it side by side with 12.04 until I have used it long enough to make sure there are no issues at all (I couldn't get wifi to work in 12.10 hence why I'm still on 12.04). Install was all successful but I get no option to choose between 12.04 or 13.04 on boot up, it just automatically boots into 12.04 as it was before. Any ideas?

Thanks,

joe.

---

### Post by darkod on 2013-04-28
In 12.04 open terminal and run:
sudo update-grub

It will detect all other OSs and make a dual boot menu. Provided 13.04 really did install successfully.

---

### Post by Jedwinjim on 2013-04-28
like a charm! thanks dude.

---

