---
title: "Ubuntu 20.04 library cant be installed no matter what trying to install steam."
date: 2020-11-21
forum: Installation &amp; Upgrades
---

### Post by techtheguy on 2020-11-21
I cant install steam no matter what i try. Dependencieo over dependencies ... you got it.
Its so frustrating. Please help me. I tried anything i could, and ended up damaging my sistem. Now its like new. here is a tutorial i followed: [https://linuxconfig.org/how-to-install-steam-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-install-steam-on-ubuntu-20-04-focal-fossa-linux)
here is what happens when i do 
sudo apt install steam:
techguy@techbook:~/steam$ sudo apt-get install steam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 steam:i386 : Depends: libgl1-mesa-dri:i386 (>= 17.3) but it is not going to be installed or
                       libtxc-dxtn0:i386 but it is not installable
              Depends: libgl1-mesa-glx:i386 but it is not going to be installed
              Depends: libudev1:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
I tried reconfiguring and adding repositories and anything i could, but that libgl1-mesa problem is still there.

Also, the real problem comes when i launch steam installer. Here is what happens:

Steam needs to install these additional packages:
    libgl1-mesa-dri:i386, libgl1:i386, libc6:i386
[sudo] password for techguy: 
......
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libgl1:i386 : Depends: libglx0:i386 (= 1.3.1-1) but it is not going to be installed
 libgl1-mesa-dri:i386 : Depends: libglapi-mesa:i386 (= 20.0.4-2ubuntu1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
Press return to continue: 


Any ideas?

---

### Post by ajgreeny on 2020-11-21
Please do not use language like you did in your post, and which I have now removed.
This is a forum for users of all ages and our terms and conditions say clearly that profanities MUST not be used.

You are obviously frustrated by this problem but you are more likely to get useful answers if you state clearly the problem and give as much information as you can.

I am not a gamer and have not used, nor do I fully understand steam and its use and installation, but the dependency problems  you ask about can be caused by having added PPA repos to your system; do you have any of those enabled?

---

### Post by techtheguy on 2020-11-21
oops. sorry. I think i have exagerated. I dont have an other PPA apart the default ones. Im sorry. Also, corrected the "human error" i did in the question. Added more useful info.. thansk

---

### Post by CatKiller on 2020-11-21
You've likely not done this bit:

```
sudo dpkg --add-architecture i386
```

Steam is 32-bit and needs a bunch of 32-bit libraries. If you don't say that it's OK to install 32-bit things, your package manager won't.

---

### Post by redmcg2 on 2020-11-26
After performing a minimal install of 20.04.1 LTS, I tried:
```
apt install steam
```

and got the following error:
```
The following packages have unmet dependencies:
       [steam:i386](steam:i386) : Depends: [libudev1:i386](libudev1:i386) but it is not going to be installed
```

I noticed that focal-updates was not in my sources.list so I ran:
```
sudo apt-add-repository ["deb http://archive.canonical.com/ubuntu $(lsb_release -cs)-updates main restricted universe multiverse"]("debhttp://au.archive.ubuntu.com/ubuntu$(lsb_release-cs)-updatesmainrestricteduniversemultiverse")
```

And after this, ```
apt install steam
``` worked.

---

### Post by ajgreeny on 2020-11-26
Great news!
Please mark as SOLVED from Thread Tools menu up top; it's a great help to others searching the forum.

---

