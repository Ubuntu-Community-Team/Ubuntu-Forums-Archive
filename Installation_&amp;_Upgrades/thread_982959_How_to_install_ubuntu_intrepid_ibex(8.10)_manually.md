---
title: "How to install ubuntu intrepid ibex(8.10) manually ?"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by rams123 on 2008-11-15
I want to install Ubuntu 8.10 manually (means when selecting partition ). I am confusing alot while choosing manually at the time of partitioning . Please I need your help in this!

BTW: How much space we have to give to swap,root and home ?

---

### Post by overdrank on 2008-11-15
> **rams123 said:**
> I want to install Ubuntu 8.10 manually (means when selecting partition ). I am confusing alot while choosing manually at the time of partitioning . Please I need your help in this!

BTW: How much space we have to give to swap,root and home ?

Hi and this link has some great info
[https://help.ubuntu.com/community/Installation/I386](https://help.ubuntu.com/community/Installation/I386)
As for the size of the partition that will depend on the size of the drive. Swap is usually twice the memory up to 1gig of memory.

---

### Post by taurus on 2008-11-15
You just pick the Manual option when you get to the partition screen.  Then, you need at least one empty partition for root filesystem and have it mount to /.  And if you have another partition for home, then mount it to /home.  You don't have to do anything for swap partition since the installer should know and automatically mounts it as swap.

For standard desktop install, it takes up about 2.5GB so it all depends on how large your harddrive is and what do you plan to do with it.  You will be saving all of your personal stuff to your own $HOME so keep that in mind want you assign space for / and /home.

How big is your harddrive and much RAM do you have in your machine?

---

### Post by rams123 on 2008-11-15
> **taurus said:**
> 
How big is your harddrive and much RAM do you have in your machine?

HDD - 80 GB 
RAM - 256 MB

I want to provide 8 GB for Ubuntu. And rest to XP. So please tell me how much I have to give to root , swap and home.

---

### Post by taurus on 2008-11-15
The default install from the desktop CD (LiveCD) will take up about 2.5GB so 8GB is not a whole lot of space.  However, if you don't plan to download anything after installing, that would be plenty.  And since it's such a small space, I wouldn't worry about creating a separate /home then.  Just have one / and one swap, about 1GB.

---

### Post by rams123 on 2008-11-16
So you recommend 2.5 GB for Ubuntu and in that 1 GB for / and 1 GB for Swap , huh ? 

**Some doubts here -**

Is there no need for creating /home ? (Am little confused why they are for)

In 2.5 GB when I give 1GB for / and 1GB for /swap , then where 0.5GB will go ?

**BTW: I heard Ubuntu will take 4 GB for installing . Correct me if am wrong.**

---

### Post by cmileto on 2008-11-16
rams that isnt even close to what was posted directly above you. He is recommending he partition his drive as a 1 gig swap and the rest as /

And nowhere near 4 gigs. What he said 2 posts above was correct.

---

### Post by taurus on 2008-11-16
I recommend you give Ubuntu 10GB.  And the reason some people suggest you have a separate /home partition because when you upgrade to the next release, you can keep all your personal files and settings in /home/<username>.  Having a separate /home is entirely up to you.

---

### Post by cochingeek on 2008-11-16
Yes I agree, if you are giving just 8Gb to ubuntu no need to have a separate /home partition. Just give 500 to 600 Mb for /swap. And the rest you can make root.
The earlier saying of swap space twice the amount of ram does not hold good now when you have gigantic RAMs like 4Gb. In such cases 1 to 2 Gb swap space will be enough.
If you still want to create a separate /home then give 1Gb for root( ie /) and give the rest for /home.Best of lucks.
so,
   _Scenario 1_,
                  500 mb  as    /swap
    The rest(about 7.5Gb) as    /

     _Scenario 2_.

                    500Mb as     /swap
                   1000Mb as     /
  The rest( about 6.5 Gb) as     /home
 
nb.A separate /home will help back up and restore later on. I would also suggest 10Gb for Ubuntu, even that may get filled up fast.

---

### Post by rams123 on 2008-11-16
*Thanks all for ur help.*

SO I have to give 1000Mb  to root(/) when I provide 8 GB for installation . 

Then how much I have to give to root(/) if I have more that ,for instance 20 GB ?

BTW Some more doubts:

1. /home is for saving personal files and downloads. Then what is the role swap and root? I mean why we have to create swap and root ?

2. Why I select automatic while partitioning how much space is given to /,swap and home ?

---

