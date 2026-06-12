---
title: "swap space, how?"
date: 2014-10-28
forum: Installation &amp; Upgrades
---

### Post by Curbside Jimmy on 2014-10-28
I have loaded ubuntu lots of times but I have never been able to figure out how to add swap space when the dialog comes up. It is part of the instalation process but as far as I can tell there is no way to do it. 

I always install ubuntu on a seperate partitioon.

How exactly does one assign swap space?

---

### Post by mastablasta on 2014-10-28
this works on manual partitioning /expert mode whatever is called now...

select /swap as mount point, dedicate disk size to that partition, then select to format it as swap.

I am not sure where you have the problem to explain it better. I mean at what step do you miss it?

---

### Post by Curbside Jimmy on 2014-10-28
I have not seen that exact choice. I actually made two partitions for ubuntu with a small one for swap space, I ended up using the large one only and skipping swap space. Are you saying that I should have chosen to format the smaller partition as /swap? I am about to install ubuntu on another computer.
Do I actually need two partions, or can this be accomplished with just one partition?

---

### Post by sudodus on 2014-10-28
Select ***Something else*** at the partitioning window. Normally all available swap partitions are set to be used automatically, but you can select or de-select each of them (if you have more than one swap partition).

You can even select to have no swap, but it is recommended to have at least a small swap partition for example 512 MB or 1 GB. If you intend to hibernate, you need at least as much swap as RAM (in Gibibytes; base 2), otherwise you can have less, and when you notice that the computer starts swapping you can close some application.

---

### Post by mastablasta on 2014-10-29
> **Curbside Jimmy said:**
> I have not seen that exact choice. I actually made two partitions for ubuntu with a small one for swap space, I ended up using the large one only and skipping swap space. Are you saying that I should have chosen to format the smaller partition as /swap? I am about to install ubuntu on another computer.
Do I actually need two partions, or can this be accomplished with just one partition?

mount point is  /swap
file format: swap

you could do it with a file but it's more complicated.

---

### Post by Herman on 2014-10-30
[Dynamic Swap Space Manager]("http://pqxx.org/development/swapspace/")  is an option worth considering for anyone who has installed without creating a swap area.
It's easy to use, all we need to do is install it. ```
sudo apt-get install swapspace
```I have been using it for years and it works well for me. Performance doesn't seem to suffer at all. A disadvantage is we lose the option to hibernate our systems, but we can still suspend if we don't want to shut down. It offers quite a savings in disk space for anyone installing with limited disk space such as in an SSD or flash memory. Also it may possibly help to reduce and spread wear on the flash cells. I use it for hard drives too.

---

