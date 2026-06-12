---
title: "No network manager gui in Intrepid"
date: 2008-09-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by psychobillyjekyll on 2008-09-12
I did a dist-upgrade last night and everything went fine, until after the reboot. I usually have to use the Network Manager GUI in Xubuntu to get perform a ip-release and renew, which gets my Intel 3945 wifi card to work properly. I am able to see the wifi card on iwconfig and can see the SSID, here is the exact output, with the encryption key blocked out.

> eth1 IEEE 802.11abg ESSID:"ckmja"
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=0 dBm
Retry min limit:7 RTS thrff Fragment thr=2352 B
Encryption key:****-****-****-****-****-****-** Security modepen
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Is anyone else having this problem or know how to fix it? 

Thanks
Justin

---

### Post by psychobillyjekyll on 2008-09-14
I am going to try a fresh install as soon as the new image downloads. I will report back on any further difficulties.

Justin

---

### Post by psychobillyjekyll on 2008-09-15
Still no connections with the wifi card. Ubuntu sees the card, but it refuses to connect to my wireless network. I have a network manager now, by the way. I have tried the iwconfig method of setting the key. I have tried the network manager method, as well. I would have thought that the Intel 3945 issues were resolved, since it had worked flawlessly since Feisty, but I guess not.

---

### Post by diebels on 2008-09-15
> **psychobillyjekyll said:**
> Still no connections with the wifi card. Ubuntu sees the card, but it refuses to connect to my wireless network. I have a network manager now, by the way. I have tried the iwconfig method of setting the key. I have tried the network manager method, as well. I would have thought that the Intel 3945 issues were resolved, since it had worked flawlessly since Feisty, but I guess not.

It's not the iwl3945 bug with workaround disable_hw_scan=1 ?

---

### Post by psychobillyjekyll on 2008-09-15
Can you point me to a link so I can check?

Thanks for the reply.
Justin

---

### Post by Nullack on 2008-09-16
To clarify are you on Ubuntu or Xubuntu?

---

### Post by psychobillyjekyll on 2008-09-16
I started out in Xubuntu and when I did my fresh install I switched back to gnome Ubuntu. So the no GUI part was in Xubuntu, but that has been fixed. I have a GUI from the fresh install, but I still cannot connect to my wireless network. I am having the same trouble that is in this post: [http://ubuntuforums.org/showthread.php?t=917274]("http://ubuntuforums.org/showthread.php?t=917274"). I am trying to figure out how John did this "manually" considering I have tried the iwconfig terminal commands. The files he attached in his one post are exactly the same as the way my files look now. I have sent him a PM and am awaiting his reply. If anyone else knows how he might have done this, by all means, let me know.

Thanks and sorry for the long post
Justin

---

