---
title: "Update Manager latest version"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by DesignerX on 2006-09-28
I want to upgrade from breezy 5.10 to dapper 6.06 (LTS)

The instructions say I need update manager version 0.42.2ubuntu12~breezy1
but I got less. 

How can I upgrade to the required version ? 
I pressed the "Reload" button at Synaptec but no upgrade seems to be available for the update manager.

And generally asking, If I want to upgrade a package, how can I know if an update exists and how do I get it using ubuntu ?

thx in advance ...

---

### Post by Kateikyoushi on 2006-09-28
You have to edit your sources.list first.

```
gksudo gedit /etc/apt/sources.list
```

Change every instance of breezy with dapper and save the file.

Then upgrade

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Finally reboot.

---

### Post by linear on 2006-09-28
You can upgrade without Update Manager. See instructions [here]("http://ubuntuforums.org/showthread.php?t=185467").

Normally, you should be notified automatically when updates are available (if Update Manager is working properly).

Synaptic should also show you upgradeable packages.

You might want to check your copy of sources.list, to make sure the official repositories are enabled.

(And it's a good idea to start with a clean sources.list when upgrading Breezy to Dapper.)

---

