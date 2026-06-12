---
title: "Galaxium how to install?"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by Wanas on 2008-06-09
i need to know how to install Galaxium from the first step...... thanks

---

### Post by Orwell on 2008-08-06
Ok, I just did this so here goes....

First of all, navigate to /etc/apt/sources.list and open it.
Click the Third Party Software tab up the top...
Click the 'add' button and in the APT line box paste

 deb [http://ppa.launchpad.net/galaxium/ubuntu](http://ppa.launchpad.net/galaxium/ubuntu) hardy main
Then click 'add source'.

Now repeat this. Click 'add' and in the APT line box paste

 deb-src [http://ppa.launchpad.net/galaxium/ubuntu](http://ppa.launchpad.net/galaxium/ubuntu) hardy main

Once you've done that, head on over to Synaptic Package Manager and search for Galaxium. (You will probably need to update first) You should see it there in the list....

voila!

(sorry if this isn't as straight forward as you wanted, I'm new to this whole thing also and not used to giving tutorials ;) )

ps I neglected to include that at some stage it will warn you about installing third-party software...just so it doesn't freak you out ;)

---

### Post by Impocta on 2009-05-13
I did add the two repositry lines to sources.list
I did add the Public Key.
I did update/refresh synaptic.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package galaxium

And still the package can't be found. Could the PPA for Ubuntu Hardy Heron be broken or did I do something wrong?(I used the PPA from launchpad for ubuntu Hardy Heron)

---

