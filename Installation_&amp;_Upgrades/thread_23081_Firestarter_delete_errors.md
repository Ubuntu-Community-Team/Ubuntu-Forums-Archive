---
title: "Firestarter delete errors"
date: 2005-03-31
forum: Installation &amp; Upgrades
---

### Post by mirtux on 2005-03-31
Hi everybody,
  i would like to deinstall Firestarter but dpkg gives me this error:
 ```

(Reading database ... 148581 files and directories currently installed.)
Removing firestarter ...
Purging configuration files for firestarter ...
dpkg: error processing firestarter (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 firestarter

``` 

Any ideas?
MC

---

### Post by ubuntu_demon on 2005-03-31
try :

sudo apt-get remove firestarter

(this doesn't purge the configuration files)

---

### Post by mirtux on 2005-03-31
Hi,
  i have removed firestarter before having tried to purge configuration files.
 ```

Package firestarter is not installed, so not removed

``` 

Regards,
MC

---

### Post by ubuntu_demon on 2005-03-31
you can try and remove some firestarter configuration files by hand by using : "locate firestarter"

Be sure only to remove firestarter files. And not something important like iptables :)

try "apt-get --purge remove firestarter" again after this.

---

### Post by mirtux on 2005-03-31
Are you sure this procedure will not broke any package? 
 ```

/etc/rc0.d/K20firestarter
/etc/rc1.d/K20firestarter
/etc/rc2.d/S20firestarter
/etc/rc3.d/S20firestarter
/etc/rc4.d/S20firestarter
/etc/rc5.d/S20firestarter
/etc/rc6.d/K20firestarter
/home/mirtux/firestarter-events.txt
/root/.gconf/apps/firestarter
/root/.gconf/apps/firestarter/client
/root/.gconf/apps/firestarter/client/filter
/root/.gconf/apps/firestarter/client/filter/%gconf.xml
/root/.gconf/apps/firestarter/client/%gconf.xml
/root/.gconf/apps/firestarter/client/ui
/root/.gconf/apps/firestarter/client/ui/%gconf.xml
/root/.gconf/apps/firestarter/firewall
/root/.gconf/apps/firestarter/firewall/dhcp
/root/.gconf/apps/firestarter/firewall/dhcp/%gconf.xml
/root/.gconf/apps/firestarter/firewall/%gconf.xml
/root/.gconf/apps/firestarter/firewall/icmp
/root/.gconf/apps/firestarter/firewall/icmp/%gconf.xml
/root/.gconf/apps/firestarter/firewall/tos
/root/.gconf/apps/firestarter/firewall/tos/%gconf.xml
/root/.gconf/apps/firestarter/%gconf.xml
/root/.gnome2/firestarter
/var/cache/apt/archives/firestarter_1.0.3-1.1_i386.deb
/var/lib/dpkg/info/firestarter.list
/var/lib/dpkg/info/firestarter.postrm

``` 

Regards,
MC

---

### Post by ubuntu_demon on 2005-03-31
[QUOTE=mirtux]Are you sure this procedure will not broke any package? 
 ```

/etc/rc0.d/K20firestarter
/etc/rc1.d/K20firestarter
/etc/rc2.d/S20firestarter
/etc/rc3.d/S20firestarter
/etc/rc4.d/S20firestarter
/etc/rc5.d/S20firestarter
/etc/rc6.d/K20firestarter
/home/mirtux/firestarter-events.txt
/root/.gconf/apps/firestarter
/root/.gconf/apps/firestarter/client
/root/.gconf/apps/firestarter/client/filter
/root/.gconf/apps/firestarter/client/filter/%gconf.xml
/root/.gconf/apps/firestarter/client/%gconf.xml
/root/.gconf/apps/firestarter/client/ui
/root/.gconf/apps/firestarter/client/ui/%gconf.xml
/root/.gconf/apps/firestarter/firewall
/root/.gconf/apps/firestarter/firewall/dhcp
/root/.gconf/apps/firestarter/firewall/dhcp/%gconf.xml
/root/.gconf/apps/firestarter/firewall/%gconf.xml
/root/.gconf/apps/firestarter/firewall/icmp
/root/.gconf/apps/firestarter/firewall/icmp/%gconf.xml
/root/.gconf/apps/firestarter/firewall/tos
/root/.gconf/apps/firestarter/firewall/tos/%gconf.xml
/root/.gconf/apps/firestarter/%gconf.xml
/root/.gnome2/firestarter
/var/cache/apt/archives/firestarter_1.0.3-1.1_i386.deb
/var/lib/dpkg/info/firestarter.list
/var/lib/dpkg/info/firestarter.postrm

``` 

