---
title: "cisco packet tracer"
date: 2012-02-10
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2012-02-10
if you like my tutorials please donate @
[http://apps.facebook.com/fundrazr/ac...d840a83be656d6](http://apps.facebook.com/fundrazr/ac...d840a83be656d6)
as i do treat this as a full time job.... yes its a $25,000 bat house fund raiser... lol its a generic drop box for donations.

upon reinstall i found that i had problems loading this tutorial.  further bug tracking i found i need to install some goodies...

i get the generic ubuntu tar @

[http://cisco.netacad.net/cnams/content/templates/LibraryHome.jsp?#/resource/lcms/cnams_site/english/generic_site_areas/library/course_catalog/PTSoftwareDownloads_Students.html](http://cisco.netacad.net/cnams/content/templates/LibraryHome.jsp?#/resource/lcms/cnams_site/english/generic_site_areas/library/course_catalog/PTSoftwareDownloads_Students.html)

to extract the tar

open terminal

alt+f2

gnome-terminal

run

then drop this block of code in the terminal

```

sudo apt-get install libkdewebkit5 wine

```

for a mac...

i highly suspect that all that needs to be done to a mac is installing wine.  i found documentation saying that safari and webkit is actually kdewebkit, i looked around, and this tutorial looks proper to build wine up. [http://www.davidbaumgold.com/tutorials/wine-mac/#update](http://www.davidbaumgold.com/tutorials/wine-mac/#update)  build up to step 3 on this page.  for mac users, do this in the terminal.  you might need to mod this block to cd to exactly where the file is located.  try the ubuntu generic tar, it should work for you if you have wine.

and then

```

cd $HOME/Downloads
tar -xf PacketTracer*
cd PacketTracer*
./install

```

(for my personal install i

```

sudo mv /opt/pt $HOME/packettracer
sudo chown $USER $HOME/packettracer 
sudo chgrp $USER $HOME/packettracer
sudo ln -s $HOME/packettracer/ /opt/pt

```

notice that the saves happen in the local exe directory, so dont forget to pull them out when upgrading / changing version.)

now once thats done symlink the binary from /opt (because it doesnt like really being installed...) to bin



```

sudo ln -s /opt/pt/packettracer /usr/bin/packettracer

```

to start the program

alt+f2

packettracer

run



so i can keep /home as a seperate storage partition.

R2(config-if)#clock rate 128000
This command applies only to DCE interfaces
there is a bug in packet tracer 5.3.3.0019. this is ccna 2 lab 9.6.1

i think if you put another serial card in the router and use its lines that they can assign DCE clock rate values.  im pretty sure the physical routers will take a DTE line and also host a DCE line.

another feature that it lacks or i have not found is the ability to enable network sessions of packet tracer, so 2 lab partners can build a network together.

---

### Post by uRock on 2012-02-10
Are you using 32 or 64 bit xubuntu? Cisco PT doesn't play well with 64bit. I run it in a 32bit VBox.

---

### Post by boblizar on 2012-02-11
im ubuntu + xfce amd_64, and the 386 packet tracer ubuntu bin doesnt play well with 64.  the generic tar runs fine.  i've found other 64 debs for ubuntu but they dont work well/are personally black listed.  now converting from 10.10 to 10.04 LTS this tutorial is broken.  i guess ill have to migrate to 12.04 LTS when it comes around in a month or 2...

[IMG]http://img192.imageshack.us/img192/5331/64pty.jpg[/IMG]

---

