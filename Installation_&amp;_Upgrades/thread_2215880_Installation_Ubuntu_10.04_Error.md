---
title: "Installation Ubuntu 10.04 Error"
date: 2014-04-08
forum: Installation &amp; Upgrades
---

### Post by leeyengyang on 2014-04-08
[COLOR=#000000]Hi guys,[/COLOR]

[COLOR=#000000]After i reboot my pc for Ubuntu 10.04 installation, then this error occur. Please Help.[/COLOR]

[IMG]http://i376.photobucket.com/albums/oo203/Vaynard_92/2014-04-09084823.jpg[/IMG]


[COLOR=#000000]Regards,[/COLOR]
[COLOR=#000000]YY[/COLOR]

---

### Post by SuperFreak on 2014-04-08
Are you trying a WUBI install of 10.04 (Ubuntu within Windows)? or a are you after a complete install with no Windows on the system? 
You should be aware that 10.04 is no longer supported and has been replaced by 12.04 LTS and in another week that will be superceded by 14.04LTS. A completely new install of 12.04  (or 14.04 if you wait a week or so)without Windows (ie Windows is wiped off of drive) I can probably help you with. You might do best though to use your Windows installation disc and once you are in the OS remove 10.04 from your programs in Control Panel of Windows
Is this an XP machine? If so best to ditch it entirely at this point

---

### Post by leeyengyang on 2014-04-10
I uninstall the previous version 12.04 because my college wants me to use version 10.04. When i open Wubi, it will ask for uninstall the previous version and proceed to install. Then i will Choose D drive as my Linux with 245gb out of 245gb because C drive contain Window. Then it will ask for reboot now. After reboot i choose Ubuntu from the boot up process and the this error Occur. Please Help

---

### Post by mastablasta on 2014-04-10
wubi can go to max. 30 GB or something like that.

in this case something went wrong as it says the file is not there or is corrupted. otherwise it should work. wubi installs inside windows on NTFS file system. it is no longer supported. and in 10.04 it had an issue after update.

you might want to explore the option of instaling it in virtualbox instead. as logn as you have at least 2 GB ram it shouldn't be an issue. have a look: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

also using 12.04 is not that much different especially if you install MATE desktop to it. 10.04 desktop is no longer supported but server is.

EDIt: do you need desktop or server? and why do you need it? for wehat purpose? in virtualbox server can be installed and then bridged. so it's like you are running a server, but the server is actually contained in virtualbox. there are even ready images that do not need install for that. ;-)

---

### Post by leeyengyang on 2014-04-10
Actually i doing a project, i need use linux for create a C programming code. i think i need desktop not server, and i got 2gb RAM and 10GB for it also..but not working. Where to change the option?
[IMG]http://i376.photobucket.com/albums/oo203/Vaynard_92/2014-04-11134640.jpg[/IMG]

---

### Post by mastablasta on 2014-04-11
ah ok so you need desktop. then it might be best to follow the guide in the link i posted. you can just use virtualbox and you could just use something more up to date like 12.04 and maybe xubuntu so it's lighter on the host operating system. asign it about 512 - 768 MB and you should be fine. you can choose even lighter desktop since desktop environment or even just a windows manager is probably not that important in your case (lubuntu, icewm, jwm, openbox...).

---

### Post by leeyengyang on 2014-04-11
I think i know what is the problem, I using Window 8,so that is the main reason the error occur..

---

