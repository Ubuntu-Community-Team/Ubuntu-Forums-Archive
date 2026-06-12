---
title: "Upgrade to 8.04 failed!"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by linzhp on 2008-04-25
There is an Ubuntu 7.10 on my Dell D630, which was upgrade from 7.04 when 7.10 was out. Today I upgraded to 8.04 using GUI "update manager". It took for about 8 hours, but most of the time was spent on searching obsolete packages to clean up. Then it prompted me whether to remove a list of package, and I chose yes. To my surprise, it removed amarok, thunderbird, pidgin, tomboy notes, etc. And it even removed x.org! After it removed all those program I used so frequently, it prompted me to restart. However, there was still no Ubuntu 8.04 entry in the grub. When I entered the default entry of 7.10, I could not start XServer. Then I tried command line upgrade:
sudo do-release-upgrade
It makes no difference. Tried
sudo apt-get install -f
Didn't work.
My graphic card is Intel 965. Anyone know the remedy?

---

### Post by dsiembab on 2008-04-25
did you try  sudo apt-get autoclean and the sudo apt-get reinstall gnome-desktop

---

### Post by Archmage on 2008-04-25
I think it failed to see all packages and therefore remove some of them.

Try:

```

sudo aptitude update ; sudo aptitude safe-update ; sudo aptitude full update ; sudo shutdown -r now ; exit

```

---

### Post by linzhp on 2008-04-26
I did
```
apt-get autoclean
```
It worked fine.
But when I tried to do ```
aptitude update
```, it said that "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem". So I did ```
dpkg --configure -a
```, it threw out a lot of errors. I don't know how to save those errors; ```
dpkg --configure -a > dpkg.log 
``` didn't work. So I took a picture of the error screen, attached with this post. Could anyone take a look at it and give some suggestion?

---

### Post by Pumalite on 2008-04-26
dpkg is saying there are too many packages missing (not configured) and that it cannot continue.
Boot a Knoppix Live CD and take a look. You might have to do a clean install.
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

---

### Post by linzhp on 2008-04-26
> **Pumalite said:**
> dpkg is saying there are too many packages missing (not configured) and that it cannot continue.
Boot a Knoppix Live CD and take a look. You might have to do a clean install.
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Could you give more details of how can Knoppix Live CD help me?

---

### Post by Pumalite on 2008-04-26
It mounts all drives/partitions automatically at boot. You might be able to check key files. And you can use it to save data and /home before a clean install.

---

### Post by linzhp on 2008-04-26
> **Pumalite said:**
> It mounts all drives/partitions automatically at boot. You might be able to check key files. And you can use it to save data and /home before a clean install.
OK. :( That means a clean reinstallation is inevitable

---

### Post by dsiembab on 2008-04-26
did you try sudo apt-get update && sudo apt-get upgrade? When you boot did you hit the esc key to see if packages where failing? sudo apt-get check, sudo apt-get -f install. The way I upgraded my computer was from 6.10 to 7.04 to 7.10. I would try all the options first before doing a clean re-install. if you type in apt-get --help it will show you all the options in terminal for apt-get.

---

### Post by linzhp on 2008-04-27
> **dsiembab said:**
> did you try sudo apt-get update && sudo apt-get upgrade? When you boot did you hit the esc key to see if packages where failing? sudo apt-get check, sudo apt-get -f install. The way I upgraded my computer was from 6.10 to 7.04 to 7.10. I would try all the options first before doing a clean re-install. if you type in apt-get --help it will show you all the options in terminal for apt-get.
The thing is, any apt-get command will result in "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem" (I've just tried). And that dpkg command results in the screen I posted previous in post #4. :(

---

### Post by arm-c on 2008-04-27
Frustrated, I am sure you are.  I have had my woes today also.

You probably did it, but just to make sure, you rand dpgk as sudo (root)?  If not, try that.

I also failed to see if you had a CD created before you tried the web update.  I used the "alternate install" cd to upgrade and I know that disk has a tool on it to do an upgrade.  Google upgrade from CD and it should pull up instructions.  For most people, it will run automatically once you insert it in the computer.  Try that.

I am a firly noob, but certainly not Brand-Noob.  Hope that works. 

ALL:  If I made any mistakes here, please provide an assist.

---

### Post by dsiembab on 2008-04-27
did you try switching your mirror?

---

### Post by linzhp on 2008-04-27
> **arm-c said:**
> Frustrated, I am sure you are.  I have had my woes today also.

You probably did it, but just to make sure, you rand dpgk as sudo (root)?  If not, try that.

I also failed to see if you had a CD created before you tried the web update.  I used the "alternate install" cd to upgrade and I know that disk has a tool on it to do an upgrade.  Google upgrade from CD and it should pull up instructions.  For most people, it will run automatically once you insert it in the computer.  Try that.

I am a firly noob, but certainly not Brand-Noob.  Hope that works. 

ALL:  If I made any mistakes here, please provide an assist.
Now I can only enter in recovery mode, and I ran all commands as root.
Having a CD b4 upgrade seems to be a good idea to me now: first, it would be faster than upgrading from the Web; and second, which seems quite wise: when the CD I order finally comes, it would be more than 1 month after the publishment. I believe there are a lot of people use Dell D630, then there would be a lot information about success and failure I can get from the web.
But for now, is the only remedy a "clean install"?

---

### Post by linzhp on 2008-04-27
> **dsiembab said:**
> did you try switching your mirror?
No, but even when I run "apt-get check", which I am sure it runs locally, won't work. Could swiching the mirror help?

---

