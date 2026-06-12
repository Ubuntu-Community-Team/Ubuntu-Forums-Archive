---
title: "edgy -&gt; feisty : no upgrade offered"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by flostre on 2007-07-20
Hello.

I am running Edgy and I would like to upgrade to Feisty. However, there is no "Upgrade"-button in upgrade-manager. So I tried starting the upgrade-manager from the command line with the -c and -d option. Neither made the upgrade-button appear. Both produced (aside from starting the actual program) the message:

warning: could not initiate dbus

Then I executed

upgrade-manager --dist-upgrade

That *seemed* to work: the update message window appeared. Only that it installed mere 19 packages and didn't require a reboot. So I'm still in Edgy.

Of course I could try to force an update with apt-get or so, but to me it looks like there is something wrong. Could you help me find out what?

Thanks,

flostre

---

### Post by Seisen on 2007-07-20
You can go through your source list and change everything from edgy to feisty then

```
sudo apt-get update
sudo apt-get distupgrade
```

---

### Post by flostre on 2007-07-21
> **Seisen said:**
> You can go through your source list and change everything from edgy to feisty then

How do you do that?


> 
```
sudo apt-get update
sudo apt-get distupgrade
```

Without the change mentioned above, both commands have no effect. My screen messages are German, so I hesitate to post them here, but in English they must be something like:
[5x (doing X...done)]
0 updated, 0 newly installed, 0 to be removed, 0 not updated

---

### Post by flostre on 2007-07-26
Doesn't somebody know how to help here?

Thanks, flostre

---

### Post by Seisen on 2007-07-26
> **flostre said:**
> How do you do that?



Without the change mentioned above, both commands have no effect. My screen messages are German, so I hesitate to post them here, but in English they must be something like:
[5x (doing X...done)]
0 updated, 0 newly installed, 0 to be removed, 0 not updated

You can open up your source list by putting this in the terminal.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by mikesmind on 2007-07-28
When you bring up the Software Updates utility, click on the Check button.  It will then check for updates and the Upgrade button will show up.

---

