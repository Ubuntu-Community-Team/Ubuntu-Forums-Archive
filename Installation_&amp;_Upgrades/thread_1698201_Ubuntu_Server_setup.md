---
title: "Ubuntu Server setup"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by sentinal822 on 2011-03-01
I've been looking for the last few days for a good how to on setting up a home server using Ubuntu 10.10. I have found several and looked them over and have installed the server on to a system and started to get it setup. now though I cannot access anything via http, even the php info. I want to start from scratch on this but would like a little help on finding the best tutorial on how to do this. The idea on what I plan to do is set it up to be able to hold mp3's on and allow them to be downloaded or played on other computers on the home network. Also will be looking to setup to have other items done as well such as a database that can accessed. I would like to be able to use both Http and Ftp on this if possible. Can someone give me some suggetions?

---

### Post by coffee412 on 2011-03-01
> **sentinal822 said:**
> I've been looking for the last few days for a good how to on setting up a home server using Ubuntu 10.10. I have found several and looked them over and have installed the server on to a system and started to get it setup. now though I cannot access anything via http, even the php info. I want to start from scratch on this but would like a little help on finding the best tutorial on how to do this. The idea on what I plan to do is set it up to be able to hold mp3's on and allow them to be downloaded or played on other computers on the home network. Also will be looking to setup to have other items done as well such as a database that can accessed. I would like to be able to use both Http and Ftp on this if possible. Can someone give me some suggetions?


I would suggest loading one of the desktop versions and then adding what you need. 

Sharing to windows? ---> install and config samba
Sharing to other linux boxes? ---> use nfs
ftp server? ---> proftp

turn off what you dont need like sendmail.

my 2 cents anyways....

coffee

---

### Post by sentinal822 on 2011-03-02
THanks.  I have Samba installed.  Not sure on exactly how to set it up.  I do have the ftp setup as well but not sure of all the settings.  Before i made a few changes I was able to get to the default webpage by entering in my servers ip address but now it just does page cannot be displayed.  Any ideas on this?

---

### Post by Red Kelly on 2011-03-04
I have written a tutorial for 10.04 it should be the same for 10.10 it includes samba in it as well as dhcp and network bridging. It is being moderated now don't know when it will come online.

Edit: here it is: [http://ubuntuforums.org/showthread.php?t=1697503&highlight=home+server+tutorial](http://ubuntuforums.org/showthread.php?t=1697503&highlight=home+server+tutorial)

---

