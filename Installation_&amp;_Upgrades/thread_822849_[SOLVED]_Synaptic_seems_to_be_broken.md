---
title: "[SOLVED] Synaptic seems to be broken"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by MunkyJunky on 2008-06-08
This has been going on a few days, and I have no idea how to fix it. 

Every time I log in, I get Package manager telling me I have 64 available updates, but when I click 'install updates' a box appears on my task bar saying 'Starting Administra...'-something. Presumably administrative tasks, or something to that effect. Then Package manager seems to hang. The task bar box disappears, and package manager does nothing, all boxes grayed out & unclickable. I cant close it either, and am forced to shift it to another desktop so I dont have to look at it, or restart the machine. 

Likewise when I  tried to install some codecs for Movie Players (specifically ones for mp4 playback) exactly the same thing happens with the codec installation window. 

Does anyone have any ideas on how to fix this? Its driving me crazy! I run Ubuntu 8.04, Gnome.

---

### Post by Sef on 2008-06-08
Try installing them from the Terminal:

Applications > Accessories > Terminal

then type or paste in this code:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Please post any success or failure here.

---

### Post by kjetilbmoe on 2008-06-08
I just installed a bunch of updates to my newly acquired ubuntu 8 installation (hardy), and now, none of my "administrative" application will launch, as with the topic app "synaptics". 

I originally discovered this problem running the "root console" - trying  to sort out why I cannot change the listening port to the openssh config file, which I am unable to save, though being the admin user.

Explanations to both cases would be appreciated :)

---

### Post by MunkyJunky on 2008-06-08
My problem is essentially the same - no admin apps want to work. I tried the aforementioned terminal commands, so far so good - everything seems to be installing. I'll post again when its finished with the final outcome.

**EDIT: Everything installed fine, but I still can't install plug-ins to Movie Player. I think, although I've now got my system updates, the problem is no closer to being fixed.**

---

### Post by Partyboi2 on 2008-06-08
Can you post the output to these commands
```
hostname
``````
cat /etc/hosts
```

---

### Post by MunkyJunky on 2008-06-08
Hostname outputs 'Odin' (the name of my computer).

cat /etc/hosts outputs the following: 

```

127.0.0.1 localhost
127.0.1.1 Odin.Aesir

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

However when I use terminal (e.g. I just tried 'Sudo apt-get update' to demonstrate this point) terminal outputs **sudo: unable to resolve host Odin**, then asks me for my root password. 

I don't know if that makes any difference, but I thought it may be worth a mention.

---

### Post by Partyboi2 on 2008-06-09
boot into recovery mode and then open up your hosts file
```
nano /etc/hosts
```
then change this line
> 127.0.1.1 Odin.Aesir
to what your hostname is, in your case Odin
```
127.0.1.1 Odin
``` then save and exit (Ctrl+o, enter, Ctrl+x)
reboot

---

### Post by MunkyJunky on 2008-06-09
That seems to have fixed it. Just for reference, my new **cat /etc/hosts** reads: 

```

127.0.0.1 localhost
127.0.1.1 Odin

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Movie Player finally let me install those codecs, and a 'sudo apt-get update' no longer pops up an error. 

Thanks for all your help! If it stops working again, I'll see if the same thing happened again, otherwise I'll post back here.

---

### Post by othcsr on 2008-06-09
Thank you, this fixed the administrative problems i was having after upgrade to 8.o4
othcsr

---

### Post by CaminoSS on 2008-06-15
I had the same problem and added the line 127.0.1.1 host-name to the System/Administration/Network Network Settings Hosts tab. This solved the problem also.

Cheers

---

### Post by Bob Unitt on 2008-06-15
This fix worked for me as well - thanks Partyboi2.

Is removing the workgroup name from the /etc/hosts file likely to have any adverse effects elsewhere in the system ?

---

### Post by Partyboi2 on 2008-06-16
> **Bob Unitt said:**
> This fix worked for me as well - thanks Partyboi2.

Is removing the workgroup name from the /etc/hosts file likely to have any adverse effects elsewhere in the system ?
correcting the hostname in the hosts file should not have any adverse effects

---

### Post by VMC on 2008-06-16
> **Partyboi2 said:**
> boot into recovery mode and then open up your hosts file
```
nano /etc/hosts
```
then change this line

to what your hostname is, in your case Odin
```
127.0.1.1 Odin
``` then save and exit (Ctrl+o, enter, Ctrl+x)
reboot

My hostname & the line contaning 127.0.1.1 are the same. But, how did other people find it changed in the first place? 

I wouldn't have even thought of looking there. Thanks!

---

### Post by Avaris on 2008-06-22
Have been looking for a fix at several websites but only this one worked

Thanks a bunch, now my install of ubuntu 8.04 is working like a penguin swimming through water :)

---

