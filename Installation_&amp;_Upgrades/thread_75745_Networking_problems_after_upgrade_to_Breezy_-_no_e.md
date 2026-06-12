---
title: "Networking problems after upgrade to Breezy - no eth0"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by scottishparrothead on 2005-10-14
I'm on a Cybermaxx laptop with built in wireless networking.  Hoary worked fine - no issues with wireless networking.

I upgraded to Breezy using CD and the synaptic package manager.  Since reboot eth0 cannot be found.  This is the output from ifconfig eth0:

eth0: error fetching interface information: Device not found

It was definitely eth0 that was in use when Hoary was working.

Any help appreciated!

---

### Post by Elitist_Phoenix on 2005-10-14
yeah, i'm sorta having the same problem. no eth0. card works fine, worked in slackware 10. don't think it was even auto detected. tried ifconfig but, though I'd ask here before I go fiddling with stuff i no nothing about :P

---

### Post by shenki on 2005-10-14
what wireless card are you using? If you don't know, type:

cd
lspci > lispci.txt

and attach the resulting file 'lspci.txt' from your home dir.

---

### Post by GigaShadow on 2005-10-15
I found that while eth0 was present (as was eth2), there was no IP, Subnet or Default Gateway information present. Interestingly enough, my DNS (Adelphia cable) stayed intact. So, I simply re-input the requisite information and I am back online! No muss, no fuss, not even a broken fingernail! :-) lol 

I have read all of the Breezy update info and, I guess that I can consider myself lucky as other than my net connection all else is working just fine!!!!   <bg>


                     G  :-)

---

