---
title: "Howto Boot install from iso like knoppix"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by Asos_Illusionist on 2007-02-03
I've got a strage situation here.. like most people i've got a laptop without a cd-rom..

It's a fijitsu amilo d 8820 that had a cd-rom, but now it's dead.. it works once in like 100 times and just for some minutes.. just to try to boot something minimum out of it.. not even a windows installation.. nah..

I've managed to install last year a knoppix distro by removing the hd from the laptop puting it on a usb frame and downloading the iso in it.. then putting it back to the laptop and booted from the same burned distro and then in the line i've inputed something like
boot=/mnt/hda1/knoppix.iso
and the installation started from the iso..

Now my present story..

I'm an ubuntu (kubuntu) user like more than a year now and i just love it ( :) )..
I've got it on my other "new" laptop (an acer 5024wlmi with ndiswrapper wifi 100% hoho)
I've also have it on 2 desktops..
Now i need it on the fujitsu.. cause i'm gonna use it as a car pc..

THE QUESTION..

Is there a way to boot install the kubuntu (xubuntu/ubuntu) distro from the iso with a way similar to knoppix iso boot install..??

Thank you very much..!

P.s. sorry'bout my lagy english.. greek people here!! :) :) :KS ):P

---

### Post by glabouni on 2007-02-03
[HOWTO: Install Edgy 6.10 from an .iso file (hd-media)]("http://www.ubuntuforums.org/showthread.php?t=316093")

if your fujistsu laptop has windows installed you can also refer to 
[Install GNU/Linux without any CD, floppy, USB-key, nor any other removable media]("http://marc.herbert.free.fr/linux/win2linstall.html")

if your fujistsu laptop has windows installed and internet access, you can try installing directly from inside windows: [http://cutlersoftware.com/ubuntusetup/](http://cutlersoftware.com/ubuntusetup/)

---

### Post by Asos_Illusionist on 2007-02-04
The fujitsu laptop only has a knoppix distro cause you can't install anything heavier because it "also" has a heating problem cause it "is" 4 years old, and i can't fix it cause i must send it abroad.. and that'll cost me a lot..
If i try to install something it just shutdown for safety.. 

The knoppix install is the only thing i've tried that didn't heat up the system to that degree to shut it down.. and i home a (xku)buntu system has the same kind of light install..

I'm gonna try some and give the results here..

Thanx anyway..

P.s. is it better through network?

---

### Post by Asos_Illusionist on 2007-02-05
I've managed somthing.. heh..

i used the guide from this thread
[http://www.ubuntuforums.org/showthread.php?t=316093](http://www.ubuntuforums.org/showthread.php?t=316093)

i made the grub work with the boot images the installation started and i stoped at the step of making a looped device..

..nice.. :) :guitar:

---

