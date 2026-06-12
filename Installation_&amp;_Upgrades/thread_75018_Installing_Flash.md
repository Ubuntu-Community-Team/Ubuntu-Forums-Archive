---
title: "Installing Flash"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by mit on 2005-10-13
Hi,

I have downloaded it and extracted the folder to the desktop. I have read i need to copy libflashplayer.so into the mozilla plugins directory.

The question is how do i do this? I have looked everywhere from within the browser. I assume it is from the terminal? Nothing is in Synaptic manager.

Thanks for looking.

---

### Post by last1 on 2005-10-13
Isn't that kind of, the complicated way of doing it? Cause all I did was enable all the repositories and select the flashplayer-mozilla package inside of Synaptic. You should be able to enable the repos by clicking settings >repositories > add, then check the boxes for community maintained and non-free.

---

### Post by mit on 2005-10-13
Hi,

I can't find any mention of flash in synaptic and i am up to date. Sorry must be missing something, i am still on the long learning curve. :D

---

### Post by az on 2005-10-13
Flashplugin-nonfree and the other flash package is in the multiverse repository.

---

### Post by mit on 2005-10-13
Hi,

I have installed the multiverse but cannot find any flash plug in's sorry. :(

---

### Post by aclaunch on 2005-10-13
To answer your question the plugin directory is in /usr/lib/mozilla-firefox/plugins/. The command is "sudo cp /location/of/libflash.etc /usr/lib/mozilla-firefox/plugins/". You may need to restart  firefox and then you can check by entering "about:plugins" in the URL/address bar.

Good Luck,
Alan

---

### Post by mit on 2005-10-14
Thanks Alan, will give that a go later. :)

---

