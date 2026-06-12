---
title: "kernal update from 2.6.32-32 to2.6.32-33 and now problems??"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by ak331 on 2011-07-17
I recently upgraded to image 2.6.32-33 these are the results and ran into problems with grub generation and it hangs and I have to restart the computer and new kernel does not show up in the menu at the start.

When I run update manager I get this message :

not all updates can be installed.
run partial update to install as many updates as possible.

if run updates it hangs and if Try to close the window I get this message 

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

when I run it in terminal the system hangs at the generating grub.cfg and just hangs

If I run synaptic manager it tells me that package is broken and I should run "sudo pkge -config -a".
 

and I am not sure whether I can manually remove the latest kernel or reinstall it as terminal freezes and synaptic manager quits after the message.

I have looked at all the messages and have not found a solution yet. I hate to reinstall the operationg system.

Any suggestions.

---

### Post by DanneStrat on 2011-07-17
Hi.

Could you post the contents of your sources.list?

Open terminal and run this:

```
cat /etc/apt/sources.list
```

This will print the contents of sources.list to standard output.

Post the output here.

---

### Post by Bucky Ball on 2011-07-17
What release still uses those kernels, [B]2.6.32-xx?

[/B]If your recently is no longer supported that could be at the bottom of your problems (any of the 9.xx releases, for instance).

---

### Post by DanneStrat on 2011-07-17
> **Bucky Ball said:**
> What release still uses those kernels, **2.6.32-xx?**

10.04 lucid lynx

---

### Post by Bucky Ball on 2011-07-17
> **DanneStrat said:**
> 10.04 lucid lynx

Thanks.

---

### Post by ak331 on 2011-07-17
Here is thesource list

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) jaunty main


I hope that helps.

---

### Post by Bucky Ball on 2011-07-18
```
sudo apt-get update
```

Disregard error, then:

```
sudo apt-get upgrade
```

This will upgrade packages, NOT the distibution.

---

### Post by SteDolphin on 2011-07-18
Hi there, I am having the same problem.

I have 10.04 amd64 and I have made the update as I was prompted to do that. Being honest I haven't seen any error message.

Now I can't boot at all, I have a blank screen with a blinking cursor ... I don't see any grub menu. Nothing at all :(

Steve

---

### Post by Bucky Ball on 2011-07-18
> **SteDolphin said:**
> Hi there, I am having the same problem.

I have 10.04 amd64 and I have made the update as I was prompted to do that. Being honest I haven't seen any error message.

Now I can't boot at all, I have a blank screen with a blinking cursor ... I don't see any grub menu. Nothing at all :(

Steve

Please post a separate thread with a descriptive title for your issue as yours is *not* the same. You will get more specific help that way. The OP can get to a desktop, just can't get updates. It gets confusing trying to work out two issues on one thread. ;)

ak331: did you run this command by the way?

```
sudo pkge -config -a
```

---

### Post by SteDolphin on 2011-07-18
Sorry, you are right ... is just that I urgently need to have this machine working, and it looked similar.

I have opened a new post.

---

### Post by ak331 on 2011-07-18
> **Bucky Ball said:**
> Please post a separate thread with a descriptive title for your issue as yours is *not* the same. You will get more specific help that way. The OP can get to a desktop, just can't get updates. It gets confusing trying to work out two issues on one thread. ;)

ak331: did you run this command by the way?

```
sudo pkge -config -a
```


I did run the command when it gave me message in the terminal generating grub.cfg and just hung there

---

### Post by ak331 on 2011-07-18
> **Bucky Ball said:**
> ```
sudo apt-get update
```

Disregard error, then:

```
sudo apt-get upgrade
```

This will upgrade packages, NOT the distibution.

I ran the command and got message as follows:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by Bucky Ball on 2011-07-18
Did you then run 'sudo dpkg --configure -a'??

---

### Post by ak331 on 2011-07-18
> **Bucky Ball said:**
> Did you then run 'sudo dpkg --configure -a'??

I did run the sudo dpkg --configure -a when it hung at generating grub.cfg and i had to reboot the system again.

---

### Post by Bucky Ball on 2011-07-18
Perhaps try:

```
sudo update-grub
```

---

### Post by ak331 on 2011-07-18
> **Bucky Ball said:**
> Perhaps try:

```
sudo update-grub
```


I tried the above command and still hangs in the terminal I had to reboot system again????.

---

### Post by Bucky Ball on 2011-07-18
Sounds perhaps like you need to reinstall grub from a LiveCD. Boot from a LiveCD, make sure you are online with a cable, and put this, from [HERE]("http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html") in a terminal, commands one at a time:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair-ubuntu
```Now Boot-Repair should be under System, probably Admin (am on Xfce at mo). Run Boot Repair and choose 'I want to install the bootloader,' as suggested [HERE]("https://help.ubuntu.com/community/Boot-Repair").

Reboot from the hard drive.

Before anyone asks, the Boot-Repair download link above tells me BR will install and run using a LiveCD boot.

---

### Post by ak331 on 2011-07-19
The above worked.

Many thanks for taking time for helping.

---

### Post by Bucky Ball on 2011-07-19
Glad it worked. ;)

Please mark thread as solved from 'Thread Tools.'

---

