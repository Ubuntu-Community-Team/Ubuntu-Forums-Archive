---
title: "Interrupted Upgrade - Can't Resume"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by jackn on 2011-10-15
I've just tried to upgrade to Oneiric from Natty.

I used the 'upgrde' button in the Update Manager.

The upgrade was going well, but at some point, the screen went dim, and I couldn't get back into my session. I shut down manually.

I now seem to be in Oneiric - the (lovely) new login screen is there, and my Update Manager doesn't suggest upgrading. 
Nor do I see the 'Release Upgrades' check when I get into 'setting' in the Update Manager. 
As far as *it* is concerned, all's well.

But I know I was only in the middle of the upgrade. Many tasks must have remained unaccomplished. I haven't played around with the new version yet, but I worry that the upgrade is incomplete and that I'll run into issues in the future.

How can I resume, or simply redo, the upgrade, to make sure it's complete?

Thanks,
jackn

---

### Post by MAFoElffen on 2011-10-15
> **jackn said:**
> I've just tried to upgrade to Oneiric from Natty.

I used the 'upgrde' button in the Update Manager.

The upgrade was going well, but at some point, the screen went dim, and I couldn't get back into my session. I shut down manually.

I now seem to be in Oneiric - the (lovely) new login screen is there, and my Update Manager doesn't suggest upgrading. 
Nor do I see the 'Release Upgrades' check when I get into 'setting' in the Update Manager. 
As far as *it* is concerned, all's well.

But I know I was only in the middle of the upgrade. Many tasks must have remained unaccomplished. I haven't played around with the new version yet, but I worry that the upgrade is incomplete and that I'll run into issues in the future.

How can I resume, or simply redo, the upgrade, to [COLOR=Red]make sure it's complete[/COLOR]?

Thanks,
jackn
I'd make sure it's completed.

In a terminal session:
```

sudo apt-get update  
sudo apt-get clean 
sudo apt-get -f  
sudo apt-get dist-upgrade

```If there was nothing to upgrade it would say so in the dist-upgrade command output.

Then check the distro info:
```

uname -r && lsb_release -a

```

---

### Post by jackn on 2011-10-16
Thank you so much for this prompt help, MAFoElffen.

I ran the suggested commands.

The first two, 'update' and 'clean' responded properly.
The -f switch, on the other hand, gave feedback which suggests that apt-get might have expected another form. I'm not sure. The standard help input it spit out is given below.
 
The distro info enquiry gave what seems like perfect information:
```
3.0.0-12-generic
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric

```
apt-get -f output:
```
apt 0.8.16~exp5ubuntu13 for i386 compiled on Oct  6 2011 15:25:29
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
(Cut here, for the sake of brevity)   

  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
```

I'm still very concerned that the upgrade is incomplete.

From man apt-get, it seems like the command for fixing broken packages should include 'install' (or 'remove'), as follows:
```
sudo apt-get -f install
```

Do you think it's a good idea to run the above command?

To me, that the upgrade appears to have gone through doesn't necessarily mean much. 
It could be that the system uses intermediate indicators for completion of the upgrade, leading it to think that the upgrade has gone through while it is in fact incomplete.

While the system appears to run normally, I've only been at it for a very short while.
And, for what it's worth, I can't run lightdm to modify the login session. I don't know whether this is as it should be or not:
```
sudo lightdm
Failed to use bus name org.freedesktop.DisplayManager, do you have appropriate permissions?
```

I appreciate your help, MAFoElffen.

---

### Post by garvinrick4 on 2011-10-16
MAFoElffen had a typo he meant sudo apt-get -f install sometimes brain works faster than
fingers. Run these to cure anything that is waiting to be installed that is already downloaded, fix broken packages and update and upgrade.
```
sudo dpkg --configure -a
```
```
sudo apt-get -f install
```
```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by boygenuis on 2011-10-16
If I may jump in, please, I'm having the same issue; however, after running "sudo apt-get upgrade" I'm still left with 2 packages not upgraded.  Suggestions?

---

### Post by jackn on 2011-10-16
Thank you very much, Garvinrick, for this advice.

I ran all the commands...

They all ran smoothly.

Other than the removal some packages, nothing to write home about.

Does this mean it's OK?
I don't know.

At this point, should I consider a fresh install?

Thank you very much for your help and attention.
jackn

---

### Post by garvinrick4 on 2011-10-16
> Does this mean it's OK?I would say yes, if you are up to date and have no broken packages you are
just fine, no reason to do anything else. Just enjoy your Ubuntu.
> Thank you very much for your help and attention.
jackn You are welcome and will keep this thread subscribed incase you have anything you want to ask.

---

