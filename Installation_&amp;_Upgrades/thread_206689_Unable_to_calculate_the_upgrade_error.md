---
title: "Unable to calculate the upgrade error"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by gfreemankc on 2006-06-30
I'm trying to upgrade from Breezy to Dapper using the upgrade GUI.  I start it, and get a message stating:
Some third party entries in your sources.list were disabled.  You can re-enable them after the upgrade...

I'm guessing that's normal and ok.

I close hte dialog and it downloads some packages, then I get another dialog stating:

Could not calculate the upgrade
A unresolvable problem occurred while calculating the upgrade.  Please report this as a bug.

The installation seems to roll back after I press the close button on that dialog...

I'd love to include some more information if I knew where to get it...

Can anyone assist?

---

### Post by xslf on 2006-06-30
Just a guess: Make sure that you have the package ubuntu-desktop installed.

---

### Post by gfreemankc on 2006-06-30
Thanks for the guess.  I do have ubuntu-desktop (0.80) installed, so it's not because it's not installed...

There also aren't any broken packages according to Synaptic Package Manager.

---

### Post by invalid on 2006-06-30
[QUOTE=gfreemankc]I'm trying to upgrade from Breezy to Dapper using the upgrade GUI.  I start it, and get a message stating:
Some third party entries in your sources.list were disabled.  You can re-enable them after the upgrade...

I'm guessing that's normal and ok.

I close hte dialog and it downloads some packages, then I get another dialog stating:

Could not calculate the upgrade
A unresolvable problem occurred while calculating the upgrade.  Please report this as a bug.

The installation seems to roll back after I press the close button on that dialog...

I'd love to include some more information if I knew where to get it...

Can anyone assist?[/QUOTE]
Open a terminal, and type the following:
```
sudo apt-get dist-upgrade
```
This will tell us what packages are having problems, and where they are originating from.

---

### Post by gfreemankc on 2006-06-30
When I run apt-get dist-upgrade I get the following:
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Also of note, when I first tried the upgrade, it told me there was a new release "Dapper" avaliable.

Now when I run the upgrade tool, it tells me 6.06 LTS is available.

*shrug*

---

### Post by Grog140 on 2006-10-15
Same problems here

---

### Post by tommcd on 2006-10-16
You could try editing your /etc/apt/sources.list and change every entry of 'breezy' to 'dapper'.
[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)
It's a little way down the page. Also,

[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)
Hope this helps.

---

