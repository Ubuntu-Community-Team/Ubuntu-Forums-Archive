---
title: "Ubuntu 9.10 alpha 4 wont boot"
date: 2009-08-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tkblackbelt on 2009-08-23
I just did a fresh install of alpha 4 and it boots to a terminal login  thing and never reaches the gui. also when i tryed start x it said fatal error no screens found.If anyone knows how to fix this it would be appreiciated

---

### Post by tkblackbelt on 2009-08-24
this is what it says when i type start 
x startx = fatal server error:
no screens found

ddxSigGiveUp: Closing log
giving up

xinit: No such file of directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error."

---

### Post by taavikko on 2009-08-24
Would help if knowing what kind of an video-chip you have?

---

### Post by redzsky on 2009-08-24
am having the same trouble after upgrading from 9.04 it could find my graphics card and but couldnt make it active, so i tried it anyway and after boot and it now just come up with blank screen ,it will still shut down though.manage to remove my graphics card by using dkms options and even ran dpkg from the rcovery menu to fix anything broken  but still no startx says no screen fatal error going to try sudo apt-get install xserver-xorg-video-ati but anyhelp would be appreciated, thanks
 
i just upgrade from not sure if it alpha4 but i think that the newest so it probably downloaded that it was from 2days ago..........

---

### Post by taavikko on 2009-08-24
> **redzsky said:**
> am having the same trouble after upgrading from 9.04 it could find my graphics card and but couldnt make it active, so i tried it anyway and after boot and it now just come up with blank screen ,it will still shut down though.manage to remove my graphics card by using dkms options and even ran dpkg from the rcovery menu to fix anything broken  but still no startx says no screen fatal error going to try sudo apt-get install xserver-xorg-video-ati but anyhelp would be appreciated, thanks
 
i just upgrade from not sure if it alpha4 but i think that the newest so it probably downloaded that it was from 2days ago..........

Purge the fglrx driver altogether,
```
sudo aptitude purge xorg-driver-fglrx
```
Then clean up the xorg.xonf
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And restart

If doing them in recovery-mode, leave the sudo out in the commands.

---

### Post by redzsky on 2009-08-24
tried that but i have a geforce 7400 go, sorry my mistake in  not specifying that. was just trying that  command  and it said on the net  it was for nvidia as well as ati( sudo apt-get install xserver-xorg-video-ati) .i tried also your commands
sudo aptitude purge xorg-driver-fglrx
sudo dpkg-reconfigure -phigh xserver-xorg
and it removed the flgrx drivers also the second line return nothing just goes to command line again.
could you please tell me ,what is the code for linux graphics driver for nvdia and i`ll try your code again, sorry for my misleading comment.i`ll try nvidia also thanks for the speedy reply and the help.

---

### Post by Eclipse. on 2009-08-24
Hi, judging from your post running alpha software is mabey not the best option for you.9.04 is the latest stable release and is better suited for you.:)

---

### Post by Lutin on 2009-08-25
I had the same problem with an old Dell Dimension 2400 (Intel integrated graphics) and the only way I could get the GUI to start was to boot the machine with the acpi=off option.

Details in this thread -

