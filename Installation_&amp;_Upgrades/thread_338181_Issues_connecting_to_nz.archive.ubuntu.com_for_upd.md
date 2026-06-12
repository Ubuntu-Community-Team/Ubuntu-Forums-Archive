---
title: "Issues connecting to nz.archive.ubuntu.com for update/upgrade"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by Maelgwyn on 2007-01-14
Hey guys

I'm trying to run apt-get update but seem to hit a wall when it tries to connect to:

```
nz.archive.ubuntu.com (202.7.6.10)
```

Is anyone else having problems with this server? :(

---

### Post by bapoumba on 2007-01-14
Hello,
I'm not using that repo. Have you tried removing the nz. from all your repo list (/etc/apt/sources.list) so that you'll know if this repo is actually down or if the probem is on your end ?

---

### Post by Maelgwyn on 2007-01-15
I've changed to the 'standard' ubuntu repo's, and it all works fine... So I'm guessing the nz. mirror is down :(

---

### Post by jpfreely on 2007-01-15
I'm having connection issues too. I don't think it's down but the redirection from nz.archive.ubuntu.com seems to be stuffed. As far as I know this actually links to Citylink's ftp.citylink.co.nz server so changing it to that might work. Haven't tried myself yet but I might because I get way faster speeds on national traffic.

Edit: Yep, changing my sources to [http://ftp.citylink.co.nz/](http://ftp.citylink.co.nz/) works a breeze. I wonder if there's someway to notify whoever's in charge that the nz.archive.ubuntu.com isn't working?

---

### Post by Maelgwyn on 2007-01-17
Could you please post your sources.list for [http://ftp.citylink.co.nz?](http://ftp.citylink.co.nz?) :) 'cause I'm not too certain how to write it up... :)

---

### Post by jpfreely on 2007-01-17
It's just a matter of find and replace, easy enough to do in gedit.

But I won't bother posting my sources.list though - seems nz.archive.ubuntu.com is back in action!

---

### Post by Maelgwyn on 2007-01-18
heh all good - I figured it out by myself! I think I'll stick with the citylink repo :)

---

### Post by jynyl on 2007-11-30
Seems like the server is down again.
```
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg  
Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)
```

Anyone have any news on this, or alternatives?

TIA

Peter

---

