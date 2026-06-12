---
title: "Breezy update"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by jonk on 2007-06-08
Today when I logged in to my server I was suprised to see that I couldn't do an apt-get update as usual.. I got a lot of errormessages that upates were not found.

So I browsed to [http://se.archive.ubuntu.com/ubuntu/dists/]("http://se.archive.ubuntu.com/ubuntu/dists/") to see what was going on and I saw that there was NOTHING breezy there at all!! :(

Is it not supported anymore or what? What do I do now?

---

### Post by patelnet on 2007-06-08
Hi,

I have also seen that none of the mirrors or the official server carry anymore Breezy.

The problem is I can't even do a dist-upgrade to my box without doing an apt-get update (according to the official upgrade instructions.)

Since my box is a VPS remotely hosted...I don't have physical access to install via CD etc.


Any help if Ubuntu has moved the breezy packages somewhere else?!?!...

Cheers,

---

### Post by zvacet on 2007-06-09
Breezy is not supported anymore.That is why your apt-get update doesn´t work.Upgrade to Dapper (and after that maybe Edgy and feisty if you want it to ) or if you have separate home partition do the clean install.If you don´t have separate home do it this way 

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by diatribe on 2007-06-09
actually if you edit your /etc/apt/sources.list, and change all of the instances of breezy to dapper and run apt-get update, it should work then and allow you to upgrade

---

### Post by patelnet on 2007-06-09
> **diatribe said:**
> actually if you edit your /etc/apt/sources.list, and change all of the instances of breezy to dapper and run apt-get update, it should work then and allow you to upgrade

Hi,

Ya i was thinking of this as well, just wasn't sure as my hosting provider provided Ubuntu server 5.10 for my dedicated VPS. I would assume the dist-upgrade would still work fine by changing all references of breezy to dapper eh?

Cheers and thanks for the info!

---

### Post by jonk on 2007-06-09
I'm a bit worried though that my system will break if i change the sources.list.. Are you sure it't a safe way to do it? I have a lot of sites, mail and stuff on my server that quite a lot of people are depending on.

---

### Post by diatribe on 2007-06-09
I'm sure this will work you have nothing to worry about, editing the sources.list will not negatively affect your system; just replace any instance of breezy with dapper

---

### Post by jonk on 2007-06-09
I'm not really worried about the editing itself, more the updating..

---

### Post by diatribe on 2007-06-09
I have upgraded since dapper using this method, once you have edited the file just type
 sudo update-manager -c -d
or
sudo apt-get dist-upgrade
breezy is outdated and no longer supported so you really have no options

---

### Post by jonk on 2007-06-09
Ok.. I'll just back up the more important stuff first then... Or leave it as is..

---

### Post by jonk on 2007-06-16
I did the upgrade yesterday and everything seem to be working perfect!

---

