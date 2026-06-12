---
title: "Swap Area...I'm confused!"
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by marck.karam on 2011-11-08
hello guys
 i have a simple question ... it's maybe existed before ...but it's make me very confused!
my question about swap area.. or Determine the size of the swap area
some friend told me that it should be Twice the size of ram ?

and other told me it Must not be greater than 4 giga ?

my laptop 
320 hard disk
4 giga ram

so What is the appropriate area to the swap on my laptop 

4giga or 8 giga ?


am waiting 4 your replay

any hint will appreciated
thx in advance

---

### Post by efflandt on 2011-11-08
Swap double RAM was in the old days when people did not have much RAM.

Now if you want to hibernate (good idea for a laptop in case battery runs low), you need at least as much swap as RAM (maybe a little extra to be on the safe side since somethings measure it in decimal 1000's instead of binary k's).

On my 8 GB desktop I do not have any swap at all. But it is on a UPS so it should not lose power if in suspend (or I simply shutdown).  Swap is not needed for suspend, which just flushes any drive writes and puts the CPU and RAM in a low power state.

---

