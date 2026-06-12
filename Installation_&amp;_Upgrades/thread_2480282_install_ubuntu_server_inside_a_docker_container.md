---
title: "install ubuntu server inside a docker container?"
date: 2022-10-24
forum: Installation &amp; Upgrades
---

### Post by silentjay2 on 2022-10-24
hello,

i have a NAS that runs docker and portainer as native apps. id like to install ubuntu server inside a docker container instead of the virtual box they offer. is this possible? also, in my limited experience with docker i know that ports need to be exposed that forward to the container ports, is it possible to just assign a docker container an ip on my lan ie 192.168.1.* to eliminate the port issue? 

tia

jay

---

### Post by TheFu on 2022-10-24
Docker is designed to run 1 program and 1 program only. It is not meant to have a full OS inside the container.
If you intend to have a full OS inside a container, use lxd/lxc instead.

You can connect an LXC to a manually created network bridge, thus allowing it LAN access. I do this for my DNS/Pi-Hole and Wallabag servers. Basically, I treat the LXC like it is a full, normal, OS install.
[https://linuxcontainers.org/lxd/getting-started-cli/](https://linuxcontainers.org/lxd/getting-started-cli/)

Use docker where it makes sense.  Don't use it for this.

I don't know what the limitation of your NAS might be.  I use a home-built NAS that isn't limited.   For NAS specific question, you need to ask on the NAS support forums.

---

### Post by silentjay2 on 2022-10-24
thank your for the input. im very new to docker and wasn't sure if this was feasible. i did notice ubuntu in the docker repository so I thought it was an option.

---

### Post by TheFu on 2022-10-24
> **silentjay2 said:**
> thank your for the input. im very new to docker and wasn't sure if this was feasible. i did notice ubuntu in the docker repository so I thought it was an option.

Feasible?  I don't know.
Good idea?  Definitely not.

---

