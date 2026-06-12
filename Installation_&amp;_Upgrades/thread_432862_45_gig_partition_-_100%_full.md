---
title: "45 gig partition - 100% full?"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by kgriffin on 2007-05-04
Hi all,

I am trying to install ubuntu on my brothers pc, who has many windows partitions, 
we have selected a 45 gig one so he can try out ubuntu.

When it gets to importing documents and profiles prompts it says the drive is 100% full.

This is slightly confusing as the partitioner gets the right one when it starts up, guided picks up sda5
sets 59% 34 gig but on step 5/7 the importing step  is says warns that the drive is 100% full.

Any ideas?

---

### Post by dannyboy79 on 2007-05-04
and you're sure that you're chosing to install ubuntu to the correct partition? why don't you boot into the live cd, then open the terminal and type this in

sudo fdisk -l

and tell me what it returns. and at the end of each of the lines, please inform me what is located on each of the partitions. this will aid me in helping you. also, you're saying that you chose the guided partitioning? when you do that, it's picking the correct partition? i wonder if it's not formatting it and leaving it NTFS and then of course ubuntu wouldn't be able to be installed on it. just give me the result of the above command and I can help.

---

