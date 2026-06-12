---
title: "ubuntu desktoop- reinstalling"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by mmistroni on 2006-12-12
hi all,
 i m fairlynew to Ubuntu (having been a  windows user for long time).
with help of a friend,,i installed ubuntu breezy on my machine from CD-rom.
after playing around for a while, i decided to upgrade to dapper and i found a link on the web on how to do that.
well, being not an expert i just launched commands listed on the site... with end result of ubuntu removing completely my ubuntu-desktop application.. so that now i am working with commadn prompt.
I am desperately trying to install ubuntu-desktop (at least for having browser)_, but every time i do that ubuntu complaints that 
 ' Depends on XX but it is not going to be installed
I tried the painful process of installing one by one the missing dependencies of ubuntu-desktop, btu this results in other missing dependencies.... and i m sure there must be a way to install an app where the system automatically resolves dependencies...

can anyone help me out? i'd  need to install ubuntu-desktop asap..

thanks in advance and regars
 marco

---

### Post by taurus on 2006-12-12
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by mmistroni on 2006-12-12
Hello taurus,
 thanks for your quick reply
unfortunately i have tried to run commands you suggested

but every time i launch sudo aptitude install ubuntu-desktop it keeps on erroring out saying
Depends on 'xxx' and it is not going to be installed

are there any way to resolve dependencies automatically?

worst thing in my case is that i dont even have browser onlinux so i need to keep on switching between win and linux to see posts and try...

thanks and regards
 marco

---

### Post by taurus on 2006-12-12
What package is that "xxx" thing?  It would be nice to know the name of that package so you can install it.  Otherwise, try installing KDE then...

```
sudo aptitude install kubuntu-desktop
sudo /etc/init.d/kdm start
```

---

### Post by mmistroni on 2006-12-12
Hello,
 packages... are many
i haven't copied all of them, but below are some of them
bluez-pin
evolution
evolution-exchange
evince
dbus-1util  

and so on
installing the above one by one still results in other missing dependencies.
i have read that sudo aptitude install install also dependencies,but for some weird reasons it seems it is not working that way on my ubuntu...

any other hints are appreciated

thanks again
 marco

---

### Post by mmistroni on 2006-12-12
hello taurus,
 still no luck [-( 

tried your latest suggestion, ubuntu complaints that some packages are missing
- gstreamer0.8-misc
- gstreamer-vorbis
- gtk2-engines-gtk-qt
- smbclient

i tried to install one of them, but it ssays that it is missing so me other dependencies.. where the version installed is ,for example, 2.0.0 and the one required is >= 2.8.0

i have tried, (as a sample) for a missing libgtk2.0-0 (required >= 2.8.0)
to launch command 

sudo aptitude install libgtk=2.8.0 but it says that it is not able to resolve library...

looks like i m entering command wrong... and also that i havet o go thru the long way of installing dependencies one by one.....
i can give up ubuntu-desktop, but i desperately  need a browser so i can  browse for ubuntu forums rather than keep on switching to windows all the time...

---

### Post by taurus on 2006-12-12
Looks to me like while going from Breezy to Edgy, it broke big time!!!  I recommend you backup your important files and reinstall Edgy from fresh instead of upgrading...

---

### Post by mmistroni on 2006-12-12
hello taurus,
 well actually it broke big time in trying to move from breezy to dapper..
i have one quick question for you, before i reinstall: i still have with me the CD with breezy version.
Is it enough that i boot the machine with the CD in? will it uninstall ubuntu and reinstall automatically, or do i have to remove the current version by myself?
if so, how?

thanks in advance and regards
 marco

---

### Post by taurus on 2006-12-12
The LiveCD won't remove the previous version for your automatically.  You just have to click the install icon to install it.  It will then ask you where you want to install so point it to where / and swap are.  Don't forget to tell the installer to format them.  However, I recommend you download and install the Edgy version instead...  It's faster and nicer than the Breezy version.  ;)

---

### Post by greylica on 2006-12-12
This is the most common linux newbie user problem, the partition scheme.
Ever, ever do it in 4 partitions if you know partitioning :

/boot ( ext3 ) 200mb ( better than suficient )
/swap ( swap ) 1X ~ 2X your amount of Ram
/     ( ext3 ) at least 8GB depending on the programs used.
/home ( ext3 ) the way you want

if something goes wrong, do not format /home
reinstall everything on the same partitions as they are intended.
This way you can avoid loose your data, and can always do a clean install.

---

