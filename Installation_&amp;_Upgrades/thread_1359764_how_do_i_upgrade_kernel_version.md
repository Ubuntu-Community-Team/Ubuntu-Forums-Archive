---
title: "how do i upgrade kernel version ?"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by remush on 2009-12-20
HI all,

I'm having trouble getting a huawei E169 usb modem to work under unbuntu 9.10 

I would like to try upgrading my kernel to a newer version but am not sure how to do it. my current version is 2.6.31-14

Any suggestions appreciated.

---

### Post by dino99 on 2009-12-20
go to synaptic

search linux-image

install the latest header & image

---

### Post by slakkie on 2009-12-20
You don't. When Ubuntu applies all kinds of updates for software in the repo's you'll upgrade your kernel as well. Provided that you have the correct meta-packages installed.

If you have the following packages installed you'll upgrade automagicly:

linux-image-generic
linux-headers-generic

If you use a different kernel then generic, pick that one, eg
linux-image-generic-pea, linux-image-ec2, linux-image-server, etc etc.

---

### Post by snowpine on 2009-12-20
2.6.31.16 is the latest kernel for Karmic, I believe.

Try:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

No idea if it will solve your modem problem though... I am guessing it won't.  Good luck!

---

### Post by jimpr13 on 2009-12-20
Why did you write the sudo apt command?I think it uses another function

---

### Post by slakkie on 2009-12-20
The apt command given is correct, yet too agressive IMO. Using upgrade instead dist-upgrade would have been better.

---

### Post by snowpine on 2009-12-20
> **slakkie said:**
> The apt command given is correct, yet too agressive IMO. Using upgrade instead dist-upgrade would have been better.

'sudo apt-get update' will not upgrade the kernel.
I never use it personally; always 'dist-upgrade' for me... why not? :)

---

### Post by snowpine on 2009-12-20
> **jimpr13 said:**
> Why did you write the sudo apt command?I think it uses another function

You *think*; I *know*. ;)

---

### Post by Gtklocker on 2009-12-20
Get the latest from kernel-ppa repos.

---

### Post by slakkie on 2009-12-20
> **snowpine said:**
> 'sudo apt-get update' will not upgrade the kernel.
I never use it personally; always 'dist-upgrade' for me... why not? :)


AFAIK it will (at least aptitude upgrades the kernel just fine with a simple safe-upgrade, I assume apt-get upgrade will do the same). Most of the time updating a kernel does not involve package removal. If it does, in those exceptional cases you would need dist-upgrade.

Running just dist-upgrade creates chaos in my head. Before I run dist-upgrade I perform a normal one. Create order in chaos. I have less packages to worry about so I can decide quicker what is done/needs to be done.

---

### Post by snowpine on 2009-12-20
Aptitude and apt-get are quite different in this regard.

```
man apt-get
```

I got this drilled into my head back in my Sidux days... try asking about 'aptitude safe-upgrade' over on the Sidux forums. ;)

---

### Post by slakkie on 2009-12-20
> **snowpine said:**
> Aptitude and apt-get are quite different in this regard.

```
man apt-get
```

I got this drilled into my head back in my Sidux days... try asking about 'aptitude safe-upgrade' over on the Sidux forums. ;)

I know they are different (in some specific details), but these upgrade commands for me are more or less the same. Still, I would still use apt-get upgrade && apt-get dist-upgrade and not just an dist-upgrade. That's how I roll ;)

---

### Post by Bachstelze on 2009-12-20
> **slakkie said:**
> AFAIK it will (at least aptitude upgrades the kernel just fine with a simple safe-upgrade, I assume apt-get upgrade will do the same).

Well, you're wrong. It doesn't.

> **slakkie said:**
> Most of the time updating a kernel does not involve package removal. If it does, in those exceptional cases you would need dist-upgrade.

No, but when upgrading to a newer major revision (like 2.6.32-8 to 2.6.32-9), it involves installing additional packages, which [font=monospace]apt-get upgrade[/font] won't do either.

> **slakkie said:**
> Running just dist-upgrade creates chaos in my head. Before I run dist-upgrade I perform a normal one. Create order in chaos. I have less packages to worry about so I can decide quicker what is done/needs to be done.

+1 to this. That's what I do too.

---

### Post by snowpine on 2009-12-20
> **slakkie said:**
> I know they are different (in some specific details), but these upgrade commands for me are more or less the same. Still, I would still use apt-get upgrade && apt-get dist-upgrade and not just an dist-upgrade. That's how I roll ;)

'pacman -Syu' is how I "roll"! ;)

---

### Post by slakkie on 2009-12-20
> **Bachstelze said:**
> Well, you're wrong. It doesn't.

No, but when upgrading to a newer major revision (like 2.6.32-8 to 2.6.32-9), it involves installing additional packages, which [font=monospace]apt-get upgrade[/font] won't do either.


Ok, then use aptitude, makes life sooo much simpler guys! :)

---

### Post by Bachstelze on 2009-12-20
> **slakkie said:**
> Ok, then use aptitude, makes life sooo much simpler guys! :)

Nothx, I'm fine with apt-get. ;)

---

### Post by bapoumba on 2009-12-20
> **remush said:**
> HI all,

I'm having trouble getting a huawei E169 usb modem to work under unbuntu 9.10 

I would like to try upgrading my kernel to a newer version but am not sure how to do it. my current version is 2.6.31-14

Any suggestions appreciated.
Have you seen this ?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

---

