---
title: "Latest software update broke my Kubuntu 17.04"
date: 2017-08-01
forum: Installation &amp; Upgrades
---

### Post by marer13 on 2017-08-01
Hi,

I recently installed updates on my Kubuntu 17.04 as I always do, they download and install....

And when I opened my computer the other day, after loggin in I saw a black screen.... with no taskbar, nothing....

So my Kubuntu became unusable...

Any suggestions how to fix it?

---

### Post by Bashing-om on 2017-08-01
marer13; Hello;

> **marer13 said:**
> Hi,

I recently installed updates on my Kubuntu 17.04 as I always do, they download and install....

And when I opened my computer the other day, after loggin in I saw a black screen.... with no taskbar, nothing....

So my Kubuntu became unusable...

Any suggestions how to fix it?

Graphic's driver broke in the update process ?

At the login screen what results with key combo ctl+alt+F1 ?
Can you log into the system here with user name and password ?

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by marer13 on 2017-08-05
It seems like a broken driver but how do I fix it?

On login screen pressing Ctrl+Alt+F1 open black screen with that looks like console.

---

### Post by BenginM on 2017-08-05
Yes, that a VT "Virtual Console" . are you able to login with your user name and passwd!

---

### Post by marer13 on 2017-08-05
Yes. What do I do next? I don't know much about "coding" in console.

---

### Post by BenginM on 2017-08-05
well, ones you logged in , the first thing you need to check is the HD/SSD space ratio left on the partition , so run $ df -h , do you see a partition as % full! this maybe one reason to be locked/blocked out, the second reason might be an issue with the Graphic driver .. if you go back to the X desktop with Ctrl+Alt+F7 what do you get ..! another reason might be that the upgrade somehow interrupted upgrading Xorg-server stacks , like *xserver*-xorg-video-nouveau , or the Intel, Amd ones.. so you might want to reinstall that to make sure it's up and running .. or the kubuntu-dekstop package missed-up / mis-configured , so you might as well make sure that installed ..

which GPU is used on this machine , Intel , Nvidia , AMD ! dual graphics ..!

---

### Post by Bashing-om on 2017-08-05
marer13; Hey;
@ BenginM; Pleased to have you on the thread .

Keeping this as the most likely cause - graphic's driver .
At that VT enter terminal command:
```

sudo lshw -C display

```
compare your result to mine:
> 
sysop@x1604:~$ sudo lshw -C display
[sudo] password for sysop: 
  *-display               
       description: VGA compatible controller
       product: GK208 [GeForce GT 710B]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:29 memory:fb000000-fbffffff memory:d8000000-dfffffff memory:e6000000-e7ffffff ioport:4c00(size=128) memory:fc000000-fc07ffff
sysop@x1604:~$

Of interest here is if the card is identified (  product: GK208 [GeForce GT 710B] ) and if/what driver is loaded for the graphic's card (  configuration: driver=nvidia latency=0 ) .

[INDENT][INDENT]the hardware has got to talk to the software
the driver is that interface
[/INDENT][/INDENT]

---

### Post by marer13 on 2017-08-06
Thanks for help so far.

When I run sudo lshw -C display

I get: 

HD Graphics 5500
Intel Corp
physical id: 2
bus info: pci@0000:00:02.0
version: 09
width: 64 bits
clock: 33MHz
capabilities: msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:50 memory:a8000000-a8ffffff memory:b0000000-bfffffff ioport:5000(size=64) memory:c0000-dffff

---

### Post by Bashing-om on 2017-08-06
marer13; Well, surprise, surprise .

The hardware is Intel, and the correct driver is loaded . A driver is not at fault !

So we look at this now as a config issue in your user account.

At the login screen what results when you boot with the guest account ? 

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by BenginM on 2017-08-06
Hiya Bashing-om , so you're thinkin' it could be a user permissions issue..!

---

### Post by Bashing-om on 2017-08-06
BenginM; Hey hey;

> **BenginM said:**
> Hiya Bashing-om , so you're thinkin' it could be a user permissions issue..!


Well, no, not permissions per se - as then I would expect a login loop to happen .
Here I look for broken configs for the DE . But with KDE I will really be struggling as I have not seen KDE in years .

[INDENT][INDENT]A know it all
[INDENT][INDENT]I am not
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by BenginM on 2017-08-07
Good answer :) , Yes , and am not familiar with KDE either ..

---

### Post by user_of_gnomes on 2017-08-07
I find that when there are graphical problems in Ubuntu or Lubuntu, bootinmgt into 'recovery mode' by holding down the left shift button and then choosing the recovery mode often allows me to get back into Ubuntu with minimal graphics so that I don't have to fix things solely through the terminal.

Of course, this is Kubuntu and I've never seen that before but I am assuming it works the same way.

---

### Post by BenginM on 2017-08-07
user_of_gnomes , true ..
 merar13 , you could try fixing packages with dpkg like this [http://imgur.com/a/jwHrB](http://imgur.com/a/jwHrB)

---

### Post by marer13 on 2017-08-08
> **Bashing-om said:**
> marer13; Well, surprise, surprise .

The hardware is Intel, and the correct driver is loaded . A driver is not at fault !

So we look at this now as a config issue in your user account.

At the login screen what results when you boot with the guest account ? 
[INDENT][INDENT]sometimes I do wonder
[/INDENT]
[/INDENT]


I tried loging in with my account and second account on this machine and what's happening is that now I can see the desktop but nothing works, there's no taskbar and can't click on anything...  :-(

---

### Post by marer13 on 2017-08-08
> **user_of_gnomes said:**
> I find that when there are graphical problems in Ubuntu or Lubuntu, bootinmgt into 'recovery mode' by holding down the left shift button and then choosing the recovery mode often allows me to get back into Ubuntu with minimal graphics so that I don't have to fix things solely through the terminal.

Of course, this is Kubuntu and I've never seen that before but I am assuming it works the same way.

I tried booting into Recovery Mode (there's an option for that in Grub, but it's the same situation...  :-(

---

### Post by marer13 on 2017-08-08
> **BenginM said:**
> user_of_gnomes , true ..
 merar13 , you could try fixing packages with dpkg like this [http://imgur.com/a/jwHrB](http://imgur.com/a/jwHrB)

I've just tried it and it asked me to download a new package, which I did.

And then restarted and...  it's back to black screen...  :-(

---

### Post by BenginM on 2017-08-08
> **marer13 said:**
> I tried loging in with my account and second  account on this machine and what's happening is that now I can see the  desktop but nothing works, there's no taskbar and can't click on  anything...  :sad:

....

> **marer13 said:**
> I've just tried it and it asked me to download a new package, which I did.

And then restarted and...  it's back to black screen...  :-(

This tells me , the Desktop entertainment is BROKEN , or missing some packages .. am on my phone atm , and am not sure which KDE packages we ned to assure  are installed for KDE desktop  .. could you please /join [#kubuntu]("irc://irc.freenode.net/kubuntu") & #ubuntu on freenode IRC network , usin freenode web-interface , [https://webchat.freenode.net/](https://webchat.freenode.net/) and ask someone whois using  KDE .. you may want to point them to this thread so they may have an idea on what's going on and what you've tried so far!

---

### Post by Bashing-om on 2017-08-08
marer13; Well ;

Continuing on our merry way .
We now know that the problem is lower than the X layer .
So what does X have to say about the matter ?
Post back:
```

cat /var/log/Xorg.0.log
cat /var/log/gpu-manager.log

```

see what
[INDENT][INDENT]tale gets told
[/INDENT][/INDENT]

---

