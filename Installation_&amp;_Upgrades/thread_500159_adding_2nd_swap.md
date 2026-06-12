---
title: "adding 2nd swap"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by Nom DePost on 2007-07-13
i have two HDs on the laptop,W2k & Ubuntu/Linux.  i'm thinking of adding a 2nd swap, ~500-MB, on W2k HD in addition to the existing 1-GB swap.
is this a worthy idea?
after setting up the 2nd swap (using Partition Magic), will i have to do anything to config Ubuntu to recognize the 2nd swap?


thank you kindly.

---

### Post by rillip on 2007-07-13
Need to know the memory size in order to tell if more swap is helpful or not.  Frankly, adding more is probably a waste of space. You're likely not using very much right now.  To check this, you can use ```
top
```.  At the top it will show you how much you are using/have free.

```

top - 13:58:51 up 1 day,  9:41,  1 user,  load average: 0.69, 0.43, 0.39
Tasks:  87 total,   2 running,  84 sleeping,   0 stopped,   1 zombie
Cpu(s):  6.3% us, 14.2% sy,  0.7% ni, 68.0% id,  1.8% wa,  0.2% hi,  8.8% si
Mem:    515004k total,   510800k used,     4204k free,     4416k buffers
Swap:  1124540k total,    18984k used,  1105556k free,   301420k cached

```

That's what mine looks like now.  You can see that with a terminal window, Opera with several tabs and ktorrent, I'm only using 20mb of swap space.  Now watch this:

```

top - 14:01:34 up 1 day,  9:44,  1 user,  load average: 0.68, 0.49, 0.42
Tasks:  98 total,   1 running,  95 sleeping,   0 stopped,   2 zombie
Cpu(s):  6.3% us, 14.2% sy,  0.7% ni, 68.0% id,  1.8% wa,  0.2% hi,  8.8% si
Mem:    515004k total,   511048k used,     3956k free,     6764k buffers
Swap:  1124540k total,    18984k used,  1105556k free,   258068k cached

```

I'm still using the same ammount after opening SpeedCrunch (KDE calculator), Evolution, and OOo Word Processor.  And I only have 512 mb of RAM.

So really, if you're using enough that more swap will help, you have too small a swap file to begin with or not enough RAM. If you don't have enough RAM, adding more swap won't help.

1gb is usually plenty of swap space, unless you're going to be hibernating the computer,

---

