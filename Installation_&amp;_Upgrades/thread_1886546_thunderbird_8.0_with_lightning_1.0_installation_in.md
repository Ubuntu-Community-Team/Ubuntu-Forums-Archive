---
title: "thunderbird 8.0 with lightning 1.0 installation in ubuntu 11.10"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by vrakesh on 2011-11-25
Hi

I downloaded the thunderbird 8.0 package( tar file ). But i dont know how to proceed from there. I searched for config file also but no luck. Can you please tell me how install it along with lightning 1.0.

I tried installing from ubuntu software center. But its downloading thunderbird 9 and lightning isnt supported for that.


Thanks in advance

---

### Post by crazy bird on 2011-11-25
> **vrakesh said:**
> Hi
 
I downloaded the thunderbird 8.0 package( tar file ). But i dont know how to proceed from there. I searched for config file also but no luck. Can you please tell me how install it along with lightning 1.0.
 
I tried installing from ubuntu software center. But its downloading thunderbird 9 and lightning isnt supported for that.
 
 
Thanks in advance
 
Remove Thunderbird 8 and add the Thunderbird Stable PPA: [https://launchpad.net/~mozillateam/+archive/thunderbird-stable](https://launchpad.net/~mozillateam/+archive/thunderbird-stable).
With this PPA the Ligthning extension will be provided as well.
 
_**Removing thunderbird:**_
- Open a terminal
- type: **sudo apt-get remove thunderbird**
- type: **sudo apt-get purge thunderbird***

---

