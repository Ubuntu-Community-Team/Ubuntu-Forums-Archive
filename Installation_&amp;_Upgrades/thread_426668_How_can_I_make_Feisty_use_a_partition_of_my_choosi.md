---
title: "How can I make Feisty use a partition of my choosing?"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by starbase1 on 2007-04-28
Hello All,
I'm now trying to install Feisty on my other PC, but I can't seem to persuade it to use the partition I want...

I have three physical rives, but Feisty only offers me the option of installing to the biggest one (460 Gb), and even then won't let me go below allocating 130 Gb, which seems a lot!

I had an EXT 20 Gb partition on the C: drive I was trying to use - when it did not use that I tried removing it, in the hope it could create it's own, but it still wants a big bite of the big drive... Choosing manual does seem a good idea, as I am completely clueless about the 'use as' or 'mount point' parameters, so I am rather nervous...

Now I have Partition magic for windows, which I feel comfortable with, so perhaps I could create it that way, then point Ubuntu at the one I create? 

Anyway, if someone could advise, or point me at some docs, I'd b very grateul,
Manythanks,
Nick

---

### Post by louieb on 2007-04-28
Manuel partition option. Just go past the first screen and on the second pick the partitions you want to use for / (root) and swap.
Check the psychocats link good stuff about manual partitioning there.

---

### Post by starbase1 on 2007-04-29
Yes, I tried that, but I seem to have something set up wrongly, or maybe missed a step? 

And what are all the file systems? Which will work with Ubuntu? And which is best? I'm guessing the EXT2 and EXT3 will work, and as it's more recent I'm also guessing that EXT3 is better than EXT2...

When I resize in Partition Magic I see warnings that the partition crosses a 1024 cylinder boundary, and may not be bootable. Is this important for Ubuntu? Does it need to be a primary partition or can it be a logical partition?

Alternatively, can I persuade it to use less of my largest disk? I also tried the manual install here, and that would not let me use less disk space... And that's a LOT for such a compact and efficient OS!

Help!
:confused:

---

### Post by louieb on 2007-04-29
The first screen in the manual partitioning  part of the install screen runs a program called GParted. I've herd this screen work some what like partition magic. I've never used partition magic. 
GParted list all your partitions on a given drive. What file system they use and how big they are.
Upper right hand corner   is drop down list to let you change which drive to view.
>  Alternatively, can I persuade it to use less of my largest disk?How much space do you want to give ubuntu?   Use partition magic or or GParted and create a partition that size. Also create a 2nd partition 1 to 2 time the size of your ram. this will be used for swap.
>  And what are all the file systems? Which will work with Ubuntu? And which is best? ... Don't know which is best. I use ext3.  
>  ... I see warnings that the partition crosses a 1024 cylinder boundary, ...
Maybe. Depends on your BIOS. [Can be worked around.]("http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap6") Just hope you don't have to. 
Linux doesn't care if in a primary or logical partition.

If the drive you want to install Ubuntu on is empty or backed up; just play around with partition magic or GParted and get the drive sliced up the way you want it.      [Nuts: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

### Post by starbase1 on 2007-04-29
Thanks **VERY** much for the info, and the links! I am now the proud owner of a PC that boots directly into Ubuntu from the HD!
:) 

Nick

---

