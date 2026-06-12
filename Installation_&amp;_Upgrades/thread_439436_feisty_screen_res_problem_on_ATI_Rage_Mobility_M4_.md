---
title: "feisty screen res problem on ATI Rage Mobility M4 AGP"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by barry.rhodes@uklidian.com on 2007-05-10
I've got a dell Inspiron 8000 laptop with ATI Rage Mobility M4 AGP card. The card is about 4 years old so should still be supported I think. All I get is 1024x768 and lower res. I know there are loads of posts on the forum on this and I've tried some of the things but no success. I've even installed feisty 3 times to see if the fix was in the install but it's not.

I've used the aticonfig and the dpkg-reconfigure option but still no success.

My screen goes up to 1600 and previous Linux installs, Ubuntu Breezy and Suse have all worked fine on install. I thought problems with screen res on X were a thing of the past.

Can someone please help - I'm ok with Linux and an experienced Linux user but this has me beat after 2 nights on this thing.

Barry

---

### Post by Wim Sturkenboom on 2007-05-12
Some points to check:
Driver installed
Driver selected in xorg.conf
Monitor vertrefresh and horizsync correct in xorg.conf
Resolutions specified in xorg.conf

---