[http://ubuntuforums.org/showthread.php?t=1244380&highlight=acpi](http://ubuntuforums.org/showthread.php?t=1244380&highlight=acpi)

Though I would go with the wise words of BwackNinja (post number 2) and edit /etc/default/grub and NOT grub.cfg. Though you will have to run "update grub" after editing - but only the once.

Hope that helps.

---

### Post by nedrige on 2009-08-25
I had the same problem. Tried:
    sudo aptitude purge xorg-driver-fglrx
    sudo dpkg-reconfigure -phigh xserver-xorg

The dpkg-reconfigure seem to do nothing. So I renamed the xorg.conf and copied the xorg.con.failsafe to xorg.conf. After that I could start the X.


cd /etc/X11
mv xorg.conf xorg.conf.something
sudo cp xorg.conf.failsafe xorg.conf
startx # or sudo /etc/init.d/gdm start

---

### Post by taavikko on 2009-08-25
> **redzsky said:**
> tried that but i have a geforce 7400 go, sorry my mistake in  not specifying that. was just trying that  command  and it said on the net  it was for nvidia as well as ati( sudo apt-get install xserver-xorg-video-ati) .i tried also your commands
sudo aptitude purge xorg-driver-fglrx
sudo dpkg-reconfigure -phigh xserver-xorg
and it removed the flgrx drivers also the second line return nothing just goes to command line again.
could you please tell me ,what is the code for linux graphics driver for nvdia and i`ll try your code again, sorry for my misleading comment.i`ll try nvidia also thanks for the speedy reply and the help.

yep.
Check that nvidia is been properly installed
```
sudo aptitude reinstall nvidia-185-kernel-source
dkms status
```

And add {Driver "nvidia"} to xorg.conf

---

### Post by gradinaruvasile on 2009-08-25
Yup, the nv opensource driver doesnt work with nvidia (i have a 8200 IGP). Install the restricted drivers.
U can do it in live mode too. The simplest way is to have a downloaded driver from the site (.run extension). Boot with livecd (x crashes), mount the drive where u have the driver, run it with sudo, start x or gdm. 
I used a usb stick to boot, made 2 partitions on it, copied the driver to the second partition - i couldnt mount the first one cause it contains the boot system.

---

### Post by redzsky on 2009-08-25
yep.
Check that nvidia is been properly installed
 	Code:
 	sudo aptitude reinstall nvidia-185-kernel-source
dkms status 
And add {Driver "nvidia"} to xorg.conf 		                   		  		  		 		 			 				__________________
thanks man tried that out code,it reinstalled driver but i think it just a bug in new version that the graphics card does`t work just now maybe .if there any chance you could explain how to make it load up without the graphics card cause it was workin before with out graphics acceleration. i`ll just have to wait till they have sorted out bugs just wanna be able to load up the desktop  to gain easy access to my files and maybe try out a different version of drivers.when i tried your code when booted up the screen goes blank without a underscore and when i switch it off it does`t show shutdown screen anymore.thanks for your help i think it was the correct information though the alpha is still buggy and if anyone can point out which files(log files and that) i should send to ubuntu to help them and help me run the best operating system in the world.thanks for everyone help and free support(which we are all lucky for that at some point in the ubuntu community unless your running windoze cause there aint fRee unless u take the R out and that spells fee support) many thanks

---

### Post by redzsky on 2009-08-25
success atleast am able to boot back in to ubuntu no windows manager and graphics acceleration. nvidia drivers says its installed but not built and firefox does seem to work even though my net connection is connected. i removed the graphics card driver with 
dkms status anand then dkms reinstall -m nvidia -v 185.18.31 -k 2.6.31-6-generic thanks for the help atleast its gotten me back into the system and i can try other stuff out now
dont know if i should try to dkms build now i still can get the graphics driver to be active any ideas?

---

### Post by redzsky on 2009-08-25
not quite sure what fixed it it was probably "sudo aptitude reinstall nvidia-185-kernel-source , and firefox now works that was am using to type this

---

### Post by redzsky on 2009-08-25
had to disable emerald and put it back to default windows manager
you can create a launcher or run from command:

to switch to emerald: "emerald --replace"
to switch to gnome default metacity: "metacity --replace"

for anyone else with the same problem

---

### Post by redzsky on 2009-08-26
anyone else with the graphics card problem should get do a seach in google for "dinxter nvidia driver" without the quotes    

thats me solved my problem and have ubuntu 9.10 running near perfect apart from tiny graphic glitch on the menu in firefox  it blanks slightly out at the wrong time wioth compizfusion

---

### Post by redzsky on 2009-08-26
[https://bugs.launchpad.net](https://bugs.launchpad.net) and my version was 173

---

