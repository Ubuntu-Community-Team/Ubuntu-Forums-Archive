---
title: "GRUB + Ubuntu + PC-BSD = Ack!"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by DarkStarAeon on 2007-01-24
Hi,

 I just installed Ubuntu on my computer at: /dev/sda1 and the swap is /dev/sda2

Problem is, I already had PC-BSD on /dev/sdb and now I can't get into it, it's not listed in Grub.

How do I edit Grub correctly so that I can boot into PC-BSD???

---

### Post by JamieC on 2007-01-24
You may want to look at [this](http://faqs.pcbsd.org/16_9_en.html), bearing in mind that GRUB options are located in /boot/grub/menu.lst. If you need further help, paste the contents of your menu.lst file here. 

You can edit it using the following (where <editor> is your preferred editor, vim, nano, etc):
```

sudo <editor> /boot/grub/menu.lst

```

---

### Post by DarkStarAeon on 2007-01-26
Thanks for the reply, much appreciated. I figured it out finally.

I ended up using this:

[http://faqs.pcbsd.org/16_10_en.html?highlight=grub]("http://faqs.pcbsd.org/16_10_en.html?highlight=grub")

but, I used the second option, set it for the second drive, and added a title, and put it at the bottom of the order...so it looks like this in Ubuntu's /boot/grub/menu.lst file:

title PC-BSD
rootnoverify (hd1,0)
chainloader +1
boot 

Then I edited the time until it loaded the default so I got more time to select which OS on which drive.

Works great.

---

### Post by metalf8801 on 2008-01-02
> **DarkStarAeon said:**
> Thanks for the reply, much appreciated. I figured it out finally.

I ended up using this:

[http://faqs.pcbsd.org/16_10_en.html?highlight=grub]("http://faqs.pcbsd.org/16_10_en.html?highlight=grub")

but, I used the second option, set it for the second drive, and added a title, and put it at the bottom of the order...so it looks like this in Ubuntu's /boot/grub/menu.lst file:

title PC-BSD
rootnoverify (hd1,0)
chainloader +1
boot 

Then I edited the time until it loaded the default so I got more time to select which OS on which drive.

Works great.

that link takes you to a page that no longer exists

---

