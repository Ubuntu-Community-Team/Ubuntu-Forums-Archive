---
title: "Latitude D600 Install"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by CasedOut on 2008-08-17
Hey all,
Totally new to Linux so please be gentle :-). I am trying to get 8.0.4 Desktop installed from CD on my Dell Latitude D600. However, every time I get past the select keyboard layout prompt (Select US, click Go Forward) the cursor just spins busy and nothing happens. I have tried installation from boot up as well as letting the live CD boot and then installing.

Anyone know what's happening?
Anyone know where to go hunting for a fix?
What more can I provide to be helpful?

Thanks in advance!

---

### Post by Vivaldi Gloria on 2008-08-17
I don't know anything about that computer but here is a standard list of things to try in your situation:


**1)** Make sure that your sytem satisfies the minumum specs:

> Ubuntu is available for PC, 64-Bit PC and Intel based Mac architectures. At least 256 MB of RAM is required to run the alternate install CD (384MB of RAM is required to use the live CD based installer). Install requires at least 4 GB of disk space.

**2)** Check the cd you are using:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

and burn it slow.

**3)** Google your computer model and ubuntu. May be there's a fix. Seach launchpad bug reports and ubuntu forums.

**4)** Play with boot options:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

**5)** Try alternate cd.

**6)** Install a cli-only system using the minimal cd:

[http://ubuntuforums.org/showthread.php?t=882596](http://ubuntuforums.org/showthread.php?t=882596)

And then add a desktop environment. For example:

sudo apt-get install ubuntu-desktop.


If nothing works file a bug report.

---

### Post by CasedOut on 2008-08-17
Alright! Now we were getting somewhere. I am now using the CLI installer and have made it all the way through the partitioning process. When it moves to install the base system there is a "Debootstrap Error - Failed getting Release file \n http://us.archive.ubuntu.com/dists/hardy/Release."

The it presents a full menu of items and I tried the Base System Install again. Same failure. 

Big Menu time again. Be smart and reselect "Detect Network Configuration". Successful. Back to big list. "Base System Install". Same failure.

Anyone have a work around? I will investigate the webs on my own in the mean time. 

As always, thank you for you time and patience with us newbies.

---

### Post by CasedOut on 2008-08-17
Alright. Totally resolved now. To those that find this: there are TWO network config steps. Install is chugging along.

---

