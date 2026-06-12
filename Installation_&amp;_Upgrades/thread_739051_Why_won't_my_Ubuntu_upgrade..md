---
title: "Why won't my Ubuntu upgrade."
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by leg on 2008-03-29
I have just logged into Ubuntu and the update icon appears. I click on it and I am told that there are 237 updates waiting for me to apply. I hit install upgrades and nothing happens. I have a sneaky feeling that this may be related to my dns information as I have had problems before. If I want synaptic to work properly I have to go into System > Network and alter the dns ip to be the same as the ip listed on my router. Just about everything else works fine with the localhost ip that is there by default. Anyway even changing this dns server does not seem to allow the upgrades to take place.

Any ideas.

---

### Post by ugm6hr on 2008-03-29
As a temporary solution - if Synaptic works, you can update from there.

Just use the Mark all Upgrades option.

Sorry I don't fully understand the networking issue to help solve the problem properly.

---

### Post by leg on 2008-03-29
Well there must be more wrong here than I think as that doesn't do anything either. Synaptic doesn't seem to be able to get the updates. After clicking Mark All Upgrades there is nothing to apply.

---

### Post by Pumalite on 2008-03-29
There are 2 things to do:
1.-Check you connection and reconfigure is necessary (System>Administration>Network Tools)
2.-Check sources.list. Post the output of:
cat /etc/apt/souces.list

---

### Post by leg on 2008-03-29
There is nothing wrong with my connection and I am currently installing Netbeans through Synaptic after altering the dns address to mirror my router.
My /etc/apt/sources.list file comments removed. ```

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by Pumalite on 2008-03-29
They should remain commented out except for 'deb-src'

---

### Post by lswest on 2008-03-29
what's the output of this command:
```
sudo apt-get update && sudo apt-get upgrade
```?  and i do believe that it doesn't matter if the source options are commented out or not, they're all valid links to places, and who knows? maybe he uses the source repos.

---

### Post by leg on 2008-03-29
> **lswest said:**
> what's the output of this command:
```
sudo apt-get update && sudo apt-get upgrade
```?  and i do believe that it doesn't matter if the source options are commented out or not, they're all valid links to places, and who knows? maybe he uses the source repos.

Thanks it seems to be working now and is currently downloading the upgrades.

---

### Post by lswest on 2008-03-29
hmm, strange, i assumed the command line would give you an error xD  Maybe after the updates are done synaptic will work again?

---

### Post by leg on 2008-03-29
and synaptic works with the exception of the upgrades anyway. It is odd!

---

### Post by lswest on 2008-03-29
yup, definately...and, just a bit of vanity :P, but if you found my first post useful, you could always thank me using the gold medal there ;) xD

and i'll continue thinking about why it won't upgrade from the GUI

---

### Post by JafaarNhh on 2008-03-29
You have to be connected to the net for updating application at add\remove:)

---

### Post by lswest on 2008-03-29
Um, he is, he said the command line worked for him.  And at the OP, can you mark this thread as solved?  That way people know we have a solution here

---

