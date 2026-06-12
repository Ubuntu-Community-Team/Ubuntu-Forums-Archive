---
title: "64bit flash player needed in karmic?"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bwallum on 2009-09-21
Hi

I used the 64bit libflashplayer.so alpha file from adobe labs in jaunty. I have just set up karmic and now need to install a flash player.

The reason I used the 64bit player was because of conflicts with ndiswrapper and nvidia drivers (185).

I have the latest 64bit libflashplayer.so (from libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz) but forget where it should go. Can you tell me which folder to put it in please?

---

### Post by Vaun on 2009-09-21
```
sudo cp -r libflashplayer.so /usr/lib/mozilla/plugins/
```

:)

---

### Post by bwallum on 2009-09-21
Thanks Vaun, hole in one!

---

### Post by itismike on 2009-10-20
Tried it but now FF crashes as soon as a Flash page is opened.  
Other resources have specified different directories for this:
/usr/lib64/firefox/plugins

Anyone know a good resource for Karmic 64 bit?

---

### Post by pferraro on 2009-10-20
> **itismike said:**
> Anyone know a good resource for Karmic 64 bit?

Try this ppa:
[https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)
ppa:sevenmachines/flash

---

### Post by novafluxx on 2009-10-20
> **itismike said:**
> Tried it but now FF crashes as soon as a Flash page is opened.  
Other resources have specified different directories for this:
/usr/lib64/firefox/plugins

Anyone know a good resource for Karmic 64 bit?

Try:
```
/usr/lib64/mozilla/plugins
```

---

### Post by libihero on 2009-10-20
after i add those repositories, what do i download to make the 64 bit flash work?

---

### Post by bwallum on 2009-10-20
> **libihero said:**
> after i add those repositories, what do i download to make the 64 bit flash work?

This is a good how to:
[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html)

Basically:-
Close browser and Rremove any flash players.
Download the file and extract libflashplayer.so file.
Place the file in the /.mozilla/plugins/ folder. If necessary make the plugins folder.
Remove nspluginwrapper using the Synaptic Package Manager.

---

