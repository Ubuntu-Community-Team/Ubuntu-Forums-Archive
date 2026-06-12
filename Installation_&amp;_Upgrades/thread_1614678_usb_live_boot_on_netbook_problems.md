---
title: "usb live boot on netbook problems"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by wisnoskij on 2010-11-05
On a Lenovo thinkpad S12 2959
and a kingston DataTraveler 101

OK I have been having a lot of strange issues while trying to install the current 10.10 netbook version of Ubuntu.

I followed the instructions right below the download for the iso.
Basically download the usb live creator and use it.
So I did (with no persistence set) and it seemed to work.

I tried booting from it and it worked, except that I have to keep pressing keys, I used the enter key and it worked.
If I stop pressing enter no progress is made.
Then at the end their is some error about no persistent space being available.

Is this normal???

and now it is booted, so I try to install a driver and it hangs.
so I try to install the OS, and it hangs.
So I try to exit and it finally gets to the next screen in the installation after I tell it to exit, but then hangs when trying to get the the next one and it will not continue.

What is wrong???

---

### Post by wilee-nilee on 2010-11-05
Check the MD5sum of the ISO, and use unetbootin.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

If you have a windows OS on there let us know so that if any thing needs to be done we can help.

---

### Post by VraiChevalier on 2010-11-05
> **wisnoskij said:**
> On a Lenovo thinkpad S12 2959
and a kingston DataTraveler 101...snip

I had some troubles using a Kingston Data Traveler and booting live distros on my Acer Aspire One. After researching it I discovered that some usb drives do not work as well as others for booting live distros. I have not had any problems with Corsair Flash Voyagers or a Patriot XT Xporter.

---

### Post by wisnoskij on 2010-11-06
Thanks for the quick replies.

Hash is the same.
Will try UNetbootin and let you know.

The netbook (new, bought today) came with with windows xp on it, but it seemed to error all the time for no good reason. Not that I expect a new laptop with loads of random crap installed on it to work well, but it raises the idea that it might be broken in some way.

@VraiChevalier: Damb, I bought the usb drive simply to do a ubuntu install. Hopefully it is returnable.

---

### Post by wisnoskij on 2010-11-06
Using unetbootin does not seem to have changed anything, same problems.

But I did try the USB stick in my desktop and it seems to boot ubuntu fine.
So it seems the issue is either with the laptop or the USB drive works on some machines but not others.

---

### Post by wisnoskij on 2010-11-06
> **wisnoskij said:**
> 
The netbook (new, bought today) came with with windows xp on it, but it seemed to error all the time for no good reason. Not that I expect a new laptop with loads of random crap installed on it to work well, but it raises the idea that it might be broken in some way.

Having used it slightly more and not gotten any more errors I think I was just unlucky the first time I used it and it was just normal windows unstableness and not reflective of a larger hardware problem.

---

