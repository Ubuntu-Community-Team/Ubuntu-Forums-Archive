---
title: "Bugs with Ubutnu 6.10 ?"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by chrisdee on 2006-11-06
Hello. I first tried installing 6.10 server version, but found that it only installed text based ubutnu. Also, neither Apache, PHP, MySQL, Mail or SSH was installed by deafult.

Im no ubuntu expert so I also need the graphic desktop
with synaptic to install many of the services. So I installed
the 6.10 Desktop version.

In synaptic it says that many of the services (eg ntp) are installed, but when I try to sync time it says I have to install
NTP. What's that all about ?

I wonder if there is a Ubuntu version that automatically installes at least Apache, MySQL, PHP, and maby SSH, NTP, Mail
some where on the ubuntu site ?
And where can I find it

---

### Post by PilotJLR on 2006-11-06
The Server version doesn't come with X, hence no graphics... servers don't need that in most cases. If you prefer to use a graphical display, do a "sudo apt-get install ubuntu-desktop" to add it.

When installing, it will ask you what software you want to install. One option is called "LAMP Server." Check that... LAMP means Linux, Apache, MySQL, PHP (perl or python)... so it's pretty easy!

---

### Post by chrisdee on 2006-11-06
Well. I actually have an Ubuntu server wich works
fine. It runs Apache, Email, MySQL, PHP, SSH, FTP and
Samba. But it is a very noisy machine, therefor am trying
to install Ubuntu on my scilent machine.

So I need the services listed above on my new installation.
As I said I now have the Desktop 6.10 version.

I wonder if I can install all the above services on this
version ?

---

### Post by PilotJLR on 2006-11-06
Sure, you can install all of these packages. Most are clearly named in Synaptic, but it may be easier to install one-by-one using the big guide:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by OriUbu on 2006-11-07
Well I can say that from running 6.10 Desktop and trying just to install mysql works at first then when you reboot will not start... even if I break out the baseball bat ](*,)

---

### Post by chrisdee on 2006-11-07
Now Iv finished installing the Ubuntu 6.10 Server image
on my machine.

But when I try to install the desktop like you described above
apt-get install ubuntu-desktop

I get the following message :

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntu-desktop
root@myserver:~#

What do I do with this ?

---

### Post by PilotJLR on 2006-11-07
Have you enabled universe repos?

If not, then uncomment the universe repos in sources.list , then do an apt-get update, then install ubuntu-desktop

---