Regards,
MC[/QUOTE]
 yeah you can safely remove them
but just to be sure mv them to a backup directory :)

---

### Post by mirtux on 2005-03-31
Thanks, but the point is: since i'm using synaptic to mantain packages, what about the residual firestarter config entry that i will see there? I think it will remain there with no possibility to delete....

Regards,
MC

---

### Post by ubuntu_demon on 2005-03-31
synaptic uses the same database as apt-get.

Maybe you should try "sudo apt-get --purge remove firestarter" once more after deleting those files by hand.

according to apt-get's manpage :

"check  is  a  diagnostic  tool; it updates the package cache and checks for broken dependencies"

so you should run "sudo apt-get check" and report the results here.

PS the residual config can't hurt and doesn't take much space. But let's find a way to remove it anyway :)

---

### Post by mirtux on 2005-03-31
Hi,
  here you are... nothing from check everything seems ok...

 ```

Reading Package Lists... Done
Building Dependency Tree... Done

``` 

Regards,
MC

---

### Post by mirtux on 2005-03-31
Just a point: i've tried to reinstall and re-remove the package but the problem is still here....

---

### Post by ubuntu_demon on 2005-03-31
[QUOTE=mirtux]Hi,
  here you are... nothing from check everything seems ok...

 ```

Reading Package Lists... Done
Building Dependency Tree... Done

``` 

Regards,
MC[/QUOTE]
 did you try  "sudo apt-get --purge remove firestarter" once more ?

here's a topic about a guy with a similar problem but with a different application :

[http://www.ubuntuforums.org/showthread.php?t=19010&](http://www.ubuntuforums.org/showthread.php?t=19010&)

You might wanna try dselect to remove firestarter and its configuration.

Also did you try to install it again and then remove it ?
**edit**

If this doesn't work we have to go in deeper. 

this is the post-removal script the error was about :

/var/lib/dpkg/info/firestarter.postrm

We have two possibilities :



1)
analyze the script by placing "echo's" in it. Running it will show where it goes wrong.

echo 1

echo 2


2) 
DONT USE THIS OPTION AT THIS MOMENT IN TIME. Because if you would go for this option first you would have to analyze what the postrm script is actually doing and make sure that the important stuff gets done. Otherwise something could get screwed up.

The hacking way :

edit the file :

sudo pico /var/lib/dpkg/info/firestarter.postrm

and put this content in :

```

#!/bin/bash

```

"chmod +x  firestarter.postrm" to make sure it is executable

Now do :
"sudo apt-get --purge remove firestarter"

---

### Post by ubuntu_demon on 2005-03-31
So if other solutions fail we are going to analyze this script. I have editted it and placed some echo's at relevant points and attached it. You can also do it yourself ofcourse but attach it in this thread then :).

Just move the attachement to /var/lib/dpkg/info/firestarter.postrm

Don't forget to chmod +x the script :)

run sudo apt-get --purge remove firestarter after you have replaced it or editted it.

The script will still fail but it will show us where it fails.Just paste the output here.

---

### Post by mirtux on 2005-04-01
NOw it worked!! :-P. Thank you_ very _much, but what you've done to the file?

Thanks a lot,
MC

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=mirtux]NOw it worked!! :-P. Thank you_ very _much, but what you've done to the file?

