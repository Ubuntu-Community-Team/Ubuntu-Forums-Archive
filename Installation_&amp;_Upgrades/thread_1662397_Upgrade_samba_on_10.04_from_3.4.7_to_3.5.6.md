---
title: "Upgrade samba on 10.04 from 3.4.7 to 3.5.6"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by rubicks on 2011-01-08
I'm pretty much new to linux, so i don't know my way around too much.  My friend setup a 10.04 server for me, and it works great for the most part.

i've been having issues with samba, which i talked about here with no responses:
[http://ubuntuforums.org/showthread.php?t=1661724](http://ubuntuforums.org/showthread.php?t=1661724)

Since I only have a partial backup I don't want to mess with updating to 10.10 because i'm worried my data would get erased and/or the software raid 0 would get messed up. And since he had trouble setting it up, i don't want to mess with it.

I want to upgrade to 3.5.6 samba and i was wondering if you guys could help me out or point me to a good guide.  i haven't found any that i'm comfortable following. sudo apt-get update and upgrade aren't grabbing the latest version.

---

### Post by davidmohammed on 2011-01-08
there is a 64bit version of 3.5.6 samba - I dont know about the quality or authenticity of this ppa though.

Add the PPA with: 
sudo add-apt-repository ppa:polslinux/ppa
sudo apt-get update && sudo apt-get install samba

---

### Post by rubicks on 2011-01-08
> **davidmohammed said:**
> there is a 64bit version of 3.5.6 samba - I dont know about the quality or authenticity of this ppa though.

Add the PPA with: 
sudo add-apt-repository ppa:polslinux/ppa
sudo apt-get update && sudo apt-get install samba

sudo add-apt-repository ppa:polslinux was what ended up working, but other than that it worked great.

can i leave this repository or should i remove it?

thanks for the help!

unfortunately, it didn't help my speed issues. :(

---

### Post by CharlesA on 2011-01-08
You can leave it.

---

