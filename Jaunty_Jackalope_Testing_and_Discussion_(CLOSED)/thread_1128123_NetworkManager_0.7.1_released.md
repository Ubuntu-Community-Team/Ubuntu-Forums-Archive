---
title: "NetworkManager 0.7.1 released"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jmmL on 2009-04-17
This is where I found out about it: [http://www.phoronix.com/scan.php?page=news_item&px=NzIxMA](http://www.phoronix.com/scan.php?page=news_item&px=NzIxMA)

The version installed in jaunty appears to be 0.7.1~rc4.1.cf199a964-0ubuntu2.

Does anyone know how many of the [improvements]("http://blogs.gnome.org/dcbw/2009/04/16/you-will-upgrade-to-networkmanager-071/") this version contains? I'm specifically interested in the power saving changes.

---

### Post by amano on 2009-04-17
There won't be any improvements or just minor bug fixes between RC4 and final. Just assume that there is already 0.7.1 installed.

---

### Post by jmmL on 2009-04-17
That's a shame; I haven't noticed the power savings!

Oh well, I'm sure folks with mobile broadband plans will be appreciative.

Oddly the "about" listing for NetworkManager still lists the version as 0.7.0.100

---

### Post by Polygon on 2009-04-17
hopefully this makes it so i can actually USE wifi on my laptop with any version of linux installed (ubuntu or arch).

now, hopefully by the time i get home its already updated in the arch repos

---

### Post by tad1073 on 2009-04-17
The update to 0.7.1 messed up wireless, again.

---

### Post by paradigm2 on 2009-04-17
> **tad1073 said:**
> The update to 0.7.1 messed up wireless, again.

My wireless has been messed up as well.  Usually if I disconnect the ethernet cable it will fallback to wireless automatically.  Now I am noticing that it isn't doing that and I cannot connect.  Not a big deal for me because I use eth0 on this computer but it shouldn't happen and I should probably fix it.

---

### Post by tad1073 on 2009-04-17
> **paradigm2 said:**
> My wireless has been messed up as well.  Usually if I disconnect the ethernet cable it will fallback to wireless automatically.  Now I am noticing that it isn't doing that and I cannot connect.  Not a big deal for me because I use eth0 on this computer but it shouldn't happen and I should probably fix it.

My problem with NM is that the signal strength drops in and out especially when other networks are detected. It is like it can't differentiate between signals.

---

### Post by crjackson on 2009-04-17
> **tad1073 said:**
> My problem with NM is that the signal strength drops in and out especially when other networks are detected. It is like it can't differentiate between signals.

Yeah, I'm seeing that took. Totally bites...

---

### Post by Sarvatt on 2009-04-18
> **jmmL said:**
> This is where I found out about it: [http://www.phoronix.com/scan.php?page=news_item&px=NzIxMA](http://www.phoronix.com/scan.php?page=news_item&px=NzIxMA)

The version installed in jaunty appears to be 0.7.1~rc4.1.cf199a964-0ubuntu2.

Does anyone know how many of the [improvements]("http://blogs.gnome.org/dcbw/2009/04/16/you-will-upgrade-to-networkmanager-071/") this version contains? I'm specifically interested in the power saving changes.



[http://cgit.freedesktop.org/NetworkManager/NetworkManager/log/?h=NETWORKMANAGER_0_7](http://cgit.freedesktop.org/NetworkManager/NetworkManager/log/?h=NETWORKMANAGER_0_7)

Theres a list of all the changes on the 7.1 branch. just assume everything above the 7.1rc4 tag in yellow isn't in ubuntu's version :)

---

### Post by garba on 2009-04-18
networkmanager... amateurish stuff at its best... those having problems with "networking" don't even realize (im talking about the less experienced users) that at a low level everything is ok and would actually work but it's nm's fault if they can't get their connection to work... 

"my wireless doesnt work" often translates to "i cant get nm to configure my wireless adapter"

rant over

---