Thanks a lot,
MC[/QUOTE]
 nothing much I just putted echo's in it so I could analyze the problem. Maybe your firestarer.postrm was up for some reason.

Do you still have the backup of your firestarter.postrm ? I want to see it.

---

### Post by mirtux on 2005-04-01
Of course. I'm attaching it....

Regards,
MC

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=mirtux]Of course. I'm attaching it....

Regards,
MC[/QUOTE]
 there are some differences. My guess is that your version contained a bug. That's the risk of running an not yet stable distro. But it's strange that it didn't get updated to the same version as mine.

---

### Post by mirtux on 2005-04-01
Well, maybe i've forgotten to say that i'm using Debian unstable, and the firestarter version was **1.0.3-1.1**. I have had also some problems with udev.... it is the risk of staying on the cutting edge version, but i think that also you can learn a lot about the programs you are running. :smile:

Regards,
MC

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=mirtux]Well, maybe i've forgotten to say that i'm using Debian unstable, and the firestarter version was **1.0.3-1.1**. I have had also some problems with udev.... it is the risk of staying on the cutting edge version, but i think that also you can learn a lot about the programs you are running. :smile:

Regards,
MC[/QUOTE]
 You're posting in a hoary forum. You don't run Ubuntu at all ? Why don't you run hoary ? It's nicer than debian unstable I think.

---

### Post by mirtux on 2005-04-01
[QUOTE=demon666_nl]You're posting in a hoary forum. You don't run Ubuntu at all ? Why don't you run hoary ? It's nicer than debian unstable I think.[/QUOTE]
Well,
   there are two main reason why i'm posting here (Hoary forum) even if i' running Debian unstable:
1) Ubuntu is based on Debian unstable, but i'm more comfortable with Debian since i can upgrade to newer version just with a few command. In the case of Ubuntu i used for a month Warty but when i tried to upgrade to Hoary all the system was messed up..... ](*,). I must have a machine that have minimum problems when upgrading!
2) I think that ubuntuforums is the best Linux forum community now in existence ;)

Regards,
MC

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=mirtux]Well,
   there are two main reason why i'm posting here (Hoary forum) even if i' running Debian unstable:
1) Ubuntu is based on Debian unstable, but i'm more comfortable with Debian since i can upgrade to newer version just with a few command. In the case of Ubuntu i used for a month Warty but when i tried to upgrade to Hoary all the system was messed up..... ](*,). I must have a machine that have minimum problems when upgrading!
2) I think that ubuntuforums is the best Linux forum community now in existence ;)

Regards,
MC[/QUOTE]
 1) probably you were upgrading to hoary in a very early stage of hoary's development.That's something that wasn't encouraged for people who wanted to have stability. Hoary is at this moment pretty stable. Hoary is probably released next week. dist-upgrading from warty to hoary at this moment works very good. Some people have to reconfigure their xserver/videocard or have some sound problems (audigy 2 users primarilly) but that's about it.

I have even upgraded my internet gateway to hoary. It's up and running for more than 20 days now without a problem.

see here for upgrading from warty to hoary :
[http://www.ubuntulinux.org/wiki/GuideToHoary](http://www.ubuntulinux.org/wiki/GuideToHoary)
[http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes)

You might want to install the hoary release candidate or wait a couple of days until hoary is released.

2) It's at least the best distro community :)

If you like our forums please join Ubuntu :)

---

### Post by mirtux on 2005-04-01
Thanks alot.... yes i tried this way some 20 days ago so maybe this is the cause. I appreciated very much Ubuntu and i have it at home so i'm in ;), but for my work and study laptop prefer to stay with Debian for some time! If in the future the differences between the two distro will come in favour of Ubuntu i will for sure move to that!

Regards,
MC

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=mirtux]Thanks alot.... yes i tried this way some 20 days ago so maybe this is the cause. I appreciated very much Ubuntu and i have it at home so i'm in ;), but for my work and study laptop prefer to stay with Debian for some time! If in the future the differences between the two distro will come in favour of Ubuntu i will for sure move to that!

