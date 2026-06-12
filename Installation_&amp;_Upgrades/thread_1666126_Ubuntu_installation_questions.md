---
title: "Ubuntu installation questions"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by CP2 on 2011-01-13
Hello all. I'm only about 2 weeks new to Ubuntu. I have a couple questions. 

1. Does Ubuntu Lucid or Maverick have a tool where you can install another version of Ubuntu over the currently used OS and still keep the settings? Please don't tell me just to do a backup. I know that's one of the obvious choices, but another obvious choice would be to use some type of upgrade wizard. 

2. Between Lucid and Maverick, which one do you prefer? I was on the #Ubuntu channel and a couple guys were kind of clowning me because I'm a newb who started with Maverick and ended up installing Lucid on the same disk different partition. They said I should have simply stuck with Maverick. I was told that Lucid was more stable and what not. I thought this might help with my ***not being able to boot up Ubuntu on the 1st, 2nd, or 3rd try*** problem that I've been having.

---

### Post by ErikNJ on 2011-01-13
> **CP2 said:**
> Hello all. I'm only about 2 weeks new to Ubuntu. I have a couple questions. 

1. Does Ubuntu Lucid or Maverick have a tool where you can install another version of Ubuntu over the currently used OS and still keep the settings? Please don't tell me just to do a backup. I know that's one of the obvious choices, but another obvious choice would be to use some type of upgrade wizard. 



What settings do you wish to keep?  Is it just for applications like email, web-browser, etc?

---

### Post by CP2 on 2011-01-13
> **ErikNJ said:**
> What settings do you wish to keep?  Is it just for applications like email, web-browser, etc?

Well more than just setting, but programs and files that I downloaded. Mainly mediatomb settings, conky script, and a few other programs i downloaded. I can download the programs again, but I'm more concerned with conky and mediatomb because I worked so hard and long (get your head out of the gutter) to get it where I wanted.

---

### Post by 0N3 on 2011-01-13
Partition your HD in 3 

/(root)
/home
swap
that way all your settings and files will be saved in /home partition

---

### Post by CP2 on 2011-01-13
> **0N3 said:**
> Partition your HD in 3 

/(root)
/home
swap
that way all your settings and files will be saved in /home partition

You mean each directory would be their own partition? 

And we are getting away from one of the original questions which i assume is being answered passively. No, there isnt and upgrade wizard that lets me keep my current programs and settings. Please correct me if I'm wrong. lol.

---

### Post by ErikNJ on 2011-01-13
I would suggest just copying the settings you'd like to keep from your home directory.  Bear in mind they will likely reside within "hidden" directories where the name begins with "."  You can see them with "ls -a" or "ctrl h" in the focused home window.

I'm not aware of a program that does this for you - it seems a bit unnecessary anyway.

---

### Post by 0N3 on 2011-01-13
Yes each directory in its own partition if you dont do that from the start unfotunately you have to do a backup, but if you partition your HD into 3 in future you wont lose those files even after a fresh install.

---

### Post by CP2 on 2011-01-13
> **0N3 said:**
> Yes each directory in its own partition if you dont do that from the start unfotunately you have to do a backup, but if you partition your HD into 3 in future you wont lose those files even after a fresh install.

Interesting tip. I wish I would have gotten the memo sooner. Lessons learned by a n00b. How large would you make each of these partitions?

---

### Post by 0N3 on 2011-01-13
/(root) 10-15GB is ideal 
swap 2-3GB
/home as the rest

---

### Post by CP2 on 2011-01-13
> **0N3 said:**
> /(root) 10-15GB is ideal 
swap 2-3GB
/home as the rest

I currently have Ubuntu on a 50 GB partition. So this should suffice. I really have to keep track of where things are. initially Ubuntu loads all of these things on one partition. Of course i would have to move the directories to their own partition. Would I need to change any settings to point to these directories in order for Ubuntu to act right?

---

### Post by 0N3 on 2011-01-13
My advice would be a fresh install setting up the partitions as above and No you wouldn't need any extra configuration to get it to work.

---

### Post by CP2 on 2011-01-13
> **0N3 said:**
> My advice would be a fresh install setting up the partitions as above and No you wouldn't need any extra configuration to get it to work.

So simple drag and drop those directories into the other partition and voila?!?! Sorry I am being so n00bish.

---

### Post by 0N3 on 2011-01-13
you kind of lost me there

Ok....

When doing a fresh install go to advanced install and from there make your 3 different partitions and then install as usual dont use the install side by side option or use the full HD go for advanced install as stated above partition your HD into 3 partitions as above and volia! install as usual.

---

### Post by CP2 on 2011-01-13
> **0N3 said:**
> you kind of lost me there

Ok....

When doing a fresh install go to advanced install and from there make your 3 different partitions and then install as usual dont use the install side by side option or use the full HD go for advanced install as stated above partition your HD into 3 partitions as above and volia! install as usual.

Alright, when I get home I'll give it a go. Thanks alot.

---

