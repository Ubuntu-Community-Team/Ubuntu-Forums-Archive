---
title: "updating failure"
date: 2015-10-03
forum: Installation &amp; Upgrades
---

### Post by de Bacon on 2015-10-03
Hi, 
I am rather ignorant when it comes to the command line interface.  In other words I know what the terminal is and a few commands for basic thing, changing permissions generally is all I use commands for.  I use a desktop system with many HDDs / partitions and use the multi system boot capability of Grub.

Problem: 
Last week while using Kubuntu 12.04, I was running the system update (security and... ) the process broke, unable to retrieve something, don't remember now what it was that didn't download.  Well it resulted in that particular OS no longer booting up to the gui.  It now boots to a shell (I think that is the proper term).  So what comes up from boot is equivalent to a terminal window but it takes up the entire monitor, having a log in prompt.  I can log in, but I have no idea what to do beyond that.  Can I correct the problem?  I don't know that this is a resolvable situation really.  I'd think there should be a method to re-do/complete the update from that prompt yet I have no idea what it would be.  

Any assistance would be appreciated.

---

### Post by Frogs Hair on 2015-10-03
If this is package related there are some commands to try. First check for errors while updating. The first two commands are equal to running the update manger.  ```
sudo apt-get update

``` ```
sudo apt-get upgrade
``` 

If there are errors note them post them here. You may also see a prompt for one of the following commands, if that's the case do so.

Fix Installation:  ```
sudo apt-get -f install 
``` Configure packages:```
sudo dpkg --configure -a 
```

---

### Post by de Bacon on 2015-10-03
Frogs Hair,

Thanks for the information.  I went through what you wrote, performed the suggestions, and it worked out just as it likely should have.  With the correct information these things seem easy, without it, eek.

Enjoy,

---

