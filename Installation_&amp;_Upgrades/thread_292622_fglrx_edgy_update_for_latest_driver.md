---
title: "fglrx edgy update for latest driver"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by thx_1138 on 2006-11-04
Hello there
I was wondering if I could get some advice, I did a fresh install last week to edgy on my laptop. I wanted my 3d card to work to its full capabilities and installed the latest ati driver (8.29.6), but I see earlier this week that ati has since upgraded to 8.30.3 fglrx drivers. My questions stem from the kernel update that popped up since I came home from work and since I really didnt see anything in the last 10 forum pages that exactly answered my question. My first question is that I used "method #2" on the ati linux wiki page to get the lastest driver onto edgy ([http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide))
I just wanted to make sure that when I get the kernel update and I want to rebuild the ati module for the updated kernel from what step can I start at in the guide to get my card updated. With that in mind is it possible to upgrade to the 8.30.3 drivers when I do the kernel upgrade and save time in the future? Thanks for any advice available.:-k

---

### Post by philippe_carlo on 2006-11-04
> **thx_1138 said:**
> Hello there
I was wondering if I could get some advice, I did a fresh install last week to edgy on my laptop. I wanted my 3d card to work to its full capabilities and installed the latest ati driver (8.29.6), but I see earlier this week that ati has since upgraded to 8.30.3 fglrx drivers. My questions stem from the kernel update that popped up since I came home from work and since I really didnt see anything in the last 10 forum pages that exactly answered my question. My first question is that I used "method #2" on the ati linux wiki page to get the lastest driver onto edgy ([http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide))
I just wanted to make sure that when I get the kernel update and I want to rebuild the ati module for the updated kernel from what step can I start at in the guide to get my card updated. With that in mind is it possible to upgrade to the 8.30.3 drivers when I do the kernel upgrade and save time in the future? Thanks for any advice available.:-k


[1] perform the upgrade (do NOT reboot just yet!)
[2] Now repeat the steps:
    - Create .deb packages
    - Remove any old fglrx debs from /usr/src/
    - Install .deb packages
    - Compile the kernel module

That should work. Normally, just recompiling the modules should work too, but you never know. You can probably automate all this, but I'm not sure that doing this n a smart way is worth the trouble. You could of course make it semi-automatic and drop the above steps in a shell script.

---

### Post by ajslater on 2006-11-04
I've attached a script that duplicates the method 2 procedure on cchtml.com.

---

