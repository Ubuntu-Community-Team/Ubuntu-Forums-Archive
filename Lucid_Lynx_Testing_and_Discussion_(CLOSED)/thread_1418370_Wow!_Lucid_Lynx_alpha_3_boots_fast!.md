---
title: "Wow! Lucid Lynx alpha 3 boots fast!"
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by RJARRRPCGP on 2010-02-28
Possibly even faster than Jaunty Jackalope!

It's like a fixed up Karmic Koala! ;) 

Even when my Barracuda 7200.12 was short-stroked, with only a 16 GB partition, was still booting slow with Karmic Koala.

---

### Post by phenest on 2010-02-28
Yep, same here. It kinda negates the need for a fancy boot screen.

---

### Post by grubdude on 2010-02-28
Is that why the Ubuntu splash screen is missing, or because this is still in Alpha?

---

### Post by phenest on 2010-02-28
> **grubdude said:**
> Is that why the Ubuntu splash screen is missing, or because this is still in Alpha?

They're adding Plymouth for a fancy splash instead, but it's really buggy with some hardware. I can't see the point if it's only there for a few seconds.

---

### Post by grubdude on 2010-02-28
Ah, yes forgot about Plymouth. I guess it is all progress.... :-)

---

### Post by cimh on 2010-02-28
On my asus eee 901 netbook alpha 2 & 3 boot from switch on to desktop in 22s and I have www link up via wifi in 32s from switch on. If I use LXDE instead of gnome the desktop is up in 16s. On this hardware (booting off ssd) these times are normally reserved for ultra slim distros like customised arch, moblin and chrome. Its truly amazing, lets hope these times continue to the full release. 

Obviously I switch off splash but it seems to me that splash is most useful when you have those old boring boots that take minutes to get going, ideally they will become redundant in time.

There seems to be one major problem with turning splash off and that is it seems to cause Random logouts which are very annoying
see: [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/518352/comments/12](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/518352/comments/12)

I hope someone finds a fix for this soon. (ps there is a fix for this just delete plymouth using synaptic)


cimh
eee901 quad booting to:  ubuntu 10.04a, eb4, eeebuntu3, puppeee

---

### Post by pererik87 on 2010-02-28
> **cimh said:**
> On my asus eee 901 netbook alpha 2 & 3 boot from switch on to desktop in 22s and I have www link up via wifi in 32s from switch on. If I use LXDE instead of gnome the desktop is up in 16s. On this hardware (booting off ssd) these times are normally reserved for ultra slim distros like customised arch, moblin and chrome. Its truly amazing, lets hope these times continue to the full release. 

Your asus has a 900 mhz processor, i don't think you are likely to get a 10s with gnome on that.

---

### Post by RJARRRPCGP on 2010-02-28
Random logouts may be caused by the web browser crashing. 

I have been noticing an issue where simply going to a web site causes X to go down! (And I don't have the wrong video driver installed!)

And unfortunately, I still have yet to be able to go to weather.com without Midori crashing! :(

And IIRC, when I was trying the new TinyMe version, when going to weather.com with Midori, when going to the local forecast display, X went down! I all of a sudden saw the login screen!

---

### Post by teh603 on 2010-03-01
> **phenest said:**
> They're adding Plymouth for a fancy splash instead, but it's really buggy with some hardware. I can't see the point if it's only there for a few seconds.Honestly, I liked the old splash better than the Plymouth-based one. Add to it the fact that it adds up to several minutes to my boot time on all hardware, and they might as well just pull it and give us a text-based splash.

---

### Post by garba on 2010-03-01
yep, it definitely is blazing fast, just given it a whirl on my netbook (acer 1101ha), it's impressive how fast this thing comes up... Still wondering what the point of a nice splash screen is!

---

### Post by dagrump on 2010-03-01
It's because they have nothing better to do, all the bugs are fixed:) :)
If you buy that I have some prime real estate you might be interested in.:)

---

### Post by Ichtyandr on 2010-03-02
beyond plymouth or usplash, its faster and more beautiful than anything I've had on my pc so far. and both firefox and ooo work significantly faster than in KK, thus its literally flying here. I've had Linux occasionally since Mandrake 7, but this is an incremental breakthrough!

---

### Post by rudihawk on 2010-03-02
My Lucid boots so quickly its pretty much insane... :O

Everything is just FAST and it looks great!

---

### Post by RJARRRPCGP on 2010-03-02
The ATA transfer may be broken in Karmic Koala. Because it did seem to feel slow after the boot and login.  

Because I heard of people having slow SATA access in the past.

---

### Post by cimh on 2010-03-02
> **pererik87 said:**
> Your asus has a 900 mhz processor, i don't think you are likely to get a 10s with gnome on that.

the 901 has a 1.6 atom processor. I didnt used to think that a sub 20s boot was possible with a large distro like ubuntu. But who knows

cimh
eee901

---

### Post by xir_ on 2010-03-03
> **RJARRRPCGP said:**
> The ATA transfer may be broken in Karmic Koala. Because it did seem to feel slow after the boot and login.  

Because I heard of people having slow SATA access in the past.

Could you provide any more info on this?

---

### Post by cyberkilla on 2010-03-03
I was just thinking this myself. It booted very quickly.

Opening programs seems marginally faster too, and I don't think its a placebo effect.

---

### Post by xlnt01 on 2010-03-03
I'm so darn impressed with this boot now. :)
On my laptop witch has an SSD drive I boot from grub to KDM login in less than 4 seconds.

Is there even a boot splash?

With a boot like this there is no need to have a boot splash at all since it will only delay the boot process even more.

To the developer team, get rid of the boot splash. Then my laptop might be able to boot within 3 seconds. ;)

