---
title: "Upgrade 10.10 to 14.04.5 via Unetbooting"
date: 2015-04-20
forum: Installation &amp; Upgrades
---

### Post by KBL on 2015-04-20
I handled this quite well I thought. Went through the process. All seemed go and got the prompt at end to reboot.
After rebooting it still boots up in 10.10 and I cannot find 14.04.5 anywhere.

Where do I start?

---

### Post by Impavidus on 2015-04-20
I don't get it. 10.10 is old, dead & buried and has been unsupported for 3 years, 14.04.5 will be released in July 2016 and no direct upgrade from 10.10 to 14.04 is supported. I suggest a clean install of 14.04.2.

---

### Post by slickymaster on 2015-04-20
> **Impavidus said:**
> I don't get it. 10.10 is old, dead & buried and has been unsupported for 3 years, 14.04.5 will be released in July 2016 and no direct upgrade from 10.10 to 14.04 is supported. I suggest a clean install of 14.04.2.
+1
Please have a read at the [Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop]("http://ubuntuforums.org/showthread.php?t=2229730") sticky.

---

### Post by KBL on 2015-04-20
That could well be my problem then.
I had no choice but to go down the Unetbooting root as DVD won't boot and no USB boot available. 
May be I should have gone for a lower spec version then onto 14.04.5?

Ok, guess I should go through the Lubuntu or Xubuntu Unetbooting root.

I'll let you know how it goes.

Thanks.

---

### Post by KBL on 2015-04-21
Ok, I have tried Unetbooting to install kbuntu, Xbuntu and 12.04.5 but still it boots in 10.10 Maverick Meerkat.

What is happening?

---

### Post by dino99 on 2015-04-21
you probably needs to clean the room, as it seems that the old grub (aka grub-legacy, grub1) is still around with its menu.list: purge them all (menu.list, grub*) and install back grub-pc on /dev/sda (sudo grub-install /dev/sda)

---

### Post by KBL on 2015-04-21
Ok, thanks.
Just how do I go about doing that?
Sorry, but still in a learning curve.

---

