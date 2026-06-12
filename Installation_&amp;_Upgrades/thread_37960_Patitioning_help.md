---
title: "Patitioning help"
date: 2005-05-29
forum: Installation &amp; Upgrades
---

### Post by Dagger28256 on 2005-05-29
I've looked through the other posts, but I can't seem to find any info on how to use the partitioning software that comes with the install disk.

I'm wanting to dual boot on my laptop, so I want to partition my xp part to be smaller, to give room for unbuntu. Everytime I try to decrease size, however, I have no clue what I'm doing.

When I choose my 80GB partition, and then select to change size, all the menus close, and just give me a command prompt sort of thing at the bottom of the screen. After a while, another screen pops up, asking if I want to make changes. Of course, since I don't know what changes were said to be made, I don't want to say yes.

Can anyone give me any help here? Is the program messing up, or do I just need to know what to type into that command prompt?

---

### Post by tread on 2005-05-29
I've never used the partition resizing tool in the install cd because I had my partitions setup correctly when I installed Ubuntu, which is a pity since I would really have liked to try it.

I know of one other way, which is to boot off the knoppix live cd and run qtparted, which gives you a partitionmagic style interface to resizing partitions.

---

### Post by clb137 on 2005-05-29
[QUOTE=Dagger28256]I've looked through the other posts, but I can't seem to find any info on how to use the partitioning software that comes with the install disk.

I'm wanting to dual boot on my laptop, so I want to partition my xp part to be smaller, to give room for unbuntu. Everytime I try to decrease size, however, I have no clue what I'm doing.

When I choose my 80GB partition, and then select to change size, all the menus close, and just give me a command prompt sort of thing at the bottom of the screen. After a while, another screen pops up, asking if I want to make changes. Of course, since I don't know what changes were said to be made, I don't want to say yes.

Can anyone give me any help here? Is the program messing up, or do I just need to know what to type into that command prompt?[/QUOTE]

Hi there,

The tool to partition ur drive in the setup is smart and clean to use, just make sure that you read everthing, remember to keep you XP on the 1st partition it will be something like HDA1 ( HD hardrive A 1st drive and 1 is the first partition)  Just tell the program the size you want and hey presto jobs agood one


good luck

clinton

---

### Post by Dagger28256 on 2005-05-29
So, when it pops up a prompt, I should just type in 20gb or something along that sort?

---

### Post by clb137 on 2005-05-29
[QUOTE=Dagger28256]So, when it pops up a prompt, I should just type in 20gb or something along that sort?[/QUOTE]


yep sort of like that  just tell it waht size you want


clinton

---

### Post by mingus on 2005-05-31
[QUOTE=clb137]yep sort of like that  just tell it waht size you want


clinton[/QUOTE]
 A quick PS to clb137's reply . . .

It's a very good practice to defrag the XP partition before resizing.  And if you are using FAT32 rather than NTFS, it's imperative you use chkdsk before the defrag.

---

### Post by clb137 on 2005-05-31
[QUOTE=mingus]A quick PS to clb137's reply . . .

It's a very good practice to defrag the XP partition before resizing.  And if you are using FAT32 rather than NTFS, it's imperative you use chkdsk before the defrag.[/QUOTE]


Yes I agree thanks for that, sometimes you can take many things for granted



clinton

---

