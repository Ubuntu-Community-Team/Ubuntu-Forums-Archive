---
title: "Upgrade to 10.10 from 10.04"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by Chris Morin on 2011-01-28
Hi, I currently have ubuntu version 10.04 and want to upgrade to 10.10.
I'm supposed to be able to do this from the "update manager" so I changed the settings of "update manager" to show new distribution releases to normal releases (as opposed to the long term support releases). After clicking on "check", I'm not prompted to upgrade, I'm just told my system is up to date. When clicking on check, I receive this error message:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513

Thanks for the help.

Chris

---

### Post by zvacet on 2011-01-29
In terminal 

```
gksudo gedit /etc/apt/sources.list
``` 

and remove that line.Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

Maybe you can try to reboot and then see if package manager is set for normal releases.

---

### Post by Chris Morin on 2011-01-29
So I did as you said, the error message is gone, but I'm still not prompted to upgrade. I reebooted and the package manager was set to normal releases.
Thanks

Chris

---

### Post by Claudestephane on 2011-01-30
> **zvacet said:**
> In terminal 

```
gksudo gedit /etc/apt/sources.list
``` 

and remove that line.Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

Maybe you can try to reboot and then see if package manager is set for normal releases.

The first  gksudo gedit /etc/apt/sources.list  command produced the following, in which I could not find line.Save or anything resembling it. My update manager settings have all but unsupported options checked. 
Your thoughts welcome, Claude):P

---

### Post by matt_symes on 2011-01-30
Hi

Open a terminal and type

```
sudo update-manager --dist-upgrade
```

Are any errors returned ?

EDIT: Missed the fact you had fixed it.

Kind regards

---

### Post by Chris Morin on 2011-01-30
> **matt_symes said:**
> Hi

Open a terminal and type

```
sudo update-manager --dist-upgrade
```

Are any errors returned ?

EDIT: Missed the fact you had fixed it.

Kind regards

Thanks for replying

After doing this I received an error message that my system was already up to date (even though I have 10.04 and want 10.10). So the upgrade didn't work.

---

### Post by matt_symes on 2011-01-30
Hi

Have a look at the command line section of this tutorial.

[http://www.ghacks.net/2010/09/28/upgrade-ubuntu-from-10-04-to-10-10/](http://www.ghacks.net/2010/09/28/upgrade-ubuntu-from-10-04-to-10-10/)

Kind regards

---

### Post by Claudestephane on 2011-01-31
Thanks Matt,

update-manager --devel-release

uneventfully produced your predicted upgrade button in update manager. Clicking on it seemed to be proceeding through the steps, alerting me that unsupported programs (Oracle's full VirtualBox) would be omitted, and could be added later. Then after a few minutes of gyrating, error msg came up that calculation of .... failed advising reporting a bug with contents of 
/var/log/dist-upgrade
/var/log/dist-upgrade/20100113-0139/apt.log
/var/log/dist-upgrade/20100113-0139/apt-term.log
/var/log/dist-upgrade/20100113-0139/main.log
/var/log/dist-upgrade/20100113-0139/term.log
/var/log/dist-upgrade/20100113-0139/xorg_fix_intrepid.log

Does that help solve the problem? Update manager after error msg, simply restored prior OS ver 10.04

Claude:-(

---

### Post by matt_symes on 2011-01-31
Hi

Hmmmm. Not sure what the problem is here. 

About the only thing i can suggest is you could update your sources.list file to point to maverick instead of lucid and then try

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

However i am not 100% sure of the implications of doing this so i would suggest you wait until someone else has a say.

If the worst comes to the worst, back up your back and perform a clean install of 10.10. This is my preferred solution anyway.

Kind regards

---

### Post by Chris Morin on 2011-02-01
> **matt_symes said:**
> Hi

Have a look at the command line section of this tutorial.

[http://www.ghacks.net/2010/09/28/upgrade-ubuntu-from-10-04-to-10-10/](http://www.ghacks.net/2010/09/28/upgrade-ubuntu-from-10-04-to-10-10/)

Kind regards

Tried this and it ended up installing 11.04. Decided to just do a fresh install with 10.10.

Thanks for the help.

---

### Post by matt_symes on 2011-02-01
Hi

```
Tried this and it ended up installing 11.04
```


Ehhh. Sorry about that. Not my finest advice.

Kind regards

---

### Post by Chris Morin on 2011-02-02
Don't worry about it. It probably had to be done anyways.

---

