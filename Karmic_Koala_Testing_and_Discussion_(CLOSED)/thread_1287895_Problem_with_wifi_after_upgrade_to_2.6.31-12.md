---
title: "Problem with wifi after upgrade to 2.6.31-12"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mareczek1982 on 2009-10-10
Hi.. I have a problem with wifi on my DELL E6400 notebook.. I've upgraded ubuntu packages to kernel 2.6.31-12 and my wifi connection stopped working, NetworkManager detects wifi networks but I can't connect to network.. On 2.6.31-13 situation is the same..

lspci shows:
Network controller: Intel Corporation Wireless WiFi Link 5100

Have you got similar problems ?

---

### Post by mareczek1982 on 2009-10-11
I've hust installed compat-wireless drivers and WICD but problem is not resolved. On ubuntu 9.10 beta x64 live cd with 2.6.31-11 wifi works fine.

---

### Post by Sweevo on 2009-10-11
Hi

I'm not sure if your problem is the same as mine, but you could try the command which worked for me - the details are in the thread here: [http://ubuntuforums.org/showthread.php?p=8073026#post8073026]("http://ubuntuforums.org/showthread.php?p=8073026#post8073026") (Post number 4 has the command in which did the trick for me)

Hope it works for you too!

Sweevo

---

### Post by rex4u on 2009-10-11
Upgrade to .13 and see if it helps you.
Good luck...

---

### Post by mareczek1982 on 2009-10-11
I've just installed 9.10 beta with 2.6.31-11 on different disk in the same notebook. Then installed all updates. Wifi works fine with 2.6.31-13 #44.
I have the same kernel on original disk  but I can't connect to wifi networks, Network Manager detects network but there is no communication with AP. 
I don't want to perform fresh install on my original disk because I've made some customizations etc.. Maybe I can simply overwrite some config files on my original disk ?? 

Sweevo:
It's not a problem with WPA.. It doesn't work even on networks without encryption. Anyway thanks for info.

marek

---

### Post by Sweevo on 2009-10-11
No problem - I didn't actually say in my post, but I couldn't actually connect to any other wireless networks (even unprotected one's) before running that command, but maybe that was because Network Manager was trying to autoconnect to my WPA2 WLAN first.

After running that command and then disconnecting from my WLAN, I can then connect to any other wireless network.

---

