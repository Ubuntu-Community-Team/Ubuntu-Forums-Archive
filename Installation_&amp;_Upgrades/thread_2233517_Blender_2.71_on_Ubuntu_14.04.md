---
title: "Blender 2.71 on Ubuntu 14.04"
date: 2014-07-09
forum: Installation &amp; Upgrades
---

### Post by captain_chaos2 on 2014-07-09
Hi
In 12.04 I simply extract the Blender 2.71 tar.bz in my home folder open the file and run the program.
In 14.04 this doesn't work, could it be as a result of my encrypting my home folder? 12.04 is not encrypted.
If so I will have to reinstall 14.04 but I would rather make sure first?

Thanks

---

### Post by hbutt875 on 2014-07-09
Try installing Blender from Ubuntu software center.:KS

---

### Post by claracc on 2014-07-09
There is a ppa repository for blender 2.71: [https://launchpad.net/~irie/+archive/ubuntu/blender?field.series_filter=trusty](https://launchpad.net/~irie/+archive/ubuntu/blender?field.series_filter=trusty)

Perhaps you will be more lucky trying to install blender from the ppa: [http://linuxg.net/how-to-install-blender-2-71-on-ubuntu-linux-mint-pinguy-os-elementary-os-and-their-derivative-systems/](http://linuxg.net/how-to-install-blender-2-71-on-ubuntu-linux-mint-pinguy-os-elementary-os-and-their-derivative-systems/) as the forementioned link addresses.

---

### Post by captain_chaos2 on 2014-07-09
Thanks but Software Center only has Blender 2.69,I have been down this road with 12.04.
 
Could it be as a result of my encrypting my home folder? 12.04 is not encrypted.

---

### Post by captain_chaos2 on 2014-07-09
HI [ 						 					]("http://ubuntuforums.org/member.php?u=749536") 				 				 					 						 	[**[COLOR=#000000]claracc[/COLOR]**]("http://ubuntuforums.org/member.php?u=749536")

I was trying to stay away from using the ppa and just loading the tar onto a memory stick and moving it across

---

### Post by captain_chaos2 on 2014-07-09
Thanks   				 				 					 						 	[**[COLOR=#000000]claracc[/COLOR]**]("http://ubuntuforums.org/member.php?u=749536")

The  [http://linuxg.net/how-to-install-ble...ative-systems/]("http://linuxg.net/how-to-install-blender-2-71-on-ubuntu-linux-mint-pinguy-os-elementary-os-and-their-derivative-systems/") link is excellent:guitar:

I would still like to know if it could it be as a result of my encrypting my home folder? 12.04 is not encrypted. 				If anyone knows?

---

### Post by claracc on 2014-07-09
You are very welcome.

I don't think the problem is to have your home folder encrypted, but I am not an expert, perhaps more expertize users can give you better explanation. My reason is that if the installation from ppa works and the one from deb package no, the problem would be dependencies.

When you extract the deb.tar package, do you obtain any error?, the file is extracted?, where is the file located?.

---

### Post by captain_chaos2 on 2014-07-09
> do you obtain any error?Nope, 
> the file is extracted?yep,
> where is the file located? I extracted first in a new folder called "Programs" in my home dir, then in the home dir and again in desktop, which is basically in home anyway and the executable wouldn't work (double clicking or right clicking and run) in any, which led me to believe it may be as a result of the encryption.
Maybe someone can shed some light. 
In the meantime I'm just trialing 14.04, it looks good.

---

### Post by monkeybrain20122 on 2014-07-09
It works here. 

Try run it in the terminal and see the error message
```
cd path/to/blender/folder
./blender
```

---

### Post by captain_chaos2 on 2014-07-09
Ok I removed blender   ..$ sudo apt-get remove blender.. ,disconnected internet and reloaded from USB stick and extracted to file /home/blender, double clicked the exe file and as you say it works. 
Why it did not work before is a mystery to me.

Both your codes turn up No such file or directory messages. S no worries it's working.

Thanks for the help.

---

### Post by monkeybrain20122 on 2014-07-09
exe file???!!!

---

### Post by kostya2 on 2014-10-01
To instal the lastest version use:

[COLOR=#555555][FONT=consolas]$ sudo add-apt-repository ppa:irie/blender[/FONT][/COLOR]
[COLOR=#555555][FONT=consolas]$ sudo apt-get update[/FONT][/COLOR]
[COLOR=#555555][FONT=consolas]$ sudo apt-get install blender

[/FONT][/COLOR]But any other version should be removed before it.
To remove, type:

[COLOR=#555555][FONT=consolas]$ sudo apt-get remove blender[/FONT][/COLOR]

---

### Post by safaldasg on 2014-10-06
Guys first install synaptic package manager
search for libSDL
install libsdl1.2-dev
Then again try running blender 2.71

---

### Post by treepleks on 2015-01-02
IRIE's PPA has not been updated for more than 6 months now. You may have a try to this  [alternate PPA]("https://launchpad.net/~thomas-schiex/+archive/ubuntu/blender") that has 2.73rc1 on it.

```
sudo add-apt-repository ppa:thomas-schiex/blender
sudo apt-get update
sudo apt-get install blender

```

---

### Post by hellocatfood on 2015-01-04
If you don't fancy adding a PPA then myself and others have provided instrucitons for installing manually. [http://askubuntu.com/a/568813/6689]("http://askubuntu.com/a/568813/6689")

---

### Post by treepleks on 2015-02-13
> **hellocatfood said:**
> If you don't fancy adding a PPA...[/URL]

What would be the advantage compared to a PPA that provides automated updates, a clean install/uninstall, which is signed digitally, and which also avoids redundancies (python3.4, ffmeg libraries...) that use disk (and RAM is you use another ffmepg dependent software at the same time) ?

---

