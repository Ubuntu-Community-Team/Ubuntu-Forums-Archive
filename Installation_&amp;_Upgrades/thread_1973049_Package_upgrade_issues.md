---
title: "Package upgrade issues"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by DKZeroCool on 2012-05-04
I just installed Ubuntu 12.04 on my desktop machine and encountered a problems. If I run an update after installing from the LiveCD image, the system crashes in many ways. 

I encountered sudo stopped working, pipe warnings and the entire xorg breaks. Without updates the OS runs fine. 

I would create a bug report on launchpad, however in order to do this I need to know which packages to report. 

These are the packages set to be updated.
```
apport
apport-gtk
dmsetup
gdb
iagno
libdevmapper-event1.02.1
libdevmapper1.02.1
liblvm2app2.2
liborbit2
libsmbclient
lightsoff
mahjongg
openssl
python-apport
python-problem-report
quadrapassel
samba-common-bin
software-center
swell-foop
update-manager
update-manager-core
xserver-xorg-core
xserver-xorg-input-synaptics
```

The first error after reboot, is the message "Could not write bytes broken pipes"

Then it tries to start LightDM but this crashes and it ends up back in the shell. Running 'startx' just provides a black screen.

The 'sudo' command also breaks forcing one to boot back to LiveCD in order to mess with things. When using sudo I get the message "sudo: no valid sudoers sources found, quitting". I have tried every work-around I could find, everything is fine but it still does not work. 

I don't think that Ubuntu has pushed multiple broken packages. So I would think that these issues has one package in common. I just need to know which of the above packages that could creates issues for both Xorg and sudo in order to create a bug report on it.

I have tried this with both 32bit and 64bit OS, both provide the same issues.

---

### Post by mips on 2012-05-04
Try installing them one at a time and see which one(s) give you hassles.

---

### Post by DKZeroCool on 2012-05-04
Yeah, only then I will break my PC once more. I have already re-installed ubuntu 4 times on it.

---

### Post by DKZeroCool on 2012-05-05
Have located the problem (Not the package causing it). After update, /etc is changed from 0755 to 0700. After changing the permissions back to 0755 everything works fine again.

---

