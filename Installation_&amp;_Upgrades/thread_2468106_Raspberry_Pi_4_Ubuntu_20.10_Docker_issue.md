---
title: "Raspberry Pi 4 Ubuntu 20.10 Docker issue"
date: 2021-10-18
forum: Installation &amp; Upgrades
---

### Post by zorin1 on 2021-10-18
I have just updated my raspberry pi 4 from 21.4 to 21.10 Desktop 64 bit version.  

When I run: docker run hello-world
I get the following error:
docker: Error response from daemon: failed to create endpoint heuristic_keller on network bridge: failed to add the host (veth69f874a) <=> sandbox (vethd6300b1) pair interfaces: operation not supported.
ERRO[0000] error waiting for container: context canceled

Anyone have any idea what is going on?  

thanks

---

### Post by zorin1 on 2021-10-19
I found out that you need the veth kernel module.  You can get this by installing 
sudo apt install linux-modules-extra-rasp[COLOR=#d4d4d4][FONT=Droid Sans Mono][COLOR=#d4d4d4]i[/COLOR]

[/FONT][/COLOR]

---

### Post by MAFoElffen on 2021-10-20
Did you install Docker from the Ubuntu Repo's or from Docker?

Download and run this script: [https://github.com/docker/docker/blob/master/contrib/check-config.sh](https://github.com/docker/docker/blob/master/contrib/check-config.sh)

It will you what is wrong and/or missing from your kernel config in relation to be able to run Docker.

---

### Post by zorin1 on 2021-10-20
> **MAFoElffen said:**
> Did you install Docker from the Ubuntu Repo's or from Docker?

Download and run this script: [https://github.com/docker/docker/blob/master/contrib/check-config.sh](https://github.com/docker/docker/blob/master/contrib/check-config.sh)

It will you what is wrong and/or missing from your kernel config in relation to be able to run Docker.

Docker is not in the Docker Repository for Impish yet, if you follow the install instructions from Docker when you add it to repo it's not found.  From what I have read somewhere not sure if it was in the forums or the bug tracker that they are adding it soon.  

I was able to install from the Docker Repository with the older ubuntu 10.04 Hirsute repository. 

I did a clean install and installed docker.io from the Ubuntu default repository.

I get the same error and it does not matter which repository that I install docker from.

The issue is not with Docker but with the VETH module not being loaded by default when you do the install of the Ubuntu 64 bit Arm version.  At first, I thought there was a problem with the kernel but glad that is not the issue.  It took me 2 days of googling to find out what the real issue was.

---

### Post by MAFoElffen on 2021-10-22
So like this solution?: [https://askubuntu.com/questions/1274221/veth-ko-missing](https://askubuntu.com/questions/1274221/veth-ko-missing)

---

