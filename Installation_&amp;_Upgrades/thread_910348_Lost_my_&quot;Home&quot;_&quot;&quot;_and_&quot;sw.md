---
title: "Lost my &quot;Home&quot; &quot;/&quot; and &quot;swap&quot; partitions!"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by B3Nji on 2008-09-04
OK here goes. 

I have a 500gb hard drive, all was going well. I had set up 1gb for swap, 6gb for my / and 413 for my home partition. The remaining 80gb I wanted to use for a windows XP install so i can play windows games fast on my new graphics card. 

Went to install windows with a copy of Tiny Xp. 

It wouldn't deal with the multiple partitions. 

So I booted into a  program i found on the disk called "part" i ran from command prompt. 

I saw an option to make partitions "hidden" I choose that option for my swap, / and home partitions. Thinking windows will just see the 80gb which i could install to, then when im done installing i could go into Ubuntu live CD, see the "windows" hidden partitions and install it all again with my old settings. 

I vaguely remember it saying something about saving the MBR thing if that helps? 

This was not a good plan. 

Now when I live boot from the ubuntu cd all i can see is 

386 gb as unallocated

and 79 gb as unknown. 

I assume the 386 gb is all my Linux partitions squashed into 1 somehow!

Can anybody help me.. ?

Thank you for all your help.

<SOLVED>

Found a thread that was posted just 4 minutes previous to me. :) 
I installed an awesome program called "testdisk" from the ubuntu live CD. 

Brought back all my partitions, worked like a charm!! :)

---

