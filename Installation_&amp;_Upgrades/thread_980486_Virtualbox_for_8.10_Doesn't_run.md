---
title: "Virtualbox for 8.10? Doesn't run"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by jessthebest on 2008-11-12
Uhmm Hi I would just like to  ask how to make the virtualbox work for 8.10?
I've alredy tried to install virtualbox-ose using the Add/Remove Programs way, I've also tried the sudo apt-get way of installing it, yet it still doesn't run.. could anyone help me pleasE?

---

### Post by athaki on 2008-11-12
you need to edit your groups under 'groups and users' and put yourself into the vboxusers group.  then you need to download specific kernel modules in order for virtualbox to run.  it should prompt you in the right direction to look in synaptic.

sorry i'm not much help; I'm at work and I don't have access to my ubuntu box.

---

### Post by jessthebest on 2008-11-12
uhm.. how do i do that? I'm totally new to ubuntu and i dont how to do pretty much of everything..

So I removed all the packages related virtualbox in sypnaptic and tried installing it through the sudo apt-get method. But when i try to run it, nothing happens.

---

### Post by athaki on 2008-11-12
[http://linuxowns.wordpress.com/2008/08/22/installing-virtualbox-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/22/installing-virtualbox-on-ubuntu/)

That explains it alot better than I could.  I'll sum it up here:Installation

Open up a terminal and copy/paste this command

    sudo apt-get install virtualbox-ose virtualbox-ose-source virtualbox-ose-modules-generic

If this won&#8217;t work for you or virtualbox complains that a module isn&#8217;t installed, open up synaptic and install virtualbox-ose-modules-2.6.24-19-generic (if 2.6.24-19 is the kernel you are running, for the moment in hardy that is the correct one).

2. Adding yourself to the group

Use this command in a terminal.

    sudo adduser username vboxusers

Replace &#8220;username&#8221; with your own username.

3. Log out and back in


the kernel version will be out of date since this article was written for 8.04 but the mechanics behind it are sound.

---

### Post by jessthebest on 2008-11-12
I just added myself to the vboxusers group and i've already installed the kernel along with the ose and yet it's still not working properly.. is there something i'm doing wrong?

---

### Post by sirebral on 2008-11-12
what problems are you having?

---

### Post by athaki on 2008-11-12
it might be that virtualbox cannot acces your kernel hence the need for a vitrualbox-ose-modules package.  there should be a virtualbox-ose-modles generic package that automatically downloads the correct kernel modules for your specific kernel in synaptic.

---

### Post by jessthebest on 2008-11-13
I can't make seem to work here's what i did. 
[http://i255.photobucket.com/albums/hh131/jessica_chin/pic02.png](http://i255.photobucket.com/albums/hh131/jessica_chin/pic02.png)

[http://i255.photobucket.com/albums/hh131/jessica_chin/pic04.png](http://i255.photobucket.com/albums/hh131/jessica_chin/pic04.png)

tell me if you need more screenshots to diagnose the problem.. please. thanks!

---

