---
title: "Change swap size for 12.04 Server, semi-guided?"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by Javik on 2013-02-14
I'm setting up a new VM running "ubuntu-12.04.1-server-amd64.iso"
 
I've had problems in the past with an Ubuntu 512 meg swap not being enough for a LAMP VM server, and having to increase the VM memory to 2 gig to keep it from crashing/freezing.
 
I want to give a new Ubuntu build more swap space, 3 gig rather than 512 meg. But I don't see how to do this.
 
Boot CD,
Guided partitioning? Yes
Size? Use 100% of disk (20 gig VM disk)
Here's what will be done (partition list, 512 meg swap). Write changes? NO
 
Partition edit screen:
 
Selecting one of these partitions gives no size change options. 
 
[IMG]http://img802.imageshack.us/img802/3572/guidedpartioningedit.png[/IMG]
 
 
Example partition options ..... no options for size change:
[IMG]http://img812.imageshack.us/img812/7571/guidedpartioningedit2.png[/IMG]
 
 
 
So, am I forced to not used guided partitioning at all and I have to figure out how to do the partition creation completely manually, to have a bigger swap?
 
A second option appears to be to do guidied partitioning, but use 3 gig less than the max disk space, then after it's all done, make a second swap from the remaining free space. Though this is more hassle yet.

---

### Post by gordintoronto on 2013-02-14
> **Javik said:**
> ...So, am I forced to not used guided partitioning at all and I have to figure out how to do the partition creation completely manually, to have a bigger swap?

Exactly! Bear in mind that significant use of swap will make your system very, very slow. Are you running huge applications that consume memory?

---

### Post by MAFoElffen on 2013-02-14
I do manual / custom partitioning. If. after install, I need to change, then I do this:
[How do I add more swap?]("https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F")

Swap is used as needed. It is not going to aimlessly swap something bigger than needed or at all if not needed. That just doesn't logically happen. Now if you don't have much RAM at all, then you swap excessively.

Swap is cheaper than RAM. (Especially considering ECC Registered!!!) But swap is understandably not faster than RAM, even if you have it on SSD.

Ubuntu's Swap FAQ recommends:
Min = RAM
Recommended = ( 2 * RAM )

My experience with Linux servers = ( 2 * RAM ) + 1 and putting that Swap on a different physical disk than root (and home)... That way it can swap while it does a read/write. Swapiness lives good on servers set at 60 (which I think is server editions default).

Note that, in relation, MS says for it's own servers ( 4 * RAM ) rounding up an additional 4MB... So the above calculations are comparatively conservative.

The above is just a rule of thumb I've kept myself to. My own curiousity, is that when you get to 16GB or more of RAM, the only way you know how much swap you really need is just take a SWAG, run it to monitor and track swap usage. Been thinking about that one... I have some script that are more accurate than Top reports.

---

