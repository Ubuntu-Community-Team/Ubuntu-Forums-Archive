---
title: "apt-get upgrade installed packages only?"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by sutherland1 on 2010-04-12
[FONT=Verdana]Hi All,[/FONT]
[FONT=Verdana]I have heavily customised version of Ubuntu 9.04 which I wish to upgrade to 9.10.[/FONT]
 
[FONT=Verdana]However I wish to only update the installed packages, and not add any more.[/FONT]
 
[FONT=Verdana]My plan is to change [FONT=Courier New]sources.list[/FONT] from [/FONT]
 
[FONT=Verdana][FONT=Courier New]**deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted multiversedeb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main**[/FONT] [/FONT]
 
[FONT=Verdana]to...[/FONT]
 
[FONT=Verdana][FONT=Courier New]**deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted multiversedeb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main**[/FONT] [/FONT]
 
[FONT=Verdana]and run [/FONT][FONT=Courier New]**apt-get update**[/FONT]
 
[FONT=Verdana]Is this the correct procedure?[/FONT][FONT=Verdana]Thanks[/FONT]

---

### Post by snowpine on 2010-04-12
No, that is **not** the recommended upgrade procedure.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Ubuntu will only upgrade the packages that are installed. In rare cases, a few extra new packages might be brought in, as dependencies can change from release to release.

I always recommend testing a Live CD of the new release first, to avoid any unpleasant surprises (like your graphic card is no longer supported, oops!)

---

### Post by garvinrick4 on 2010-04-12
This will upgrade your sources list to karmic and dist upgrade your 
OS. Have a nice day.


sudo sed -i 's/jaunty/karmic/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade

---

### Post by sutherland1 on 2010-04-12
Thanks for the reply - just so I'm clear, only "*apt*-*get dist*-*upgrade" *will be needed?

---

### Post by dannyboy79 on 2010-04-12
> **garvinrick4 said:**
> This will upgrade your sources list to karmic and dist upgrade your 
OS. Have a nice day.


sudo sed -i 's/jaunty/karmic/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade

and that is NOT the recommended way. but I suppose users will do what they do. 

recommended way is 
```
sudo apt-get update && update-manager -d
```

---

### Post by sutherland1 on 2010-04-12
[FONT="Verdana"]This command worked perfectly...[/FONT]
[FONT="Courier New"]sudo sed -i 's/jaunty/karmic/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade
[/FONT]

---

