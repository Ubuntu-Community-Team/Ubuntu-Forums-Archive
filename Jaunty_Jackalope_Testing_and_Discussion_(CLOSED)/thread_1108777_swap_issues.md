---
title: "swap issues?"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Neon Lights on 2009-03-28
errmmm. So I've been having random lockup issues with Jaunty, and I realized, it's been using no swap at all. After doing some poking around, it seems my swap partition isn't mounting or is being turned off, or not being turned on, upon boot.

Anyone else have this? I'm sure I could just add a swapon command to my session or something, right? But if it's not an isolated incident...It needs help. :p

---

### Post by Nullack on 2009-03-28
Well with my 2gig ram on the test box I dont ever hit swap. Are you sure your running out of physical ram?

---

### Post by Kevbert on 2009-03-28
Swap rarely gets used unless you use hibernate. If you know how to get lockups run a visible terminal prior to the lockup with the command
```
top
```
to see what program/process is causing the problem.

---

### Post by kansasnoob on 2009-03-28
It could be a UUID problem.

Compare the SWAP uuid's between thes two files:

```
sudo blkid -c /dev/null
```

```
cat /etc/initramfs-tools/conf.d/resume
```

Also is Usplash working properly? Quite often the "quiet" boot is lost at the same time. So you might want to look at:

```
cat /etc/fstab
```

Never, ever edit /dev/null! Just let me know if the SWAP uuid's match or not and I'll tell you how to proceed.

PM me if necessary.

---

### Post by esseferio on 2009-03-28
Hi,
i was having something similar, mainly while browsing with Firefox. So, first I disabled all plugins and extensions, just to make sure. Nope.

Then I disabled the tracker... Which seems to have "solved" that particular issue. Now, it's not like I use the tracker anyway, but :

1) Is it OK to ?
2) Is this a bug (and then, my, I'm gonna have to try and learn how to fill those bug reports :))

Regards,

Serge

---

### Post by Neon Lights on 2009-03-28
> **Nullack said:**
> Well with my 2gig ram on the test box I dont ever hit swap. Are you sure your running out of physical ram?
1gig, and firefox gets up to 500mg (it's flash -.-).

> **kansasnoob said:**
> It could be a UUID problem.

Compare the SWAP uuid's between thes two files:

```
sudo blkid -c /dev/null
``````
cat /etc/initramfs-tools/conf.d/resume
```Also is Usplash working properly? Quite often the "quiet" boot is lost at the same time. So you might want to look at:

```
cat /etc/fstab
```Never, ever edit /dev/null! Just let me know if the SWAP uuid's match or not and I'll tell you how to proceed.

PM me if necessary.
They're different. o.O
Usplash is working properly though.

---

### Post by kansasnoob on 2009-03-28
> **Neon Lights said:**
> 1gig, and firefox gets up to 500mg (it's flash -.-).


They're different. o.O
Usplash is working properly though.

OK. the most common cause of this is having moved or resized the SWAP partition. Give me a little bit here to pull up the proper instructions - one thing - always a good idea before editing any file - create a simple backup of all three of those outputs.

I always just copy-n-paste the outputs of all three into a simple word document using Open Office or Abiword. Then name it whatever you wish so you can find it if you happen to make a "oops".

I'll post back directly! Must feed my goats!

---

### Post by kansasnoob on 2009-03-28
Actually just look at my post #5 here:

[http://ubuntuforums.org/showthread.php?t=1090556](http://ubuntuforums.org/showthread.php?t=1090556)

---

### Post by Neon Lights on 2009-03-28
Kay, I got them to be all the same, however it's still off upon reboot. :/

also, if it means anything, ```
sudo swapon -a
``` gives ```
swapon: cannot stat c84421f4-dd26-44fa-a3b5-1f025a8674b0: No such file or directory
``` however ```
sudo swapon -U c84421f4-dd26-44fa-a3b5-1f025a8674b0
``` worked fine. -confused- o.o haha.

---

### Post by sgosnell on 2009-03-28
Are you sure you made the right corrections?  If you made them the same by making them both the old UUID, it won't work, and you would likely get what you now have.

---

### Post by kansasnoob on 2009-03-28
Actually post the output of:

```
sudo blkid -c /dev/null
```

```
cat /etc/fstab
```

```
cat /etc/initramfs-tools/conf.d/resume
```

And, please tell me you DID NOT edit blkid! If you did tell me you created a backup as suggested!

The most common "fail" in that process is NOT waiting for the command:

```
sudo update-initramfs -u
```

to complete! It takes a couple of minutes. It's not done until you see your normal command prompt in terminal!

---

### Post by Neon Lights on 2009-03-28
> **kansasnoob said:**
> Actually post the output of:

```
sudo blkid -c /dev/null
``````
cat /etc/fstab
``````
cat /etc/initramfs-tools/conf.d/resume
```And, please tell me you DID NOT edit blkid! If you did tell me you created a backup as suggested!

The most common "fail" in that process is NOT waiting for the command:

```
sudo update-initramfs -u
```to complete! It takes a couple of minutes. It's not done until you see your normal command prompt in terminal!

```
/dev/sda2: UUID="c84421f4-dd26-44fa-a3b5-1f025a8674b0" TYPE="swap" 
```
```
c84421f4-dd26-44fa-a3b5-1f025a8674b0 none            swap    sw              0       0
```
```
RESUME=UUID=c84421f4-dd26-44fa-a3b5-1f025a8674b0
```

and I waited until I got back to the regular command prompt. It was only about 30 seconds though.

---

