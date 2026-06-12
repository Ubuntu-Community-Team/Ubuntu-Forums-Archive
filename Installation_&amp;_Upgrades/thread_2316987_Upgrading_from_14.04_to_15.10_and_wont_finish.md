---
title: "Upgrading from 14.04 to 15.10 and wont finish"
date: 2016-03-12
forum: Installation &amp; Upgrades
---

### Post by Clanstyles on 2016-03-12
After apt-get upgrade was running it froze on "Setting up keyboard-configuration" I checked error logs, dpkg.log had:
> 2016-03-12 12:30:42 startup packages configure
2016-03-12 12:30:42 configure keyboard-configuration:all 1.108ubuntu9 <none>
2016-03-12 12:30:42 status half-configured keyboard-configuration:all 1.108ubuntu9

I can't figure out why it's not finishing or what to do. Any ideas?

---

### Post by grahammechanical on 2016-03-12
What state is the installation in now? If the upgrade has not finished, have you shut down and re-started? Or, do you still have an incomplete upgrade that is still frozen? 

What you do will all depend on what you have already done. If you have backed up your data then you have a little less worry if a restart ends up with a completely unusable system.

If the restart loads to any kind of working desktop environment we can run

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

And that might finish the upgrade.  We can also at the boot menu select Advanced options for Ubuntu and then select recovery mode. At the recovery menu we can select Network to set up an internet connection and then select Root shell prompt and then run

```
apt-get update
apt-get upgrade
apt-get dist-upgrade
```

To get back to the recovery menu we type enter and then we can select Resume and see if that gets us to a working desktop. There is one more thing we can do. We can prepare ourselves for the last resort of a fresh install.

Regards.

---

### Post by kansasnoob on 2016-03-12
What method did you use to upgrade?

---

### Post by kansasnoob on 2016-03-12
Possibly this bug:

[https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/1509392](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/1509392)

---

### Post by Clanstyles on 2016-03-12
I upgraded via the recommended upgrade popup. So via the package manager i assume. I'm able to boot into 15.10 but I'm not able to manage my packages since it didn't finish configuring a few packages (the keyboard is the one getting stuck).

---

### Post by kansasnoob on 2016-03-12
Try:

```
sudo dpkg-reconfigure keyboard-configuration
```

---

### Post by Clanstyles on 2016-03-12
I'm getting
```
/usr/sbin/dpkg-reconfigure: keyboard-configuration is broken or not fully installed

```

---

### Post by kansasnoob on 2016-03-12
OK, you're going to have to try some things and be sure to post back here any errors. It may also be neccessary to repeat any number of these commands in no specific order. To start:

```
sudo apt-get update
```

Next we'll try --fix-broken and/or --fix-missing suffixes which can be used both with dist-upgrade or with a specific package like:

```
sudo apt-get install keyboard-configuration --fix-missing
```

Or:

```
sudo apt-get install keyboard-configuration --fix-broken
```

Or with dist-upgrade like:

```
sudo apt-get dist-upgrade --fix-missing
```

Or:

```
sudo apt-get dist-upgrade --fix-broken
```

A lesser used, and seldom helpful suffix is --ignore-missing. But it's seldom helpful although once in a while it can break a log jam long enough to get other packages installed and/or upgraded.

Another helpful command is:

```
sudo dpkg --configure -a
```

And yet another is:

```
sudo apt-get -f install
```

And, as I already said, you may need to repeat any of those in no specific order. If apt-get update shows any errors at all that will prevent you from going any further so let us know.

---

### Post by Clanstyles on 2016-03-13
```
sudo apt-get install keyboard-configuration --fix-missing
``` 
This did the same thing (stuck at keyboard-configuration)

```
sudo apt-get dist-upgrade --fix-missing
```
Still, same thing. I was missing a few packages (flashplugin-installer libotr5 liboxideqt-qmlplugin liboxideqtcore0 liboxideqtquick0 oxideqt-codecs-extra) - I don't use flash plugins ever... not sure why it's included.

```
sudo apt-get dist-upgrade --fix-broken
```
This does the same thing. No actual changes to be made 

```
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
26 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
```

I should note, I haven't been able to run any these commands without running the command below first. I then try to CTRL+C before it hits Setting up keyboard-configuration. I should note I see the message it's starting it and I cancel it. I have also let it run and it just freezes.
```
sudo dpkg --configure -a
```

I should note, sudo apt-get -f install is an option, I would like to avoid using it. I want to see if we can narrow down what the issue with the keyboard-configuration setup is.

---

### Post by kansasnoob on 2016-03-13
Does sudo apt-get update display any errors at all?

---

### Post by Edison_James on 2016-03-13
I have never had success with upgrades and don't even bother trying anymore. I wait for a new version and do a clean install.
An upgrade to 15.10 becomes redundant in a few weeks anyway as the new 16.04 LTS will be released.

---

### Post by Clanstyles on 2016-03-13
> **kansasnoob said:**
> Does sudo apt-get update display any errors at all?

This doesn't do anything, it's not a valid command.

> **Edison_James said:**
> I have never had success with upgrades and don't even bother trying anymore. I wait for a new version and do a clean install.
An upgrade to 15.10 becomes redundant in a few weeks anyway as the new 16.04 LTS will be released.

I understand what you're saying. I don't really want to reformat if possible.

---

### Post by sammiev on 2016-03-13
```
sudo apt-get update 
```

This is what kansasnoob suggested.

---

### Post by Bashing-om on 2016-03-13
Clanstyles; Hello;

Is your keyboard functional at this time ?
What results ?
```

sudo apt-get --reinstall install xkb-data

```

depending on that result is what we do next.

[INDENT][INDENT]maybe yes
[INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kansasnoob on 2016-03-13
> **sammiev said:**
> ```
sudo apt-get update 
```

This is what kansasnoob suggested.

+1! I'd listed it first in my [post #8]("http://ubuntuforums.org/showthread.php?t=2316987&p=13454471#post13454471") because if that shows any errors at all then we need to find out why. Basically if the software cache can't update properly then we can't expect any other package transaction to work properly.

---

