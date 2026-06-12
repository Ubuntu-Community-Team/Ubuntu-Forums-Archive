---
title: "custom distro"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by Pete Griffin on 2012-02-12
I am looking for a little guidance re: custom distro.
I have:
[LIST]
[*]Ubuntu V.10 LTS
[*]Installed UCK, Docky
[*]Have created a new distro which includes Docky, latest updates, this all works as advertised.
[/LIST]
I have created what I call a standard config desktop for roll out. I would like to include, in the distro, all configuration that I have done on my desktop. ie. my Docky settings, any user accounts that I have created, wallpaper........ so that roll out is easier.

Any suggestions would be appreciated.

---

### Post by jerrrys on 2012-02-12
A place to start

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=custom+iso&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=custom+iso&sa=Search&cof=FORID:9)

---

### Post by Megaptera on 2012-02-12
and also don't overlook Remastersys ..." Remastersys is a tool that can be used to do 2 things with an existing Debian,  Ubuntu or derivative installation.
It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install. It can make a distributable copy you can share with friends.  This will not have any of your personal user data in it."
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by Pete Griffin on 2012-02-13
Thanks for your feedback.

I ran Remastersys, it is straight forward to use. The one issue that I ran into was when I took the image to another hardware configuration I kept getting an incompatible hardware error.  

Being a newby I am not very comfortable with command line instructions, but I guess this is the opportunity to learn, UCK and command line seems to be the way to go.

---

### Post by mastablasta on 2012-02-13
> **Pete Griffin said:**
>  
I ran Remastersys, it is straight forward to use. The one issue that I ran into was when I took the image to another hardware configuration I kept getting an incompatible hardware error. 
 
 
Did you maybe use some proprietary drivers on the system you remastered? or some special settings? 
if you did, then remove those and remaster it again. usign opensource ones should make it more compatible with other PC configurations.

---

### Post by Pete Griffin on 2012-02-13
I believe that it is a processor issue. My dev system is an AMD and target is P4 laptop. According to some blogs this is an issue for neophytes like myself.

---

### Post by mastablasta on 2012-02-13
well 64bit OS won't fit onto a maschine with 32bit CPU, but a 32bit OS will fit on a maschine with 64bit CPU ;-)

i believe some pentiums 4 were indeed 32bit

---

