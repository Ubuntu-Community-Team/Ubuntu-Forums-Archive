---
title: "searchin a minimal jaunty cd image"
date: 2009-02-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cmay on 2009-02-28
i have been running jaunty for some month but i reinstalled debian for a while and going back to jaunty is a bit hard since the different iso image i get downloaded wont work for some reason or anohter. 

is there anyone that knows where i can  a iso image of jaunty that has the alternative installer and will let me uncheck everything (desktop && standardsystem ) like in debian so i can use openbox.

 i have one pc i use regular for testing beta versions of linux and to try something new with 700 mzh and 512 mb ram but its in use for something else right now so i would like to try and run jaunty on my  really old pc wiht 600 mzh and 300 mb ram and use openbox and lxde for desktop. 

it runs blazingly fast with debian lenny that way so i figure i could make jaunty run good enough on those specs. 

thanks for the time.

---

### Post by MarblePanther on 2009-02-28
[http://cdimage.ubuntulinux.org/daily/current/](http://cdimage.ubuntulinux.org/daily/current/)

---

### Post by broussaille on 2009-02-28
[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/)

here are mini iso / about 10 mio

---

### Post by cmay on 2009-02-28
> **MarblePanther said:**
> [http://cdimage.ubuntulinux.org/daily/current/](http://cdimage.ubuntulinux.org/daily/current/)
sorry i have to ask but how come they are oversized and can not fit on a cd?

---

### Post by MarblePanther on 2009-02-28
> **cmay said:**
> sorry i have to ask but how come they are oversized and can not fit on a cd?

They mention that its a bug of some sort.  Maybe they were too hasty in building the image.  You can always use the usb-installer to install to a usb-drive though or burn it to a dvd.

---

### Post by cmay on 2009-02-28
> **MarblePanther said:**
> They mention that its a bug of some sort.  Maybe they were too hasty in building the image.  You can always use the usb-installer to install to a usb-drive though or burn it to a dvd.
  
thanks.

i can not use the dvd as i have a computer with out the dvd drive to use for jaunty this time. its my old computer and it still uses a cd-rw drive so i figured i would do like i do on debian with a minimal install but it seems like its easyer to install gobuntu which i got on a cd and just upgrade.

 or the regular hardy image if that will install on the specs 600 mzh and 300 mb ram. i had xubuntu in it for a very short time but i can have more light distros running great on it. debian and vector linux is very fast.
 
thanks for the time anyway.

---

### Post by MarblePanther on 2009-02-28
> **cmay said:**
> thanks.

i can not use the dvd as i have a computer with out the dvd drive to use for jaunty this time. its my old computer and it still uses a cd-rw drive so i figured i would do like i do on debian with a minimal install but it seems like its easyer to install gobuntu which i got on a cd and just upgrade.

 or the regular hardy image if that will install on the specs 600 mzh and 300 mb ram. i had xubuntu in it for a very short time but i can have more light distros running great on it. debian and vector linux is very fast.
 
thanks for the time anyway.

I understand, I also do not have a dvd burner.  But like the OP mentioned, you can also use the mini .iso's.

Why not Intrepid?  You can always use the Intrepid server install disc and choose whatever graphical environment you want.
(Which will work for your RAM).  You can also use the alternate cd for Intrepid.
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

---

### Post by cmay on 2009-02-28
yes thats the option i guess. i have burned too many bad cd lately and i  really would like not to waste anymore but the alterative intrepid i think could come in handy someday so i think i want to try get of those burned right. i have a old drive and sometimes its not burning the images correct so i end up wiht useless datadisks and for live cd or install cd i even burn at lowest speed but still too many of them do not work right. 
i can always upgrade from the regular intrepid disk i already have if i cant get the altenative burned right. 
thanks.

---

### Post by MarblePanther on 2009-02-28
No problem.  If you have a 1gb usb stick, that might be more useful to install an image onto that.

---

### Post by jerrylamos on 2009-02-28
Here's the alternates that will fit on a CD and are pretty current:

[http://cdimage.ubuntu.com/releases/jaunty/alpha-5/](http://cdimage.ubuntu.com/releases/jaunty/alpha-5/)

Should boot and run install on a 256 mb pc.  It uses text mode screens which you can get used to after a few times.  Much much less trouble than the graphical installer ubiquity on ubuntu which doesn't work for me most of the time.

I do use manual partitioning to put the image in the partition I want.  Lately 5 gb is plenty of space.

I use CD/RW which work for several burns before needing replaced.  Much cheaper that way.

My older pc's use intel graphics chips which jaunty doesn't run on unless you boot in rescue mode then do 
xfix attempt to fix xorg.conf
select root prompt
nano /etc/X11/xorg.conf
after "Configured Video Device" put:
OPTION "NoAccel"
ctrl-o
ctrl-x
exit
resume normal boot

jerry

---

### Post by cmay on 2009-03-01
> **jerrylamos said:**
> Here's the alternates that will fit on a CD and are pretty current:

[http://cdimage.ubuntu.com/releases/jaunty/alpha-5/](http://cdimage.ubuntu.com/releases/jaunty/alpha-5/)

Should boot and run install on a 256 mb pc.  It uses text mode screens which you can get used to after a few times.  Much much less trouble than the graphical installer ubiquity on ubuntu which doesn't work for me most of the time.

I do use manual partitioning to put the image in the partition I want.  Lately 5 gb is plenty of space.

I use CD/RW which work for several burns before needing replaced.  Much cheaper that way.

My older pc's use intel graphics chips which jaunty doesn't run on unless you boot in rescue mode then do 
xfix attempt to fix xorg.conf
select root prompt
nano /etc/X11/xorg.conf
after "Configured Video Device" put:
OPTION "NoAccel"
ctrl-o
ctrl-x
exit
resume normal boot

jerry

i wish the jaunty release would include a textbased install option like in gutsy. i am used to using debian minimal install image and i can better use the textbased and the livecd installer has some bugs in it. i almost quit using ubuntu becouse i had a really hard time getting hardy and intrepid installed. i still use gutsy to install intrepid. i have to upgrade from gutsy . i have not been able to burn an succcenfull burn of hardy or intrepid alternative installer yet.

---

