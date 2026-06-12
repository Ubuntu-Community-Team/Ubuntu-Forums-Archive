---
title: "E: Unable to locate package"
date: 2014-03-20
forum: Installation &amp; Upgrades
---

### Post by ottawajoe2 on 2014-03-20
Hi, everytime I try to install a package, I get 
[I]
Reading state information... Done
E: Unable to locate package 

[/I]I've scoured the internet and I've come up empty handed. Can anyone tell me what to do here? I've gone into package manager and reloaded, I've used sudo apt-get udate. Nothing. What exaclty is this E:? Is it a location on my HDD?
Any help would be greatly appreciated. I love linux but I find it uphill work at times. Pride and common sense keep me from returning to MS Windows.

---

### Post by deadflowr on 2014-03-20
Always helps to know what package you are trying to install.

As well as what version of Ubuntu.

Because even though the package might exist on one version doesn't mean it will on another, or that it has a different name on the other.

---

### Post by ottawajoe2 on 2014-03-21
I'm using Ubuntu 12.04. I'm trying to install flashplayer. I d'loaded it from Flash website, extracted it to my Desktop. A folder called usr is now there. After doing a CD Desktop, I did a sudo get-apt install usr and I get the message. It gives me the message for everything I try installing. I'm contemplating starting to drink.

---

### Post by lisati on 2014-03-21
It's likely that using "apt-get" isn't the way to go. Have a look in the folder usr for a file with a name like "README" or "ReadMe.TXT" - if there's one there, it might have instructions in it.

---

### Post by deadflowr on 2014-03-21
You can simply delete that file and folder.
To install flash on ubuntu use this command
```
sudo apt-get install flashplugin-installer
```

This installs the flashplugin installer, which in turns downloads the flashplugin from Adobe and installs it.
It'll also keep up with the security updates, so you won't have to keep downloading a fresh version every time flash gets updated.

---

### Post by ottawajoe2 on 2014-04-02
Ok, now I'm gettting annoyed. EVERY time I try to install a software program, I get this message:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package clipgrab-3.4.2
E: Couldn't find any package by regex 'clipgrab-3.4.2'[/I]

In this instance, I tried to load clipgrab. I have absolutely no idea what that "E:" is about. Can anyone shed some light on this for me at all please?

---

### Post by ottawajoe2 on 2014-04-02
Hi 

Everytime I try to install a software program, I get this message:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package clipgrab-3.4.2
E: Couldn't find any package by regex 'clipgrab-3.4.2'[/I]

In  this instance, I tried to load clipgrab. I have absolutely no idea what  that "E:" is about. This happens with every software I try to install. I d'load it, extract it to my desktop, CD Desktop, use "Sudo apt-get Install the software program and I get the above message. Can anyone explain what is happening?

Thanx

---

### Post by steeldriver on 2014-04-02
It means there is no package for clipgrab in the Ubuntu repositories, however there appears to be a PPA (personal package archive) provided here:

[URL="https://launchpad.net/~clipgrab-team/+archive/ppa/+build/5835147"]https://launchpad.net/~clipgrab-team/+archive/ppa/+build/5835147

[/URL]

---

### Post by QIII on 2014-04-02
Threads merged.

Please do not create duplicate threads in different areas of the Forums.  It causes confusion and dilutes the community's efforts to provide help.  

You were already getting help in this thread.

---

### Post by ottawajoe2 on 2014-04-03
Sorry, will clean it up.

---

