---
title: "Can Ubuntu be installed on a MediaTek MT8183 Chromebook"
date: 2021-07-24
forum: Installation &amp; Upgrades
---

### Post by szegedin74 on 2021-07-24
...

---

### Post by Frogs Hair on 2021-07-25
No, Chrome books are proprietary and don't allow other Linux operating systems to be installed. The only option is [coruton]("https://github.com/dnschneid/crouton") which is use at your own risk.

---

### Post by TheFu on 2021-07-25
> **Frogs Hair said:**
> No, Chrome books are proprietary and don't allow other Linux operating systems to be installed. The only option is [coruton]("https://github.com/dnschneid/crouton") which is use at your own risk.

This isn't strictly correct.  Chromebooks have protections to block running other OSes, but those protections can sometimes be removed and a different boot firmware can be loaded to allow booting any CPU-compatible OS.  After making the physical changes to boot a different OS, chromeOS will never install or run on that system again.

I think that CPU isn't generally used, so there will be little effort put into supporting it by anyone other than the vendor.
I wouldn't buy any non-Intel chromebook and before I bought, if I were planning to run a Linux desktop, I'd do research on all the required steps for the specific device.  Every model is different.  Some models cannot run Linux.  Start here: [https://mrchromebox.tech/](https://mrchromebox.tech/)  Look for the exact model ... the ending 'a, b, c' matters too.  I don't see MT8183 in the supported devices, but I didn't look for any specific model - because none was provided.

BTW, I've run Ubuntu  with a lite window manager on 2 chromebooks beginning in 2012.  I played with Crouton in the beginning, but found it lacking in a key capability that I required.  I haven't used a chromebook in about 3 yrs. Cheap, used, off-lease, laptops without the massive limitations that all chromebooks have are much more capable and easily acquired where I live for 50% off the "new" price.  I switched from a nice, but limited Toshiba CB2 3550 ($430 - Core i3, 4G RAM, 16G storage) to an Asus laptop with 8G RAM, 1TB HDD, Core i5 and all the other normal laptop capabilities for $305. Over twice the performance, twice the RAM, ooodles more storage, for over $100 less money.

As tempting as chromebooks are, if you aren't already a Linux power user, I wouldn't suggest attempting this feat.  Get a cheap laptop instead. You'll be happier.

---

### Post by szegedin74 on 2021-07-25
...

---

### Post by TheFu on 2021-07-25
My knowledge could be out of date. The last time I had chromeOS on any of my devices was early 2016.

Chromebooks can work off-line.

Also, chromebooks have a "guest" login, so you don't need to have a gmail account to use it.  I ran crouton from a guest account about 3 months. Just have a USB flash drive to store any documents.

---

### Post by szegedin74 on 2021-07-26
...

---

### Post by TheFu on 2021-07-26
Again, my data could be out of date, but my Core i5 8th gen gets 8 hrs of battery, which is a little less than my 2015 Core i3 chromebook.
Neither has ever left me without power in the middle of a work day.  Most of the time, in power saving config under battery, the screen dims quickly and I think about the lowest I've seen either in typical use is 40% battery.

Of course, I'm not doing video transcoding on either of these.  For editing in a full-page text editor (avoid the GUI!!!!), I can't imagine power use being that much assuming you don't use a bloated DE or bloated editor.

Now, if you forget to plug in and recharge overnight - who's fault is that?

---

