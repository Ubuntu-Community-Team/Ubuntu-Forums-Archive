---
title: "can someone dumb this down for me i dont understand how to do this"
date: 2011-08-28
forum: Installation &amp; Upgrades
---

### Post by TheDevilMr666 on 2011-08-28
Re: Acer Aspire Mic Fix?
Hurray I got it to work, thanks to marcosbelancon from the bug report.

Below is what I did

Step 1: Download [ftp://ftp.alsa-project.org/pub/drive...1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.20.tar.bz2)


Step 2:extract the contents.
Open terminal and cd (change directory) to where you downloaded the driver e.g usr@usr-laptop:~$cd Desktop Note: remember its case sensitive once in the correct directory untar the driver using the command tar -vxf alsa-driver-1.0.20.tar.gz


Step 3:Compile the driver (note you need Check install if you don't have it use apt-get install to get it e.g sudo apt-get install checkinstall) then run the commands bellow takes a little while to do its thing


./configure
make
sudo make install


Step 4:
Configure alsa-base.conf
Add the following line to the end of /etc/modprobe.d/alsa-base.conf file I did this by using the command 

sudo gedit /etc/modprobe.d/alsa-base.conf


I added these two lines at the end of the conf file then saved it
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=acer


Step 5:
Reboot and for me it worked hope this helps someone

---

### Post by jerrrys on 2011-08-28
whats it suppose to do?  and wouldnt a title like "alsa how to" help

---

### Post by TheDevilMr666 on 2011-08-29
all i know is its supposed to fix my internal micro phone i dont know what the alsa is i just found this on the posts and its for my laptop to make the micro hone work again but idk what im supposed to do exactly the compiling and configuring and checking the drivers

---

### Post by jerrrys on 2011-08-29
your link is dead

---

