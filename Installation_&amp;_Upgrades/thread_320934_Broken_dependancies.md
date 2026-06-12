---
title: "Broken dependancies"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by nomadique on 2006-12-18
I was trying to reinstall audacious. But on reinstallation it asked for some dependancies so i nstalled them manually one of them was fontconfig-config. In the result everywhere now i get the message about broken dependacies and i can't fix it with any obvious method. Not in the Synamptic manager not with sudo apt-get install -f

nomad@nomad-laptop:~$ sudo apt-get --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies.
  libfontconfig1: Depends: fontconfig-config (= 2.3.2-7ubuntu2) but 2.4.2-1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

Can anyone else give me a sound solution for the problem please? Untill then i can't install anything on the system

---

### Post by an.echte.trilingue on 2006-12-18
For me, this is usually caused by having not updated in a while (ie, apt-get doesn't know about foo v1.5.2, which replaces foobar v0.9 and returns an unmet dependancy issue because it can't find foobar >= v0.9 because foobar is now called foo).  Always fixed for me with
```
sudo apt-get update 
sudo apt-get upgrade
```

Take care,
-mat

---

### Post by nomadique on 2006-12-18
Thanksfor responce, i tried it and it didnt help.

nomad@nomad-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
  libfontconfig1: Depends: fontconfig-config (= 2.3.2-7ubuntu2) but 2.4.2-1 is installed
E: Unmet dependencies. Try using -f.


nomad@nomad-laptop:~$ sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies.
  libfontconfig1: Depends: fontconfig-config (= 2.3.2-7ubuntu2) but 2.4.2-1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

---

### Post by bulldog on 2006-12-18
Did you try the 'repair broken packages' option in synaptic?
Never had a problem to repair broken packages with it.

---

### Post by nomadique on 2006-12-18
Yes, it gave me this answer 

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

Can someone tell me please what are held packages and how can i unhold them?? Really this starts to piss me of, all system is stuck because of one broken component, every system tool now just stops telling me that i have to fix it.

---

### Post by bulldog on 2006-12-18
> **nomadique said:**
> Yes, it gave me this answer 

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

Can someone tell me please what are held packages and how can i unhold them?? Really this starts to piss me of, all system is stuck because of one broken component, every system tool now just stops telling me that i have to fix it.

To resolve your broken packets synaptic needs to break other packets,this can be caused by held packets.
Held packets are the ones who can't be installed because you have broken packages.
You can't un- hold them till you have solved the broken packages.
That's why you better use the repositories to install applications.

Can tell you horror story's with Fedora and SuSe and the rpm packages.

---

### Post by nomadique on 2006-12-18
Don't really need any more horror stories, i don't know how to solve this one ;) The only solution is to reinstal ubuntu? ;))) Everything depends on everything and you can;t work until you solve something.

---

### Post by tiakun on 2007-03-03
I found this on [COLOR="Blue"][https://answers.launchpad.net/ubuntu/+ticket/3510](https://answers.launchpad.net/ubuntu/+ticket/3510)[/COLOR]

```
sudo apt-get install fontconfig-config=2.3.2-7ubuntu2
```

That should help. It worked for me but take your own risk. :KS

---

### Post by Kateikyoushi on 2007-03-03
Hopefully, but I guess we won't know after 3 months.

---

### Post by Scollk on 2007-03-03
I just had the exact same problem, and that solution did work. Thanks very much

---

