---
title: "linux-image-2.6.311 and intel graphics"
date: 2009-07-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2009-07-01
Currently I can't boot with that kernel, because my screen remains black (switched off)
I have an intel X4500hd
do you have my same issue?

---

### Post by buzzmandt on 2009-07-01
I don't have the same issues but on my intel 950 mobile neverwinter nights runs very choppy/slow, unplayable.  Runs fine in .30-10 .  something happened with the intel graphics cards, seems also to have affected nvidia and ati as well, maybe and xorg/kernel issue?

---

### Post by yelo3 on 2009-07-01
In my case it's like kernel mode setting is not working...is the 950 mobile the same model as mine?

---

### Post by sbergman27 on 2009-07-01
I have X4500 video, and currently, when it goes to start X, I just get some random lines partway across the screen... and nothing more. To get anything usable at all, I have to go back to 2.6.30 *and* use the vesa driver. Are we the only two people having problems?

---

### Post by jerrylamos on 2009-07-01
black screen of death on this IBM Thinkpad R31 with intel i830 graphics.

Workaround:

When grub2 screen comes up
e
down arrow twice
at end of kernel line after quiet splash add 
nomodeset
ctrl-x

boots up O.K. since KMS is turned off.  

Runs O.K. but slowly, namely GtxPerf runs in 70 seconds instead of 50.  

This is a 1 gHz Celeron which isn't very fast.  It does internet browse, internet mail, office, internet flash video O.K. on small window, perfectly usable however KMS is in the wrong direction at this stage in debug.

I saved some logs by dual booting to intrepid image (runs fine!) so let me enter a launchpad bug.

Jerry

---

### Post by buzzmandt on 2009-07-01
> **yelo3 said:**
> In my case it's like kernel mode setting is not working...is the 950 mobile the same model as mine?

I don't think so, but don't quote on me on that

---

### Post by Aries K on 2009-07-01
Have Nvidia graphics and I can confirm this.

---

### Post by geojorg on 2009-07-01
I can confirm the same issue with Dell Inspiron 1420
with Intel Graphic Card, the workaround did work for me

---

### Post by camper365 on 2009-07-01
On a thinkpad t43 with an ATI X300, I log in, but I see black boxes where a window pops up instead of the window itself. I don't see the gnome panels either. I like the smaller font on the tty though.

---

### Post by caryb on 2009-07-01
Can confirm with Kubuntu & Nvidia 140M chipset as well

Cary

---

### Post by graaant on 2009-07-01
Same deal with Dell E6400
Booting alright with 30.10, have not tried the workaround for .31 yet.
Assuming this will be fixed shortly?

---

### Post by drfox on 2009-07-01
My workaround is to escape into grub2, arrow down to the 2.6.30-10 (or earlier) kernel, and press enter. It boots right into my gdm session; with 2.6.31-1 I can't startx.

HTH

Larry

---

### Post by ghindo on 2009-07-01
Has a bug been filed?

---

### Post by nanog on 2009-07-02
edit /boot/grub/menu.lst

and add nomodeset to the end of your kernel parameter like this:

```
kernel          /boot/vmlinuz-2.6.31-1-generic root=UUID=9ba679c5-6127-4724-ab47-b9875823c345 ro quiet splash **[COLOR="Red"]nomodeset[/COLOR]**
```

---

### Post by psyke83 on 2009-07-02
> **caryb said:**
> Can confirm with Kubuntu & Nvidia 140M chipset as well

Cary

Your issue is probably not related. This seems to be a KMS issue for Intel graphics users - it can be confirmed by booting with "nomodeset" as nanog mentioned.

---

### Post by caryb on 2009-07-02
> **psyke83 said:**
> Your issue is probably not related. This seems to be a KMS issue for Intel graphics users - it can be confirmed by booting with "nomodeset" as nanog mentioned.

My bad! I tried it & didn't do a thing. I will start a new post with my problem.


Thanks Cary

---

### Post by psyke83 on 2009-07-03
> **caryb said:**
> My bad! I tried it & didn't do a thing. I will start a new post with my problem.


Thanks Cary

The "nomodeset" option is to disable KMS, so it's for Intel graphics users. I was suggesting that the folks in this thread other than you should test this boot option.

---

