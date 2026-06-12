---
title: "Installation goes black"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by 24C41 on 2010-12-23
Right, I'm trying to install 10.10 on a piece of hardware I don't know the specs for. The problem I've encountered appears when I boot from the installation-CD. After a few seconds it puts the screen to sleep-mode.
Any suggestions on what might cause this?

---

### Post by cipherboy_loc on 2010-12-23
What happens when you turn the display off, then on when it enters sleep mode? Oh, and does pressing random keys (preferably none that may interfere with the boot) turn it back on? Oh, and can you get past this into an OS (you should do something for 10 minutes and come back to spare your time; the LiveCD can be slow...) in the end?


Edit:

Possible and Unlikely Causes (without knowing more so some could be unreasonable):
1) Your display could be acting up.
2) Ubuntu does not like your graphics card.
3) When you burned the LiveCD, you did not check the MD5 sum.

As I said before, they are just guesses without knowing more.



Cipherboy

---

### Post by kansasnoob on 2010-12-23
Do you have access to any other Ubuntu/Linux Live CD's?

I'm asking because this certainly sounds like Ubuntu is not happy with the hardware and ultimately it would be nice to see the output of:

```
lshw
```

But, if you have no other Live CD's, try booting the Live CD again and as soon as you see the two small graphics at the bottom of the screen press a key (you only have about 3 seconds), and then you'll see something similar to this:

[https://help.ubuntu.com/community/BootOptions?action=AttachFile&do=get&target=mainboot.png](https://help.ubuntu.com/community/BootOptions?action=AttachFile&do=get&target=mainboot.png)

Then press the F6 key and select "nomodeset" and see if that works.

---

### Post by sikander3786 on 2010-12-23
+1 to nomodest parameter. It should definitely solve the issue here. Lets see how that goes.

And if you are able to successfully install Ubuntu using nomodeset, you might need to insert nomodeset in Grub once you boot from the HDD. Let us know and we would try to guide you then.

And, Welcome to the forums :-)

---

