---
title: "Installation problems"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by Imagine3 on 2006-09-27
I am runing off of the Live CD. I have partitioned 6 GB of my HDwith gparted. I now have 2 partitions in the "Prepare Partitions" menu. The unallocated one and the origional one. Do i firstneed to make it a new partition or just click forward. THe reason I ask is when i click forward, i get an option of a Mount Pointm, size (which is the size of the origional partition) Partition which I cannot tell what partiton that is, and a reformat option. I did backup everything, but i just dont want to screw it up.

Im also very new to Linux, but I wanted to dabble in it and eventualy if i like it, switch to it competely.

---

### Post by marcelm on 2006-09-27
There has to be a ext3 partition and a swap partition for an install.

---

### Post by _teo_ on 2006-09-27
Hi, I am not sure whether I understand what you did. Why do you have unallocated space?

I can help you, but first I need to get the picture. Please, let me know whether following is correct:
- you allocated a 6 GB partition on your hard drive and intend to install there
- the rest is left unallocated, isn't it?

Did you allocate a swap partition?
And one more question: is there any other OS already installed? Windows maybe?

---

### Post by Imagine3 on 2006-09-27
I actually figured it out with help from another site. But what was going on was...I have an 80GB drive on my laptop. XP Pro is installed, and until I find a way to run all the programs I need (Photoshop, Illustrator, Dreamweaver) in Linux, Im need to keep Windows.

I used gparted to resize my main partiton. which left me with 6 GB of unpartitioned space. Then the rest of it is dedicated to widows still. 

I felt uneasy about installing Ubuntu on what looked like it was the actual partition that windows uses. But I did and it is running perfectly. All I have to do is when i start my computer choose Ubuntu or Windows. 

But thank you for your help. 

--------------------------------

I did post this a few mintues ago in a new thread but ill ask it here since i have your attention and willinglness to help. 

Ok, i just got Ubuntu installed on my laptop. So far I like it a lot (first time using any form of Linux). I am noticing some funny things with Firefox though.

1. I cannot right click on the page to bring up the ability to save images, view source etc..

2. When I try to install extensions, a small box pops up in the middle of the screen. It origionally looks like a little orange/brown bullet point up. When I go to resize the box it is just a plain white box with nothing in it. Is it even possible to add extensions to Firefox in Ubuntu?

3. Not Firefox related but is it possible to run programs like Macromedia Dreamweaver and Adobe Photoshop/Illustrator in Ubuntu. I know there is Gimp which is a free sub for photoshop, but if I can, I would rather run Adobe products since I spent good money on them. I still have windows XP Pro installed on a different partition so its not a big deal but just would like to know.

Thanks for your help in advance. Also so far, I am really loving the clean feel of Ubuntu.

Brian

---

### Post by _teo_ on 2006-09-27
> **Imagine3 said:**
> I actually figured it out with help from another site.
Good.

> **Imagine3 said:**
> 
1. I cannot right click on the page to bring up the ability to save images, view source etc..

No idea - here works.

> **Imagine3 said:**
> 
2. When I try to install extensions, a small box pops up in the middle of the screen. It origionally looks like a little orange/brown bullet point up. When I go to resize the box it is just a plain white box with nothing in it. Is it even possible to add extensions to Firefox in Ubuntu?

Yes, usually when you navigate to a page which requires additional plug-ins, Firefox is giving you an option to install them. But I cannot say what is wrong with your installation.

> **Imagine3 said:**
> 
3. Not Firefox related but is it possible to run programs like Macromedia Dreamweaver and Adobe Photoshop/Illustrator in Ubuntu. I know there is Gimp which is a free sub for photoshop, but if I can, I would rather run Adobe products since I spent good money on them. I still have windows XP Pro installed on a different partition so its not a big deal but just would like to know.

Yes, you can - [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
However I will encourage you to learn Gimp. This isn't that difficult.

---

