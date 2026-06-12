---
title: "wireless"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by PyrexKidd on 2010-01-06
I'm relatively new to Ubuntu and I'm having quite a bit of trouble getting my wireless card set up.

I've been using the tutorial on:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I'm using a BroadCom wireless PCI card.  chipset BCM4306 (ver3)
and the newest Ubuntu 9.x

In the process of following the instructions I ran the following command
```
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist
```
[FONT=monospace]
and I also found what looks like drivers on my Ubuntu install disk for my card, so I'm thinking that maybe I don't need the tutorial and Ndiswrapper to run the windows drivers.

--OR--

While I was Following the tutorial i used ndisgtk to install my drivers it recognized that I had a card and i can see the ssid of my router.

but i came up with an error that it could not verify if the card was present.  after clearing the error message the gui said card was present.

i installed bmcwl5.inf and bmcwl5a.inf and that's when the card recognized the network.

so i'm not sure where i need to go from here.  like I say I'm new to Linux 




also

how do i log into /root?

when i type ```
login
```
i get something like
```
can not log in without a valid root or something more linuxie
```


[/FONT]

---

### Post by neednewlaptop on 2010-01-06
You can try to find the type of wireless card by starting a terminal and entering

lshw -C network

---

### Post by PyrexKidd on 2010-01-07
what about running ubuntu inside windows?

---

