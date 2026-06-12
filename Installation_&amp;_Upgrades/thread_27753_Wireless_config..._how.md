---
title: "Wireless config... how??"
date: 2005-04-17
forum: Installation &amp; Upgrades
---

### Post by telmo on 2005-04-17
Hi,
I want to install a costumized ubuntu warty instalation with the following:

Xorg
XFCE4
2.6.10-5-686 kernel
No Gnome

Kin of a lighter ubuntu.
But i have a problem. I need to configure wireless but without having to install 'anything' from gnome to configure the internet.

Is there a way i can configure wireless settings via text-mode?

thx.

---

### Post by telmo on 2005-04-17
Anyone??  :neutral:

---

### Post by bored2k on 2005-04-17
[QUOTE=telmo]Anyone??  :neutral:[/QUOTE]
 Warty installation with Xorg and 2.10 kernel ? Why not go with Hoary ?

---

### Post by telmo on 2005-04-17
Sound doesn't work properly with hoary. :S
I really need to install wireless in text mode. That's my main problem... but i don't see how i can solve it.  :-?

---

### Post by telmo on 2005-04-17
Ok, i managed to install ndiswrapper properly. I modprobed it and it's there! Now, what can i do to configure my ESSID and WEP KEY in the console and bring up the connection?

Anyone?

I tried 
```

iwconfig wlan0 mode Managed
iwconfig wlan0 essid (my essid)
iwconfig wlan0 key restricted (my wep key)
/etc/init.d/networking restart
```

But that's as far as i can go... :(

And when i reboot the wireless is not configured any more...  ](*,)

---

### Post by epb613 on 2005-04-20
[QUOTE=telmo]Ok, i managed to install ndiswrapper properly. I modprobed it and it's there! Now, what can i do to configure my ESSID and WEP KEY in the console and bring up the connection?

Anyone?

I tried 
```

iwconfig wlan0 mode Managed
iwconfig wlan0 essid (my essid)
iwconfig wlan0 key restricted (my wep key)
/etc/init.d/networking restart
```

But that's as far as i can go... :(

And when i reboot the wireless is not configured any more...  ](*,)[/QUOTE]
 I bet your missing the wlan0 entry from your /ect/network/interfaces file. Post the contents of it and I'll tell you what to add.

---

