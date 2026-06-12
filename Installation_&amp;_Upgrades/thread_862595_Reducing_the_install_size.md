---
title: "Reducing the install size"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by POMAH on 2008-07-17
Hi guys, I was looking for diffrent linux distributions to put on my soon to be bought MSI Wind. After many days of searching and reading I decided that xubuntu would be a perfect start for me as a newbie to the Linux world. 

But there is a little problem that I have, does anyone know if xubuntu works well with the Atom platform? Does the WIFI, Webcam, Bluetooth and graphics work "out of the box" or does it need tweaking?

I read that a fully installed xubuntu installation takes around 1,5 Gb of space. I would like to cut it down. I need to remove packages and add some, I will need Firefox 3, Thunderbird 2, VLC, Pidgin, a picture manager (just something to show images). I also need drivers for the Atom platform.
So my question is:
1) Is there any easy way to remove alot of the applications before even installing xubuntu? I'm thinking of something like nlite/vlite but for Linux, is there anything like that out there?

Please think of me as a complete newbie to the Linux environment, I'm good with windows but never tried out Linux.

---

### Post by avtolle on 2008-07-17
A minimum install might be the answer to your question: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Once installed, you then could add the xubuntu-desktop package, Firefox, Thunderbird, etc.  to the installation, and hopefully tailor your system just as you wish it to be.

---

