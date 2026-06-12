---
title: "Install probs"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by postaldude32 on 2010-10-22
New to this linux stuff.  Heard good things about Ubuntu 10.10.  Tried it out on my sons computer, and it loaded well.  Decided to try it out on my computer, used USB to test it out, but it wouldn't get past the purple splash screen w/ Ubuntu in the middle of it w/ the little dots under it.  Even tried making cd instead, same outcome.  Any ideas?

---

### Post by Rubi1200 on 2010-10-22
Hi and welcome to the forums :)

Please post the specifications for the computer in question (and, as a bonus, those of your son's computer too if that is not too much trouble).

Thanks in advance.

---

### Post by postaldude32 on 2010-10-22
My computer is an olderemachine w/ a huge 40 gig HD.  Have about 2gig of mem.  Celeron processor. Has an Nvidia 8400 I think.  Sorry can't be more specific, Not at home.  Sons computer is an HP pavilion w/ 80 gig HD 2 gigs of mem. AMD proc. w/ ati radeon xpress 200 integrated graph.

---

### Post by Rubi1200 on 2010-10-22
You can try passing some parameters when the CD is booting and see if it helps:

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

Now hit Enter and hopefully you will be at the desktop on the LiveCD.

Let us know if this helps.

---

### Post by postaldude32 on 2010-10-22
Thank you for the quick response.  Will give it a shot as soon an I can.:)

---

