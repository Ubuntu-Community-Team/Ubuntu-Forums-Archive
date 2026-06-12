---
title: "Installing Xubuntu 8.04 beta on hard drive (Boot loader option)"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by hanzj on 2008-03-22
Hello. I'm installing Xubuntu 8.04 beta on a computer. In final stage (Step 8 of 8), the advanced option has a check mark on the box beside "Install Boot Loader". The following line has "Device for Boot loader installation.". In the dropdown list, "(hd0)" is what was preselected. Is this correct? Or should I change from (hd0) to "/dev/sda" or to "dev/sda1". Please help! Thanks.
what happens if i change device from (hd0) to "/dev/sda"?
There's nothing else on computer (No windows, no other ubuntu flavor)

---

### Post by forestpixie on 2008-03-22
Leave it as it is - I've never needed to change it on normal installations.

---

### Post by hanzj on 2008-03-22
My computer hung at 15% of "installing System". It was "Detecting File Systems"..

Should I just re-try?

---

### Post by forestpixie on 2008-03-22
I'd check the cd - there's an option when it boots.

Did you burn it slowly and check the md5sum.

---

### Post by hanzj on 2008-03-22
Forest,
I burned it at max speed, and i checked the iso's md5sum. it mashes the hash.

I did "check CD for defects"and it's fine. No problem.

---

### Post by forestpixie on 2008-03-22
Gnerally best to burn them slowly - buti fit checks I guess it's ok. Did you try again?

---

### Post by hanzj on 2008-03-22
Yes,
I changed the "device to which boot loader installs" from 
(hd0)
to
/dev/sda


Installation is currently making more progress than before. 
8-)

---

### Post by hanzj on 2008-03-22
But now it's stuck at 94%:cry:
Stuck in the sense that it's not going to 95%.
But not stuck in the sense that the progress bar at the background is not doing the barber pole movement (e.g. [http://en.wikipedia.org/wiki/Image:Barber-pole-01.gif](http://en.wikipedia.org/wiki/Image:Barber-pole-01.gif))

"Configuring hardware".

It's been at 94% for about 10 minutes now.
Running a P3; 200 MB Ram

---

### Post by forestpixie on 2008-03-22
Leave it to do it's thing you've only got a bit of RAM

---

### Post by hanzj on 2008-03-22
Even after 15 minutes?
Ok. I guess waiting won't hurt. if not, maybe i'll install some non-ubuntu linux.

What's lighter than Xubuntu but still user-friendly enough for an olderly person who is used to point-and-click?

---

### Post by forestpixie on 2008-03-22
Yea - give it some time - mine takes about 5 minutes to get the last bit done. Put xubuntu on a really old pc here and it did take a long time to finish. Once it's loaded you should have plenty of RAM to run it.

---

### Post by hanzj on 2008-03-22
Still stuck at 94%. Been at 94% for about 20 minutes now!
Re: your last sentence:
You sayin I should get more RAM, forest? or that the RAM I currently have will be more than enough?

---

### Post by Kiri on 2008-03-22
200mb is not much... I dont think it will run very well on that. But it should still at least run.

---

### Post by forestpixie on 2008-03-22
The figures are
> Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.

I have a pc here running it - slowly - on 128Mb, I don't really know much about other distros to run on low RAM.

Once it's installed see what it's like

---

### Post by hanzj on 2008-03-22
Finally got Xubuntu installed.
it's running. but it's slow.
Does anybody know of a lighter Linux distro, BUT STILL good for olderly people who are used to point and click?

---

### Post by forestpixie on 2008-03-23
You could try fluxbox - which is just a different window manager - xubuntu uses xfce.
You can install it from within xubuntu and then when you login - in the bottom left click sessions and choose it there.

```
sudo aptitude install fluxbox
```

I'm sure if the thread gets seen you'll get other suggestions from those more knowledgeable than me, if not start a thread in abs beginners.

---

