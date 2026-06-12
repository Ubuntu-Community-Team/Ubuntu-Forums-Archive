---
title: "Duplicate sources.list entry"
date: 2015-07-09
forum: Installation &amp; Upgrades
---

### Post by thunderbirdje on 2015-07-09
Hello all,

I'm trying to install RabbitVCS as per instructions from [http://wiki.rabbitvcs.org/wiki/install/ubuntu]("http://wiki.rabbitvcs.org/wiki/install/ubuntu") as a install from the Ubuntu Software Center and afterwards applying [the "fix" for nautilus 3 ]("http://aruizca.com/how-to-integrate-rabbitvcs-with-nautilus-file-manager-in-ubuntu-14-04-trusty-tahr/") didn't work as in "the RabbitVCS context submenu not showing in Nautilus".

I've noticed this warning after the step "sudo apt-get update" from [the "fix" for nautilus 3]("http://aruizca.com/how-to-integrate-rabbitvcs-with-nautilus-file-manager-in-ubuntu-14-04-trusty-tahr/") but don't know how to solve it.

```
W: Duplicate sources.list entry http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu/ trusty/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_rabbitvcs_ppa_ubuntu_dists_trusty_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu/ trusty/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_rabbitvcs_ppa_ubuntu_dists_trusty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

My distribution is Ubuntu 14.04 Trusty.

Thanks for any suggestion!

---

### Post by Jrmie_bellion- on 2015-07-09
try making a backup of the sources.list file : 
```
 sudo cp /etc/apt/sources.list ~/sources.list.bak
```

and then open it : 
```
sudo gedit /etc/apt/sources.list
```

and try to remove these two lines to see if that solves the problem.

If not and/or if that creates other problems, restore your backup with :
```
sudo cp ~/sources.list.bak /etc/apt/sources.list
```

---

### Post by thunderbirdje on 2015-07-09
> **Jrmie_bellion- said:**
> try making a backup of the sources.list file : 
```
 sudo cp /etc/apt/sources.list ~/sources.list.bak
```

and then open it : 
```
sudo gedit /etc/apt/sources.list
```

and try to remove these two lines to see if that solves the problem.

If not and/or if that creates other problems, restore your backup with :
```
sudo cp ~/sources.list.bak /etc/apt/sources.list
```

The thing is that my sources.list only contains the line:
```
## Rabbit Subversion
deb http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu trusty main
```

---

### Post by Jrmie_bellion- on 2015-07-09
Is there nothing else than this line ?? I'm not an expert, but that doesn't seem normal, mine has more than 50 lines on 15.04.

You can try generating a fresh one using a tool like this one : [http://repogen.simplylinux.ch](http://repogen.simplylinux.ch)

---

### Post by monkeybrain20122 on 2015-07-09
Open the dash, look for Software&Updates. Go to the tab "other software",  find he duplicate entry, right click and remove it. That's  it. 

Alternatively, open terminal 
```
cd  /etc/apt/sources.list.d
ls

```

Find the repeated one and delete it. say foo appears twice

```
sudo rm foo
```

Third party ppas now live as separate files in the directory  /etc/apt/sources.list.d rather than as entries in the single file /etc/apt/sources.list

---

### Post by thunderbirdje on 2015-07-09
> **Jrmie_bellion- said:**
> Is there nothing else than this line ?? 

This is the only line referring to rabbitvcs. FYI my sources.list attached [ATTACH]263098[/ATTACH]. Note that I add the extension .txt to be able to upload it.

---

### Post by Jrmie_bellion- on 2015-07-09
Ok that looks better ;)

You can try removing this line, or try thunderbirdje's solution.

---

### Post by thunderbirdje on 2015-07-09
That did it monkeybrain2012.

Thanks a lot! Thank you too Jrmie_bellion-.

---

### Post by howefield on 2015-07-09
Remove this entry 

```
/etc/apt/sources.list.d/rabbitvcs-ubuntu-ppa-trusty.list
```

Remove it.

Edit : too late :)

---

