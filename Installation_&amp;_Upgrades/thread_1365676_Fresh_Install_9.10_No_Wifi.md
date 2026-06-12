---
title: "Fresh Install 9.10 No Wifi"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by Ishigawa on 2009-12-27
I've got 2 hp laptops with a different problems on each. I already posted my other dilemma.
This one is on my HP 2133 Netbook. I did a fresh install of 9.10 on it. It has Vista Business OS on it, so I used the install disc to partition the hard drive and made a dual boot machine out of it.
I can't get the wifi to turn on for it when in Ubuntu. Wifi comes on just fine into  Vista OS, but turns itself off when it boots into Ubuntu, and I can't get it to turn on.
Thanks for any help.

---

### Post by damianburrin on 2009-12-27
I had a similar problem with the HP/Compaq Mini 110c  In the hardware section there was an option for restricted drivers.  I found that using this for the wifi fixed the problem.  (the wifi card on my hp is one of the broadcom range)
 
HTH
Damian

---

### Post by Gramps on 2009-12-27
I'll bet it has a Broadcom wireless nic my Gateway netbook along with my Dell laptop both have the Broadcom wireless nic.

To get wifi to work on them I connected them to a ethernet network and did an update. After a reboot I was able to use System/Administration/Hardware Drivers to Activate the Broadcom drivers. You will need a connection to the internet to Activate them. After activation another reboot and wifi would them work after I picked my wifi from the list.

---

### Post by Ishigawa on 2009-12-27
Thanks everybody for the super fast replies! Sounds like this one might be easily enough taken care of! We have dsl at work, so I'll try it out in the morning. And yes, I believe that it is a broadcom. That sounds all too familiar.
Thanks again. I'll repost and let you know if that takes care of it tomorrow.

---

### Post by dantm on 2009-12-30
Is there a way to do an update without having hard wired ethernet connection?  We're in a college dorm and the wifi is centralized for the building; there are now wired connections.
 
Thanks!

---

### Post by Ishigawa on 2010-01-16
Just now got a chance to reply. That did fix the problem. Thanks for the help!

---