Regards,
MC[/QUOTE]
 please explain why you prefer to stay with debian unstable.I'm curious because hoary has security-updates and debian unstable doesn't.

---

### Post by mirtux on 2005-04-01
Well, it's just a question not of security-updates or things like that... i know that now hoary is mature, but my experience in updating was not positive.

Maybe now things have changed (i hope), but when i used Warty (installed in December) everyone was working with Hoary (Warty was just 2 months), just backporting for new programs: i would have liked to have kde 3.3.2 that was released but there was only kde 3.2.2.... the only was of getting 3.3.2 was to use the hoary repositories. I don't like that kind of development. The life of a distribution is not really 6 months. I like as, in the Debian unstable case, when i'm running a distro that needs just a simple click for upgrading.

Regards,
MC

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=mirtux]Well, it's just a question not of security-updates or things like that... i know that now hoary is mature, but my experience in updating was not positive.

Maybe now things have changed (i hope), but when i used Warty (installed in December) everyone was working with Hoary (Warty was just 2 months), just backporting for new programs: i would have liked to have kde 3.3.2 that was released but there was only kde 3.2.2.... the only was of getting 3.3.2 was to use the hoary repositories. I don't like that kind of development. The life of a distribution is not really 6 months. I like as, in the Debian unstable case, when i'm running a distro that needs just a simple click for upgrading.

Regards,
MC[/QUOTE]
 canonical/ubuntu is oriented at gnome I like this. Ubuntu is quite new. So it takes a while to get everything organized. 

Kubuntu is a project by the community to integrate the latest KDE into Ubuntu. latest KDE in Ubuntu is only now a viable option. see kubuntu.org

upgrading warty to hoary is as easy/hard as upgrading debian

---

### Post by mirtux on 2005-04-01
As i wrote in another thread i don't like this distribution split. I don't understand why people must work with kde OR with gnome. In my case i'm usually working with kde as a window manager, but i'm using a lot of gnome programs, like gthumb for example. I think that this has not been a good choice for the community.

Regards,
MC

---

### Post by ubuntu_demon on 2005-04-01
It's not a distribution split. They just thought up a crazy name for the project :). Yeah they got a different install cd but the only way it differs is that it installs kubuntu-desktop (kde) instead of ubuntu-desktop (gnome).

You can choose to install kubuntu-desktop on a working ubuntu machine and still have acces to gnome. You only have to do "sudo apt-get install kubuntu-desktop" and "sudo dpkg-reconfigure gdm". The other way around is also possible.

If you want kde just download the kubuntu release candidate. kubuntu becomes final together with hoary (obviously since they use the same repo's)

---

### Post by mirtux on 2005-04-01
That's a good news, and a good point. 

Thanks,
MC

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=mirtux]That's a good news, and a good point. 

Thanks,
MC[/QUOTE]
 I know :-D

You could try the live-cd to see if you like it. If you don't you can try again next week when it gets released or in a couple of months.

---

### Post by mirtux on 2005-04-01
Oh yeah, i've just tried the live cd.... and then i installed at home... the only problem is that there i don't have a live and fast internet connection, so i cannot install packages... 

However my quite bad experience remains... 

Regards,
MC

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=mirtux]Oh yeah, i've just tried the live cd.... and then i installed at home... the only problem is that there i don't have a live and fast internet connection, so i cannot install packages... 

However my quite bad experience remains... 

Regards,
MC[/QUOTE]
 Maybe you can help test and give feedback.

from [http://www.kubuntu.org](http://www.kubuntu.org) :

> 
With one week to go until our first final release we are now looking for testers and feedback on the Release Candidate


Or maybe try again next week or later. You have to keep in mind that this is a community effort that hasn't been started very long ago. I'm sure kubuntu will improve in time.

here's the kubuntu forum :

[http://ubuntuforums.org/forumdisplay.php?f=65](http://ubuntuforums.org/forumdisplay.php?f=65)

---

