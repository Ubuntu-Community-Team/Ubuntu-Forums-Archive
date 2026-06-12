---
title: "Installing Gnome on Kubuntu?"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by AlexBryan on 2006-06-10
Hi I have Ubuntu running on one computer and kubuntu running on my laptop (both the newest versions of dapper). If I install the KDE environment in Ubuntu would it be the same as if I was using Kubuntu? And if I installed the Gnome environment in Kubuntu would I be able to use programs like Synaptic Package Manager? I've heard you can do this, could someone tell me how I would go about installing Gnome on Kubuntu? If I did install one would it overwrite the other or can you have both on one system? If so how easy is it to switch between the two?

---

### Post by aysiu on 2006-06-10
You can have both on one system.

Installing one will give you the full version.

But if you have both, you will have *both*. That means if you have Kubuntu and Ubuntu on one partition, you'll have *both* Adept and Synaptic. You'll have both Kate and Gedit. You'll have both Firefox and Konqueror.

The one major complaint about having both is crowded menus. I go in and manually delete the extraneos entries, so it's not a big deal to me.

You switch between the two by clicking on *session* on the login screen.

[http://www.psychocats.net/ubuntu/gnome.html](http://www.psychocats.net/ubuntu/gnome.html) will give you more details.

---

### Post by drummer on 2006-06-10
You can install any number of desktop environments, and to switch between them you select which you would like to login with in GDM (the login screen). To install Gnome, install the package ubuntu-desktop and it will install all the packages normally installed with a Ubuntu install.

---

### Post by Princey on 2006-06-10
[QUOTE=AlexBryan]Hi I have Ubuntu running on one computer and kubuntu running on my laptop (both the newest versions of dapper). If I install the KDE environment in Ubuntu would it be the same as if I was using Kubuntu? And if I installed the Gnome environment in Kubuntu would I be able to use programs like Synaptic Package Manager? I've heard you can do this, could someone tell me how I would go about installing Gnome on Kubuntu? If I did install one would it overwrite the other or can you have both on one system? If so how easy is it to switch between the two?[/QUOTE]

First of all, you don't need gnome to use synaptic package manager. It's as easy as typing ```
sudo apt-get install synaptic
``` in the terminal and voila, it's done after you input your password.

Secondly, it's possible to install gnome on Kubuntu and vice versa. It won't replace your base system. It just gives you a choice to start at log in whether gnome or kde. Again, just a simple ```
sudo apt-get install kdm
``` if you're using gnome or ```
sudo apt-get install gdm
``` if you're on Kubuntu. 

But again, if you just want synaptic, go with my first point. No need to install gnome. For me, I prefer synaptic over Adept although improvements have been made with Dapper Drake as to it's interface and explanatory notes. It's just a simple ```
sudo apt-get install synaptic
``` and after typing in my password and the prompt returns, I'm ready to go. Good luck.

---

### Post by aysiu on 2006-06-10
[QUOTE=Princey]First of all, you don't need gnome to use synaptic package manager. It's as easy as typing ```
sudo apt-get install synaptic
``` in the terminal and voila, it's done after you input your password.[/quote] That's a good point. If all you want is Synaptic, installing Gnome, too, is a bit extreme.

> 
Secondly, it's possible to install gnome on Kubuntu and vice versa. It won't replace your base system. It just gives you a choice to start at log in whether gnome or kde. Again, just a simple ```
sudo apt-get install kdm
``` if you're using gnome or ```
sudo apt-get install gdm
``` if you're on Kubuntu.  A slight correction: KDM and GDM are display managers that mainly manage the login screen. Gnome and KDE are desktop environments that are the main way users interact with Ubuntu after having logged in.

Also, the best way to install a new desktop environment is with *aptitude*, not *apt-get*, as it'll make the desktop environment easier to remove later, should the user wish to do so.

---

### Post by Princey on 2006-06-10
Thanks Ayisu for the corrections

---

