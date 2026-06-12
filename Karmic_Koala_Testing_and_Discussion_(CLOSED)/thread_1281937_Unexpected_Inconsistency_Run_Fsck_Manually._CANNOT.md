---
title: "Unexpected Inconsistency: Run Fsck Manually. CANNOT BOOT UBUNTU"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2009-10-03
Hi All,

I am not able to boot Karmic due to some reason. I have attached the screenshot with the error. It asks me to press Control D and nothings happens. I have tried this on both my Dell 6400/E1505 and Virtualbox without any luck. Has anybody got the solution please?

Thanks,
SK.

---

### Post by Woody1987 on 2009-10-03
i get that alot, just type fsck /dev/sda1 then type reboot, it should then work again, although it is likely to happen again, im not aware of any permanent solution but it should be fixed for the release hopefully.

---

### Post by donniezazen on 2009-10-03
> **Woody1987 said:**
> i get that alot, just type **fsck /dev/sda1** then type **reboot**, it should then work again, although it is likely to happen again, im not aware of any permanent solution but it should be fixed for the release hopefully.

This indeed solved the problem for now. Hopefully they will fix this issue before release.

Thanks,
SK

---

### Post by MoebusNet on 2009-10-03
This doesn't work on my Karmic-beta install; the boot bypasses fsck and hangs trying to access the encrypted HDD.

BTW, I don't know how that emoticon got there (thumbs-down); I didn't put it there.

---

### Post by Longinus00 on 2009-10-03
This happens all the time in virutalbox, I notice it does it every time I make a snapshot. It hasn't happened for a long time on my machine where karmic is really installed though.

---

### Post by trulan on 2009-10-03
That thumbs-down emoticon shows up a lot.  It's like it's easy to bump or something, it gets selected by default if you click the wrong place or hit the wrong key or something.  Either that or it's something to do with your web browser blocking one of the scripts that the forum uses.  When I first started posting on here I was constantly having to edit my posts to remove the dumb thing.

---

### Post by bennachie on 2009-10-04
I've had the same problem on three different machines (Lenovo Thinkcentre desktop, Compaq C700 laptop and Asus eeePC-1000H). None of them could be described as powerhouses, but all have been - and two are once again - running 9.04 very happily. I'll have another go with 9.10 Beta and try the recommended workaround.

While perhaps not unexpected at Beta stage, this sort of thing should be considered an absolute show-stopper for any version claiming to be a "release candidate", never mind a "release".

---

### Post by donniezazen on 2009-10-04
> **bennachie said:**
> I've had the same problem on three different machines (Lenovo Thinkcentre desktop, Compaq C700 laptop and Asus eeePC-1000H). None of them could be described as powerhouses, but all have been - and two are once again - running 9.04 very happily. I'll have another go with 9.10 Beta and try the recommended workaround.

While perhaps not unexpected at Beta stage, this sort of thing should be considered an absolute show-stopper for any version claiming to be a "release candidate", never mind a "release".

Totally agree. Its a huge show stopper. The worse than that is nvidia-glx graphic driver which works perfectly in earlier distros is bugged in Karmic. In-spite of reporting the problem for Alpha 5&6 the issue has not been fixed. I do not know, what all the people, who have been faithful to Ubuntu, with Nvidia drivers, will do.

Since Ubuntu is a community project, so, i am not blaming anybody, i am just hoping that our hard working developers will fix this issue soon.

Thanks,
SK

---

### Post by fela on 2009-10-04
Now before you guys start hammering karmic for having a little (yes: little) bug, let me tell you this:

the error that the OP posted is a clock error. Basically what I think is happening is that the hardware clock is behind the local time, and it's not loading the local time before it does the filesystem check. The filesystem is labeled with its last write time, which of course is the local time, so it looks like the filesystem was mounted in the future to the operating system.

I'm not totally sure how to fix it permanently because I only ever got that by my own actions, but it is a little bug and only requires a fsck on each reboot (so it's not a show stopper as some guys seem to be saying).

---

### Post by donniezazen on 2009-10-04
> **fela said:**
> Now before you guys start hammering karmic for having a little (yes: little) bug, let me tell you this:

the error that the OP posted is a clock error. Basically what I think is happening is that the hardware clock is behind the local time, and it's not loading the local time before it does the filesystem check. The filesystem is labeled with its last write time, which of course is the local time, so it looks like the filesystem was mounted in the future to the operating system.

I'm not totally sure how to fix it permanently because I only ever got that by my own actions, but it is a little bug and only requires a fsck on each reboot (so it's not a show stopper as some guys seem to be saying).

I do not mind it because i use Ubuntu to learn something new everyday but it would be hard to convince people that they will have to run a command then only their computer will boot. Surely the developers will fix it before release. I think its a minor problem for pro but for a novice not able to start his/her PC is definitely a disaster.

Nvidia driver is also a big problem.

---

### Post by Peter09 on 2009-10-04
Yes, I had this happen to me as well, in virtualbox. I did notice that in the previous version of virtualbox it incorrectly set the time.I'm wondering if the two things are connected.

---

### Post by shafin on 2009-10-04
Maybe you can change the hardware clock in BIOS to get rid of this.

---

### Post by fela on 2009-10-04
Can someone please explain to me what's so hard about typing:

```
fsck /dev/sda1
```

---

### Post by dasunst3r on 2009-10-04
> **fela said:**
> Can someone please explain to me what's so hard about typing:

```
fsck /dev/sda1
```While you and I may have the skill to know what to do and/or the patience to find out what to do, people would generally say, "This piece of junk is broken already..." and stop right there.

---

### Post by MoebusNet on 2009-10-04
> **fela said:**
> Can someone please explain to me what's so hard about typing:

```
fsck /dev/sda1
```

See my post above:

"This doesn't work on my Karmic-beta install; the boot bypasses fsck and hangs trying to access the encrypted HDD."

---

### Post by Bebby on 2009-10-14
I got this error message after my ubuntu had unclean shutdown and it happened right after I'm finished updating Firefox 3.0 to 3.5 in ubuntu =P. I didn't get a snapshot pic of the error message though *sorry* 

I started my desktop pc and it was running the scan due to unclean shutdown and at 85% it broought me to the error message that indicates you have to run fsck manually. In the end of the displayed message it prompted me to either press ctrl-d or entered my root pass. I entered my root pass instead and I got into the bash. From that point on, simply:
1. I type:
 ```
fsck /dev/sda2
```
(NOTE: sda1 was for my windows, I have dualboot ubuntu and windows on this desktop pc)

2. In my case (might be different, simply read the question displayed on your screen), they were all pretty much "Yes" as my answer =).

3. Voila, it's done! I reboot my system by typing: 
```
sudo shutdown -r now
```
enter your root password as prompted =)


System restored =P, it's booting normally =) ... I'm back up and running with my ubuntu! =)

---