### Post by Pumalite on 2008-07-17
Is this what you are looking for?:
[http://blog.canonical.com/?p=13](http://blog.canonical.com/?p=13)

---

### Post by POMAH on 2008-07-17
> **Pumalite said:**
> Is this what you are looking for?:
[http://blog.canonical.com/?p=13](http://blog.canonical.com/?p=13)

I saw that distribution, but it is not fully done yet. The minimal CD is looking nice, but is it hard to install the packages?
What packages do I need to install? 
I mean I have no idea what drivers or packages to install to make the WIFI or Bluetooth to work properly.

---

### Post by avtolle on 2008-07-17
This may give you a bit of guidance: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) (a bit dated, but still useful).

---

### Post by Vivaldi Gloria on 2008-07-17
> **POMAH said:**
>  The minimal CD is looking nice, but is it hard to install the packages? What packages do I need to install? I mean I have no idea what drivers or packages to install to make the WIFI or Bluetooth to work properly.

The alternative cd contains a command-line only install which can be found in the F4 menu in the boot menu. The minimal cd installs the same cli ubuntu sytem but it downloads everything from the net so it takes a longer time. Both have the hardware drivers contained in the regular ubuntu install.

Then you can install one of the desktops using the commands

sudo apt-get install ubuntu-desktop
sudo apt-get install xubuntu-desktop
sudo apt-get install kubuntu-desktop

But this will give exactly the same versions of the regular desktop cds so there is no point in installing them this way.

I also think that xubuntu is not light at all. I suggest you install a cli-only system and then install openbox. See

[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

---

### Post by logos34 on 2008-07-17
> **Vivaldi Gloria said:**
> The alternative cd contains a command-line only install which can be found in the F4 menu in the boot menu. The minimal cd installs the same cli ubuntu sytem but it downloads everything from the net so it takes a longer time. Both have the hardware drivers contained in the regular ubuntu install.

Then you can install one of the desktops using the commands

sudo apt-get install ubuntu-desktop
sudo apt-get install xubuntu-desktop
sudo apt-get install kubuntu-desktop

But this will give exactly the same versions of the regular desktop cds so there is no point in installing them this way.

I also think that xubuntu is not light at all. I suggest you install a cli-only system and then install openbox. See

[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

+1

I agree about the minimalCD.  And I don't understand why there is no option to choose a cli-only, or base-install (without DE)...instead it just starts downloading the equivalent of the desktop install cd.  Getting and burning the minimal iso is a jiffy, but the whole process actually ends up taking longer because it automatically starts downloading everything (and from a slow server at that)!

---

### Post by Vivaldi Gloria on 2008-07-17
> **logos34 said:**
> And I don't understand why there is no option to choose a cli-only, or base-install (without DE)...

Actually you can use it to install a cli system by entering "cli" at the boot menu. See [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

> instead it just starts downloading the equivalent of the desktop install cd.  Getting and burning the minimal iso is a jiffy, but the whole process actually ends up taking longer because it automatically starts downloading everything (and from a slow server at that)!

Agreed. The nice thing about the minimal cd is that it sometimes works in systems where the other cds fail for some reason.

---

### Post by logos34 on 2008-07-17
> **Vivaldi Gloria said:**
> Actually you can use it to install a cli system by entering "cli" at the boot menu. See [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal).

Is that all you have to do?  I checked it out a while back, but apparently not in any great detail because I don't remember that.

---

### Post by Vivaldi Gloria on 2008-07-17
> **logos34 said:**
> Is that all you have to do?  I checked it out a while back, but apparently not in any great detail because I don't remember that.

Yeah. I just tried a week ago. It's no different than the cli version you get from the alternate cd with the F4 option.

---

### Post by POMAH on 2008-07-18
Oki so after I do the CLI install, what do I get? Is xfce really that big? Or is just openbox so much better? Or are they diffrent things? Please remmber that I am totaly new to this Linux thing.

But I guess that I can not make a preconfigured install CD? With all the packages and such ready, and all I have to do is to put it in, choose partition and press enter?

Is it easier to install the full setup and then remove packages you dont need?

Oki I now found this: [http://aptoncd.sourceforge.net/screenshots.html](http://aptoncd.sourceforge.net/screenshots.html)

So now all I need to do is to figure out the easiest way of installing a basic system with a graphical interface and a packagemanager.

EDIT: After reading more of this: [https://help.ubuntu.com/community/Installation/LowMemorySystems#Adding](https://help.ubuntu.com/community/Installation/LowMemorySystems#Adding) a Window Manager

I now see it has all the help I need, exept for one thing, is there still no  way to automate this process? Preferably sitting on a Vista OS computer? What window manager do you recommend me to use? I want it to look more like the traditional vista/xp look, and be light on the resources. IceVM? Openbox?

And btw thx alot for the help so far, this is by far the most active Linux community I have seen so far.

---

### Post by Vivaldi Gloria on 2008-07-18
> **POMAH said:**
> Oki so after I do the CLI install, what do I get? Is xfce really that big? Or is just openbox so much better? Or are they diffrent things? 

But I guess that I can not make a preconfigured install CD? With all the packages and such ready, and all I have to do is to put it in, choose partition and press enter?

If you want to go with xubuntu then it's easy, just install the xubuntu cd and you're done. You don't have to bother with first installing a cli system and adding the desktop later.

If you want openbox then you have to install a cli sytem and then add openbox to it. That InstallationLowMemorySystems page you mentioned gives the necessary commands for that and also see urukrama's page (he's also an active member here):

[http://urukrama.wordpress.com/openbox-guide/#Installing](http://urukrama.wordpress.com/openbox-guide/#Installing)

> Is it easier to install the full setup and then remove packages you dont need?

That's not very easy in general. Your choice is really between two things: A xubuntu install or adding openbox to a cli install.

> Oki I now found this: [http://aptoncd.sourceforge.net/screenshots.html](http://aptoncd.sourceforge.net/screenshots.html)

Aptoncd has nothing to do with installing. It's about saving the programs you installed in a system so if you install them somewhere else you don't have to download them again, you use the aptoncd cd.

>  So now all I need to do is to figure out the easiest way of installing a basic system with a graphical interface and a packagemanager.

EDIT: After reading more of this: [https://help.ubuntu.com/community/Installation/LowMemorySystems#Adding](https://help.ubuntu.com/community/Installation/LowMemorySystems#Adding) a Window Manager

I now see it has all the help I need, exept for one thing, is there still no  way to automate this process? Preferably sitting on a Vista OS computer? What window manager do you recommend me to use? I want it to look more like the traditional vista/xp look, and be light on the resources. IceVM? Openbox?

And btw thx alot for the help so far, this is by far the most active Linux community I have seen so far.

Let's write your options again:

1) xubuntu cd - easy to install using the xubuntu cd, not very light system

2) cli + openbox - install using the guides above, very light sytem

I suggest you try both of them! Then decide which one you like. Installing a new system is not hard and to be honest, I think it's fun.

Both have customizable looks. But I don't know if you can get them to look like vista as you want.

---

### Post by POMAH on 2008-07-18
After playing around alittle with VirtualBox, I decided that I like Openbox, but I just cant seem to some stuff to work properly. I cant seem to get a menu to show, I want to atleast have a menu like the XP startmenu, but there is no such option as I can see in the Openbox.

---

### Post by Vivaldi Gloria on 2008-07-18
> **POMAH said:**
> After playing around alittle with VirtualBox, I decided that I like Openbox, but I just cant seem to some stuff to work properly. I cant seem to get a menu to show, I want to atleast have a menu like the XP startmenu, but there is no such option as I can see in the Openbox.

It's been a while since I looked at openbox. I don't remember the details. But urukrama writes about it here:

[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

Read section 4.

Edit. Sorry it's section 8.

---

