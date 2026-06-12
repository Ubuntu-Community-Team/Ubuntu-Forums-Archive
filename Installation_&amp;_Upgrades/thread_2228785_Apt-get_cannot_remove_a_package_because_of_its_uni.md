---
title: "Apt-get cannot remove a package because of its uninstalled dependencies."
date: 2014-06-09
forum: Installation &amp; Upgrades
---

### Post by noah-stride on 2014-06-09
So I decided to install flightgear on my ubuntu 14.04 install. A mistake indeed. One of the packages seems to download but not configure correctly. This is causing problems on apt-get meaning I cant install anything without an error. The package is flightgear specific. I have had enough and just want out. So i decided to apt-get remove --purge flightgear. It tells me the following packages have unmet dependencies. it lists the dependency required and says it is not going to be installed. I tried -f install. No luck. Am I really being told that a piece of software needs to be complete to be removed?!??!?!

---

### Post by LastDino on 2014-06-09
Command is
```
[COLOR=#000000][FONT=Consolas]apt-get --purge remove {package_name}
```

I could be wrong and your way might be working as well, but this is what I usually use and it works like magic.[/FONT][/COLOR]

---

### Post by noah-stride on 2014-06-09
Still doesnt work.
Heres what I get:
noah@noah-GA-78LMT-S2P:~$ sudo apt-get --purge remove flightgear
[sudo] password for noah: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 flightgear-data-all : Depends: flightgear-data-ai (>= 3.0.0~) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by megabean on 2014-06-09
I have the same problem as you do for almost a year now.... Also have been trying to find a sollution and tried just about everything and more what people on this fórum have suggested but no luck. My latest try was to free some space by deleting old Linux headers which are not used anymore using the apt-get --purge remove {package_name} as suggested by someone because one header just does not want to download but it doesn´t let me do that either. After a while my thread was ignored completely and no more answers came so i hope you have more luck and i´ll keep na eye open for any results that might pop up,,,new results or sollutions that is ;-)
cheers,

---

### Post by LastDino on 2014-06-09
Never had such a problem tbh, but you could try from synaptic, maybe? 

Also, try things like;
```
sudo apt-get autoremove
```

Then
```
sudo apt-get clean
```

Run that purge command later to see if it has any effect whatsoever. I'm reaching for straws here, but worth a try.

---

### Post by noah-stride on 2014-06-12
I have tried both...
No avail
noah@noah-GA-78LMT-S2P:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 flightgear-data-all : Depends: flightgear-data-ai (>= 3.0.0~) but it is not installed
E: Unmet dependencies. Try using -f.
noah@noah-GA-78LMT-S2P:~$ sudo apt-get clean
noah@noah-GA-78LMT-S2P:~$ sudo apt-get remove flightgear
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 flightgear-data-all : Depends: flightgear-data-ai (>= 3.0.0~) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I really need help. This is a pain in the ass. I can provide any logs/etc people need!

---

### Post by Bashing-om on 2014-06-12
noah-stride Hello.

Up front, I really do not understand all I do not know about the package management system.
This is going over my head:
```

sysop@1310mini:~$ apt-cache depends flightgear-data-ai
flightgear-data-ai
  Breaks: fgfs-base
  Breaks: <fgfs-base:i386>
  [color=red]Breaks: flightgear[/color]
  Breaks: flightgear:i386
sysop@1310mini:~$

```

But anyway, let's see what happens with a directive to install 'flightgear-data-ai' . Maybe get some additional info to see our path clear to a solution.
```

sudo apt-get install flightgear-data-ai

```

Looking to get the application installed to the point where the package manager can (UN-)install.

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times I do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bapoumba on 2014-06-12
How did you install flightgear ? From the ppa ?
[https://launchpad.net/~saiarcot895/+archive/flightgear](https://launchpad.net/~saiarcot895/+archive/flightgear)

Please post your sources.list and ppas or third party repos :
```
cat -n /etc/apt/sources.list
ls /etc/apt/sources.list.d
```

---

### Post by noah-stride on 2014-06-17
I installed it, probably a bad idea, from the ubuntu software center.

---

### Post by noah-stride on 2014-06-17
After approximately 8 attempts to install it. It just installed.
Magic. Thanks guys. We will never know the cause!

---

### Post by Bashing-om on 2014-06-17
noah-stride; Great !

We can surmise just for the 'fun'.

Maybe; the mirror you are accessing was not up-to-date and awaiting "held packages" files to be brought in ?
Maybe; your system's data bases were not up to date with that of the mirror ?
Maybe; inconsistent control files on your system that the smart package management system finally fixed ?

But, in the end all that matters is all is good now.
 
Please mark this thread solved; aides others seeking the solution, 
helps keep the forum clean and 
precludes others miss-directing efforts to aid.

[INDENT][INDENT]keep on
[INDENT][INDENT][INDENT]keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

