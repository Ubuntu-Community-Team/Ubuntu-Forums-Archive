---
title: "Server Install w/ xserver?"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by tonydm on 2006-08-06
Hi all,

I am wanting to install the server version of Ubuntu.  I like the idea of "LAMP" and having all four key servers installed in an integrated and configured fashion at installation.  However, I do like having the GUI.  The Download page says that the Server version does not install an xserver.  Is this statement saying it "can't" be selected and installed as an option at the time of installation?

Thank you

Tony

---

### Post by neilp85 on 2006-08-06
I have an idea that you might want to try. After installing the LAMP server you could try installing the ubuntu GUI using apt.

sudo apt-get ubuntu-desktop

According to the description that package depends on all the packages needed to run the Ubuntu desktop. I haven't tried this myself, nor do I know if this is even feasible but it might be worth a shot. The main problem I foresee with this is the configuration of the Xorg. I'm not sure if installing this package will handle of the necassary setup. There are probably other problems that I'm too shortsighted to see but if this does work I think that would be pretty cool. If you try this could you post about the experience as I'm sure others may want to know.

---

### Post by az on 2006-08-06
> **tonydm said:**
>  Is this statement saying it "can't" be selected and installed as an option at the time of installation?

Thank you

Tony

Using the server cd, no, you cannot install a GUI at the time of installation.  You can, however, install one once you reboot into your new system.

Install, reboot and then log in.  The run

sudo apt-get install ubuntu-desktop linux-386
and that will fetch the packages from the ubuntu repositories and install them.

Alternatively, you can acheive the same thing by installing the Desktop version of Ubuntu (from a shipit cd or just download the Desktop cd) and then installing

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

The desktop packaged do not interfere with the LAMP packages and vice versa.  The linux-386 package will install a desktop kernel which will run server applications just fine, and will handle extra dektop-type doodads like funky mice and stuff.

You probably don't want to be running a desktop environment on a production server, since that goes against best-security practices, which is why there is no GUI on the Server cd.

---

### Post by az on 2006-08-06
> **neilp85 said:**
> The main problem I foresee with this is the configuration of the Xorg. I'm not sure if installing this package will handle of the necassary setup. There are probably other problems that I'm too shortsighted to see but if this does work I think that would be pretty cool. 

I does work and it is cool.  When installing, xserver-xorg will scan and configure the graphic hardware.

As mentioned above, you will probably need a desktop kernel or your mouse may not move.

---

### Post by tonydm on 2006-08-06
Thanks guys, for your replies.

I'll give it a try.  I simply like working in a GUI environment when configuring things and like webmin as well as the GUI mysql utils.  You get spoiled, I admit, using the Windoze and Gnome GUI's after years of DOS and command lines, batch files, scripts, and the like.  I seem to fight the text based editors in unix.  So I pander to my challenge.

Thanks again

Tony

---

### Post by tonydm on 2006-08-08
Azz, your right.  It does work and it is slick!:p   After a while, I was up and running with a desktop.  I love it.  Thanks again.

Tony

---

### Post by DaBruGo on 2006-08-09
> **azz said:**
> 
 
You probably don't want to be running a desktop environment on a production server, since that goes against best-security practices, which is why there is no GUI on the Server cd.
 
Hi AZZ,
 
I have a quick question about server security (if someone chooses to run a desktop environment on a production server).
 
Is it safe to have a desktop environment on a server as long as you only have it running when you want to briefly use it and then get out of it?
 
For example, I have been playing around with ubuntu and fluxbox on a USB memory stick [(here)]("http://www.ubuntuforums.org/showpost.php?p=903914&postcount=53") and it seems to run fairly well. All I do is login at the command prompt when I startup the computer and then I run the "startx" command to get into the desktop environment (fluxbox). And when I am done, I just exit out of fluxbox and am back to a command prompt.
 
Is that a relatively safe way to use a desktop environment on a production server, or is it inherently dangerous just because you have the desktop environment loaded in general.
 
Just curious,

 
Dave

---

### Post by DaBruGo on 2006-08-10
> **DaBruGo said:**
> Hi AZZ,
 
I have a quick question about server security (if someone chooses to run a desktop environment on a production server).
 
Is it safe to have a desktop environment on a server as long as you only have it running when you want to briefly use it and then get out of it?
 
For example, I have been playing around with ubuntu and fluxbox on a USB memory stick [(here)]("http://www.ubuntuforums.org/showpost.php?p=903914&postcount=53") and it seems to run fairly well. All I do is login at the command prompt when I startup the computer and then I run the "startx" command to get into the desktop environment (fluxbox). And when I am done, I just exit out of fluxbox and am back to a command prompt.
 
Is that a relatively safe way to use a desktop environment on a production server, or is it inherently dangerous just because you have the desktop environment loaded in general.
 
Just curious,
 
 
Dave
 
anyone got any advice on this...

---

