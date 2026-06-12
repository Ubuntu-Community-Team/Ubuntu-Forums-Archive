---
title: "I need help! (Ubuntu 9.10 Karmic Koala)"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by trixa_13 on 2010-03-25
[COLOR=Red]I need help everyone![/COLOR]

[COLOR=Purple]a.) How to repair Cairo Dock[/COLOR]
[COLOR=DarkGreen]b.) How to repair Update Manager[/COLOR]
[COLOR=Blue]c.) How to repair Add/Remove Applications[/COLOR]
[COLOR=DarkOrange]d.) How to repair Ubuntu Software Center[/COLOR]
[COLOR=Teal]e.) How to repair Synaptic Package Manager[/COLOR]






 [COLOR=Purple]Originally, I wanted to uninstall Cairo-Dock with OpenGL and I searched the internet for it. In it, it says to put the command, "sudo apt-get remove cairo-dock cairo-dock-plug-ins", in the terminal and I entered it. After the process was completed, there was a command with "apt-get autoremove" and I also entered it. Many installed packages was listed and I was prompted if I wanted to continue and I typed Y. Then, they were uninstalled. After I restarted and loggged out and logged back in, Cairo Dock with OpenGL was still there but no plug-ins were detected so it says that it will just close the application since it is useless to run the application with no plug-ins. I tried installing it again but there was an error which says:   

 "E:Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E:The list of sources could not be read."   

 So, I messed up Cairo Dock. If anyone knows how to repair it, please help! 
[/COLOR]   





 [COLOR=DarkGreen]After it, I noticed that there is a stop sign in my panel. I clicked it and the Update Manager showed up but there is also an error which says exactly the same above: 

 "An unresolvable problem occurred while initializing the package information.  Please report this bug against the 'update-manager' package and include the following error message:  'E:Malformed line 59 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read."   

 Please help![/COLOR]  






 [COLOR=Blue]I also opened Add/Remove Applications and it prompted me with an error:   

 "This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'." 

 Please help![/COLOR]  





[COLOR=DarkOrange]
 I also checked Ubuntu Software Center since I cannot open Add/Remove Applications. And it showed me that there were no installed applications! It do not also show any softwares that I haven't installed yet. In short, it is not working. I really do not know what to do. Please help me![/COLOR]





[COLOR=Teal]
[/COLOR]  [COLOR=Magenta][COLOR=Teal]Synaptic Manager is not also working. After I opened it, it showed me this message:   

 "E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."[/COLOR]

[/COLOR]   
 But I am not yet really acquainted with Ubuntu 9.10 Karmic Koala so I really do not know what to do. And I'm really afraid to edit anything since I messed up once.





    
 This is my sources.list:

[COLOR=DarkRed]# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
# newer versions of the distribution.

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu](http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu) karmic main ## Cairo-Dock-PPA-Weekly
deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) karmic main ## Cairo-Dock-PPA-Stable
deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) karmic main ## Cairo-Dock-PPA-Stable
deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) karmic cairo-dock ## Cairo-Dock-Stable
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe
deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) cairo-dock ## Cairo-Dock-Stable
deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) karmic cairo-dock ## Cairo-Dock-Stable
deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) karmic cairo-dock ## Cairo-Dock-Stable
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
[/COLOR]        

 And the 59th line is this:

[COLOR=DarkRed]deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) cairo-dock ## Cairo-Dock-Stable[/COLOR]


 Please help me! I really do not know what to do! If possible, please answer me within this day because I'm afraid that my father will find out after he comes home since we're both sharing a computer. I'm also using Ubuntu 9.10 Karmic Koala.


 Thanks in advance! =)

---

### Post by zvacet on 2010-03-25
I think that line should be 

deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) karmic cairo-dock ## Cairo-Dock-Stable

To correct that type in terminal

```
gksudo gedit /etc/apt/sources.list
```

and make that line look as above.Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

Maybe you will need 

```
sudo apt-get -f install
```

EDIT: next time let name of thread be more descriptive.That way you will get help faster and you will help others with same problems.

---

### Post by trixa_13 on 2010-03-25
> **zvacet said:**
> I think that line should be 

deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) karmic cairo-dock ## Cairo-Dock-Stable

To correct that type in terminal

```
gksudo gedit /etc/apt/sources.list
```and make that line look as above.Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```Maybe you will need 

```
sudo apt-get -f install
```EDIT: next time let name of thread be more descriptive.That way you will get help faster and you will help others with same problems.
[COLOR=DarkOrange]
[/COLOR][FONT=Comic Sans MS][SIZE=4][COLOR=DarkOrange]THANK YOU VERY MUCH! :p
I will keep your reminder in mind! [/COLOR][/SIZE][/FONT][COLOR=DarkOrange]:D[/COLOR]

---

### Post by daethyme on 2010-03-28
Hi, My problem is very much like Trixa except the line.

I can't do anything in the terminal due to this message:

E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/abiword-stable.list
E: Unable to lock the list directory

All the stated problems are the same, no synaptic pkg. access, No janitor access, no terminal access becuase it doesn't recognize sudo, and I can't remove Abiword, where all this started. I was upgrading from the terminal and quit, against the warning because it took forever... it still doesn't respond when i type the apt-get upgrade item. But it did spit out a software sources page and I see no problem w/ line 2... that message states this also:

E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/abiword-stable.list
E: Unable to lock the list directory

the synaptic message is:

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I don't know where or what the repository is where I'm supposed to go to fix this.

My sources list is:

  	 	 	 	 	 	   
 deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) karmic main restricted 
 deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) karmic main restricted 
  
 ## Major bug fix updates produced after the final release of the 
 ## distribution. 
 deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) karmic-updates main restricted 
 deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) karmic-updates main restricted 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
 ## team. Also, please note that software in universe WILL NOT receive any 
 ## review or updates from the Ubuntu security team. 
 deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) karmic universe 
 deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) karmic universe 
 deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) karmic-updates universe 
 deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) karmic-updates universe 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team, and may not be under a free licence. Please satisfy yourself as to  
 ## your rights to use the software. Also, please note that software in  
 ## multiverse WILL NOT receive any review or updates from the Ubuntu 
 ## security team. 
 deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) karmic multiverse 
 deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) karmic multiverse 
 deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) karmic-updates multiverse 
 deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) karmic-updates multiverse 
  
 ## Uncomment the following two lines to add software from the 'backports' 
 ## repository. 
 ## N.B. software from this repository may not have been tested as 
 ## extensively as that contained in the main release, although it includes 
 ## newer versions of some applications which may provide useful features. 
 ## Also, please note that software in backports WILL NOT receive any review 
 ## or updates from the Ubuntu security team. 
 # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse 
 # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse 
  
 ## Uncomment the following two lines to add software from Canonical's 
 ## 'partner' repository. 
 ## This software is not part of Ubuntu, but is offered by Canonical and the 
 ## respective vendors as a service to Ubuntu users. 
 # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner 
 # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner 
  
 deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) karmic-security main restricted 
 deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) karmic-security main restricted 
 deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) karmic-security universe 
 deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) karmic-security universe 
 deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) karmic-security multiverse 
 deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) karmic-security multiverse
 
I've read a bunch of posts and still do not see my issue.
thank you for any help.
dae

---

