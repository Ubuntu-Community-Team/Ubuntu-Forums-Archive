---
title: "no apt sources for ubuntu-9.10-desktop-amd64"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by ramaswamyps on 2012-10-18
i have now installed ubuntu-9.10-desktop-amd64 on my C855D toshiba satellite
brand new laptop dual booting with windows 7 OEM
i am not able to get any pdate for any packages with synaptics and apt-get
the source list does not update saying 404
what is possible to update?
i did not see any suitable for my laptop
ubuntu-12 does not boot in this system

kindly advice as necessary
thanks

---

### Post by drmrgd on 2012-10-18
Version 9.10 is no longer supported, and as such those repositories not longer serve updates.  It's odd that a brand new laptop won't run 12.04 - especially if it has the capability of running Windows 7.  However, if that's truely the case, you might try v10.04, which is to be supported a little (but not too much!) longer.

---

### Post by kc1di on 2012-10-18
> **ramaswamyps said:**
> i have now installed ubuntu-9.10-desktop-amd64 on my C855D toshiba satellite
brand new laptop dual booting with windows 7 OEM
i am not able to get any pdate for any packages with synaptics and apt-get
the source list does not update saying 404
what is possible to update?
i did not see any suitable for my laptop
ubuntu-12 does not boot in this system

kindly advice as necessary
thanks
ubuntu 9.10 reached end of life in April 2011 and thus there will be no update repositories available you need to get at least ubuntu 10.04.1 lts which will still be good until April 2013.

But with the machine you mentioned ubuntu 12.04 lts should work fine also.

12.04 should boot for you but you may have to enter some kernel option. here's a link that may help.
[https://help.ubuntu.com/community/BootParameters]("https://help.ubuntu.com/community/BootParameters")

---

### Post by ramaswamyps on 2012-10-18
mmmmm :(
i liked the 64 bit insallation.
now that i have started download of 64 bit ubuntu-12.04.1-desktop-amd64.iso
will come  back after i could install and run it
thanks for replies

---

### Post by ramaswamyps on 2012-10-18
ubuntu 12.04.1-desktop- amd64 installed somewhat successfully.
video soetimes flickers.
a notice comes up saying restricted software /drivers available for my laptop. also says it is not free.
if i nstall i will have to pay for it??

---

### Post by drmrgd on 2012-10-19
Not free?  That's a bit surprising (and hard to imagine).  I don't think I've ever seen the need to pay for a driver before.  Are you sure you read that correctly?  What drivers is it saying are availble?

---

### Post by SwiftPengu on 2012-10-19
I think not-free means proprietary drivers without a GPL licence
[http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html)

---

### Post by kc1di on 2012-10-19
> **ramaswamyps said:**
> ubuntu 12.04.1-desktop- amd64 installed somewhat successfully.
video soetimes flickers.
a notice comes up saying restricted software /drivers available for my laptop. also says it is not free.
if i nstall i will have to pay for it??

no you don't have to pay but it's not an open source license. 

what you need to do is install the following.
I find it easier to do it from a terminal
open a terminal and type the following commands: (one at a time)
```
sudo apt-get update
```
```
sudo apt-get install ubuntu-restricted-addons ubuntu-restricted-extras
```
That will install most of the codecs you need for flash and other video formats.

Also the flicker may be because the open source driver for your video card is not up to speed. in that case if the video card maker has made a linux driver for your card it would be considered non-free license. you can check for a propitiatory driver by going to system settings > additional drivers.
good luck

---

