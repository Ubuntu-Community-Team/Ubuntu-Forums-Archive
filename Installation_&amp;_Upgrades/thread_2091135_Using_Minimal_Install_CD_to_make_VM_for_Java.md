---
title: "Using Minimal Install CD to make VM for Java"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by sirgad on 2012-12-04
My aim is to create a very small VM in Parallels Desktop on my Mac containing Ubuntu.  I've decided to start with the [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD"), making reference to [a brief tutorial]("http://www.psychocats.net/ubuntu/minimal").

The purpose of the VM is to run Java for the purposes of using [Sweet Home 3D]("http://www.sweethome3d.com/index.jsp"), as I don't want to install Java on my host OS (OS X "Mountain Lion").  The tutorial linked above involves installing the following once the Minimal install is complete:

xorg
xterm 
gdm 
icewm
menu 
firefox 
gksu 
synaptic

But that's it.  Can anyone tell me which additional packages (if any) I'll need to install to make Java and Sweet Home 3D work?

Thanks.

---

### Post by ibjsb4 on 2012-12-04
I would replace "gdm" with "lightdm", its a smaller package and will do fine for a display manager.

No need to install xorg, its in the lightdm package.

icewm and menu I have not used.  A personnel preference for me is gnome-panel which will give you a menu and a couple of panels and works fine for a stand alone window manager.

Synaptic is a good choice and nothing wrong with xterm.

Just go ahead and install Sweet Home, if dependencies are missing you will be notified.

Edit:  If you use gnome-panel, install without recommends or you will get dumped on  :)  Here's the whole thing:

```
sudo apt-get install lightdm synaptic xterm && sudo apt-get install --no-install-recommends gnome-session-fallback
```And of course you will add whatever java you need.

One more thing:  This is using the terminal only install in the mini.iso and I left out gksu and FF, but that can be added after.

---

### Post by sirgad on 2012-12-04
> **ibjsb4 said:**
> I would replace "gdm" with "lightdm", its a smaller package and will do fine for a display manager.

No need to install xorg, its in the lightdm package.

Neat.

> icewm and menu I have not used.  A personnel preference for me is gnome-panel which will give you a menu and a couple of panels and works fine for a stand alone window manager.

Ta.

> Synaptic is a good choice and nothing wrong with xterm.

K.

> Just go ahead and install Sweet Home, if dependencies are missing you will be notified.

Great :)

> Edit:  If you use gnome-panel, install without recommends or you will get dumped on  :)  Here's the whole thing:

```
sudo apt-get install lightdm synaptic xterm && sudo apt-get install --no-install-recommends gnome-session-fallback
```And of course you will add whatever java you need.

One more thing:  This is using the terminal only install in the mini.iso and I left out gksu and FF, but that can be added after.

I'll post back with the results.  Cheers.

---

### Post by ibjsb4 on 2012-12-04
Ok, one more thing.

When you first boot up your new install the panels will be black and you will not be able to see your menu.  To correct this:

**Alt **+ **Right click** on a blank (black) part of the panel.  Go to properties>background and set to solid color and 100% opaque.

---

### Post by sirgad on 2012-12-04
> **ibjsb4 said:**
> Ok, one more thing.

When you first boot up your new install the panels will be black and you will not be able to see your menu.  To correct this:

**Alt **+ **Right click** on a blank (black) part of the panel.  Go to properties>background and set to solid color and 100% opaque.

Thank goodness you posted that.  I was wondering what was wrong! :)

If I could ask a further question: on boot, Ubuntu insists on waiting for a network connection before continuing.  If I disable the Network Connection in Parallels configuration for that VM, Ubuntu just sits there waiting for a connection until x + 60 seconds have passed.  Once booted, the System Settings > Network > Wired has an "options" box, but it's greyed out.  How an I tell Ubuntu not to look for a network connection when booting?

---

### Post by ibjsb4 on 2012-12-04
> **sirgad said:**
> Thank goodness you posted that.  I was wondering what was wrong! :)

If I could ask a further question: on boot, Ubuntu insists on waiting for a network connection before continuing.  If I disable the Network Connection in Parallels configuration for that VM, Ubuntu just sits there waiting for a connection until x + 60 seconds have passed.  Once booted, the System Settings > Network > Wired has an "options" box, but it's greyed out.  How an I tell Ubuntu not to look for a network connection when booting?


Ok, you got me guessing.  So here's my guesswork  :)

Go to:

/var/lib/NetworkManager/NetworkManager.state

And change "NetworkingEnabled=true" to false

Then to startup the internet when needed:

sudo /etc/init.d/networking restart

If that works you can turn that command into an icon and put it in the panel.

Also look like the forum is going down, did you see the notice?

---

### Post by ibjsb4 on 2012-12-04
A few more things.

I believe you do not have a file manager yet and you probably could  use an editor.

```
sudo apt-get install nautilus gedit
```

This can be used to edit /var/lib/NetworkManager/NetworkManager.state.

In terminal

```
gksudo nautilus
```

And navagiate to Filesystem (on the left) /var/lib/NetworkManager/NetworkManager.state

Double click on it and that will open your editor.

Just be careful what you do while using gksudo.  This gives you root privileges to change things without question.

---

### Post by sirgad on 2012-12-06
> **ibjsb4 said:**
> Ok, you got me guessing.  So here's my guesswork  :)

Go to:

/var/lib/NetworkManager/NetworkManager.state

And change "NetworkingEnabled=true" to false


This doesn't stop the OS from looking for a network connection on boot, unfortunately.  Any further suggestions?

Oh, as for gedit: I'm comfortable with Vim, so I don't need that, but thanks.  One issue I'm having though is that, with Vim, using the cursor keys to navigate is fine until I go into Insert mode, at which point the cursor keys start entering As, Bs and Cs instead of moving the cursor.  Any idea why that might be?

Thanks :)

---

### Post by ibjsb4 on 2012-12-06
I do not use vim, so no help there.

As for disabling the internet I would look here.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=disable+internet+network+search+at+boot&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=disable+internet+network+search+at+boot&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

You could also start a couple of new threads on vim and network since the title of this one does not pertain to your new questions.

---

