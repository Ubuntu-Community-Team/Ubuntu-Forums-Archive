---
title: "Upgrade Failed  10.04-&gt;10.10"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by armware on 2010-10-04
Following the instructions at:
[https://help.ubuntu.com/community/MaverickUpgrades/Kubuntu](https://help.ubuntu.com/community/MaverickUpgrades/Kubuntu)


I chose to upgrade from the internet, so I ran: kdesudo "do-release-upgrade -m desktop -f kde -d"

the dialog appeared it said something about my system not being upgradeable. i closed it without thinking and began to search for answers. i had to re-run the command above and it did not give me an error, but instead the option to start the upgrade which i chose.

i opted to install all the package maintainers config file versions, making myself a backup copy for the ones i had custom edits in.

i could provide more details on this, but this is not the reason for my post, which i'll skip to.

i believe my system to be in an unstable state, as the upgrade failed when it got to installing grub-pc. if i run: sudo dpkg --configure -a, it still fails giving me:

```

adam:~$ sudo dpkg --configure -a          
Setting up grub-pc (1.98+20100804-5ubuntu2) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 30
Errors were encountered while processing:
 grub-pc
```

i'm worried about rebooting. anybody have any thoughts? questions? suggestions? i'm open to them all.

bug report:  [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/654705](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/654705)

---

### Post by andrewthomas on 2010-10-04
```
sudo aptitude purge grub-pc
```

followed by 

```
sudo aptitude update && sudo aptitude install grub-pc
```

---

### Post by armware on 2010-10-04
I did a few things before I read your post, I won't know if it worked until I reboot so I'm posting this before hand.

What I did was ran:

```

sudo update-grub-from-legacy

```

Then:
```

sudo aptitude install grub-pc

```

which finished successfully. Running:

```

sudo apt-get update;sudo apt-get dist-upgrade

```

finished without incident.

---

### Post by andrewthomas on 2010-10-04
> **armware said:**
> 

```

sudo update-grub-from-legacy

```
I didn't realize that you had upgraded to 9.10 also.

---

### Post by armware on 2010-10-04
I hadn't thought of that. I do prefer to upgrade between versions, and only do wipe/reinstalls if things get squirrely.

For how long does this effect my setup, or is this a special case (new fancy grub version)? I would have thought that once my 10.04 was setup the previous upgrade would not have mattered.

---

### Post by andrewthomas on 2010-10-04
Once you got rid of your grub legacy you will never have to deal with it again.  

You should be all good now.

---

### Post by armware on 2010-10-04
Yep, rebooted and things are working great. Typing this on Kubuntu 10.10. Thanks andrew.

---

### Post by andrewthomas on 2010-10-04
You're welcome.

---

