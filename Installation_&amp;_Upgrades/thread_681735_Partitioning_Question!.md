---
title: "Partitioning Question!"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by Crazy_Chris on 2008-01-29
Hi, Ive been using Ubuntu 7.04 as a trial for around a month.. and liked it so much that ive decided to install 7.10 Gutsy (dual boot with Vista - **Vista already installed**) on my new Dell laptop!
When i previuosly installed Ubuntu i used the wubi automatic installer, but this time round i plan on manually partitioning my 320gb HDD and installing from the live CD. 

Ive been reading up on partioning, but there are a few things that still confuse me.. 

If I set up my HDD like this,
[[IMG]http://img379.imageshack.us/img379/2128/partitioning5bu8.th.png[/IMG]](http://img379.imageshack.us/my.php?image=partitioning5bu8.png)
using this program ( [http://www.fs-driver.org/](http://www.fs-driver.org/) ) to allow Vista the ability to access and modify the Ext3 portions of the HDD 
as shown on this page: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) 

will my Vista system files **AND** all my installed Vista applications and games be located on the "Windows Vista (NFTS)" or  will windows applications and games i install after partioning be on "Ubuntu /home - Shared data (Ext3)", the shared portion off the HDD? I ask because i am trying to  decide what size each partion should be, and while i plan on using the majority of the HDD as the  shared partion for music and movies, the vista applications and games i have installed, and will continue to do so after installing Ubuntu, will take up quite abit of space, and i dont want to run out! and also, are all Ubuntu apps installed to the root ( Ubuntu / Ext3  ) or home partions? - also asking for the same reasons!

Sorry if these questions either dont make sense, or have been answered somhere else!

Thanks, Chris =D

---

### Post by forestpixie on 2008-01-29
windows apps will install to the ntfs drive - the fs driver allows windows to see the ext3 partitions, afaik you can't install win apps to the ext3 shared partition

programs are generally installed to /, configs go to /home a bit like c:\docs and settings has win config files

hope that helps some

---