---

### Post by RJARRRPCGP on 2010-03-04
> **xir_ said:**
> Could you provide any more info on this?

Even though this thread was written for Jaunty Jackalope, this possibly is still occurring with Karmic Koala:

[http://ubuntuforums.org/showthread.php?t=1150108&highlight=ATA+slow](http://ubuntuforums.org/showthread.php?t=1150108&highlight=ATA+slow)

---

### Post by RJARRRPCGP on 2010-03-04
Even though this bug is listed for kernel 2.6.20, this problem may still be occurring. :( 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730)

And this thread:

[http://ubuntuforums.org/showthread.php?t=447474](http://ubuntuforums.org/showthread.php?t=447474)

---

### Post by xir_ on 2010-03-04
> **RJARRRPCGP said:**
> Even though this bug is listed for kernel 2.6.20, this problem may still be occurring. :( 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730)

And this thread:

[http://ubuntuforums.org/showthread.php?t=447474](http://ubuntuforums.org/showthread.php?t=447474)

Thanks for the info I've been having an issue with a laptop drive like this for a while on a machine. Whenever my system starts to swap it literally grinds to a halt and i have to kill all x server processes. I'm going to read this material with interest.

:)

---

### Post by mk_kano on 2010-03-09
> **cimh said:**
> the 901 has a 1.6 atom processor. I didnt used to think that a sub 20s boot was possible with a large distro like ubuntu. But who knows

cimh
eee901

I am pretty sure they are targeting a 10s boot on a midrange system which Canonical refers to as an atom based netbook.

---

### Post by Seren on 2010-03-09
> **xlnt01 said:**
> I'm so darn impressed with this boot now. :)
On my laptop witch has an SSD drive I boot from grub to KDM login in less than 4 seconds.

Is there even a boot splash?

With a boot like this there is no need to have a boot splash at all since it will only delay the boot process even more.

To the developer team, get rid of the boot splash. Then my laptop might be able to boot within 3 seconds. ;)

You can suppress the splash on your install by appending 'nosplash' at the end of the kernel command line in grub.

---

### Post by ElSlunko on 2010-03-09
> **phenest said:**
> Yep, same here. It kinda negates the need for a fancy boot screen.

I feel the same way. I did manage some combo of drivers to get a glimpse of it and it looks nice indeed. I don't miss it much though because of the fast boot time.

---

### Post by teo_rossi on 2010-04-05
Well, unfortunately my Lucid isn't that fast. I installed it on a new VAIO CW2 laptop, fully updated. The boot process takes at least 2 minutes.

Why is that happening? I attach the dmesg log

---

### Post by teh603 on 2010-04-05
I just switched to Kubuntu, and it still boots really fast, although I don't get the Plymouth splash for some reason. The new KDE feels like something out of Star Trek or Babylon 5 compared to the version I had to use three years ago on my Xandros-based eeePC 701. Oh, and the package manager works and properly handles dependencies, compared to the Xandros one that choked up on the second tier of them.

---

