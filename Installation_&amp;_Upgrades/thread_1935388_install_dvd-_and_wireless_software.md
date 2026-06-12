---
title: "install dvd- and wireless software"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by beplay on 2012-03-04
Hello!

i'm new in Ubuntu!

i'm trying to install my wireless WUSB300N network adapter,
i've the software for windows, i think...
i tryied to do the thing that "slice of linux" recommended:
[http://sliceoflinux.com/2011/05/09/que-hacer-despues-de-instalar-ubuntu-11-04-natty-narwhal-paso-a-paso/](http://sliceoflinux.com/2011/05/09/que-hacer-despues-de-instalar-ubuntu-11-04-natty-narwhal-paso-a-paso/)
But the computer says that doesn't recognize the directory...
i'm in a bucle... please i need help. 
i did it:
cd ~/Public/Drivers
bash: cd: /home/belen/Public/Drivers: No existe el archivo o el directorio
belen@belen-N34AS1:~$ sudo ndiswrapper -i netmw245.inf
couldn't open netmw245.inf: No existe el archivo o el directorio at /usr/sbin/ndiswrapper-1.9 line 219.
belen@belen-N34AS1:~$ opt/ndis/:
bash: opt/ndis/:: No existe el archivo o el directorio
belen@belen-N34AS1:~$ #mkdir/opt/ndis
belen@belen-N34AS1:~$ #tar xvf WUSB300N.tar C
belen@belen-N34AS1:~$ /opt/ndis/
bash: /opt/ndis/: No existe el archivo o el directorio


what i can do to install the wireless, i think maybe ubuntu doesn't recognize de cd-rom to.
i don't understand the system already, so i need all the steps, like where is the window or aplication, and what i need to open....

This is being crazy... jejejeje funny and crazy... learning a LOT !

Hugs! Thanks

Belén

---

### Post by grahammechanical on 2012-03-04
I have never used Ndiswrapper. I do not speak from experience and I cannot read Spanish. 

Do you have Ndiswrapper installed on your system?

Open the Ubuntu Software Centre and search for ndiswrapper. You will be able to install a Graphical User Interface (GUI) for Ndiswrapper that may make it easier.

I am not an expert on using the terminal but I think that this is wrong

> mkdir/opt/ndis

It should be 

> mkdir /opt/ndis

Look at section 3.4 in this link

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

It is in English. Sorry.

Are you aware of these links?

[http://www.ubuntu-es.org/forum]("http://www.ubuntu-es.org/forum")

[http://doc.ubuntu-es.org/Documentaci%C3%B3n]("http://doc.ubuntu-es.org/Documentaci%C3%B3n")

Regards.

---

