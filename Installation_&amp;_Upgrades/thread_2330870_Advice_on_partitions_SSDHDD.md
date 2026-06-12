---
title: "Advice on partitions SSD/HDD"
date: 2016-07-15
forum: Installation &amp; Upgrades
---

### Post by joshymcd2 on 2016-07-15
Hey,
Having just finished a course where i had to use windows i've decided to switch back to linux (Ubuntu) and was looking for some advice/ideas on where to put my data/partitions.
My laptop has a 120GB SSD and a 500GB HDD
I tend to install lots of programs (i work as a software developer (and freelance web dev/design) so like to experiment with lots of different languages and development environments) 
Im thinking (assuming anything not explicitly defined will go to my SSD by default)

SSD
/            -     50GB
SWAP      -     20GB (I have 16GB of ram atm)

HDD
/usr        -     100GB
/opt        -     50GB
/home     -     ...


The other option (which i think i prefer tbh) is to install everything on the SSD and have symlinks to music, pictures, projects, etc.
is there a downside to this? im basically worried about how much space installed programs may take up


Thanks
Josh

---

### Post by DuckHook on 2016-07-15
Welcome to the forums, joshymcd2

Your proposed partition layout is certainly workable, but you may find the hard-wired partitions somewhat inflexible. I see four options:

[LIST=1]
[*]Use your proposed layout. There is nothing wrong with it and it is very workable.
[*]Keep everything to just /. Don't spin out /usr /opt or /home. Instead, symlink those directories to your HDD
[*]As (2) above but symlink only data in /home.
[*]Install your whole system on a LVM. This gives you the most flexibility and has a few fringe benefits like permitting system snapshots.
[/LIST]
I'm not sure which suits you better. For example, my natural propensity is to offload /tmp and swap to save write fatigue on the SSD, whereas your needs require large /usr and /opt. That is to say, since everyone's needs are different, everyone must make their own determination. You are obviously no newcomer to Linux, so are the best judge of your own needs and circumstances.

---

### Post by squirrel3 on 2016-07-15
SSDs are nice and fast. But space is always nice too. You have to weigh the pros and cons. If you use a lot of software then you might want a bigger HDD. Of course SSDs are insanely fast and are great for programs. I would use the 500 HDD and just upgrade the RAM if you're looking for speed. It's completely up to you. I had a Crucial SSD but it filled up really fast due to my programs, etc. Since you're a programmer, you might want the larger one for space.

---

### Post by Dennis N on 2016-07-15
Consider a system using LVM - that way you don't need to make guesses at installation time how large any partition might become over time. Adjustments are easy to make afterward. Also use GPT partitioning over MS-Dos.

---

