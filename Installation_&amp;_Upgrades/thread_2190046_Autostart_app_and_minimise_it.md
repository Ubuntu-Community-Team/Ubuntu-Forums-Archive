---
title: "Autostart app and minimise it"
date: 2013-11-25
forum: Installation &amp; Upgrades
---

### Post by m.strajnar on 2013-11-25
Hello!
I've been using ubuntu for 2 years and managed to do most things I needed by reading forums and guides. I can't find a solution for this particular problem tho.

I have LXDE with LDXM desktop.

I've installed ultimate mouse lite on my android tab [https://play.google.com/store/apps/details?id=com.negusoft.ucontrol](https://play.google.com/store/apps/details?id=com.negusoft.ucontrol) to simulate mouse and keyboard on my tab and use it to control ubuntu.
  I also installed required receiver program on ubuntu and everything works OK!

I have to manually start this application on ubuntu every time I log in. So I created .desktop file to launch app automatically and it works OK. This is what I created:

> [Desktop Entry] 
Type=Application
Exec=ucontrol

The problem is that launching app opens a GUI. I want this GUI hidden at startup.

So I added this line to .desktop file and nothing happens. It launches GUI anyway.

> NoDisplay=true

Deleted this line and replaced it with this line, but than app doesn't autostart anymore:

> Hidden=true

How can I start this app minimised (or even better in background). I must warn you that I suck at programming and too difficult commands are my nightmare. Every command I used I copyed from somewhere, so please make it simple if possible... THANX A LOT FOR ANY HELP!

---

### Post by Toz on 2013-11-25
Hello and welcome to the forums.

Here is a [link to a tutorial]("http://www.webupd8.org/2011/02/how-to-start-applications-minimized.html") on how to use devilspie to start applications minimized.

---

### Post by vasa1 on 2013-11-25
OP is using LXDE and I'm assuming that Openbox is the window manager. If that is so, it's possible to specify that a particular application should always open minimized (aka iconified) whether it autostarts or not. I've written about it here: [http://askubuntu.com/a/291862/25656](http://askubuntu.com/a/291862/25656)

---

### Post by m.strajnar on 2013-11-28
Thank you! I managed. So, if anyone needs it, this is what I did:

Install ultimate mouse lite aplication on android device.

[https://play.google.com/store/apps/details?id=com.negusoft.ucontrol&hl=en](https://play.google.com/store/apps/details?id=com.negusoft.ucontrol&hl=en)

Go to computer and enter in terminal:

> sudo apt-get install openjdk-6-jre
sudo apt-get install libbluetooth-dev

Download receiver from this site:

[http://www.negusoft.com/index.php/ultimate-control/downloads](http://www.negusoft.com/index.php/ultimate-control/downloads)

Extract receiver.tar to $HOME/foldername

Enter in terminal:

> CD $HOME/foldername

> sudo sh install
sudo ucontrol

Configurate application in GUI

Enter in terminal:

> sudo apt-get install devilspie

create .devilspie folder in $HOME folder
create file ucontrol.ds in $HOME/.devilspie folder

Enter in terminal:

> sudo leafpad $HOME/.devilspie/ucontrol.ds

Add text:

> ; generated_rule ucontrol
( if
( begin
( is ( application_name ) "SWT" )
)
( begin
( skip_tasklist )
( minimize )
( println "match" )
)
)

> sudo leafpad /etc/xdg/lxsession/LXDE/autostart

Add lines:
> ucontrol
devilspie

Connect to your computer using ultimate mouse lite application on your android.

---

