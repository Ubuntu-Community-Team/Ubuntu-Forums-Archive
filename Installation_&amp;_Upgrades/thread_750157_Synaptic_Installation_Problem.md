---
title: "Synaptic Installation Problem"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by PRAEst76 on 2008-04-09
Been trying to install updates on my girlfriend's Acer Aspite laptop and Synaptic won't finish the installation. It seems to download the files from the repository ok, but then just sits on the apparent installation. It's been a while since I used Ubuntu myself so I'm still trying to find my feet, but syslog shows nothing pertaining to synaptic. The synaptic log in /root/.synatpic/log/ doesn't appear to exist for these installs.

When I switch on the terminal output in Synaptic I get: 

```
Unknown install result.
```

Repeated over and over until I kill synaptic.

Any ideas/pointers? This might be related to how Synaptic is interacting with apt on this system, but I can't figure out how. Aptitude and apt-get seem to work fine.

---

### Post by Rocket2DMn on 2008-04-09
Why don't you try from the terminal so we can see more output.  First, let's configure with dpkg since this fixes a lot of package manager problems
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```
Post all the output here and we'll see what's up.

---

### Post by PRAEst76 on 2008-04-10
> **Rocket2DMn said:**
> Why don't you try from the terminal so we can see more output.  First, let's configure with dpkg since this fixes a lot of package manager problems
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```
Post all the output here and we'll see what's up.
Sadly we've used up our meagre bandwidth quota for the month (we currently live in a emote area and have to rely on a GPRS connection most of the time) and can't afford to do a full upgrade. This will have to wait a few weeks.

However I'm fairly certain there will be no problems. Using apt-get from the terminal is fine. It's just Synaptic that seems to be having issues and I'm not sure how to get any relevant feedback from that.

Me, I'm happy using apt to install packages, but this is my girlfriends computer and it's been hard enough getting her to use Linux without having to teach her the command line as well.

---

### Post by Rocket2DMn on 2008-04-10
Well, that is rather strange, you could try reinstalling synaptic using apt-get i suppose (when you get the bandwidth).
```
sudo apt-get install --reinstall synaptic
```
Otherwise we need more details, maybe viewing the details of the installation and giving a screenshot would help.

---

