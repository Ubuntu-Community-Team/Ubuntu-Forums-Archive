---
title: "Live CD and USB problems with T41"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by goseph on 2010-06-12
Hi everyone!

I am trying to install Ubuntu on an IBM T41 think pad but I am having problems booting, I have created successful live CDs and live USBs that work on other computers. Withe the Live USB - I get simply "Boot Error" when I select it as the boot device, when I select the Live CD I get a flashing cursor for about 5 minutes and then eventually I get GRUB as if the CD wasn't there.

Possibly related:
I have replaced the original (windows) HD with a slightly larger one with an older pre-installed Ubuntu.

Can anybody help!!

---

### Post by Rubi1200 on 2010-06-12
What kind of graphics card do you have?

Are there any error messages at the GRUB screen?

Which version are you trying to install?

I will assume Lucid, but the more information you provide the better people here can offer help.

---

### Post by goseph on 2010-06-12
lshw tells me:
*-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon Mobility M7 LW [Radeon Mobility 7500]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm bus_master cap_list
                configuration: latency=66 mingnt=8
                resources: memory:e0000000-e7ffffff(prefetchable) ioport:3000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff(prefetchable)




There are no error messages, I am working in Karmic 9.10 and attempting to do a fresh install of 10.04, not an upgrade. I guess I am hoping to do a fresh install because I have edited loads of things and installed things and I want a fresh start.

Thankyou for speedy response!

---

### Post by Rubi1200 on 2010-06-12
Are you trying to install on a separate drive?

This may or may not be of use:

[http://ubuntuforums.org/showpost.php?p=9239795&postcount=19](http://ubuntuforums.org/showpost.php?p=9239795&postcount=19)

I hope this helps.

In my opinion, if you are satisfied with Karmic and it works for you, it might be better to wait until the bugs are ironed out in Lucid before making it your main system.

---

### Post by goseph on 2010-06-12
Same Drive, I don't even get as far as the Ubuntu Logo, is it likely this will be fixed by 10.04.1?

---

### Post by Rubi1200 on 2010-06-12
That is odd that you don't even get to the Ubuntu logo! Hmm, not sure what to suggest now.

As far as the next release in October (10.10), I cannot say whether or not these issues will be resolved by then.

Keep searching the forums for answers and hopefully someone will have an answer for your particular setup.

:-)

---

### Post by goseph on 2010-06-12
ok, thankyou for trying :D I love this community

---

