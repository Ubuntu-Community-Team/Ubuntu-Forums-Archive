---
title: "remove install to disk option from live cd"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by getglenn on 2009-11-25
i want to give my co-workers a copy of the ubuntu live cd but would like to remove the 'install to disk' option from the menu...

the reason being, i would rather be there to guide them when/if they decide to install to hard disk, to avoid any problems

i am aware of some ways to 'remaster' an install cd but have not had any luck with them in the past...

i'm hoping there is a simple method and would appreciate any help or suggestions that point me in the right direction

many thanks
glenn o

---

### Post by presence1960 on 2009-11-25
> **getglenn said:**
> i want to give my co-workers a copy of the ubuntu live cd but would like to remove the 'install to disk' option from the menu...

the reason being, i would rather be there to guide them when/if they decide to install to hard disk, to avoid any problems

i am aware of some ways to 'remaster' an install cd but have not had any luck with them in the past...

i'm hoping there is a simple method and would appreciate any help or suggestions that point me in the right direction

many thanks
glenn o

you want to take all the fun out of it. Some of my best learning experiences were the result of a bonehead move on my part. You can't control people nor can you be there to hold hands every step of the way. Allow them the same opportunities you have enjoyed. There is a difference between "support" and "control".

---

### Post by jessiebrownjr on 2009-11-25
> **presence1960 said:**
> you want to take all the fun out of it. Some of my best learning experiences were the result of a bonehead move on my part. You can't control people nor can you be there to hold hands every step of the way. Allow them the same opportunities you have enjoyed. There is a difference between "support" and "control".

This is similar to what I was going to say... You are being over protective here. if a simple suggestion to wait for your guidance doesn't keep them from clicking install, then by all rights they can't be mad at you for the results. heck when I was a child;the only way I learned about computers was to break/fix things in that order :-)

GJ on sharing the Ubuntu experience though!

---

### Post by darkod on 2009-11-25
In case you still decide trying to do this, I might give a suggestion. I haven't tried it myself but while looking inside the ubuntu 9.10 ISOs and trying to put both 32bit and 64bit version install files on the same usb stick, I noticed the following:
The Ubuntu Main Menu (the text part) seems to be in the folder isolinux in the file text.cfg. In that file you can clearly see the menu items for Try Ubuntu, Install Ubuntu, etc. I guess if you delete Install Ubuntu entry and recreate a CD/ISO with that modified text.cfg it should remove the option from the menu.

---

### Post by jessiebrownjr on 2009-11-29
> **darkod said:**
> In case you still decide trying to do this, I might give a suggestion. I haven't tried it myself but while looking inside the ubuntu 9.10 ISOs and trying to put both 32bit and 64bit version install files on the same usb stick, I noticed the following:
The Ubuntu Main Menu (the text part) seems to be in the folder isolinux in the file text.cfg. In that file you can clearly see the menu items for Try Ubuntu, Install Ubuntu, etc. I guess if you delete Install Ubuntu entry and recreate a CD/ISO with that modified text.cfg it should remove the option from the menu.

There is an option to install it from the live version of Linux once you boot it too

---

