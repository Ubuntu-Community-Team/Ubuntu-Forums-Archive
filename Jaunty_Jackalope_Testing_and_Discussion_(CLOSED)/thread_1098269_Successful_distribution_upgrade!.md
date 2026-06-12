---
title: "Successful distribution upgrade!"
date: 2009-03-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by whoop on 2009-03-16
I couldn't resist anymore and did a distribution upgrade on my main machine (don't worry I have backups). It went totally successful! I have been upgrading this machine since gutsy (probably even feisty but I am not 100% sure about that), without doing any fresh installs.

After I did the upgrade I even converted my ext3 partition to ext4 using a usb pen-drive (I used the "USB startup disk creator" in jaunty) which would boot jaunty-live; cause I didn't want to waste a cd for an alpha live-cd.
The ext3 to ext4 conversion also went well.

Just wanted to inform you guys that all went really smooth :guitar:

---

### Post by Kow on 2009-03-16
Same here yesterday.

---

### Post by agim on 2009-03-17
I generally avoid upgrades like this. I usually use the disk, but its nice to see how well its working. I am using Kubuntu 9.04. I have been since alpha 4, and its amazing how stable everything is. A few application bugs, but nothing major. At least not for me.

Things look good so far for 9.04.

---

### Post by mattshurtleff on 2009-03-17
same same, very pleased!! now if i could just get my wireless card 2 work with this release i'll be pleased as pie.

---

### Post by jepong on 2009-03-17
i'm new with kubuntu. im using kubuntu 8.10, how do you upgrade to Ubuntu 9.04 Alpha 6?

---

### Post by dbulante on 2009-03-17
I also took the plunge today, and everything went well.  I am impressed with this latest version.  It seems like it is so stable and works like a charm.

---

### Post by jepong on 2009-03-17
is mobile broadband working ok now?

---

### Post by dentaku65 on 2009-03-17
> **jepong said:**
> is mobile broadband working ok now?

Works pretty well. In my case a vodafone connect card (pcmcia) as soon as I inserted a networkmanager wizard starts to configure the connection without issues.

---

### Post by nyarnon on 2009-03-17
Good for you and enjoy the experience, but...... sorry to spoil your party guys but this cannot be said often enough.

***Jaunty is alpha as an alpha it will bound to give you hurt sooner or later. This might go as far as dataloss.***

Now please be aware of that !!!

---

### Post by Nullack on 2009-03-17
The main reason its not crashing all over the place is because its got a released kernel version and a very soon to be released gnome version. Theres still plenty of bugs though.

---

### Post by jepong on 2009-03-17
> **jepong said:**
> i'm new with kubuntu. im using kubuntu 8.10, how do you upgrade to Ubuntu 9.04 Alpha 6?

will sudo apt-get dist-upgrade work with kubuntu to upgrade to kubuntu 9.04 alpha 6?

---

### Post by taavikko on 2009-03-17
> **jepong said:**
> will sudo apt-get dist-upgrade work with kubuntu to upgrade to kubuntu 9.04 alpha 6?


Yes, if you've set the repos point to jaunty.

More preferred way is to use, somthing like
```
sudo do-release-upgrade -d
```

If it states no release found, set the "prompt=normal" in
/etc/update-manager/release-upgrades

---

### Post by whoop on 2009-03-17
> **nyarnon said:**
> Good for you and enjoy the experience, but...... sorry to spoil your party guys but this cannot be said often enough.

***Jaunty is alpha as an alpha it will bound to give you hurt sooner or later. This might go as far as dataloss.***

Now please be aware of that !!!

That's why we backup our stuff..

---

### Post by Mr. Picklesworth on 2009-03-17
> **whoop said:**
> I couldn't resist anymore and did a distribution upgrade on my main machine (don't worry I have backups). It went totally successful! I have been upgrading this machine since gutsy (probably even feisty but I am not 100% sure about that), without doing any fresh installs.

After I did the upgrade I even converted my ext3 partition to ext4 using a usb pen-drive (I used the "USB startup disk creator" in jaunty) which would boot jaunty-live; cause I didn't want to waste a cd for an alpha live-cd.
The ext3 to ext4 conversion also went well.

Just wanted to inform you guys that all went really smooth :guitar:

I've been doing that since 7.10 on this machine. (Which had Ubuntu installed on December 3, 2007). Except with Intrepid (late beta), I've always upgraded into the late alpha stage of the next release. No problems so far.

The upgrade process is really way better than people think. All we need is a firey red warning message when people are doing things that could completely botch the Debian infrastructure. (*cough*automatix*). I even install piles of things from source and don't have any problems. Just always remember to put them in /usr/local (instead of /usr) and nothing goes wrong.

Never hurts to reset a few configuration files and tinker with partitions here and there, but I haven't felt the need to reformat completely. The file system (symlinks ftw!) makes it really straight forward to hold the system together as it grows.

---

### Post by whoop on 2009-03-17
Well it backfired a little bit today: I got a "Error 13: Invalid or unsupported executable format" when I switched on my machine this morning. It was caused by a combination of ext4 and grub. Solved it with a live-usb:
```

sudo bash
mount /dev/sda5 /mnt
grub-install /dev/sda --root-directory=/mnt --recheck

```
So it wasn't a 100% flawless :-)

---

### Post by bgiannes on 2009-03-17
just started upgrading.....


i'm hoping it fixes a number of probs i've been having with my 8.10 server

cifs crashing, kernel panics.....

lets see.....

---

### Post by bgiannes on 2009-03-20
well i've got into trouble with 9.04

I had to move another PC so i unpluged it's ethernet,

The 9.04 box was mounted to a drive on that PC w/ smb,  the result was a kernel panic on the 9.04 box....

after rebooting the network serves would not restart, i could not even ping it, (eth0 is still install) ifconfig shows the correct card info....

---

