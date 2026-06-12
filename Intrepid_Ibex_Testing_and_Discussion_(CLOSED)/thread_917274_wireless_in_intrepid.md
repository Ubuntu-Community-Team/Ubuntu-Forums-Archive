---
title: "wireless in intrepid"
date: 2008-09-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by johnn1949 on 2008-09-11
intel pro wireless 3945-iwl3945

When I have Hardy installed the network icon sees no wireless networks,I have to click connect to another network and fill in the blanks.  Then it connects if I wave the laptop around until it connects.

In Intrepid it sees the networks and connects almost immediately.  

Is there a difference in the way the Ubuntu versions handle wireless or do you think it just isn't installed right in Hardy?

I haven't made any changes to the default installations in either.

Thanks 
John

---

### Post by Nullack on 2008-09-12
Its due to the new approach in network manager, please refer to the alpha release notes RE what is new and also a thread here in this forum

---

### Post by johnn1949 on 2008-09-12
"iwlist scan" before and after connecting in Hardy

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results


Attachments are before and after connecting manually

---

### Post by johnn1949 on 2008-09-12
Thanks Nullack,

Now I can just wait for Intrepid to get better.

---

### Post by nanog on 2008-09-12
Hardy uses 0.66 which is a minor revision of 0.6. Intrepid uses 0.7 which includes a major rewrite and support for lots of new drivers. 

There is an 0.7 package available for hardy [here]("https://launchpad.net/~network-manager/+archive").

Add the appropriate repo to you sources.list, upgrade, and install network manager and the applet.

Be aware that this may hose your network. You can fix this by removing 0.7 and installing your chached 0.66 network manager.

---

### Post by psychobillyjekyll on 2008-09-15
John, Can you tell me how you connected manually? I am having the same trouble you did, with the same wifi card. 

Thanks
Justin

---

### Post by duksandfish on 2008-09-15
I have a question, does/ will the Atheros 5007EG wifi card work out of the box with Intrepid? (some people have managed to get it working in Hardy, though i have not...). I would dowload a live cd but my internet has been playing up recently..... But if it does, then that would be great as it is the only thing really holding me back from setting up an ubuntu and xp dual boot (using mandriva atm as it is the only linux distro that works with the 5007EG)

---

### Post by GuitarRocker2562 on 2008-09-15
Download the torrent, this way if your connection fails it is no problem.

---

### Post by Gina on 2008-09-15
I've found the current version of Firefox continues the download after a power cut and restart.  I'm not sure when it started doing this - it certainly didn't used to.

---

### Post by inportb on 2008-09-15
> **duksandfish said:**
> I have a question, does/ will the Atheros 5007EG wifi card work out of the box with Intrepid? (some people have managed to get it working in Hardy, though i have not...). I would dowload a live cd but my internet has been playing up recently..... But if it does, then that would be great as it is the only thing really holding me back from setting up an ubuntu and xp dual boot (using mandriva atm as it is the only linux distro that works with the 5007EG)

The ath5k driver does not fully support the Atheros 5007EG so no, it does not work fully out of the box. Madwifi-ng still works on Hardy and Intrepid, though; just follow the instructions and blacklist ath5k in Intrepid. I also [got injection working]("http://www.inportb.com/2008/07/27/madwifi-support-for-ar5007-ar2425-with-injection-aircrack/") quite easily.

---

### Post by BC7333 on 2008-09-15
> **johnn1949 said:**
> intel pro wireless 3945-iwl3945

When I have Hardy installed the network icon sees no wireless networks,I have to click connect to another network and fill in the blanks.  Then it connects if I wave the laptop around until it connects.

In Intrepid it sees the networks and connects almost immediately.  

Is there a difference in the way the Ubuntu versions handle wireless or do you think it just isn't installed right in Hardy?

I haven't made any changes to the default installations in either.

Thanks 
John

After fiddling around for months with Intrepid and getting a lot of hangs that I think are somehow network related, I reverted to Hardy, but instead used ndiswrapper (why didn't I think of that before..) with my 3945..  Having better luck than before with network manager 0.7 now also working well.

As dumb as it sounds, I remember well waving my laptop around to get it to connect ;) strange but true..

---

