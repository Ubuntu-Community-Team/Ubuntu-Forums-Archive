---
title: "Bogging down in Linux partitioning strategy"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by Multi-Booter on 2007-12-02
OK guys, I have long-since forgotten the 'primer' I recieved in Linux partition strategy.

With that said, I really didn't consider it at all until I was already in the install process creating partitions and could not create any more. It was well past midnight... I just 'blanked' on it and went ahead forward with the install.

But I have been meaning to re-visit the issue and also try to find a retainable strategy I can ABSORB for future use.

Since installing, I have read several things on Linux partitioning. But I have just gotten bogged down in every one of them and not adopted a logical strategy.

The problem for me is that everything I have read starts out OK, then drifts to the far left and far right without enough iron-clad fact. You know what I mean?.... Too much possible theory and not enough concrete stuff.

So if anyone knows the strategy well, could you please put it in a block format for me?... Small blocks/paragraphs, condensed down as much as possible...

Basically pick a strategy to work around the limitations and stick to that logical strategy?.... I GET bogged down in the "drifting"....

THANKS

---

### Post by starcannon on 2007-12-02
swap should be as much or double the amount of your ram
always put /home on its own partition
everything else is just preference.

---

### Post by mikewhatever on 2007-12-02
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

Can you be more specific. What do you want to know?

---

### Post by Multi-Booter on 2007-12-02
> **starcannon said:**
> swap should be as much or double the amount of your ram
always put /home on its own partition
everything else is just preference.

> **mikewhatever said:**
> [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

Can you be more specific. What do you want to know?

Good posts... both cover what I do essentially.

I like it myself, I think it is good, etc... but it does not address the other side of partitioning strategy... partition limitations...

What I mean is, you can only have so many partitions... but there are ways to work around this.... 

That's what I am getting bogged down in trying to learn/retain/absorb.

---

### Post by jken146 on 2007-12-02
You can only have a certain number of primary partitions (I think it's 4) but if you create an extended partition you can have as many logical partitions within that as you want.

---

### Post by Multi-Booter on 2007-12-02
Yeah, I think you are right... 4.

But things I'm trying to sort out are... 4 per disk or 4 per linux OS?

Also, I get the primary & extended partition thing... and that using other types of partitions is how you work around the limitation.... well you are not really working around it, but instead using other partitions besides primary.

This is to me partitioning strategy... planning to avoid wasting primary partitions.

So now, what I am trying to absorb here is "what" has to be on primary partitions?

Also, I'd like to iron out the 'theory' into fact as to what can be made work in the other partitions? I think this is where all the 'drifting' into possibilities goes on... and this is where I get bogged down...

---

### Post by Pumalite on 2007-12-02
Windows must have a primary partition; Ubuntu is most comfortable in a logical one. 4 primary partitions per disk. From the 3rd primary, make and Extended partition and within that you can put as many logicals as you want.

---

### Post by Multi-Booter on 2007-12-02
> **Pumalite said:**
> Windows must have a primary partition; Ubuntu is most comfortable in a logical one. 4 primary partitions per disk. From the 3rd primary, make and Extended partition and within that you can put as many logicals as you want.

Thanks... that's a big part of where I read a lot of drifting.

Really, when it comes to Linux, there is just a recommendation that some things be on a primary partition.
As in they do not have to be.... right?

The recommendation being that you put /boot on the first and that it be primary...

So then, you use one of your 4 to create an extended partition... inside of which you can create many logical partitions... inside of which you can store the other linux stuff.

---

### Post by Pumalite on 2007-12-02
'
Really, when it comes to Linux, there is just a recommendation that some things be on a primary partition.'

This is false. The rest is a repetition of what I already stated.

---

### Post by Multi-Booter on 2007-12-05
So nothing "must" be on a primary partition?

---

### Post by Pumalite on 2007-12-05
Not for Ubuntu.

---

