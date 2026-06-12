---
title: "GDM Missing Can't logon deleted gnome 3"
date: 2011-10-10
forum: Installation &amp; Upgrades
---

### Post by liouvina on 2011-10-10
So I upgraded to 11.04 everything was working fine and then upgraded to gnome 3 and decided I wanted unity back so I tried to remove gnome 3 so I can use unity and messed up a lot of stuff. My gdm login screen is missing and when I try to reinstall ubuntu-desktop it gives me errors and I have no idea what to do from here. Please help me. =(

---

### Post by MAFoElffen on 2011-10-10
> **liouvina said:**
> So I upgraded to 11.04 everything was working fine and then upgraded to gnome 3 and decided I wanted unity back so I tried to remove gnome 3 so I can use unity and messed up a lot of stuff. My gdm login screen is missing and when I try to reinstall ubuntu-desktop it gives me errors and I have no idea what to do from here. Please help me. =(
I don't know what Gnome3 removed... or what errors you siad it gave you on reinstalling ubuntu-desktop.  It sounds like it left some unresolved dependencies.

Did you install gnome 3 through sysnaptic or through the gnome 3 PPA?

If PPA, did you remove the PPA and purge PPA?

Did you try to install ubuntu-desktop from apt-get, synaptic or aptitude?

If you are at a commandline, what if you did
```

rm -r ~/.gnome*

```That would remove your customisation from gnome, to avoid any conflict between gnome3 and gnome2...
```

sudo service gdm stop
sudo apt-get remove --purge ubutnu-desktop
sudo apt-get update
sudo apt-get -f
sudo apt-get dist-upgrade
sudo apt-get install ubuntu-desktop
sudo apt-get update
sudo service gdn start

```

---

### Post by liouvina on 2011-10-12
I'm not sure. I'm not new to Ubuntu, I've just never messed around with it this much. I upgraded to 11.04 and upgraded to gnome 3, I'm pretty sure via ppa and then realized I didn't like it so tryed to go back to gnome 2 so I can use unity, ended up messing a lot of dependencies up for Ubuntu-Desktop when I tried using your steps it told me "package ubuntu-desktop is not installed so not removed. It later told me after I tried "sudo apt-get update 
"E:Type Ain is not known on line 2 in source list /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list. 
E: The list of sources could not be read. 
 
Also, I can't log onto Ubuntu. I've been trying to fix it via recovery mode "Drop to Root shell prompt. Thank you so much for trying to help. I'm beyond helpless and frustrated. =(

---

### Post by liouvina on 2011-10-12
Also I tried to install Ubuntu-desktop from your instructions and it prompted me with this:
 
The following packages have unmet dependencies
Ubuntu-Desktop : 
Depends: Alacarte
Depends: Baobab
Depends: evince
Depends: Gedit
Depends: Gnome-Applets
Depends: Gnome-control-center
Depends: Gnome-Menus
Depends: Gnome-Panel
Depends: Gnome-Screenshot
Depends: Gnome-Search-Tool
Depends: Gnome-Session
Depends: Gnome-system-log
Depends: Gnome-Terminal
Depends: Indicator-applet-session
Depends: Metacity
Depends: Nautilus
Depends: Software-Center
Recommends: Brasero
Recommends: Empathy
Recommends: Evolution
Recommends: Evolution-exchange
Recommends: Nautilus-Share
Recommends: totem
Recommends: totem Mozilla

---

### Post by liouvina on 2011-10-12
Also, when I tried "rm -r ~/.gnome*" It told me this, 
 
"rm: cant remove '/root/.gnome*:No such file or directory

---

### Post by MAFoElffen on 2011-10-12
> **liouvina said:**
> I'm not sure. I'm not new to Ubuntu, I've just never messed around with it this much. I upgraded to 11.04 and upgraded to gnome 3, I'm pretty sure via ppa and then realized I didn't like it so tryed to go back to gnome 2 so I can use unity, ended up messing a lot of dependencies up for Ubuntu-Desktop when I tried using your steps it told me "package ubuntu-desktop is not installed so not removed. It later told me after I tried "sudo apt-get update 
[COLOR=Red]"E:Type Ain is not known on line 2 in source list /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list. 
E: The list of sources could not be read. [/COLOR]
 
Also, I can't log onto Ubuntu. I've been trying to fix it via recovery mode "Drop to Root shell prompt. Thank you so much for trying to help. I'm beyond helpless and frustrated. =(
See your error above in red?  Remember when I ask if you removed and purged the Gnome3 PPA?  I can see you didn't as it is still looking there...

Do this first
```

sudo ppa-purge ppa:gnome3-team/gnome3/ubuntu[FONT=monospace]
[/FONT]
```
Or edit these line manual out of your software sources
```

deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) natty main  
deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) natty main 

```

---

### Post by liouvina on 2011-10-12
When I try "sudo ppa-purge ppa:gnome3-team/gnome3/ubuntu" 
 
It gives me this, 
 
"E: Type 'ain' is not known on line 3 in source list /etc/appt/sources.list.d/gnome3-team-gnome3-natty.list
E: The list could not be read. 
Warning: apt-get update failed for some reason
 
ppa to be removed: gnome3-team/gnome3 ubuntu
Warning: Could not find package list for PPA: Gnome3-team/gnome3 ubuntu
 
Also, when I try to boot into ubuntu all that pops up is this
 
Ubuntu 11.04 Liouina-laptop tty2 
 
liouvina-laptop login: 
 
I try to log in and then this, 
 
Last login: 
 
Welcome to Ubuntu 11.04
 
*documentation: help.ubuntu.com
 
Liouvna@liouvina-laptop:~$ 
 
So I have no idea how I would log in any other way. 
 
Again, thank you for your help.

---

### Post by MAFoElffen on 2011-10-12
> **liouvina said:**
> When I try "sudo ppa-purge ppa:gnome3-team/gnome3/ubuntu" 
 
It gives me this, 
 
"E: Type 'ain' is not known on line 3 in source list /etc/appt/sources.list.d/gnome3-team-gnome3-natty.list
E: The list could not be read. 
Warning: apt-get update failed for some reason
 
[COLOR=Red]ppa to be removed: gnome3-team/gnome3 ubuntu
Warning: Could not find package list for PPA: Gnome3-team/gnome3 ubuntu
[/COLOR]  
Also, when I try to boot into ubuntu all that pops up is this
 
Ubuntu 11.04 Liouina-laptop tty2 
 
liouvina-laptop login: 
 
I try to log in and then this, 
 
Last login: 
 
Welcome to Ubuntu 11.04
 
*documentation: help.ubuntu.com
 
Liouvna@liouvina-laptop:~$ 
 
So I have no idea how I would log in any other way. 
 
Again, thank you for your help.
Okay I looked through  this on one of my test boxes. I guess ppa-purge is not installed as a default and I got the url of the PPA wrong:[FONT=monospace]
[/FONT]```
sudo apt-get remove libgtk-3-common 
sudo apt-get install ppa-purge 
sudo ppa-purge ppa:gnome3-team/gnome3 
sudo apt-get install gnome-panel

```And after ensuring GNOME3 is gone, reboot.
```

sudo apt-get update 
sudo apt-get dist-upgrade 
sudo apt-get install ubuntu-desktop

```I found these instructions which would explain how you created those unmet dependencies
> 
_Removing GNOME3 and going back to stock 11.04  _Following these steps will remove the GNOME3 PPA and revert your packages:
```

sudo apt-get install ppa-purge 
sudo ppa-purge ppa:gnome3-team/gnome3   

```While downgrading, if aptitude gives the following output:
[quote]Leave the following dependencies unresolved:
    gnome-control-center-data recommends gnome-control-center (<< 2.91) [...]   Then type this when it asks you to enter yes/no: - gnome-control-center-data (Note the "-" in the beginning, its important). Then press enter, and then it shouldn't show any packages under Leave the following dependencies unresolved. Type y, and you should soon be downgraded normally to the Ubuntu 11.04 packages.
[/QUOTE]Now, typing 
```

- gnome-control-center-data

```where it would ask yes/no... that's something "new" I learned today.

---

### Post by liouvina on 2011-10-12
You have no idea how much your help means to me, again thanks. 
 
I tried your first set of codes and the first two lines didn't give me any errors but then when I got to:
 
[COLOR=red]sudo ppa-purge ppa:gnome3-team/gnome3 [/COLOR]
 
updating packages list
E: Type 'Ain' Is not known on line 3 in source list etc/apt/sources.list.d/gnome3-team-gnome3-natty.list
E: The list of sources could not be read.
Warning: Apt-get update failed for some reason
PPA to be removed: Gnome3-team-gnome3
Warning: Could not find package list for PPA: Gnome3-team gnome3
 
[COLOR=red]sudo apt-get install gnome-panel[/COLOR]
 
Reading package lists... done
Building Dependency tree... done
Reading state information.... done
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of incoming. 
The following packages have unmet dependencies:
Gnome-Panel : 
Depends: Gnome-control-center (>= 1:2.8 .2-3) BUT IT IS NOT GOING TO BE INSTALLED
Depends: Gnome-Menus (>= 2.16.1) BUT IT IS NOT GOING TO BE INSTALLED
Recommends: Gnome-session (>=2.26)BUT IT IS NOT GOING TO BE INSTALLED
Recommends: Evolution-data-server BUT IT IS NOT GOING TO BE INSTALLED
Recommends: Alacarte BUT IT IS NOT GOING TO BE INSTALLED
E: Broken Packages
 
Should I continue with your next set of directions?

---

### Post by 23dornot23d on 2011-10-12
Type into a terminal       ```
 gedit /etc/apt/sources.list     
``` cut and paste what you see .... into the thread please ....  we will go from there ....

It is quite possible something is not quite as it should be in the above file .....

once it is corrected it should give us a chance ....

If you are not keen on editing the file .....

try

sudo apt-get install aptitude

see if we can do it this way ..... ( if aptitude install ok it may be ok to proceed )
aptitude does dependancy checks and will try to find a good solution for you

---

### Post by liouvina on 2011-10-12
[COLOR=red] gedit /etc/apt/sources.list[/COLOR]
[COLOR=#ff0000][/COLOR] 
[COLOR=black]The program 'gedit' is currently not installed. Youc an install it by typing: [/COLOR]
[COLOR=black]apt-get install gedit[/COLOR]
[COLOR=red][/COLOR] 
[COLOR=red]apt-get install gedit[/COLOR]
[COLOR=#ff0000][/COLOR] 
[COLOR=black]Reading package lists... done[/COLOR]
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yeat been created or been moved out of incoming. 
 
The following information may help to resolve the situation:
 
The following packages have unmet dependencies 
 
Gedit: depends: gedit-common (< 2.31) but 3.0.6-0ubuntu1~natty1 is to be installed
E: Broken packages
[COLOR=#ff0000][/COLOR] 
[COLOR=black][/COLOR]

---

### Post by 23dornot23d on 2011-10-12
type

sudo apt-get install aptitude

sudo aptitude update

sudo aptitude install gedit


you can answer n 
( for no untill it gives a solution where it downgrades some packages and allows a install of gedit  )

we will start here if you get stuck post the text you see or a screen shot please I really want to take
a look at the sources list ....... you could try this ..... just to view it ...... from a terminal then cut and paste it
 
less /etc/apt/sources.list


q will get you out .....

---

### Post by liouvina on 2011-10-12
[COLOR=red]sudo apt-get install aptitude[/COLOR]
[COLOR=red][/COLOR] 
[COLOR=red][COLOR=#000000]Reading package lists... done
Building dependency tree
Reading state information... Done[/COLOR]
[/COLOR][COLOR=red][/COLOR]
[COLOR=red][COLOR=black]aptitude is already the newest version. [/COLOR][/COLOR]
[COLOR=red][COLOR=#000000][/COLOR][/COLOR] 
[COLOR=red][COLOR=#000000]The following packages were automatically installed and are no longer required: [/COLOR][/COLOR]
 
(they give me a long list of packages here, I'm having to retype everything from a different computer, I'll retype them if needed though.) 
 
Use 'apt-get autoremove' to remove them. 
 
[COLOR=red][COLOR=#000000]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded[/COLOR]
[/COLOR]

---

### Post by liouvina on 2011-10-12
[COLOR=red]sudo aptitude update[/COLOR]
 
[COLOR=black]E: Type 'Ain' Is not known on line 3 in source list etc/apt/sources.list.d/gnome3-team-gnome3-natty.list[/COLOR]
[COLOR=red][COLOR=black]E: Type 'Ain' Is not known on line 3 in source list etc/apt/sources.list.d/gnome3-team-gnome3-natty.list[/COLOR]
[COLOR=black]E: The list of sources could not be read.[/COLOR]
[COLOR=black]E: Type 'Ain' Is not known on line 3 in source list etc/apt/sources.list.d/gnome3-team-gnome3-natty.list[/COLOR]
[COLOR=black]E: Type 'Ain' Is not known on line 3 in source list etc/apt/sources.list.d/gnome3-team-gnome3-natty.list[/COLOR]
[COLOR=black]E: The list of sources could not be read.[/COLOR]
[COLOR=black]E: couldn't read list of package sources[/COLOR]
 
sudo aptitude install gedit

[COLOR=black]E: Type 'Ain' Is not known on line 3 in source list etc/apt/sources.list.d/gnome3-team-gnome3-natty.list[/COLOR]
[COLOR=red][COLOR=black]E: Type 'Ain' Is not known on line 3 in source list etc/apt/sources.list.d/gnome3-team-gnome3-natty.list[/COLOR]
[COLOR=black]E: The list of sources could not be read.[/COLOR]
[COLOR=black]E: Type 'Ain' Is not known on line 3 in source list etc/apt/sources.list.d/gnome3-team-gnome3-natty.list[/COLOR]
[COLOR=black]E: Type 'Ain' Is not known on line 3 in source list etc/apt/sources.list.d/gnome3-team-gnome3-natty.list[/COLOR]
[COLOR=black]E: The list of sources could not be read.[/COLOR]
[COLOR=black]E: couldn't read list of package sources[/COLOR]
[COLOR=#000000][/COLOR] 
[COLOR=#000000]They give me the same error for both commands. [/COLOR]
[/COLOR][/COLOR]

---

### Post by 23dornot23d on 2011-10-12
Type

less /etc/apt/sources.list


q will get you out .....


But post the output you see ...... cut and paste it if you would please ....

I have a feeling this file may be in a mess ...
[COLOR=red][COLOR=red][COLOR=black]
It is pointing to an error that in this file there is a error on line 3 

source list etc/apt/sources.list.d/gnome3-team-gnome3-natty.list


Can you run synaptic at all ......... from the menu

other choice is to disable the repository from synaptic .....
[/COLOR][/COLOR][/COLOR]

---

### Post by liouvina on 2011-10-12
Haha, I have two laptops.  One runs windows and the other ubuntu. I'm in recovery mode on the root shell prompt because I can't log in. I'll retype everything for you but it'll take a few minutes. I don't mind, I apprecitate the help.

---

### Post by 23dornot23d on 2011-10-12
To save you typing it all out ....

If you have it typed out show me what you have 

but

[B]
we may have to move this file first (has there seems to be a error in it and we have to sort it first)

[/B][COLOR=red][COLOR=red][COLOR=black]
sudo mv /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list [/COLOR][/COLOR][/COLOR][COLOR=red][COLOR=red][COLOR=black] /etc/apt/sources.list.d/gnome3-team-gnome3-natty.temp[/COLOR][/COLOR][/COLOR][COLOR=red][COLOR=red][COLOR=black] 


[/COLOR][/COLOR][/COLOR]Then try to run 



[B]sudo aptitude update

( only other thing I can think of is running from the live CD .... then you can get to your files from a GUI
and use gedit etc .... )
[/B]

---

### Post by liouvina on 2011-10-12
I just finished typing it out: 
 
 
 
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_- Release i386 (20091028.5)]/ Karmic main restricted
# See [http://help.ubuntu.com/community/upgradenotes](http://help.ubuntu.com/community/upgradenotes) for how to upgrade to 
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
## Major bug fix updates produced after the final release of the 
## distribution. 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-upates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the ubuntu
## team. Also, please not that softeware in universe will not recieve any
## review or updates from the ubuntu security team. 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/natty](http://us.archive.ubuntu.com/ubuntu/natty) universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
## N.B. software from the repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please not that software in 
## Multiverse WILL NOT receive any review or updates from the Ubuntu
## Security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty muitverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty muitverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates muitverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates muitverse
## Uncomment the following tw olines to add software from the 'backports'
## repository.
## N.B. software from the repository may not have been tested as 
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports will not receive any review
## Or updates from the ubuntu security team. 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'Partner' repository. 
## This software is not part of ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users. 
deb [http://archive.canonical.com/](http://archive.canonical.com/) ubuntu natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security mutiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security mutiverse
# deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) lucid maind # disabled on upgrade to lucid
# deb-src deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) lucid maind # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) lucid main # disabled on upgrade to lucid
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main #third party developers repository
deb [http://download.tuxfamily.org/glxdock/repository/ubuntu](http://download.tuxfamily.org/glxdock/repository/ubuntu) natty cairo-dock ## cairo-dock-stable
end

---

### Post by 23dornot23d on 2011-10-12
Brilliant .....

That file looks ok .....

so lets move the other one and try the update .....

[B]we may have to move this file first (as there seems to be a error in it and we have to sort it first)

[/B]Ain error ....... ( its a corrupt file ,,,, the M is missing it would be ok if it was  ....... main )[COLOR=Red][B]
E: Type 'Ain' Is not known on line 3 in source list etc/apt/sources.list.d/gnome3-team-gnome3-natty.list[/B][/COLOR]
and that is probably the error un the UGR list  ............

you could have a look .... similar way to before ..... but it may need correcting ..... 
its in line 3 .... but there may be more wrong with that file

[COLOR=red][COLOR=red][COLOR=black] less /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list[/COLOR][/COLOR][/COLOR]


--------------------------------------------------------------

My other option is to move it ....... but this may not be the best way ..... ( if the other one can be corrected )
[COLOR=red][COLOR=red][COLOR=black]
sudo mv /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list [/COLOR][/COLOR][/COLOR][COLOR=red][COLOR=red][COLOR=black] /etc/apt/sources.list.d/gnome3-team-gnome3-natty.temp[/COLOR][/COLOR][/COLOR][COLOR=red][COLOR=red][COLOR=black] 

[/COLOR][/COLOR][/COLOR]Then try to run 

[B]sudo aptitude update

[/B]

---

### Post by liouvina on 2011-10-12
> **23dornot23d said:**
> To save you typing it all out ....
 
If you have it typed out show me what you have 
 
but
 
 
**we may have to move this file first (has there seems to be a error in it and we have to sort it first)**
 
[COLOR=red][COLOR=red]
[COLOR=red]sudo mv /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list [/COLOR][/COLOR][/COLOR][COLOR=red][COLOR=red][COLOR=black]/etc/apt/sources.list.d/gnome3-team-gnome3-natty.temp[/COLOR][/COLOR][/COLOR][COLOR=red][COLOR=red]
and j 
 
[/COLOR][/COLOR]Then try to run 
 
 
 
**sudo aptitude update**
 
**( only other thing I can think of is running from the live CD .... then you can get to your files from a GUI**
**and use gedit etc .... )**

 
 
When I ran [COLOR=red]**sudo aptitude update **[/COLOR][COLOR=black]I recieved a long list of errors. If you'd like to see I'll type them out for you. Also, my laptop doesn't have a cd drive. It's a dell 11z so I'll have to find my flashdrive. I just don't want to lose all my files. I have two laptops but the one running Ubuntu is my main. I have everything on there. Would there be an option on the flashdrive to repair whatever I've damaged? It's been so long since I've the options on there. Again, thank you so much. [/COLOR]

---

### Post by liouvina on 2011-10-12
Oh, I'll try your new instructions now.

---

### Post by liouvina on 2011-10-12
[COLOR=red]less /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list[/COLOR]
[COLOR=black]/etc/apt/sources.list.d/gnome3-team-gnome3-natty.list: No such file or directory[/COLOR]
 
[COLOR=red]sudo mv /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list /etc/apt/sources.list.d/gnome3-team-gnome3-natty.temp [/COLOR]
[COLOR=red][/COLOR] 
[COLOR=red][COLOR=black]mv: cannot stat [COLOR=black]/etc/apt/sources.list.d/gnome3-team-gnome3-natty.list: No such file or directory[/COLOR]
[/COLOR]
**sudo aptitude update**

[COLOR=black]I get a list of errors. It lists all the urls from the list and under them says "could not resolve 'Url' [/COLOR]
[COLOR=#000000][/COLOR] 
[COLOR=#000000]I'll give an example of one[/COLOR]
[COLOR=#000000][/COLOR] 
[COLOR=#000000]Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty release.gpg[/COLOR]
[COLOR=#000000]  Could not resolve '[Http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty release.gpg'[/COLOR]
[/COLOR]

---

### Post by 23dornot23d on 2011-10-12
I will have to come back to this later ...... need to find another way to sort this ......

Be back later on .......

---

### Post by liouvina on 2011-10-12
No problem, thanks again! =)

---

### Post by 23dornot23d on 2011-10-12
[COLOR=black]/etc/apt/sources.list.d/gnome3-team-gnome3-natty.list: No such file or directory

That tells me the file has gone - which the package manager looks for .....

but why is it giving a error on line 3 .......
[/COLOR][COLOR=black]E: Type 'Ain' Is not known on line 3 in source list etc/apt/sources.list.d/gnome3-team-gnome3-natty.list[/COLOR]
[COLOR=black] 
try the command below >>  LS are  the first two letters ..... in lowercase .......


**ls /etc/apt/sources.list.d/**


The command above just lists the files - to see what files are there .........

This Guy had the same problem .... [**LINK**]("http://coffeecup83.blogspot.com/2011/05/ubuntu-1104-cant-apt-get-update.html")
he just removed the file and everything was ok ...... from what he wrote in his blog .....

then 
sudo apt-get update 

I may not be here when you return but there seems to have been a lot of queries about the
same problem ........ look through the [_***solved ones***_]("http://ubuntuforums.org/showthread.php?t=1737917") ...... 
[HERE IS THE SEARCH I DID]("http://www.google.com/search?client=ubuntu&channel=fs&q=%2Fetc%2Fapt%2Fsources.list.d%2Fgnome3-team-gnome3-natty.list&ie=utf-8&oe=utf-8")

unless anyone else sees this thread and knows a quick solution ...


There has been a bug raised against this ....[ **BUG REPORT**]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/640784")
[/COLOR]

---

### Post by liouvina on 2011-10-12
I found this [https://answers.launchpad.net/ubuntu/+source/gnome-session/+question/158705](https://answers.launchpad.net/ubuntu/+source/gnome-session/+question/158705) from the search you posted and I'm not sure where to go from here. 
 
I'm on Nano I have [COLOR=red]/etc/apt/sources.list.d/gnome3-team-gnome3-natty.list [COLOR=black]pulled up ready to edit, but I have no idea what I'm trying to do. Should I just erase the text? I've never messed with Nano so I don't know if it'd accomplish anything. One of my main errors was this:[/COLOR][/COLOR]
[COLOR=red][COLOR=#000000][/COLOR][/COLOR] 
[COLOR=red]E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list
E: The list of sources could be read[/COLOR]
[COLOR=red][/COLOR] 
[COLOR=red][COLOR=black]Maybe through Nano I can resolve this error? [/COLOR][/COLOR]
[COLOR=red][COLOR=#000000][/COLOR][/COLOR] 
[COLOR=red][COLOR=#000000]This is what I currently have pulled up on Nano[/COLOR][/COLOR]
[COLOR=red][COLOR=#000000][/COLOR][/COLOR] 
[COLOR=red][COLOR=#000000]deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) natty main[/COLOR][/COLOR]
[COLOR=red][COLOR=#000000]deb-src [COLOR=red][COLOR=#000000] [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) natty main[/COLOR][/COLOR]
[/COLOR]
[COLOR=black]Any suggestions? [/COLOR]
[/COLOR]

---

### Post by 23dornot23d on 2011-10-12
Their seems to be no problem with what you have there .....

I expected a M to be missing off of Main on line 3 ......

lowercase m though ...... main .....

That is what the error is reporting the fix would be to add the m back into the file ..... in the correct place
but its not looking as if there is a problem .... with what you have shown ...


you could try the mv command with that file now .... or remove it and se if the computer will update
you have the neccessary information to put it back fresh again now .....

That was why I gave the command earlier ..... mv filename.list filename.temp

as far as I know the filenam only gets read if it ends in .list
so changing it to something else ..... would allow it to be ignored ...

similar to what the guy did in his blog ...... but he just removed it ...... I play safe keeping files
but now we know whats in it its easy to replace ...... 

so its upto you ..... mv or rm that file.list

will achieve what you need to get update to work ......

once we can update we can then add packages and get your system working again .....

Unless of course there is a m missing in which case it just wants re-adding back into the file .....

---

### Post by MAFoElffen on 2011-10-12
> **23dornot23d said:**
> Type into a terminal       ```
 gedit /etc/apt/sources.list     
``` cut and paste what you see .... into the thread please ....  we will go from there ....

It is quite possible something is not quite as it should be in the above file .....

once it is corrected it should give us a chance ....

If you are not keen on editing the file .....

try
```

sudo apt-get install aptitude

```see if we can do it this way ..... ( if aptitude install ok it may be ok to proceed )
aptitude does dependancy checks and will try to find a good solution for you
+1  Yes, that would be better.  That changes in the syntax would be every where it said "apt-get" > replace with "aptitude".

Yes, since 11.04, aptitude is not a default installed apt.  11.10 (new install) starts synaptic as not being a default app...
> 
[COLOR=red][COLOR=#000000]This is what I currently have pulled up on Nano[/COLOR][/COLOR]
 
[COLOR=red][COLOR=#000000]deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) natty main[/COLOR][/COLOR]
[COLOR=red][COLOR=#000000]deb-src [COLOR=red][COLOR=#000000] [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) natty main[/COLOR][/COLOR]
[/COLOR]
[COLOR=black]Any suggestions? [/COLOR][/COLOR]
Delete those 2 lines!!! That's why it keep comming up with errors on the gnome3 ppa.

Yes go on with the commands.  What was in the second half of that post is what Ubuntu says it the normal procedure.  Which not knowing the little special note tip at the end about " - gnome-control-center-data" would tend to screw things up...

I'm now thinking that since you didn't know that "special note" when you uninstalled gnome3, maybe if you also installed/reinstalled:
```

sudo aptitude install --reinstall gnome-control-center
sudo aptitude install --reinstall gnome-menus
sudo aptitude install --reinstall gnome-session
sudo aptitude install --reinstall Evolution-data-server
sudo aptitude install --reinstall gnome-panels
sudo aptitude install --reinstall alacarte

```Just a curiosity on that one... but it "seems" logical.

---

