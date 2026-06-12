---
title: "Virtualbox"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by deepblue80 on 2007-08-20
hELLO
I am a newbie to linux and have taken the plunge with my hardware upgrade. now i tried installing virtualbox and the synaptic manager froze. so i rebooted the system thinking it will just clean the slate. well i am wrong - i cannot install anything now as it keeps giving me a weird message 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

i cant even update see this

deepak@deepak-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

now looking  up on the net there were a few commands that i found to clear the cache as one user put it, i wrote 
sudo /var/cache/apt/pkgcache.bin

then it gave me this message

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.


when i try to run dpkg --configure -a it gives me this msg 

dpkg: requested operation requires superuser privilege

i didnt create any user account and i only have 1 account that i use to login - i presume this is the root so why does it tell me thtat i dont havce superuser privilege? 
i am at my wits end as i cannot install anything now till i have sorted this out - anyone see a solution other than a re-install?
regards?

---

### Post by Warpedflash on 2007-08-20
you need to have the sudo command in front of those commands

sudo apt-get update
sudo dpkg --configure -a

it will ask for your password enter it and the command will run

---

### Post by deepblue80 on 2007-08-21
> **Warpedflash said:**
> you need to have the sudo command in front of those commands

sudo apt-get update
sudo dpkg --configure -a

it will ask for your password enter it and the command will run

Thanks - it did run but i dont know what to write next! would you have any idea? it gives me a list of options (very similar to DOS) but what commands to i use to configure it myself!!?

---

### Post by forestpixie on 2007-08-21
what do you mean  - what do you want to write next? it gave you a list of options? do you mean it didn't work properly - what do you get now if you do 

```
sudo apt-get update
```

does it work? paste the output here if not

if it does what are you actually trying to achieve now

---

### Post by deepblue80 on 2007-08-21
> **forestpixie said:**
> what do you mean  - what do you want to write next? it gave you a list of options? do you mean it didn't work properly - what do you get now if you do 

```
sudo apt-get update
```

does it work? paste the output here if not

if it does what are you actually trying to achieve now

i am trying to install an application but i just cant. when i run the synaptic manager it gives me this error message

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

what do i do?

ps
in terminal i tried sudo apt-get autoclean to get rid of the old archives but got this message

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by forestpixie on 2007-08-21
try this 

```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

---

### Post by deepblue80 on 2007-08-21
> **forestpixie said:**
> try this 

```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

i tried that and got this in the terminal

dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `virtualbox' missing, assuming package has no files currently installed.
105997 files and directories currently installed.)
Removing virtualbox ...

then i wrote sudo apt-get virtualbox, and i got 

deepak@deepak-desktop:~$ sudo apt-get install virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package virtualbox has no installation candidate

---

### Post by forestpixie on 2007-08-21
It's not in the repos is it? Did you not download the virtualbox deb previously from innotek

if you still got it or it's in the trash get it back on the desktop and dblclick it (I think)

---

### Post by deepblue80 on 2007-08-21
> **forestpixie said:**
> It's not in the repos is it? Did you not download the virtualbox deb previously from innotek

if you still got it or it's in the trash get it back on the desktop and dblclick it (I think)

right i have gone to the virtualbox website and downloaded it, the package installer ran as soon as it downloaded but there is no progress at all.... i think this is was led me to reboot thesystem last time and it in effect has the installation manager in a limbo. is there any input expected from the user (i.e. me) during this process specially installaling virtualbox - i dont see any popup windows and when i press the terminal button on the package installer which is in process of installing, i see the license terms and conditions - its very similar to a freeze in windows! the only difference is i dont see the blue screen of death - other apps r working fine!

---

### Post by forestpixie on 2007-08-21
yes somewhere there should be an 'OK' for you to click or tab on to so you can enter - is it hidden behind anything - I'm sure it's there somewhere - if not don't close it yet - just leave it hanging  there waiting until..

rather than wait here for another answer which might be  a while - post a new thread but in the Absolute Beginners forum instead it can be quicker there

good luck

---

