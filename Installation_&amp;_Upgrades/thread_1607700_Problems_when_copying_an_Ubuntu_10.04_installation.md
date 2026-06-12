---
title: "Problems when copying an Ubuntu 10.04 installation to another PC"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by SchenkeM on 2010-10-28
Dear all,

first of all 'Hello' to everyone in this forum. I'm recently facing some problems when copying an Ubuntu installation to a different machine.
At our institute we want to have the same installation on every machine in the network, so we do one installation and simply copying the installation to different machines.

For the sake of clarity and I think this might also be useful for other users to know, here is our procedure to copy an installation to a different machine:

1) run a live CD/Ubuntu installation disc on the target and source system
2) mount root-file-system on both systems
3) goto target system and copy the root-installation from the source by:
    'cd /mnt/<root-installation-target>'
    'ssh root@<source> "cd /mnt/<root-installation-source>; tar cvfpsl - ." | tar xvfpsl - .
4) adapt network settings and UUIDs in fstab to fit the target machine
5) adjust grub2

done!

This procedure used to work for Ubuntu 8.04 LTS, although our machines do not have the same Hardware. But with the Ubuntu 10.04 LTS release, this procedure doesn't work anymore. We are facing some troubles on the target machine with audio output (doesn't work), graphic issues (slow downs) and in the worst case it didn't boot anymore. If we run an installation from an Ubuntu installation disc everything works fine. 

I was comparing a list of installed packages -> are the same
I was comparing the "/etc"-directory with meld -> no significant changes

So I have no idea which settings do not fit the target machine.
Does anyone know if there is a way to somehow reconfigure the installation according the hardware?
Hopefully anyone in this forum has an idea.

Best regards, Maik

---

