---
title: "Live CD installer: 8.04 1 specific question"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by mwparis on 2008-09-18
Hi all,

My first post and first attempt to install Ubuntu 8.04 using the Live CD installer.

Here's the scenario: [Dell XPS M1330, 320GB]

-Vista is installed (and for masochistic reasons I want to keep it) but I have no files on it

-Used Vista to shrink its partition as small as I could get it

-Booted from Live CD to install

-Now at "Step 4 of 7" "Prepare partitions" and I'm doing a manual partitioning

-I want to:
  ---shrink the Vista partition further
  ---create new partitions for Ubuntu (swap,root,boot,home) in the free space

What is going to happen to the windows partition when I shrink it?

Will the repartition destroy it? Will I have to reinstall windows?

Thanks.

Mark

---

### Post by oilchangeguy on 2008-09-18
> **mwparis said:**
> Hi all,

My first post and first attempt to install Ubuntu 8.04 using the Live CD installer.

Here's the scenario: [Dell XPS M1330, 320GB]

-Vista is installed (and for masochistic reasons I want to keep it) but I have no files on it

-Used Vista to shrink its partition as small as I could get it

-Booted from Live CD to install

-Now at "Step 4 of 7" "Prepare partitions" and I'm doing a manual partitioning

-I want to:
  ---shrink the Vista partition further
  ---create new partitions for Ubuntu (swap,root,boot,home) in the free space

What is going to happen to the windows partition when I shrink it?

Will the repartition destroy it? Will I have to reinstall windows?

Thanks.

Mark

you need to leave no less than 50gb for vista. there is no reson to shrink as small as you can get it. what do you think is going to happen the next time you run visa, and it wants to do an update? you'll end up regreting it if you do this.

---

### Post by mwparis on 2008-09-18
Hi. 

Thanks. Yes, you're probably right -- though I don't use Windows a lot, this could be a problem.

I should have given the sizes: Vista allowed me to resize to about 135GB and I want to reduce it to 100GB.

In any case, I've decided to wipe the MediaDirect partition since it was the "fourth" primary partition and put Ubuntu there.

According to another thread, using Gparted on the Windows partition can(?) cause a problem which can be fixed using [**this**.]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/")
Any comments on this?

Any comments/criticisms related to this plan are welcome.

---

### Post by mwparis on 2008-09-25
Just to tie this off -- 

I used Gparted, without incident, to resize the partition. It worked like a dream.

Next: creating another partition and installing the 64 bit version...

---

