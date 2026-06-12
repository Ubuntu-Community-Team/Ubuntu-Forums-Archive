---
title: "FireWire Ethernet?"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by Physicist on 2006-06-29
I am doing a fresh installation of Ubuntu 5.10 on my desktop Dell Dimension 9100
with an network adapter ``Intel(R) PRO/1000 PL Network Connection''. In the step of ``detect network hardware'' the Ubuntu installation pop up a window telling me:
 ``there is no ethernet hadware detected but there is a FireWire network interface detected, this is possible, but not likely......do you want to install firewire network interface?''
then it let me to select``yes/no'' if I selected yes, it further tell me that there is no driver and I need to install a module manually if I have it on my CD.... 

what should I do? Should I install 6.06 and burn it up and try with that?

---

### Post by Maggot on 2006-06-29
Personally...I'd install 6.06 seeing as you are just installing 5.10 and having an issue.

I think there was an issue with firewire conflicting with network cards.

---

### Post by syrphid on 2006-10-14
Well, I have exactly the same problem with 6.06,using the alternate CD. [Can't use the live CD version as no output from my Nvidia graphics card].

With an Abit VP6 mainboard with two PIIIs, I get "No Ethernet card was detected, but a Firewire interface is present..."
There is no Firewire interface, but I've given it a choice of 3 NICs with different chips and still get this result.
Sorry, but Ethernet interface is fine with Win2000 .

Just tried the CD in a Pentium I machine with 3C509B, and get same result!

Checked md5sum on the .iso, burned as slow as possible, Ubuntu install has checked the integrity of the CD as OK.

Any ideas please?

---

