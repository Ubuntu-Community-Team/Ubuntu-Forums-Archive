---
title: "How can i use my TV Card"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by xMoDx on 2008-05-29
i have ubuntu hardy,

i bought AverMedia,  AVERTV Hybrid+FM Cardbus any one could guide me how can i use this so i can watch TV using my Ubuntu Hardy..

---

### Post by didac on 2008-05-29
I recommend mplayer. Download it and type

mplayer tv://1

It comes with a manual explaining all the different options.

---

### Post by xMoDx on 2008-05-29
> **didac said:**
> I recommend mplayer. Download it and type

mplayer tv://1

It comes with a manual explaining all the different options.


there is no drivers that i should install? because when i insert my TVcard i get system hangup and i need to force boot it :(

---

### Post by xMoDx on 2008-05-29
someone from irc told me he used ndiswrapper , i would like to confirm from you guys if this is posible? the guy from irc wont tell me how exactly he made it work, :confused:

---

### Post by didac on 2008-05-30
Ah, that's worse!

Follow these links:

[http://ubuntuforums.org/showthread.php?t=263552](http://ubuntuforums.org/showthread.php?t=263552)
[http://gentoo-wiki.com/HARDWARE_avertv_cardbus](http://gentoo-wiki.com/HARDWARE_avertv_cardbus)
[http://www.mythtvtalk.com/forum/viewtopic.php?p=23286#23286](http://www.mythtvtalk.com/forum/viewtopic.php?p=23286#23286)

Check if you can make it work with:

```
sudo modprobe cx88xx card=6
sudo modprobe cx8800
```

or
```

sudo modprobe saa7134 card=85
sudo modprobe saa7134 card=85,99
```

Don't start recompiling your kernel yet.

But, if you cannot even boot with the card inserted, try this:

```
sudo gedit /etc/modprobe.d/saa7134
```

Enter the following line:

```
options saa7134 card=85,99
```

Save and reboot. Maybe you'll have to test card card=85 alone or the cx88x module. Looks like yours is going to be the saa7134 module.

---

