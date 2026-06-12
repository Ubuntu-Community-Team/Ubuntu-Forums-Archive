---
title: "no internet after upgrade"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by silent380 on 2010-11-08
I just upgraded to karmic koala and now i can't connect to the internet. Am running dual boot with vista and it works fine, it's just ubuntu that has the prob. If anyone can help I'd greatly appreciate it as I've grown fond of ubuntu and would rather keep using it than go back to windows. Thanks in advance.

---

### Post by Frogs Hair on 2010-11-08
What type of connection do you use and is there any connection type showing in the Network Connections GUI on the preferences menu ? If not , it can be added there.

---

### Post by silent380 on 2010-11-08
I'm connected using a wireless network, if thats what you meant, but i do see the network on my gui and when i click to connect it just tries for a little while and then says that I'm disconnected. Once it did connect but immediately disconnected.

---

### Post by sindahir on 2010-11-09
After the upgrade I had also problems to connect to my wireless network. Doesn&#7831; matter if it was secured by wep or open. It tries to connect and then came back with wrong password (when encrypted) or only disconnect (when connect to a open network)

This did the trick for me on a Toshiba Tecra 9100, Intel wireless card (driver= orinoco_cs):

[http://ubuntuforums.org/showthread.php?t=1593250&page=3](http://ubuntuforums.org/showthread.php?t=1593250&page=3)

---

### Post by TBABill on 2010-11-09
Was this wireless device working previously (before upgrade) in Ubuntu? If so, do you recall having to take any extra steps to enable it or download a proprietary driver?
 
Which model card is it? Post the output of ```
lspci
``` and within that output should be the model of your card.

---

### Post by silent380 on 2010-11-16
> **TBABill said:**
> Was this wireless device working previously (before upgrade) in Ubuntu? If so, do you recall having to take any extra steps to enable it or download a proprietary driver?
 
Which model card is it? Post the output of ```
lspci
``` and within that output should be the model of your card.
 Everything was working fine before. I don't think I had to do anything special last time but if i did I had a working connection. I have an Atheros card I believe. I hope that helps if you need more info just let me know.

---

### Post by silent380 on 2010-11-17
O.K so I got fed up with waiting on windows all the time so I decided to just wipe ubuntu off my drive and start again. This time I installed meerkat. Now I got an "error 15"
I am starting to wonder if I should keep trying, been at it all day now. Can't seem to find anything on here that helps. Someone pleez help before i give up!

---

### Post by RJARRRPCGP on 2010-11-17
Sorry, looks like you have to wipe all partitions and start over.

---

### Post by silent380 on 2010-11-17
O.K I solved my problem. Simply reformatted partition and reinstalled meerkat and VOILA! no more grub error and internet works. Thnx 4 yor help everyone

---

