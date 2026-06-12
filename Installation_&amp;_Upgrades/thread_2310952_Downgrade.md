---
title: "Downgrade?"
date: 2016-01-23
forum: Installation &amp; Upgrades
---

### Post by Sopan_Kaushal on 2016-01-23
Hello everyone. This is Sopan Kaushal and this is my first post in here. Though I have been a frequent visitor to your forum since ages now. I have been using Ubuntu when it was like Ubuntu 7. something. But due to unavoidable circumstances I was not able to use a PC for like 3 years. 

Here I am now with nothing that I can remember anything which I used to do, so I would like you guys help.

I have installed Ubuntu 15.10. Is this a good idea? Or should I switch to the LTS before it's too late?

If yes is it possible to somehow downgrade or something to Ubuntu 14.04 LTS so that I do not loose my data this is the only OS that is on my HDD.

Sorry if this has been asked before I am still learning to get back up on my feet. Kindly advice.

EDIT1:  I thought I might give a little bit of what I am doing currently. I have completed my CCNA and now I am perusing CEH, looking forward to doing an ESCA and OSCP afterwards. I want to make my career in Pen-Testing.

---

### Post by howefield on 2016-01-23
Is 15.10 working for you ?

If it is I'd leave it alone, 15.10 is supported until July this year with the next LTS (16.04) is due out in April. 

That gives you around 3 months to get to 16.04 before 15.10 goes end of life, you will be able to upgrade from 15.10 to 16.04 which will be supported for 5 years.

---

### Post by Sopan_Kaushal on 2016-01-23
There have been issues with sources list and updates and all but yes it is working for me fine right now. 

Also looking forward to upgrade to an LTS I feel like a noob installing 15.10 in the first place. I should have know better. Also can I tag along with another doubt of mine in here or am I supposed to make another post for that?


I am trying to install OpenVAS on my Ubuntu but I am not getting a proper read on how to can you guide me about the same please as well?
BTW Fanks a lot for the fast reply :D

---

### Post by vasa1 on 2016-01-23
> **Sopan_Kaushal said:**
> ... Also can I tag along with another doubt of mine in here or am I supposed to make another post for that?
...
I suggest you start new threads for distinct issues with explicit titles. That would be more helpful to those searching for solutions to similar issues.

---

### Post by pfeiffep on 2016-01-23
> **Sopan_Kaushal said:**
> Hello everyone. This is Sopan Kaushal and this is my first post in here. Though I have been a frequent visitor to your forum since ages now. I have been using Ubuntu when it was like Ubuntu 7. something. But due to unavoidable circumstances I was not able to use a PC for like 3 years. 

Here I am now with nothing that I can remember anything which I used to do, so I would like you guys help.

I have installed Ubuntu 15.10. Is this a good idea? Or should I switch to the LTS before it's too late?

If yes is it possible to somehow downgrade or something to Ubuntu 14.04 LTS so that **I do not loose my data this is the only OS that is on my HDD.**

Sorry if this has been asked before I am still learning to get back up on my feet. Kindly advice.

EDIT1:  I thought I might give a little bit of what I am doing currently. I have completed my CCNA and now I am perusing CEH, looking forward to doing an ESCA and OSCP afterwards. I want to make my career in Pen-Testing.You might consider [moving your home directory to a separate partition]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

---

### Post by grahammechanical on 2016-01-23
> If yes is it possible to somehow downgrade or something to Ubuntu 14.04 LTS so that **I do not loose my data this is the only OS that is on my HDD.**

No. Each release of Ubuntu is built on the code base of the last release and goes through a 26 week development period during which there are massive changes to the code base. Since the release of 14.04 we have had 15.04 as well as 15.10. There is a massive difference in code between 14.04 and 15.10.

Some of us upgrade to each new release of Ubuntu and so we are always running a supported release. The difference between LTS releases and Interim releases is the frequency of upgrading. Whether we are on 14.04 LTS or 15.10 we are going to have to upgrade to 16.04 sooner or later. There is no escaping that fact if we want to continue using a supported version of Ubuntu.

I have a separate partition for my data. Not a separate /home partition. With a separate partition for data I can install different Ubuntu family members and access my data from whichever version or flavour of Ubuntu I am using. I can upgrade or fresh install without any worry that I might loose my data by accident.

If data is important to you then think about having another partition or even another hard drive to keep the data or the backups of data on.

Regards

---

### Post by Sopan_Kaushal on 2016-01-23
> **pfeiffep said:**
> You might consider [moving your home directory to a separate partition]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

But wouldn't installing an OS in the other partition be easier than moving home directory to a different partition???


> If data is important to you then think about having another partition or  even another hard drive to keep the data or the backups of data on.

On it as we speak... A new hard drive will be awesome... :D

---

### Post by pfeiffep on 2016-01-23
> But wouldn't installing an OS in the other partition be easier than moving home directory to a different partition???If you have plenty of disk space AND you want another OS yes.
One advantage of moving home to another partition is you can install a fresh install and choose not to format your home partition. Some folks upgrade without problems, other install fresh most of the time to avoid issues (I always do fresh installs)

---

### Post by Sopan_Kaushal on 2016-01-24
> If you have plenty of disk space AND you want another OS yes.
One advantage of moving home to another partition is you can install a  fresh install and choose not to format your home partition. Some folks  upgrade without problems, other install fresh most of the time to avoid  issues (I always do fresh installs)

Yes you are right... I also choose a fresh install, actually reduces the work and time it takes to get things started.

---

