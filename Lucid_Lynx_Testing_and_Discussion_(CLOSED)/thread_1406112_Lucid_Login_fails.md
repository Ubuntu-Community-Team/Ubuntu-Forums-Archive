---
title: "Lucid Login fails"
date: 2010-02-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sirkeith on 2010-02-13
Afternoon, I thought I had seen this problem earlier but I can't seem to find it. have had the same problem repeatedly. I download a daily release, it checks out good, but I can't login. It just loops, over and over. Todays release included. I removed Plymouth which stops the lock up but can't get past the login screen. Any thoughts would be appreciated, it is getting harder and harder to buy CD-R's in this part of the world. ;)

keith

---

### Post by ranch hand on 2010-02-13
First RW is you friend.

Try booting to recovery and using the text login and then type;
```

startx

```
I bet that puts you right in on your desktop.

---

### Post by sparker256 on 2010-02-13
> **sirkeith said:**
> Afternoon, I thought I had seen this problem earlier but I can't seem to find it. have had the same problem repeatedly. I download a daily release, it checks out good, but I can't login. It just loops, over and over. Todays release included. I removed Plymouth which stops the lock up but can't get past the login screen. Any thoughts would be appreciated, it is getting harder and harder to buy CD-R's in this part of the world. ;)

keith

With today's daily build I do no get a login screen, I am taken right to the desktop. A few weeks back I did have the login problem but for the last couple of weeks that problem is gone for me. In testing daily builds I have been using a thumb drive which is cheaper in the long run.

Bill

---

### Post by ubername on 2010-02-13
[http://ubuntuforums.org/showthread.php?t=1400654](http://ubuntuforums.org/showthread.php?t=1400654)

I've been getting similar probs.

Screen freezes after entering password in GDM

running GDM from 'recovery mode' from root prompt works OK

Something which might be related is: 'telinit 3' from root prompt also causes freeze. (I do that when messing with NVIDIA drivers from recovery mode)

---

### Post by LKjell on 2010-02-13
> **sirkeith said:**
> Afternoon, I thought I had seen this problem earlier but I can't seem to find it. have had the same problem repeatedly. I download a daily release, it checks out good, but I can't login. It just loops, over and over. Todays release included. I removed Plymouth which stops the lock up but can't get past the login screen. Any thoughts would be appreciated, it is getting harder and harder to buy CD-R's in this part of the world. ;)

keith

Get a usb pen

---

### Post by sirkeith on 2010-02-13
Thanks for the replies. I should have said more in my original post though. Command line login does work. Startx does not. I have not been able to get my laptop to boot from or load an iso image from a USB pen or key chain or anyother name they have. I am not experienced enough to say much more.

keith

---

### Post by zika on 2010-02-13
Try with nomodeset in kernel line in Grub. That works for me with 2.6.33...

---

### Post by ubername on 2010-02-14
I think I have misunderstood your original post - Do you have ubuntu installed at all on you box or are you just trying to run from CD, which is failing?

---

### Post by sirkeith on 2010-02-14
Hi Zika, I tried nomodeset and no success for me. I appreciate the suggestion.

Ubername, I am installing the software. Awhile back I had the login problem on the live cd but I tried an install and login worked from the same release. 

I have a day off coming so I am just going to give it a rest until I came back to work and then I will download a new daily build and see how it goes. I think there are a couple of things tied into this problem for me.

Thanks

keith

---

### Post by sirkeith on 2010-02-18
Had a nice couple of days off work. Came back today and downloaded rhe dailey build. Burned it real slow to my cd-r, cd-r seems to check out okay. But no success installing it to hard drive, nor in running a live cd from it. I really liked Lucid when it was running on the 2.6.32.9 kernel.

Anyone know where I an find a build running on that kernel?

Take care

keith

---

### Post by Ibidem on 2010-02-18
I think that's about alpha1.  I've had little luck finding an alpha1 iso, though.

---

### Post by sirkeith on 2010-02-18
> **Ibidem said:**
> I think that's about alpha1.  I've had little luck finding an alpha1 iso, though.

I found a 2.6.32-7-generic on a cd. It is woderful, for now.

Could send it to ya??

---

### Post by Ibidem on 2010-02-18
I'm fine right now; I have a custom install from ~alpha1 that I never really hosed.
CDs wouldn't help, anyhow. (Aspire One netbook)
For backup I've got Kuki Linux (Jaunty), and also TCL 2.4.
Besides that I have Freedos, XP, and nimblex; AntiX isn't booting.
So...
I hope to try out Fedora 12 and/or SL 5.
But the long and short is don't bother sending it.

Ibidem

---

