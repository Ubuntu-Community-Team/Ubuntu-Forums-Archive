---
title: "Ubuntu Server + Desktop"
date: 2012-02-15
forum: Installation &amp; Upgrades
---

### Post by YesGood on 2012-02-15
Hi,

I need a .iso of the ubuntu server +Ubuntu Desktop.
And so I do not need make sudo apt-get install ubuntu-desktop in all of my installation of Ubuntu Server.

I need Ubuntu Server, but I do not like the black screen of the Ubuntu Server.

I lose much time the ubuntu-desktop  installation with the command line.

And I search a tool, which it join the both versions of Ubuntu in a .iso. The server and Desktop.

I see the Ubuntu Customization Kit, but I do not know if this is the best tool. 

Help me..;)

---

### Post by josephmills on 2012-02-15
there are many types of desktops out there lightweight ones like lxde which you can install with the command 
```
sudo apt-get install lxde-core
```
then there are other I just wrote about them here 
see post #8 [http://ubuntuforums.org/showthread.php?t=1925948](http://ubuntuforums.org/showthread.php?t=1925948)
figure out which one you like and install. there is also other things like gnu pannel and webmin and many other to replace the windows manager of a server (kinda)I hope that this helps

---

### Post by haqking on 2012-02-15
> **YesGood said:**
> Hi,

I need a .iso of the ubuntu server +Ubuntu Desktop.
And so I do not need make sudo apt-get install ubuntu-desktop in all of my installation of Ubuntu Server.

I need Ubuntu Server, but I do not like the black screen of the Ubuntu Server.

I lose much time the ubuntu-desktop  installation with the command line.

And I search a tool, which it join the both versions of Ubuntu in a .iso. The server and Desktop.

I see the Ubuntu Customization Kit, but I do not know if this is the best tool. 

Help me..;)


When running a server it is best practice to not use a DE.

Why is it you "need" Ubuntu Server ?

All server services that Server can provide work the same way in the desktop Ubuntu version if its just a server service you require ?

---

### Post by snowpine on 2012-02-15
It is probably faster/quicker to add the web services you need (Apache, MYSQL, or whatever) to your Ubuntu Desktop than to add ubuntu-desktop to your Server.

Most server admins do not use a GUI (particularly not a bloated/buggy GUI like Unity--just my opinion :)). You can learn how to administer a server using the command line by following this guide: [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

---

### Post by YesGood on 2012-02-15
:)Thanks for answer.

Yes, I need the Ubuntu Server, but need the GUI. It is better for me.

And search a way of create an iso of both version. desktop and server :confused:

---

### Post by josephmills on 2012-02-15
look into 
remastersys [http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
and 
debian live [http://live.debian.net/manual/](http://live.debian.net/manual/)
my friend you will find what you are looking for (as far as making a live iso of your system)
hope this helps

---

### Post by YesGood on 2012-02-15
Thanks

I used the remastersys,but the iso had a problem with the ssh.

And so I  need other tools.

Thanks for the links. I will see the Debian Manual 

You know if  is possible with the ubuntu Customizer Kit .?

---

