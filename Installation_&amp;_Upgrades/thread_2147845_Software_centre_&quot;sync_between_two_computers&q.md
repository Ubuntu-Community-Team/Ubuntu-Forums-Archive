---
title: "Software centre &quot;sync between two computers&quot; can not see other computer"
date: 2013-05-23
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2013-05-23
I'm trying to sync the packages between two machines using software centre. Both are registered on my ubuntu one account but I can not get software centre to show me both machines to do the syncing.  Any suggestions how to debug the problem?

Thanks a bunch,

J

---

### Post by ibjsb4 on 2013-05-23
> sync the packages

You want both machines to have the same software?

Both machines have the same software, but need to be sync?

Sync is normally done with a package like rsync.  Rsync is a terminal program (already installed by default) that can have a GUI added to it, like grsync or luckybackup.  All are in the software center.

---

### Post by jamaas on 2013-05-23
I want them to have the same packages loaded on them, just got a new notebook and want all the same stuff as on my desktop, without trying to install it all manually.  Ubuntu software centre will not show both computers, even though both are registered with Ubuntu One ... any suggestions?

Thanks

J

---

### Post by ibjsb4 on 2013-05-23
There are several ways to do that.  My way:

Install [synaptic package manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9") and make a [markings list]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager+markings+list&sa=Search&cof=FORID:9").  No need to go through UbuntuOne.  Its a small list and can be transfered via USB (thumb drive).  This will make an exact copy of all packages installed.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get install synaptic
```

---

### Post by jamaas on 2013-05-23
Thanks, I got a makings list but it seems to be empty?

Thanks

J

---

### Post by ibjsb4 on 2013-05-23
File>save markings as

[ATTACH=CONFIG]242937[/ATTACH]

I save to desktop and don't forget to "save full state".  Then transfer marking list to your other computer and install via synaptic using file>read markings.

Please post back if you have more questions :)

---

