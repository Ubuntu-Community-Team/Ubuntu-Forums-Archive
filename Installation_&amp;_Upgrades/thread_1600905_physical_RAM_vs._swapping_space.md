---
title: "physical RAM vs. swapping space"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by SaintDanBert on 2010-10-19
Folks,
    I run 32-bit Ubuntu with the PAE extension. This enables use of my physical memory as:  two slots, 2 GBytes per slot, total 4 GBytes.
That is 4 x ( 1024 x 1024 x 1024) or 4,294,967,296. Alternately, that is (2**32) -1 or 4,294,967,295.

    Suspend features require that swapping space be larger than available memory.  **fdisk -l /dev/sda** reports that my swap partition is 4000153+ blocks at 512 bytes/sector (1 sector is 1 block) or 2,048,078,336 -- half of what I thought I allocated or need.

[highlight]Q1: [/highlight]Do I need fdisk to report that my swap space is larger than the 4,294,967,296 number or 8388609 blocks, 512 bytes/sector?

[highlight]Q2: [/highlight]Using **gparted** or similar, how do I make my swap space larger?

[highlight]Q3: [/highlight]Can I create a **swap file** for use as extra suspend space without changing partition details?

---

### Post by SaintDanBert on 2010-10-19
Now I'm really confused:
```

[color=green]prompt$ [/color]**free -m**

             total       used       free     shared    buffers     cached
Mem:          3949       3128        820          0        386       1996
-/+ buffers/cache:        745       3203
[highlight]Swap:         3906          0       3906[/highlight]


```

---

### Post by garner_nc on 2010-10-19
You can create a swap file to use as additional swap space. I've seen numerous posts about doing this. I just don't recall how. Google may be your friend here.

All the Best,
D. White

---

### Post by SaintDanBert on 2010-10-20
I (1) know that it is possible, and (2) know how to create a "swap file" versus a swap partition.

The release notes for **sleep** and **hibernate** state that (paraphrase) "swap space must be at least the size of physical memory"

My question:  Does the **suspend** processing use swap file space as well as swap partition space to satisfy its needs for somewhere to write system state for sleep or hibernate operations?

Merci d'avance,
~~~ 0;-Dan

---

### Post by psusi on 2010-10-20
Hibernate requires a swap partition ( not file ) >= your physical ram size.  Suspend does not.  Many people, myself included, run without a swap partition and just use suspend.

If you want to resize, then boot the live cd and fire up gparted.  It's user interface is pretty self explanatory.

---

### Post by -kg- on 2010-10-20
Sleep mode is Suspend mode, and you don't need swap for Suspend mode...only for hibernate.  From the following page:

[http://manpages.ubuntu.com/manpages/jaunty/man8/pm-suspend.8.html]("http://manpages.ubuntu.com/manpages/jaunty/man8/pm-suspend.8.html"):

>  **pm-suspend**
           During suspend most devices are shutdown, and [COLOR="Red"]system state is saved
           in RAM[/COLOR]. The system still requires power in this state. Most modern
           systems require 3 to 5 seconds to enter and leave suspend, and most
           laptops can stay in suspend mode for 1 to 3 days before exhausting
           their battery.

       **pm-hibernate**
           During hibernate the system is fully powered off, and [COLOR="Red"]system state
           is saved to disk[/COLOR]. The system does not require power, and can stay
           in hibernate mode indefinitely. Most modern systems require 15 to
           45 seconds to enter and leave hibernate, and entering and leaving
           hibernate takes longer when you have more memory.


In Suspend mode power is cut to all non-essential parts of the computer in order to save energy.  RAM is not non-essential in this case, and power is maintained to RAM in order to save its contents.

In Hibernate mode the computer is completely shut down, but before it is shut down the contents of RAM are saved to SWAP in order to maintain the state of the computer before shutdown.  All programs that were running and data that was in memory will be there upon reboot.

Frankly, Hibernate is useless to me.  It takes longer to reboot than a normal reboot, since you've also got to load the info from Swap back into RAM.  I can remember where I was, I can save everything before I shut down, and rarely do I ever find myself in the situation that I need everything back exactly as it was on reboot.

If I want to do that, I use Suspend which, while using power, minimizes its usage and comes back up in almost no time.  It also doesn't use Swap - it just maintains the information in RAM.

Another consideration is the amount of RAM you have.  Unless you run some esoteric memory hog that uses massive amounts of memory (like intensive multimedia processing or CAD/CAM software that you need to operate and make changes as quickly as possible), if you have anywhere above, say, 2 GB, you're unlikely to ever use Swap at all (unless you elect to use Hibernate).

I have 2 GB of RAM in this desktop, and have burned CDs, done some limited audio processing, etc., and I don't think I've ever have used the Swap file.  Whenever I pull up System Monitor, it shows that the Swap partition has not been used.

Just a few things for your consideration.

Other than that:

> Q2: Using gparted or similar, how do I make my swap space larger?

Read at the link in my signature block.

> Q3: Can I create a swap file for use as extra suspend space without changing partition details?

Probably, but you'll have to do some manipulation of partitions unless you happen to have some free space on your hard drive right next to the swap partition into which you can expand it.

---

### Post by SaintDanBert on 2010-10-20
> **-kg- said:**
> 
...
In Hibernate mode the computer is completely shut down, but before it is shut down the contents of RAM are saved to SWAP in order to maintain the state of the computer before shutdown.  All programs that were running and data that was in memory will be there upon reboot.

Frankly, Hibernate is useless to me.  It takes longer to reboot than a normal reboot, since you've also got to load the info from Swap back into RAM.  I can remember where I was, I can save everything before I shut down, and rarely do I ever find myself in the situation that I need everything back exactly as it was on reboot.
...


I agree about sleep vs. hibernate, but there is one situation where I find hibernate handy.

[indent]
I'm madly working on something and need to leave for a meeting.
The meeting requires a lengthy drive + meeting itself + return trip.
During this walk-about, I need to continue working on battery power.
[/indent]

In these cases, the elapsed time might take too much from battery charge to enable a useful walk-about work session. Hibernate to the rescue.  Even though the network connection won't be "the same", the standard wake-from-hibernate network retry simply fails and a fresh scan finds whatever it there at the time.

Cheers,
~~~ 0;-Dan

---

