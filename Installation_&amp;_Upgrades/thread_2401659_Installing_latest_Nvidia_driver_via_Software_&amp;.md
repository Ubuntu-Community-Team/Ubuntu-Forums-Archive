---
title: "Installing latest Nvidia driver via Software &amp; Updates vs command line"
date: 2018-09-20
forum: Installation &amp; Upgrades
---

### Post by ubuntini2 on 2018-09-20
Hi
Want to install latest 400.xxx nvidia driver in Ubuntu 18.04.
Normally I *_always_* wait for the driver to become available in *Software & Updates*.

However, reading [this]("https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux") I was wondering if there is any potential problem installing via the command line?

The corollary to this question is why does it seem the latest driver is not immediately available in Software & Updates since I am using a PPA?

(2nd method in above link - **Automatic Install using PPA repository to install Nvidia Beta drivers**)

ie 

> $ sudo apt update

then either
> $ sudo ubuntu-drivers autoinstall

or

> $ sudo apt install nvidia-xxxx

---

### Post by deadflowr on 2018-09-20
The ppa needs to be updated to include the 4XX drivers first.
It's lagging behind, I guess.
I've never seen any difference as to when new drivers are in software and updates and when they are installable through command line.

---

### Post by ubuntini2 on 2018-09-20
Thanks. So guessing there is always a delay before the PPA is updated...
Just wary of doing ANY driver upgrades via command line though in the past my problems were a result of manually downloading the driver directly from Nvidia. Will never attempt that again!

---

### Post by Bashing-om on 2018-09-20
ubuntini2; Hello -

Patience - the drivers are coming:
[https://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-410.57-Beta-Released](https://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-410.57-Beta-Released)

just takes some time for our developers to tweak and test prior to releasing for common usage :)

as to install, Nvidia advises:
> 
Note that many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this rather than NVIDIA's official package.


[INDENT][INDENT]a work in progress
[/INDENT][/INDENT]

---

### Post by ubuntini2 on 2018-09-20
Thanks. Will wait for the PPA. May I ask on average what the delay is between a new driver release and the PPA being updated?

---

### Post by Bashing-om on 2018-09-20
ubuntini2 - well ---

> **ubuntini2 said:**
> Thanks. Will wait for the PPA. May I ask on average what the delay is between a new driver release and the PPA being updated?

Deep subject -
Most depends on the amount of help they get from the community: see the notes:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

and also the calls for help:
[http://albertomilone.com/blog/?p=670](http://albertomilone.com/blog/?p=670)

[INDENT][INDENT]open source, we are all in this together
[/INDENT][/INDENT]

---

