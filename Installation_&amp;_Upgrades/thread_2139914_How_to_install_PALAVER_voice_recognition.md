---
title: "How to install PALAVER voice recognition?"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by ferguson1951 on 2013-04-28
Hello everybody.
I use Ubuntu 12.04 LTS Precise 32 bit.
I would like to install Palaver voice recognition app.
Can anyone help?
Thanks and regards

---

### Post by gal007 on 2013-07-06
> **ferguson1951 said:**
> Hello everybody.
I use Ubuntu 12.04 LTS Precise 32 bit.
I would like to install Palaver voice recognition app.
Can anyone help?
Thanks and regards

Hi! You need to:
0) download the zip from here: [https://github.com/JamezQ/Palaver](https://github.com/JamezQ/Palaver)
1) Install dependencies:
sudo apt-get install sox python-argparse libsox-fmt-mp3 mutt wget espeak xvkbd xautomation

2) Then exctract the zip file and then move that dir to the location you want to install. Eg I moved to /opt
sudo mv /home/gaby/Software/Palaver-master /opt/
3) Open a terminal and change to the Palaver's dir:
cd /opt/Palaver-master
4) Run setup and follow the instructions:
sudo ./setup
5) Create the hotkey shortcut. System Settings->Keyboard->Shortcuts->Custom shortcuts-> (+) and complete with something like this:
name: voice
ComNand: /opt/Palaver-master/hotkey
Then click on the new shortcut to choose the keys combination.
6) Press the key combination to listen. Press again to recognize what you said. EG: Open text editor. Press combination. Say "type Hello. I am Gabriela". press combination again.

P/d: I really can't configure for spanish.

---

### Post by its4theshah on 2013-12-27
Hello nice people, I have installed the dependencies, but when i press the hotkey nothing happens. I'm running Ubuntu 13.10 64 bit. Thank you in advance

---

