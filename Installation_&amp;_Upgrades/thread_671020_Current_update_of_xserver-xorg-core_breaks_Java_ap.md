---
title: "Current update of xserver-xorg-core breaks Java apps"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by W.McL on 2008-01-18
The current Update of xserver-xorg-core to version 1.3.0.0.dfsg-12ubuntu8.1 seems to break graphical Java applications.
If you already installed the update, you can solve the problem by downgrading xserver-xorg-core to the previous version 1.3.0.0.dfsg-12ubuntu8
To downgrade (on gutsy), open a terminal and type ```
sudo apt-get install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8
```

See [here]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969") for the Launchpad bug report.

---

### Post by Jburgess on 2008-01-18
Thanks for the heads up. I noticed all the java apps broken after the update (azureus, vlc, eclipse etc). I have reverted and all is fine now. So what to do now? Should I wait until another update becomes available via the update manager ? Thanks

---

### Post by PetePete on 2008-01-18
on fiesty type

```

sudo aptitude install xserver-xorg-core=2:1.2.0-3ubuntu8

```
to downgrade..

---

### Post by stefan.pasat on 2008-01-18
very helpfull! it fixed my problem with eclipse

---

### Post by GolanTrevize on 2008-01-18
@ W.McL thanks a lot for the advise and link to the bug database

that saved my day

---

### Post by doctorpx on 2008-01-18
thanks! i can work now!

---

### Post by jensaug on 2008-01-18
Crashed my gnome settings manager though, cannot start it. No theme nor Swedish keyboard.... any solutions?

"Unable to start the settings manager 'gnome-settings-daemon'."

Jens

---

### Post by oneiota on 2008-01-18
Thanks this fixed Eclipse for me.

Jensaug, I had to restart Ubuntu before the downgrade appeared to fix my problem.  Could that be the issue for you, or have you already tried a restart?

---

### Post by pouns on 2008-01-18
thank you !
this effectively fixes problems with eclipse.
Does anyone notice a problem with suspend too ?

---

### Post by Killerdackel on 2008-01-18
Why is such an update in the stable part of Ubuntu?

---

### Post by heindsight on 2008-01-18
I installed the update and haven't had any problems on my 64bit gutsy system. It seems this problem only affects 32bit systems.

---

### Post by jensaug on 2008-01-18
> **oneiota said:**
> Thanks this fixed Eclipse for me.

Jensaug, I had to restart Ubuntu before the downgrade appeared to fix my problem.  Could that be the issue for you, or have you already tried a restart?

Could have sworn that I had, but (another?) restart got gnome-settings-daemon to start! Thanks.

---

### Post by rgeddes on 2008-01-18
I assume the file is being blocked for now:
> 
$0> sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  avahi-autoipd avahi-daemon ddclient libavahi-client-dev libavahi-client3 libavahi-common-data libavahi-common-dev libavahi-common3
  libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1 libavahi-qt3-1 libxfont1 xserver-xorg-core
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 3677kB/4520kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main xserver-xorg-core 2:1.3.0.0.dfsg-12ubuntu8.1
  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

----/home/rgeddes
$100> 

I think it's better to removed  the package from the server once it's a known problem... it would save some traffic over the internet as well as some time for users...

We've seen the same issue with xorg before.... xorg is a touchy issue.... time to try a new approach for updating xorg.....

---

### Post by unknow2006 on 2008-01-18
kind late for me, i got the broke patch and now i cant use my ubuntu, reach the loging screen but after i type all correctly the xserver just restart and send me back to the login screen.

Edit:
I just solved my problem, was my compiz got corrupt in some way, i've uninstalled it and its working now, ill gonna w8 till they fix this and install compiz again, thx for the help.

Edit 2:
The problem was more bad than i though, i had to reinstall the nvidia drivers lol, i think i didnt even needed to remove compiz in the end, well ill try tomorrow install compiz again.

---

### Post by Zill on 2008-01-18
> **Killerdackel said:**
> Why is such an update in the stable part of Ubuntu?
A very good question!

It is bad enough to release dodgy updates for "bleeding edge" versions such as Gutsy but it is totally unacceptable to break LTS versions (ie. Dapper) which are supposed to provide ultra reliable systems.

In my view, this kind of error with bad kernel and Xorg updates is happening too often with Ubuntu.
QA need to seriously review their testing and admin procedures to ensure this never happens again, particularly with LTS versions.

---

### Post by p_quarles on 2008-01-18
They are reviewing the process to ensure it doesn't happen again. That and more can be seen here:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

Also, this is by no means specific to Ubuntu. Debian (including Etch) is dealing with the same problem right now.

---

### Post by oscarsfriend on 2008-01-18
> **unknow2006 said:**
> Edit 2:
The problem was more bad than i though, i had to reinstall the nvidia drivers lol, i think i didnt even needed to remove compiz in the end, well ill try tomorrow install compiz again.

That is right.  The update installed a file over a symlink to a file needed by your nvidia drivers -- reinstalling the nvidia drivers, or reinstating the symlink will fix the problem.  More info here: [http://ubuntuforums.org/showthread.php?t=671091](http://ubuntuforums.org/showthread.php?t=671091)

---

### Post by yogibear15 on 2008-01-18
security updates for gutsy now has version 2:1.3.0.0.dfsg-12ubuntu8.2 which fixes this problem (for Eclipse, at least).

---

### Post by jtreach on 2008-01-19
It's good they are reviewing the way x updates are processed. Another completely unrelated x update broke my system before, once is fine but twice in a couple of months signals that there is something seriously amiss.

---

### Post by cheeby on 2008-01-19
Recreating the symlink worked for me as well, and I was able to work with the new xorg-server-core files, too.

Thank you!

cheeby

---

### Post by yetanothersteve on 2008-01-19
I am on 64bit feisty and had no problems. java visual apps and eclipse working fine.

I did immediately install new Nvidia drivers after doing the xserver-xorg-core update because I was one version behind on the Nvidia drivers.

---

### Post by novice_forever on 2008-01-19
> **W.McL said:**
> 
To downgrade (on gutsy), open a terminal and type ```
sudo apt-get install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8
```

How does this work on **feisty?** When I try the mentioned command, I get this:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Version '2:1.3.0.0.dfsg-12ubuntu8' for 'xserver-xorg-core' was not found

```

Thanks in advance,

novice forever

---

### Post by novice_forever on 2008-01-19
Now I tried to use Synaptic/Package/Force Version...

I get this warning:
"You are about to install software that can't be authenticated! Doing this could allow a malicious individual to damage or take control of your system."

What am I going to do now??

---

### Post by novice_forever on 2008-01-19
The most recent update 8.3 solved the problem.

---

### Post by Harish TM on 2008-01-20
Hi, 

            I was trying to sort out this problem before reading this thread when I messed something up with my Java. I have given details at: [http://ubuntuforums.org/showthread.php?p=4171423](http://ubuntuforums.org/showthread.php?p=4171423)


           Could someone please help?

---

### Post by williammanda on 2008-01-20
I have three computers that updated:
64 bit C2D
64 bit AMD
32 bit PIV
The 64 bit AMD was the only one to have a problem of not being able to login. I down graded the xorg and reloaded Nvidia drivers and now it works.

---

