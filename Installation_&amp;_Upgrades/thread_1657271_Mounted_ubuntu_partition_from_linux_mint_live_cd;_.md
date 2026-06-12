---
title: "Mounted ubuntu partition from linux mint live cd; suddenly became read-only"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by vik_2010 on 2011-01-01
I've been running ubuntu for a while, but I decided today I'd check out linux mint.

I created a live cd, and ran it. During my test, I discovered I could mount my linux partition and access my files there.

I thought this was neat, so I opened up a couple files. I didn't make any changes; i just opened them. I also opened GParted, but I don't think that makes any difference.

However, when I ended my session and rebooted Ubuntu, the partition had suddenly become read-only, and I couldn't load it. 

I then rebooted my linux mint live cd. I could no longer open that partition, and "sudo stat" said the size of the partition (I think i checked the partition in /dev/sda3, where ubuntu is located) was 0.

That can't be right, though, because GParted states that sda3 has some 22 GiB of data on it.

Can anyone help me out?

Best,

-Vikram

---

### Post by vik_2010 on 2011-01-01
> **vik_2010 said:**
> I've been running ubuntu for a while, but I decided today I'd check out linux mint.

I created a live cd, and ran it. During my test, I discovered I could mount my linux partition and access my files there.

I thought this was neat, so I opened up a couple files. I didn't make any changes; i just opened them. I also opened GParted, but I don't think that makes any difference.

However, when I ended my session and rebooted Ubuntu, the partition had suddenly become read-only, and I couldn't load it. 

I then rebooted my linux mint live cd. I could no longer open that partition, and "sudo stat" said the size of the partition (I think i checked the partition in /dev/sda3, where ubuntu is located) was 0.

That can't be right, though, because GParted states that sda3 has some 22 GiB of data on it.

Can anyone help me out?

Best,


-Vikram

EDIT: When I run sudo fsck -a /dev/sda3 after booting from a live CD, a  message pops up saying "A read attempt ran up short." - or something  similar - "Are you sure this drive is not empty?" And running fsck -a  /dev/sda4 (which is my linux swap partition) states that the "drive is  in use."

I have no idea what that means.

Also: The first time, I could at least get a shell prompt for ubuntu. If I choose a linux boot at grub, now I get a blank screen, and have to reboot my box.

---

