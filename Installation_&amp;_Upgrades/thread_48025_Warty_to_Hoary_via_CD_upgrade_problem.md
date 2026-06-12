---
title: "Warty to Hoary via CD upgrade problem"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by dOOd on 2005-07-10
Howdy folks,
I just got my 10 hoary cd's in the mail and decided to try to upgrad my current wonderful Warty installation to Hoary via the CD as outlined with this post in the wikki:

[https://wiki.ubuntu.com/HoaryUpgradeNotes?highlight=%28cd%29%7C%28upgrade%29](https://wiki.ubuntu.com/HoaryUpgradeNotes?highlight=%28cd%29%7C%28upgrade%29)

And I have a problem. It seemed the upgrade went fine. There were a couple of questions asking me if I wanted to keep my current config file or over write it. Seeing this was a upgrade I chose overwrite. In hindsight it seems that was a mistake. 

Now for the problem. I dual boot with Win98SE and now in Grub I get TWO kernel options:

2.6.10-5-386 and 2.6.8.1-3-386. But no matter which kernel I choose I get a Debian login screen, and when I login I get a grey screen with my cursor and that is it. No menu's no right click options, no nothing. Using Insert CD I have found that all of my files are still there, and yes I made a complete backup of all files in the Warty installation prior to upgrading. I believe one of those config files that I chose to over write was a mistake. How can I get to the Hoary login? Which config files do I need to change and what commands do I need to change them?

Thanks in advance for any help.

~;-)

---

### Post by dOOd on 2005-07-11
Anyone have any tips or suggestions on this? I suppose I could do a fresh install from the CD. However I would like to avoid that if possible.

THanks

---

### Post by dOOd on 2005-07-11
Nobody has any ideas on this? Do yall need more information? Do I need to change my deoderant?

 :razz:

---

### Post by dOOd on 2005-07-12
Well I ran out of time. I need the linux side of my system up and running so I did a fresh install. Needless to say it's going to take a while to get everything back to the way it was. I'm really shocked that no one could give me an answer or at least point me in the right direction. Heck even some theories would have been nice. Oh, and I have been lurking here for the last six months, as no posting was ever needed on my part up till now. My luck when I have a problem where I DO have to post, I get squat.

 :roll:

---

### Post by musicman2059 on 2005-07-12
Well, maybe you shouldn't have overwritten the config files but did you try to:

```
sudo dpkg-reconfigure xserver-xorg
```

first?

---

