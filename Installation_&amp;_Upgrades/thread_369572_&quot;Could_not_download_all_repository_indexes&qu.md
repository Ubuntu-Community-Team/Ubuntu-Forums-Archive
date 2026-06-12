---
title: "&quot;Could not download all repository indexes&quot;"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by pombe on 2007-02-24
Hi all.  

I'm getting "could not download all repositories" errors in synaptic package manager, which then lists all the repositories in my sources list as being broken.   If I try to update or install through a terminal (ssh) it doesnt work either.   It says that the repositories arent accessible although if I type the IP into firefox I can browse through them just fine.  ("101 network is unreachable")

Backstory :

I managed to break my mythtv install, got tired of trying to figure out what I messed up and decided to nuke the thing

I'm pretty much following this as writ, the only additional step being that i've mounted a second harddrive:

 [https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)

I've reinstalled Edgy fresh, did all the updates to the newest versions, installed openssh, xfs utilites, NPT, and my Nvidia drivers.   

I'm now at the point of installing mythtv-frontend, backend, database and mysql, but now nothing works.   I tried the canadian, us and main repositories, and cant connect to any of them... (yes, its connected to the internet...)

Anyone have any idea what I've buggered up?  This install is like 2 hours old and I've done nothing except whats mentioned above...

Thanks

Corey

---

### Post by taurus on 2007-02-24
Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
```

---

### Post by pombe on 2007-02-24
arg.   I figured it out.   

I thought hard and realized that the only other thing that I did that wasnt listed above was that I assigned a static IP after I installed openSSH.  I changed that back to dynamic and all of a sudden I'm downloading again...  of all the stupid $#%@^#@$:mad:   I didnt even have to restart the computer...

Not a clue why static/dymanic would matter...

---

### Post by Sponge34 on 2007-02-24
>>Not a clue why static/dymanic would matter...

'cos sometimes your router may not talk the same DHCP language as Ubuntu.... I have  a couple of hacks applied to edgy, and dapper, (not sure which one did the trick) cos my router/ubuntu dont play very well together by default.

S.

---

