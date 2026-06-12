---
title: "rt2870 in Intrepid?"
date: 2008-09-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Jackie999 on 2008-09-04
Anyone know where you find what new drivers etc will be included with the new ubuntu 8.10, Intrepid Ibex?
I could never get the rt2870 to work for me in Hardy and was hoping it would be in Ibex..or maybe even in Alpha5 ?

---

### Post by milanvora2 on 2008-09-05
can't answer if it will be included or not.
but i just installed a the 2870 drivers yesterday and got it to work very easily.
hwere did you get blocked ?

---

### Post by Crafty Kisses on 2008-09-05
> **Jackie999 said:**
> Anyone know where you find what new drivers etc will be included with the new ubuntu 8.10, Intrepid Ibex?
I could never get the rt2870 to work for me in Hardy and was hoping it would be in Ibex..or maybe even in Alpha5 ?

There will be from what I heard, I'm not sure though.

---

### Post by Jackie999 on 2008-09-05
Milanvora ...I compiled it quite a number of times and it seemed to go just fine..but the ra0 never showed up in iwconfig so I was stuck. I don't know enough to troubleshoot why it didn't work..all the posts I read seemed to suggest when you were done the install that the device would be present. I gave up trying and just ran a cat5 and can't try now since I'm now running on Alpha4.
I have another usb wireless I'm trying at the moment ...the AWUS036H (rtl8187) which wouldn't stay connected for very long - this was a bug that they are also working on.

---

### Post by garthberry on 2008-09-05
I have posted a patch [here]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/185193") for version 1.3.1.0 of the RT2870 driver from Ralink. The patch updates the driver so it compiles and functions on kernels > 2.6.26.

Cheers,

Garth

---

### Post by RaZoR1394 on 2008-09-13
> **garthberry said:**
> I have posted a patch [here]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/185193") for version 1.3.1.0 of the RT2870 driver from Ralink. The patch updates the driver so it compiles and functions on kernels > 2.6.26.

Cheers,

Garth

That's a great patch you've made. I was loosing hope as ndiswrapper didn't work. It's working quite well except I'm not getting speeds over 3MB/s.

---

### Post by Jackie999 on 2008-09-17
I'm not sure how to run the patch - I did try and got a load of errors. I'm taking all the Ibex updates and wonder if that's why? Can anyone supply a howto for it?
I got fed up running the cat5 across the floor to connect so tried the ndiswrapper again with the rt2870 and got freezing almost right away.
I have 2 usb wireless and am quite disappointed that neither work. The rtl8187 (with native driver) drops connections after a minute or two and requires a reboot to get it working again, there are bug posts about it but so far is useless. And the rt2870 with ndiswrapper freezes. I don't want to invest in another usb wireless only to find it doesn't work either. The devices work just fine in windows.

---

### Post by RaZoR1394 on 2008-09-17
If you would have searched for rt2870 you would have found my howto I did 4 days ago.

[http://ubuntuforums.org/showthread.php?t=919044&highlight=rt2870](http://ubuntuforums.org/showthread.php?t=919044&highlight=rt2870)

It works perfectly for me.

---

### Post by Jackie999 on 2008-09-17
Very nice how to RaZoR1394 ..you're right..I missed it.  I followed all the well laid out steps and still have no wireless device in iwconfig so I'm back where I started. I know it works for others ...I'm not sure what it is about my usb stick that it just doesn't want to work :(

---

