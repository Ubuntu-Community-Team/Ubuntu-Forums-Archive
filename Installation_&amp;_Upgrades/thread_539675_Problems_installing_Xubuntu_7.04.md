---
title: "Problems installing Xubuntu 7.04"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by nxmedia on 2007-08-31
I installed Ubuntu Server on a new computer, but then I realised what I needed was Xubuntu. So, I'm trying to install that now.

Everything seems to work fine with the live CD thing, and I can click install, and get so far. It gets to the final loading bar, reaches 15%, and then says:

**Failed to create file system**
The ext3 file system creation in partition 1 of IDE slave (hdb) failed.

I have tried deleting all the partitions and trying again, it still gets the same error message whatever I do. Anyone have any thoughts?





Edit:

The hard drive is the only hard drive and is 160 GB.
There are no other operating systems installed (other than Ubuntu, but I think that's gone now I've deleted the partitions (right?)).

---

### Post by Pumalite on 2007-08-31
Try Xubuntu Alternate cd: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by nxmedia on 2007-08-31
Hmm, I'll try that.

I'm running out of blank CD's... I've burned Xubuntu onto them so many times today only to find I've done it wrong.

---

### Post by merlinus on 2007-08-31
You can easily add xubuntu to server without any cd installation.

```

sudo aptitude update && sudo aptitude install xubuntu-desktop

```

-merlin

---

### Post by Pumalite on 2007-08-31
I learn something new everyday.

---

### Post by ryangoff on 2007-09-11
I was getting somewhat of the same errors. I already had Ubuntu 7.04 installed, found out my system couldn't really hack it (it's an old system), and then tried to install Xubuntu 7.04. I'd get 5% into disk partitioning (I was doing a full partition) and I'd get the "Xubuntu failed to create a file system" error message. I found a bug report that says basically "We're sorry. We couldn't fix it in time for the release. Here's the work around:"

  ```
Boot the desktop CD.
  Go to Applications -> Settings -> Settings Manager.
  Select "File Manager".
  Switch to the "Advanced" tab.
  Click on the "Configure" link ("Configure the management of removable drives and media ...").
  Uncheck "Mount removable drives when hot-plugged" and "Mount removable media when inserted".
  Close all the windows just opened, and start the installer.
```

Here's the full link: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259")

Hopefully this will help you guys

---

### Post by stevepb on 2007-10-24
Hi,

Thank you ryangoff!! That wasa great help! I had the exact problem and you've made my day :D

I am installing Linux xubuntu for the first time. I have used Linux before, but i'm in no way very familiar with its' masses of shell commands etc.

I now find my company has the need for a data storage device which can be access using our newly acquired VNP routers. Basically all i want the linux box to do is provide storage using an already existing pptp connection for remote users and a ipsec permenant vnp connection between two node offices.

Can any one tell me if I have chosen the right distro to do this?

i'm guessing i'll have to use the samba file sharing. I wonder where i can find some advice on setting this up to run with the XP and Vista system??

Any advice is very welcome and mucho appriciated!

Thanks

---

