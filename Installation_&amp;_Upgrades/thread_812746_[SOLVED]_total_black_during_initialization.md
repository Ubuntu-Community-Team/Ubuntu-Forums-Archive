---
title: "[SOLVED] total black during initialization"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by arturieto on 2008-05-30
I have partitioned my hardisk for windows xp and kubuntu.  my kubuntu was upgraded recently.  Today I received my shipit cd on ubuntu 8.04.  my idea was to install also ubuntu in my kubuntu desktop.I did so start the process by placing the cd on cdrom and restarted boot of my computer. The grub has initialized and I selected kubuntu.  then it so happened, that the initialization did not materialized. the whole initialization turned into a total black out of the screen.  I waited for minutes but nothing goes further.  So I forcibly turned off the process by cutting off the power supply and started boot again.  The problem repeated.  So I decided not to place the cd and started boot.  Again the problem repeats.  I thought of opening the windows xp.  It opens normally.

to solve the problem I begin to think that I would format the hda1 partition through Norton partition magic.  My idea is to make the partition clean and install ubuntu 8.04 using the cd.  Is it ok.  or what shall I do to install ubuntu again?

please help, I am arturieto from the philippines.

---

### Post by zvacet on 2008-05-30
First of all you can not add any desktop to your existing Ubuntu with live CD.If you want to do it from CD you need alternate CD.Do you still have your Kubuntu working?If not you have two options:

1. Install Kubuntu again and then install Ubuntu desktop with 

```
sudo aptitude install ubuntu-desktop
```

2.Install Ubuntu from live CD and later add Kubuntu desktop if you want 

```
sudo aptitude install kubuntu-desktop
```

---

