---
title: "Lost wireless on upgrade"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by CowDoctor on 2010-01-27
Dear Friends,
   New and ignorant here.  I got a new System 76 netbook, love it, went to upgrade Ubuntu and since, have not been able to get wireless to work.  Wireless light is off, no switches work to activate.  Unit has no CD drive, can't get on internet without connection. Not sure this is the correct forum.   What can I do?
Yours hopefully,
Joe Snyder

---

### Post by stim on 2010-01-27
try system->administration->hardware drivers and see if your wireless card is activatable(?) through there.  If not.....plug it in to the wired network, run these commands in terminal

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

then reboot, and try. post back with the results of the command before rebooting.

---

### Post by CowDoctor on 2010-01-31
Sorry this took so long.  Not easy access to hard wired network.  After the command, it loaded a lot of stuff.  Final words:
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
OK to reboot?
Thanks,
Joe

---

### Post by stim on 2010-01-31
yup, give it a reboot and check system->administration->hardware drivers.

---

### Post by CowDoctor on 2010-01-31
stim,
   Well, sadly, still tells me no drivers found.  Still not wireless light, nor response to keyboard or mechanical switches??  What next?
Thanks for trying,
Joe

---

### Post by CowDoctor on 2010-09-06
Dear Friends,
   If you can look at the previous messages on this thread, I still have this nice netbook that is basically a really expensive doorstop as no wireless access.  I would really like to get it fixed so I can use it.  ANY help would be welcome at this point.
Yours hopefully,
Joe

---

### Post by KasRoth on 2010-09-07
I'm a new user too, you can see my driver problem in the unanswered thread below yours. Basically I ended up going to [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) and put that on a USB drive. When the startup began I hit f2 and did a full install where i rewrote everything. 

Then I got to a wired connection and used that code that was listed above. I waited a while still wired and then I installed two drivers after my restart, I could then find the wireless and it WORKS!  Hope you have some luck too! I can try to help you if you like. I'm learning this slowly.

---

### Post by DilbertDave on 2010-09-09
I don't normally like posting links to other Q&A sites in forums but considering the length of time that has past since you originally posted I'll make an exception.

Try asking your question in [http://ubuntu.stackexchange.com](http://ubuntu.stackexchange.com) - if you do get an answer then be sure to post it back here so that others can benefit from it.

[Moderators: if this is deemed as inappropriate then please feel free to delete, I'm just trying to help :D]

---

### Post by lechien73 on 2010-09-09
Could you post the output of:

```
lspci
```

to tell us what wireless network card you have? You may have to install the Lucid backports, which contain the compat-wireless package.

---

### Post by CowDoctor on 2010-09-12
Dear Friends,
    Thanks for all the suggestions, questions, and good ideas.  I managed to get in touch with a tech assistant from System 76 who walked me through a series of trials and errors that finally resulted in a working netbook ... so for now, problem solved.
    I see, however, that Ubuntu wants me to download a newer version.  Dare I try it?  
Yours gratefully,
Joe

---

