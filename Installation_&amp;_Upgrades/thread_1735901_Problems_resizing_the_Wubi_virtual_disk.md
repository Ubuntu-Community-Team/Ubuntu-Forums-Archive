---
title: "Problems resizing the Wubi virtual disk"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by Musicmaker384 on 2011-04-21
I've been trying to resize my Wubi disk for quite some time now, and I've had a lot of people help me with how to do it. I finally found out. But I've been having these problems.

I enter the following command in a terminal...

sudo bash wubi-resize_1.3b.sh 32

...to increase the size of the Wubi disk by 32GiB.

However, the terminal gives me this error:

bash: wubi-resize_1.3b.sh: No such file or directory

I don't know if I'm entering the command wrong. I don't think I am. I used the "HOWTO: Resize the WUBI virtual disk" thread here on Ubuntu Forums. I copied the command exactly and I get that error and I don't know why.

There is also a manual way of resizing the disk, but I am not comfortable with those commands and so I don't want to use them.

Help, anyone?

---

### Post by bcbc on 2011-04-22
Normally when you download the script it goes into the Downloads folder.

So go to the terminal and enter:
```
cd Downloads
sudo bash wubi-resize_1.3b.sh 32
```

If it's not in that directory you'll have to figure out where you saved it. The next time I recommend placing any questions on the Howto thread so I get notified.

---

