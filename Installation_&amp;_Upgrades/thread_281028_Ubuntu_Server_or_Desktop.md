---
title: "Ubuntu Server or Desktop"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by RunsWithScissors on 2006-10-20
Not sure what to do here

I was gonna install Ubuntu Server on this machine that used to be a windows 2003 server. But then I read that it  does not install a user interface. What should I do?

I need:

LAMP architecture for website testing.

a user interface for a feww apps I need to run on the system need 
the gui.

Graphical remote access. I dont think that there is something that would let me use Windows XP's remote desktop client is there?

Anyway not sure what to start with ? should I just install Desktop and install LAMP? or is there a command that will make server install the UI xorg and gnome?

---

### Post by taurus on 2006-10-20
Install the desktop version.  Then whatever else you need to install, use aptitude!!!  Nice and easy...

---

### Post by Old Pink on 2006-10-20
If you get the server edition, then type ```
sudo apt-get install ubuntu-desktop
``` you'll have a user interface. :D

---

### Post by RunsWithScissors on 2006-10-20
Thanx Pink
What about remote desktop? 
any suggestions there?

---

### Post by RunsWithScissors on 2006-10-20
I get the following erroe when I try to insall the desktop on the server
E: Couldn't find package ubuntu-desktop

what gives?

---

### Post by taurus on 2006-10-20
Exactly what did you run?  Need the whole command...  Try

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by jpmrblood on 2006-10-20
For remote desktop access, if you want to connect to Windows, you could use rdesktop, e.g.:

```
U-Box#> rdesktop 192.0.0.12 
```

For remote access from Windows to Linux, you could use VNC or install X on your Windows. Btw, for both solutions, you must install ubuntu-desktop package.

But, from the problem you mention, I figure you just want to have access to your linux box and use it as dedicated server. But, you would like to edit anything there using your Windows box. If that's the case, you could install open ssh and you could use any scp/ssh client to connect there:
```
 #> sudo apt-get install openssh-server 
```

Or, if you like, you could install SAMBA and configure the server to have the http docs directory accessible. You could mount your ubuntu box as network directory. So, you could edit your whatever  web project from your Windows box and have it running in your ubuntu box. Try this guide and look for folder/directory sharing:
[http://ubuntuguide.org/wiki/Dapper]("http://ubuntuguide.org/wiki/Dapper")

---

### Post by John.Michael.Kane on 2006-10-20
RunsWithScissors if your building from the server install.

You need to edit your sources.list

```
sudo nano /etc/apt/sources.list
```

uncomment the repo's. save the file,and exit

Run ```
sudo aptitude update
```

To install run
sudo aptitude install **(place your desktop and program choice here)**

these are some to pick from
ubuntu-desktop
xubuntu-desktop
kubuntu-desktop

---

### Post by RunsWithScissors on 2006-10-20
look like it is working thanx

---

### Post by Soarer on 2006-10-21
For remote logon, with full screen GUI,the best I have used is NX from NoMachine ([www.nomachine.com)](www.nomachine.com)).

Its free...

---

