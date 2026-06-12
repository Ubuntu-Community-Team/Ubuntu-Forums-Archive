---
title: "Remove unity-greeter and install gdm?"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by sazawal on 2012-10-23
I am running gnome-shell 3.6 in Ubuntu 12.10. I want to remove unity-greeter and install gdm. What I should do? 
In my synaptic manager both unity-greeter and gdm are installed (gdm was already installed, I never installed it). Also my /etc/lightdm/lightdm.conf says,

```
$ cat lightdm.conf 

[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter
```

I have already tried removing unity-greeter package but it got me into so much trouble. I fixed it from the recovery mode by reinstalling unity-greeter. My question is, if I have removed unity-greeter why ubuntu was not taking gdm as the default login screen?

Help!!

---

### Post by oldos2er on 2012-10-23
Post moved to its own thread.

---

### Post by MG&amp;TL on 2012-10-23
```
sudo dpkg-reconfigure gdm
```

(should) will give you a list of options about which DM you want to use.

---

### Post by dino99 on 2012-10-23
install lightdm-gtk-greeter
purge ubuntu-desktop
purge unity-greeter

then make the change into the conf file:

#greeter-session=unity-greeter
greeter-session=lightdm-gtk-greeter

---

### Post by sazawal on 2012-10-23
Thank you MG&TL and dino99, it worked for me. Sorry for the trouble [[COLOR=#DD4814]**oldos2er**[/COLOR]]("http://ubuntuforums.org/member.php?u=338320")

---

### Post by sazawal on 2012-10-25
I have another question. The commands,

```
sudo dpkg-reconfigure lightdm
```and

```
sudo dpkg-reconfigure gdm
```leads to the same configuration menu where I can select between lightdm and gdm. So, my question is, are lightdm and unity-greeter the same thing ? If yes, then how can I remove unity-greeter (or lightdm) and just keep gdm?

I am currently using gdm as my login screen. Should I remove the package unity-greeter from Synaptic Package Manager?

---

### Post by MG&amp;TL on 2012-10-25
Nope. I'll explain how lightdm works, then maybe you'll understand a bit better.
 
LightDM just exposes an API for logging in (hence 'Light'DM), etc, which means that interfaces like *unity-greeter* and *lightdm-gtk-greeter *can use it without worrying about the low-level stuff.
 
To use a Display Manager (*dm), you need to set a default to start. All *dpkg-reconfigure* does is reconfigure the package. When you configure a package, if said package supplies an alternative to something already installed, it provides you with an option to choose the default.
 
Because gdm and lightdm are both Display Managers, it provides a menu (or should do), from which you can choose the default.
 
To remove lightdm:
 
```
sudo apt-get remove lightdm
```

---

### Post by sazawal on 2012-10-26
Okay, I think I got it now. 

unity-greeter and lightdm-gtk-greeter are two different interfaces. Currently my ubuntu has unity-greeter which allows to set the default display manager. Two display managers being lightdm and gdm. 

lightdm-gtk-greeter is currently not installed in my system. What happens if I install it? I suppose it will allow to set the default display manager just like unity-greeter. Can it act as a replacement of unity-greeter?

---

### Post by MG&amp;TL on 2012-10-26
> unity-greeter and lightdm-gtk-greeter are two different interfaces. 

Yup, they're both frontends to lightdm.

> Currently my ubuntu has unity-greeter which allows to set the default display manager. Two display managers being lightdm and gdm. 


Nope. Lightdm controls all the low-level stuff, unity-greeter provides a pretty frontend.

> lightdm-gtk-greeter is currently not installed in my system

Indeed not.

. > What happens if I install it?

As far as I know, nothing. You'll need to change /etc/lightdm/lightdm.conf to use lightdm-gtk-greeter instead of unity-greeter. 

>  I suppose it will allow to set the default display manager just like unity-greeter. Can it act as a replacement of unity-greeter?


Yes, and no. The Display Manager is just a piece of software which allows things like login and a pretty login box. The pretty login box can be done with a separate piece of software, like unity-greeter, or embedded within the display manager (like gdm). 

Greeters provide frontends (unity-greeter) to Display Managers (lightdm) , which launch sessions (Gnome, KDE, Unity).

---

