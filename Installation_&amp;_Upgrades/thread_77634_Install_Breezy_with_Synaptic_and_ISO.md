---
title: "Install Breezy with Synaptic and ISO?"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by Focx on 2005-10-17
Hi,

I currently have somewhat instable internet and no burner, so I downloaded the ISO (connection keeps failing, so I don`t want to use synaptic directly) and wonder if I can add the mounted iso to synaptic and upgrade offline that way?

thank you :)

---

### Post by grendel74 on 2005-10-21
I did it this way : 

#sudo mkdir /media/upgrade
#sudo mount -o loop ubuntu-5.10-install-i386.iso /media/upgrade

#sudo mv /etc/apt/sources.list  /etc/apt/sources.list.bak
#sudo vi  /etc/apt/sources.list

Insert the line : 

deb file:///media/upgrade breezy main restricted

Then : 

#sudo apt-get update
Cross your finger, here you go : 
#sudo apt-get dist-upgrade 

 Good Luck.

---

### Post by kevin_hill54 on 2005-10-21
WOW!!

How easy was that!!

30 minutes and we are rolling and not even a reboot.

I hope it all works still.

Let you know soon.

Kevin

---

### Post by almostlinux on 2005-10-25
wonderful ! grendel74 .. worked perfectly for me ! thanks a lot :)

---

### Post by ytseshred on 2005-10-25
After we have 5.10 installed as mentioned above, do we have to change the /etc/apt/sources.list to something that will get the 5.10 version of synaptic packages?

---

