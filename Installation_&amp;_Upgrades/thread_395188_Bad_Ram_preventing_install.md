---
title: "Bad Ram preventing install"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by Grafster on 2007-03-27
So I've made multiple attempts to install edgy and/or feisty. In each case (booting post upgrade online upgrade, booting from different CDs) I've had the same Kernel Panic/failed synch error.

(It's come up before once or twice but for the life of me I can't figure out why).

Dapper, both HD installs and CD boots perfectly every time. The CDs used all tested properly (i.e. checksum's match, etc.)

Having run out of all other explanations I ran a Memtest.

This morning the memtest said I've got bad ram:
[FONT="Courier New"]
Test |  Pass |        Fail Address                |   Good   |    Bad      |Err bits| Count Chan
  7   |    5    |  00037f78b64  --  895.5MB |96e93aac| 96e93aae|   2     |      1
[/FONT]

Assuming I don't want to buy new ram are there any suggestions on how to handle this?

[edit: for some reason I can't get the post to properly show the spaces in the table above. Hope it is still readable...]

---

### Post by simonn on 2007-03-27
You have 2 options.

1) New RAM.

or

2) Less RAM - if you have multiple simms and experiment to find which one is dodgy.

Is the memory under warranty?

---

### Post by Grafster on 2007-03-27
Definitely 2.

Not under warranty.

Not buying new memory. Dapper runs fine (95+% of the time), so I have a usable amount of RAM. 

I remember reading somewhere that you can set Grub to mem=x where x is less than the value of the bad memory and it will skip the bad memory.

Or that there is a way to instruct Grub to not use the two bad memory 'chunks'.
I think they would be: 96e93aac and 96e93aad, right?

---

### Post by Grafster on 2007-03-28
I will try to add the line
MEM=890

and see what happens.

---

### Post by Grafster on 2007-03-28
deleted as post made no sense

---

### Post by Grafster on 2007-03-28
Can someone explain to me why you can't edit previous posts that have been made? Why have an edit button? Why force people to post everything twice?

Anyway
I've been popping in and out the two RAM sticks to see if I can isolate the problem. It's proved ... isolation resistant. The exact same kernel error is generated every time.

Ran memtest on one stick last night
Test | Pass | Fail Address | Good | Bad |Err bits| Count Chan
6 | 9 | 00037f78b64 -- 895.5MB | 7fffffff | 7ffffffd | 2 | 1

Trying the second stick now

[Incidentally the CD's all checked out on other computers (no checksum errors).]

---

### Post by gdmellott on 2007-03-28
Hi,  I had a machine of my own pull something similar.  Often I am able to get things working better on a machine with a silicone gel compound used by auto mechanics to keep (computer and battery) connections from corroding.  I ONLY DO THIS WITH OLD COMPUTERS THAT NO WARRANTY EXIST FOR ANY MORE.  If first started using WD-40, or the likes, to clean contacts.  That particular machine did not improve, though.  Eventually it went down all together.  It may have been due to mixing memory stick inapproriately.  I think the North bridge, the chip that connects the computer's central processing unit (CPU) to the memory and other places was failing.

Sincerely,

Gregory D. MELLOTT

---

### Post by Grafster on 2007-04-02
thanks for the suggestion.
It definitely wasn't the RAM. I found a good stick and the error still replicates.

---

### Post by slayerboy on 2007-04-02
> **Grafster said:**
> thanks for the suggestion.
It definitely wasn't the RAM. I found a good stick and the error still replicates.

Then the memory chip slots on your motherboard are going bad/have gone bad.  If your computer is not under warranty and you have a fairly large case you could swap out the motherboard, but you'll be looking at having to buy a new CPU and memory anyways unless you can find a used board that runs the same stuff you have now.  How old is this computer?

Might be time to get a new computer, bud...:(

---

### Post by Grafster on 2007-04-02
> **slayerboy said:**
> Might be time to get a new computer, bud...:(
Nos! I just built this one like two years ago!!
grr.

It's all swappable, but since I don't really play games and and the current motherboard is newish (MSI Platinum Neo2) I'm not really interested in spending money on another board.

That's well outside of the topic of conversation.

I should just have stuck with Dapper.

---

