---
title: "Lubuntu 64-bit installation"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by heedongyee on 2011-05-19
After several usuccessful attempts at installing 64-bit Lubuntu on an Asus netbook via the mini.iso file on USB, I finally got it working by first installing 64-bit Ubuntu Natty and then adding Lubuntu to it.  

The only problem is that I still have all the applications that come with Ubuntu.  Is there any way to purge my system of all the Ubuntu fat, thereby restoring what Lubuntu should be?  Or must I remove everything I don't need bit by bit?

---

### Post by JC Cheloven on 2011-05-19
I usually do a bad job when "purging the system" from bundled apps. Sometimes they have deep roots ;)

A better way of installing when problems do arise, is doing a minimal install (from an alternate install cd, choose "install a command-line system"). Then install the lubuntu meta package (sudo apt-get install lubuntu-desktop). Or if you want even more control, you may install the lxde metapackage and then the apps you exactly want. 

Hope this helps

EDIT: in a secon read, ¿is your asus netbook 64bit capable? Well, if you ran 64bit regular ubuntu on it, then it is. Only, I find it a bit strange.

---

### Post by kansasnoob on 2011-05-20
> **heedongyee said:**
> After several usuccessful attempts at installing 64-bit Lubuntu on an Asus netbook via the mini.iso file on USB, I finally got it working by first installing 64-bit Ubuntu Natty and then adding Lubuntu to it.  

The only problem is that I still have all the applications that come with Ubuntu.  Is there any way to purge my system of all the Ubuntu fat, thereby restoring what Lubuntu should be?  Or must I remove everything I don't need bit by bit?

[http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

---

### Post by linuxinstalledfromhdd on 2011-05-20
Or you could use Madbox OS and then install Lubuntu environment.

---

### Post by dandroid13 on 2011-05-20
Or you could try this: [http://www.omgubuntu.co.uk/2011/05/lubuntu-64bit-image-available-for-download/]("http://www.omgubuntu.co.uk/2011/05/lubuntu-64bit-image-available-for-download/")

---

### Post by heedongyee on 2011-05-24
Ok fellas, thanks for the responses.  

Like JC Cheloven I did a horrible job uninstalling gnome and kde pork, threw in the towel, and begrudgingly installed 32 bit before I rechecked this tread.  Thanks for the link, dandroid13, as I now have 64 bit running well!  BTW I've got the Atom N550 processor which is 64-bit happy!

---

### Post by dandroid13 on 2011-05-25
> **heedongyee said:**
> Ok fellas, thanks for the responses.  

Like JC Cheloven I did a horrible job uninstalling gnome and kde pork, threw in the towel, and begrudgingly installed 32 bit before I rechecked this tread.  Thanks for the link, dandroid13, as I now have 64 bit running well!  BTW I've got the Atom N550 processor which is 64-bit happy!

Glad I could help you :)
BTW, since it's a *unofficial* iso if you have any issues then try [iQunix OS]("http://iqunix.sourceforge.net/index.html"), the bare-bone Ubuntu and install lubuntu-desktop from Synaptic

---

