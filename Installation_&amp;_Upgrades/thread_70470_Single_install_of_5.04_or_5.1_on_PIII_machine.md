---
title: "Single install of 5.04 or 5.1 on PIII machine"
date: 2005-09-30
forum: Installation &amp; Upgrades
---

### Post by Adam Boettiger on 2005-09-30
I have a Sony PCG z505JS PC laptop that is old and I want to use as a pure linux machine. Right now it has Win 98 on it. My first challenge was getting broadband access on it, which I have done.

What I would ultimately like to do is to do a net install of 5.1 Ubuntu using DOS to boot 5.1 in a graphical interface that will partition the drive. Problem is, I have no CD Rom player to boot from. I've only got a networking port with broadband access and a USB drive for floppy.

I can download the .iso files package to the laptop, but have no idea how to partition the drive and initiate an install using DOS commands. I want to totally wipe Win 98 from the machine and use the entire drive for 5.1 and a swap drive.

Is there a net install that will partition and overwrite Win 98 as it installs ubuntu? If so, what is the command to do this from DOS?

Thanks

---

### Post by Leif on 2005-09-30
I would recommend that you keep your windows partition for the moment, just in case things don't go just perfect. See if you can get your hands on something like partitionmagic, and resize your drive from windows, creating space for ubuntu.

there are several methods for installation detailed here :

[https://wiki.ubuntu.com/Installation](https://wiki.ubuntu.com/Installation)

for you particularly, see these :

[https://wiki.ubuntu.com/Installation/Netboot](https://wiki.ubuntu.com/Installation/Netboot)
[https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)

and while ubuntu 5.10 is going to come out soon, if you're going to install ubuntu before it comes out, please install 5.04. you can upgrade it to 5.10 afterwards very easily.

---

