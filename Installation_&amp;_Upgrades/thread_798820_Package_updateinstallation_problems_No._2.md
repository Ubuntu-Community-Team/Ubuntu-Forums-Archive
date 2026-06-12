---
title: "Package update/installation problems No. 2"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by CJ_Hudson on 2008-05-18
Hi, 
after solving my initial updates installation problem successfully using:

apt-get dist-upgrade

 I now have another one generated when I tried to install a video codec thingy from here:

[https://help.ubuntu.com/community/RestrictedFormats/StreamingVideo](https://help.ubuntu.com/community/RestrictedFormats/StreamingVideo)

...and the error I get is:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

(The intial:

sudo apt-get update

,seems to function correctly and compiles the list.)

I would be extrmely grateful for any assistance in this matter.

Mogbug

---

### Post by Pumalite on 2008-05-18
Try:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade.

---

### Post by CJ_Hudson on 2008-05-19
Hi,
I also obtain an error message on start-up:

The Panel encountered a problem while loading DAFIID:GNOME_MixerApplet





Please can you advise me on this issue because I think I typed an incorrect commend in the terminal window and accidentally pressed return before I could correct it.

---

### Post by iaculallad on 2008-05-19
Try reinstalling "gnome-applets" and it's dependencies "gnome-applets-data" using Synaptics.

---

### Post by dhemir on 2008-05-19
> **Pumalite said:**
> Try:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade.
 where we will type these,I am a bit new for ubuntu :)

---

### Post by iaculallad on 2008-05-19
> **dhemir said:**
> where we will type these,I am a bit new for ubuntu :)

Access your terminal: 

Applications->Accessories->Terminal

That's where you input those commands.

---

### Post by CJ_Hudson on 2008-05-19
Hi iaculallad,
The error message

The Panel encountered a problem while loading DAFIID:GNOME_MixerApplet

didn't appear again after re-booting. When it asked me if I wanted to delete the offending applet I typed "No".

Mogbug :-)

---

### Post by iaculallad on 2008-05-19
> **MogBug said:**
> Hi iaculallad,
The error message

The Panel encountered a problem while loading DAFIID:GNOME_MixerApplet

didn't appear again after re-booting. When it asked me if I wanted to delete the offending applet I typed "No".

Mogbug :-)

Navigate through Synaptic Package Manager and re-install the "gnome-applets" and its dependencies "gnome-applets-data".

---

### Post by dhemir on 2008-05-20
will i write all of them or try one by one?when i copy all of them it makes some process and stops??? 
thanks

---

### Post by iaculallad on 2008-05-20
> **dhemir said:**
> will i write all of them or try one by one?when i copy all of them it makes some process and stops??? 
thanks

If this is the command you are mentioning:

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade.

Execute the commands one at a time. Let the first command finish its task before executing the second and third command.

---

### Post by dhemir on 2008-05-20
i think it started....really thanks...you became a candle to my darkness..thanks for your kindness.. :)

---

### Post by iaculallad on 2008-05-20
Glad to be of help :) Good Luck and Go Ubuntu

---

