---
title: "Partioning help needed"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by Vaidya on 2007-09-25
Well, I have a stable running Feisty all setup.

I realised that I should have partioned the HDD (80GB) into 3 parts, root, data and swap instead of 2 partions only like I have now.

Well, used Gparted and did the needful.

Except I think I ended up using an option to resize before the data (or something like that, bear with me, I am fairly new to this)

Now, I have 15 GB of unformattted partition (which Gparted does not give option to format into ext3 or any other format)

When I run live CD, i get the option of setting the new format as root ...

Ok.... here is how I want to do this, please tell me if it will work:

1. Run Live CD and install Feisty on the new partion.

2. Use aptONcd to retrieve all my packages into the new partion thus set up

3. Delete old files from my 65 GB partition and use this for data 

The question are: 

WILL I LOSE MY DATA?

Also, my lyrics are kept in MySQL, will Amarok lose them? 

Will this approach work or is there a better way?

Looking forward to some help on this.

---

### Post by logos34 on 2007-09-25
Before you do all that try the [Gparted live cd]("http://gparted.sourceforge.net/")--see if it allows you to format that unallocated space.

---

### Post by maybeway36 on 2007-09-25
Where did the 15GB partition come from? Is your old ext3 still there?

---

### Post by Vaidya on 2007-09-25
Hi...

The 15 GB is the outcome of Gparted's resizing efforts.

Only, it is not formatted at all.

I will try to format it through Live CD gparted session and see if that helps.

Thank you.

---

