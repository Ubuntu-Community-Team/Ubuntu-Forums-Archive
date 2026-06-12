---
title: "Can't install Ubuntu 10.10 final on my PC"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by arepaking on 2010-12-18
Folks,
Somehow I've been really unlucky with Ubuntu 10.10. When I run the CD choose any of the three options offered by Grub, the system just waits for 20-30 seconds and gives me a screen with Green squares. 

Here's a video I made when 10.10 was in beta. The problem is still the same even in the final version. [http://www.youtube.com/watch?v=KKiks45jMEU](http://www.youtube.com/watch?v=KKiks45jMEU)


I have an Intel Dual Core 2.0Ghz PC with 8GB ram and an Nvidia GeForce 6200 graphics card. I have Ubuntu 10.04 on it which installs and works fine. its only the 10.10 that I have this problem with.

Any ideas out there?

---

### Post by TBABill on 2010-12-18
This is strange. Normally when you install Ubuntu you do not go to a Grub screen. You should boot to a graphic screen asking what you want to do. Where was the download from? Which version did you download? Could this be a server version you downloaded instead of the main version?

Also, did you verify the md5sum to be sure you had a good download?

---

### Post by arepaking on 2010-12-18
I downloaded the .ISO images from [www.ubuntu.com](www.ubuntu.com) -> Desktop and I selected 64bits.

The name of the file downloaded is: ubuntu-10.10-desktop-amd64.iso

I was also expecting to see the graphical interface.

---

### Post by arepaking on 2010-12-18
> **TBABill said:**
> This is strange. Normally when you install Ubuntu you do not go to a Grub screen. You should boot to a graphic screen asking what you want to do. Where was the download from? Which version did you download? Could this be a server version you downloaded instead of the main version?

Also, did you verify the md5sum to be sure you had a good download?

How can I verify the md5sum?

---

### Post by Rubi1200 on 2010-12-18
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I also suggest you run the boot info script from the LiveCD and post it here (link at the bottom of my post with instructions).

If you are using the LiveCD, you can use the nomodeset parameter by hitting F6 as the first screen starts to load on the CD.

---

### Post by arepaking on 2010-12-18
> **Rubi1200 said:**
> [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I also suggest you run the boot info script from the LiveCD and post it here (link at the bottom of my post with instructions).

If you are using the LiveCD, you can use the nomodeset parameter by hitting F6 as the first screen starts to load on the CD.

Thanks for pointing out how to check the MD5SUM. Here are my resutls.

```

homer@DLINK:~/Downloads$ md5sum ubuntu-10.10-desktop-amd64.iso 

1b9df87e588451d2ca4643a036020410  ubuntu-10.10-desktop-amd64.iso

homer@DLINK:~/Downloads$ 
```

---

### Post by Rubi1200 on 2010-12-18
The hash is fine, so that isn't the problem.

Did you burn the image to CD at the lowest possible speed?

---

### Post by arepaking on 2010-12-18
> **Rubi1200 said:**
> The hash is fine, so that isn't the problem.

Did you burn the image to CD at the lowest possible speed?

Not at the slowest. I had burned so far two dics (1st - High Speed; 2nd - Medium). But I will go ahead and burn a 3rd dics at the slowest possible speed and I will report my results.

Thanks!

---

### Post by arepaking on 2010-12-18
Ok,
I used a different computer and burned the CD on the lowest possible speed yet I get the same results.... green squares as shown in the video link above.

What could it be!? I resist to think that I am the only person in the planet with this problem :(

---

### Post by Rubi1200 on 2010-12-18
Try this to get the CD booting:

Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter:

nomodeset

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --**

Now hit Enter and hopefully you will be at the desktop.

_You may have to start with F6 as the first step in your situation._

Good luck and let me know how it goes please.

---

### Post by arepaking on 2010-12-18
> **Rubi1200 said:**
> Try this to get the CD booting:

Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter:

nomodeset

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --**

Now hit Enter and hopefully you will be at the desktop.

_You may have to start with F6 as the first step in your situation._

Good luck and let me know how it goes please.

Hi Rubi,
It did not work.. Same Results (Green Squares)....

---

### Post by Rubi1200 on 2010-12-19
I don't know what to tell you :confused:

It seems as if it is probably graphics or hardware related, but how to narrow it down?

If 10.04 works for you, stick with it.

I have been testing 10.10 and, to be honest, there are not that many changes that would make it worth upgrading or upsetting your current setup.

If I find more information about this, I will post back here.

Good luck!

---

