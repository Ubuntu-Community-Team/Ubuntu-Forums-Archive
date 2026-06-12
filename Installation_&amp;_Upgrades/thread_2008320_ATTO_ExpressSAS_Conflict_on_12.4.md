---
title: "ATTO ExpressSAS Conflict on 12.4"
date: 2012-06-22
forum: Installation &amp; Upgrades
---

### Post by jackstrat357 on 2012-06-22
I had ATTO SAS modules (ExpressSAS Adapters) running on Ubuntu 10.4 for two years now. Upgraded to 12.4 and now there are issues. There is a known conflict between the ATTO SAS driver and the PM8001 driver. Here's what I did to work around it. I'd like to compare notes...

1) I disabled the ATTO driver in the BIOS via a setting in the ATTO card NVRAM. Now the BIOS doesn't hang.

2) The ATTO driver installer renames the pm8001.ko driver to pm8001.bkup. A cheap way to black list it - however even with the pm8001 driver removed, after boot-up the driver is still loaded. How it got there I don't know.

3) After booting I can 'rmmod pm8001' then 'insmod esas2hba' then I'm in business.

There must be a better solution. Is grub loading the pm8001 driver? Every three or four boots the boot-up hangs with a blank pink/orange Ubuntu screen. Looks like something bad is happening in grub.

Anyone dealing with this?
thx, Jack.

---

### Post by SebastianMWS on 2012-09-02
Hello Jack,

I realize that I'm bumping a pretty old thread (unanswered, on top of that), but nevertheless - did you try to fix the problem by following instructions on ATTO website ?

Here's the link (scroll all the way down, to a paragraph titled "ATTO 6Gb ESAS HBA & Linux kernel 2.6.33 [FONT=&quot][/FONT]  ").

Url: [http://www.attotech.com/support/trouble/linux.html](http://www.attotech.com/support/trouble/linux.html)

In case you solved the issue in the meantime, I'd be interested to know was was the ultimate workable solution for you - using the Kernel driver pm8001.ko, or ATTO driver esashba2 ?

Kind regards,

Bostjan

---

