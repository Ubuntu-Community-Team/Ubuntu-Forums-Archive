---
title: "Upgrade to 14.4.1, then signing in problem."
date: 2014-08-29
forum: Installation &amp; Upgrades
---

### Post by lcwyche2 on 2014-08-29
I tried to clean install latest Ubuntu from ISO disc. Process went as slow as a lazy glacier. Decided to use ISO disc from April, and upgrade from there. This went OK. Then tried and discarded several of the more unusual desktop environments, including Bhodi and Plasma 5. Problem developed with sign in. When I input last character of my password the display changes to 'Guest Session'. This is before I press enter.

I format the sector this install was on. I re-install from the April ISO. While watching the install I notice that the word 'bhodi' is occurring. I add the kubuntu desktop. This works OK for a couple of days, except that the sound backend does not start.

Then just now I try to sign on. I get the bongo sound of welcome. Then the bug(?) has returned and I cannot sign in as me. 

Thanks for your help.

---

### Post by kansasnoob on 2014-08-29
Please post the full terminal output of:

```
cat /var/log/installer/media-info
```

---

### Post by lcwyche2 on 2014-08-30
loz@loz-Comp:~$ cat /var/log/installer/media-info
Ubuntu 14.04 LTS "Trusty Tahr" - Release amd64 (20140417)loz@loz-Comp:~$ 


Thanks

---

### Post by grahammechanical on 2014-08-30
When you install do you format that partition as part of the installation process? If not, then stuff from previous installations will get left behind.

---

### Post by lcwyche2 on 2014-08-30
Just after my earlier reply I realised that it referred to the system I am using now, not the system I am trying to install.
Has the super- slow installation for 14.04.1 been mentioned before? Has this been fixed?
Has the signing on problem occurred before?
I remember that on this occasion I did not use Gparted to format the partition before installation.

Thanks for your help

---

