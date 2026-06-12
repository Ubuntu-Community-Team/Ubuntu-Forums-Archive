---
title: "Dualboot/swap file question"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by Breadpazoid on 2008-03-01
Hi all,

While I'm a seasoned Windows veteran and hardware/computer building junkie, I am a total Linux newbie. I've chosen Ubuntu as my main OS for my new laptop (specs at bottom of post) and I also want XP on it as the secondary.

Please link me if there is already a post on this, and if so, forgive my blindness. :oops:

Questions:
1. Everything I've read about dual booting tells me to create a swap partition. I am okay with this, but...can Ubuntu use a swap -file- on its own partition or do I have to create a separate one just for swap?
2. If I do have to create a separate partition, can I remove said partition after install or am I stuck with it? (I ask because I've read literature on Ubuntu using a swap file, not a swap partition...maybe I'm misreading?)
3. I've also heard once that Ubuntu doesn't work with all hardware. Is there a list of what it supports/doesn't out there? (Or, is there anything in my laptop specs at the bottom of this post that would raise a red flag?)

Thanks kindly in advance for any help with this!

(PS: How, how, how I wish that Ubuntu/open source was more widely talked about. I've hated Windows for years and I can't wait to move on to something better now that I've found it. Was massively impressed by a test run of Ubuntu Live. Two thumbs up.)

Laptop specs: Intel Core 2 Duo Mobile T9300 2.5GHz 6MB L2 cache; 4GB DDR2 667 RAM; 512MB NVidia 8600GT; 160GB 5400rpm HDD

---

### Post by scragar on 2008-03-01
it's easier to install windows first, then intall ubuntu, and ubuntu will automaticly create any swap partiton it needs if you just select GUIDED when it asks.

nothing in your specs would cause a problem as I can see, esspecialy since your using the same graphics card as my new comp :P.

---

### Post by Fekosa on 2008-03-01
As regards the dual boot question, you could try this guide:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Pumalite on 2008-03-01
Or this:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
(/swap=RAM in laptop if you want hibernation)

---

### Post by lha on 2008-03-02
> **Breadpazoid said:**
> 
1. Everything I've read about dual booting tells me to create a swap partition. I am okay with this, but...can Ubuntu use a swap -file- on its own partition or do I have to create a separate one just for swap?
2. If I do have to create a separate partition, can I remove said partition after install or am I stuck with it? (I ask because I've read literature on Ubuntu using a swap file, not a swap partition...maybe I'm misreading?)
3. I've also heard once that Ubuntu doesn't work with all hardware. Is there a list of what it supports/doesn't out there? (Or, is there anything in my laptop specs at the bottom of this post that would raise a red flag?)


1. Ubuntu can use a swap file. See [http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html]("http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html") for instructions.

2. You don't have to create a swap partition during installation - just use manual partitioning. It is possible to remove a swap partition if you create one during installation. It is, however, easier to install without swap partition than it is to remove a partition and expand other partitions so that the whole hd is accessible.

3. Use liveCD to find out if everything works on your laptop. The [community docs]("https://help.ubuntu.com/community/") have a partial hardware compatibility list.

---

### Post by Breadpazoid on 2008-03-03
Okay, that answers my questions. Can't wait to get it running (I'll have it in about a week yay!)

---

