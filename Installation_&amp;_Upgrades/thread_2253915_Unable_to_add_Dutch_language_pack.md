---
title: "Unable to add Dutch language pack"
date: 2014-11-23
forum: Installation &amp; Upgrades
---

### Post by Will_Moonen on 2014-11-23
Hello Everyone,

I'm trying to add the Dutch language to an existing installation of Ubuntu 14.04.1.
I tried with the system settings, Synaptics package manager and sudo apt-get command - see below the results of the APT-GET.

```
will@Stinkpad:~$ sudo apt-get -f install language-pack-gnome-nl-base language-pack-nl-base language-pack-gnome-nl language-pack-nl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 language-pack-gnome-nl : Depends: language-pack-gnome-nl-base (>= 1:14.04+20140707) but 1:14.04+20140410 is to be installed
 language-pack-nl : Depends: language-pack-nl-base (>= 1:14.04+20140707) but 1:14.04+20140410 is to be installed
E: Unable to correct problems, you have held broken packages.
will@Stinkpad:~$ 

```

I don't quite understand what it says.
But it seems something like "you are trying to install and older version".

Either way - is there someone out there that can clarify this? And more important how do I fix this?


Thanks - Will

---

### Post by wil5 on 2014-11-23
Hello,

i,m installing Ubuntu 14.04 almost daylay for the computerclub in Voorburg, Netherlands.
Last week everything normal, with the dutch language.
Sinds yesterday at the first reboot appears the message, languagepakkage is not complete.
The update says not possible  missing the dutch language pakkage.
The pakkage installer is removing the dutch pakkage on installation. Remaning is a uk version with a dutch mix.
So we are waiting until the bug is fixt. Dutch beginners must have a complete dutch fresh installation.
How to handel this??  Thankyou.
Forgive me my pour english.

---

### Post by bapoumba on 2014-11-23
[https://bugs.launchpad.net/ubuntu/+source/language-pack-nl-base/+bug/1394923](https://bugs.launchpad.net/ubuntu/+source/language-pack-nl-base/+bug/1394923)
You may want to mark this bug as affecting you too. There is a work around.

---

### Post by bapoumba on 2014-11-23
@ wil5 : merged your thread in here, as this is the same problem.

---

### Post by wil5 on 2014-11-23
@ bapoumba : Missing languagepac- nl afther a fresh installation. Serveral attempts.

---

### Post by bapoumba on 2014-11-24
Have you tried the workaround from the bug report, post #8 ?

---

### Post by wil5 on 2014-11-24
@ bapoumba.

Please make a fresh install in a different language and look in the installationscreen (details) and find out that the bug is serious.
The mistake is in the installation scripts. Last wensday everything was ok. The bug was in the script from friday intill now.
Thankyou in advanced.

---

### Post by Topsiho on 2014-11-24
Hallo Will_Moonen,

I think the problem is that you should first update (bijwerken) your system first.
As it happens (toevallig) one (or more) of the files that are needed is obsolete (verouderd) and should be updated first, before you can install the files that you want.

Groeten van

Topsiho

---

### Post by wil5 on 2014-11-24
Just a minute ago installed new updates, mostly about language.
Now it is posible to update and change the language in systemsettings.
I now put in a empty harddisk and make fresh install. When don i will post the resaults about the Dutch language. 
Back in 90 min.

---

### Post by bapoumba on 2014-11-24
The workaround in the report says you should enable the -proposed repositories, that will allow the missing dependencies to be satisfied. -proposed repositories are not usually recommended as they are to test packages. In this case, either you get to use them, or wait for the regular packages from the regular repos to be fixed.

---

### Post by wil5 on 2014-11-24
I did a fresh installation on a spare harddisk.
Still not possible to chance and select the language in systemstetting. 
All the updates are installed.
For the time being i [COLOR=#000000]wait for the regular packages from the regular repos to be fixed.
Tomorrow whe have to install Mint for the dutch beginners.
Afther the bug is fikst whe switsing back to Ubuntu.

Thankyou.


[/COLOR]

---

### Post by wil5 on 2014-11-24
I [COLOR=#000000]wait for the regular packages from the regular repos to be fixed.
In the time being switching back to Mint for the Dutch beginners.
Thankyou, speak you all later.[/COLOR]

---

### Post by Will_Moonen on 2014-11-25
The [suggested workaround]("https://bugs.launchpad.net/ubuntu/+source/language-pack-nl-base/+bug/1394923") fixed things for me.
No more unresolved dependencies and an update of the language pack was installed successfully.

Thanks everyone for the contribution!

---

### Post by Topsiho on 2014-11-25
For those who are reading this: I just received updates for these files, so I think the problem is resolved now, and workarounds are not necessary.
(Ik heb vandaag (25 nov) updates ontvangen van de betrokken bestanden, en ik denk dus dat hierna het probleem is opgelost, en er geen extra maatregelen meer nodig zullen zijn).

Topsiho

---

### Post by wil5 on 2014-11-25
Solved.

From the Dutch forum.

Go to Software sourches\Updates and select proposed. 
Open system\language  now you are able to update and make chances.

Afther the reboot your language is ready.

WHEN DON UNSELECT " proposed "

Solved.

---

