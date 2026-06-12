---
title: "Going to install Ubuntu...a few questions"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by klato on 2006-10-08
Hi guys,

I've got a new 120gb hard drive here and I want to install ubuntu on it. I've read that in linux, a seperate partition is desirable for swap, root (although i guess this doesn't apply to ubuntu since there's no root user?), and home. What I want to know is, should I create these partitions, or will the installation create the necessary partitions for me and format them with the correct filesystem?

Also, since Edgy is coming out soon, should I just wait for that, or will I be able to upgrade my system to Edgy when I install 6.06? Furthermore, if I make changes to my system in 6.06, will my settings remain when/if I upgrade?

Thanks!

---

### Post by bruenig on 2006-10-08
> I've got a new 120gb hard drive here and I want to install ubuntu on it. I've read that in linux, a seperate partition is desirable for swap, root (although i guess this doesn't apply to ubuntu since there's no root user?), and home. What I want to know is, should I create these partitions, or will the installation create the necessary partitions for me and format them with the correct filesystem?
You still need a / partition. That is the root partition (not to be confused with root user). Everything in the filesystem is underneath the / partition. If you install ubuntu and just click right through the graphical install it will do it for you and you will be able to use it. It will create a / and a swap partition. If you want a seperate /home partition, you will need to do that manually in the install.
> Also, since Edgy is coming out soon, should I just wait for that, or will I be able to upgrade my system to Edgy when I install 6.06? Furthermore, if I make changes to my system in 6.06, will my settings remain when/if I upgrade?
I might wait. It is 18 days away but ultimately that is up to you. If you decide to go with dapper and then upgrade to edgy. You can do that without reinstalling by just upgrading through the repositories. It is probably a good idea if you plan to go with dapper and then change to edgy to have a seperate /home partition as that is the partition with all personal settings in it.

---

### Post by klato on 2006-10-08
Thanks for the reply. Are the partitions sized automatically or do I need to make any changes? Also, how big should the home partition be then? I've got a lot of music files, where do you think would be the best place for them so that anyone on the system can access them?

---

### Post by randell6564 on 2006-10-08
> **klato said:**
> Hi guys,

I've got a new 120gb hard drive here and I want to install ubuntu on it. I've read that in linux, a seperate partition is desirable for swap, root (although i guess this doesn't apply to ubuntu since there's no root user?), and home. What I want to know is, should I create these partitions, or will the installation create the necessary partitions for me and format them with the correct filesystem?

Also, since Edgy is coming out soon, should I just wait for that, or will I be able to upgrade my system to Edgy when I install 6.06? Furthermore, if I make changes to my system in 6.06, will my settings remain when/if I upgrade?

Thanks!
Hi!  Ubuntu will do the partitioning for you, no need to wonder!  Just select the drive to install to and Ubuntu will take care of the rest!

As far as eventually wanting to install Edgy, when it is released, you will get a notification message from your Update Manager, then you can just choose to update, and edgy will be installed!

---

### Post by randell6564 on 2006-10-08
> **klato said:**
>   I've got a lot of music files, where do you think would be the best place for them so that anyone on the system can access them?

You can create a seperate partition for storage, accessable by any user, or just use your /home folder.

---

### Post by klato on 2006-10-08
randell,

How much space should typically be given to /home?

---

### Post by randell6564 on 2006-10-08
> **klato said:**
> randell,

How much space should typically be given to /home?
There is NO such thing as "Typically" with Linux!  You can size it to whatever you want!  Mine is 10GB.

---

### Post by randell6564 on 2006-10-08
Oh, and BTW.,I am currently downloading the[ Edgy Alternate 6.10 beta]("http://us.releases.ubuntu.com/6.10/").

Just in case you don't want to wait for the official release!

---

### Post by klato on 2006-10-10
How about the swap partition?  I have 512mb of RAM.  I've been reading around and have seen people doing 1.5xRAM, which for me would be a 768mb swap partition (I have the same size in Windows and it seems to work ok). I've also seen 2.0xRAM, which would be 1gb. Not much difference, really...but what is the best size for me?

Also, how can I get perfect partition sizes?  If I select, say, 1gb as a parition size, or will it be a screwy number slightly less or whatnot due to cluster size?

I know this might be nit picking, but I want to know everything before I install =)

---

### Post by randell6564 on 2006-10-10
> **klato said:**
> How about the swap partition?  I have 512mb of RAM.  I've been reading around and have seen people doing 1.5xRAM, which for me would be a 768mb swap partition (I have the same size in Windows and it seems to work ok). I've also seen 2.0xRAM, which would be 1gb. Not much difference, really...but what is the best size for me?

I know this might be nit picking, but I want to know everything before I install =)
I can't get into all that!  Not that "nit picky" about it! LOL! :), but just so you know, I also have 512MB of ram and I **just let ubuntu create the ****default partitions**, and I Love my Ubuntu!

---

### Post by klato on 2006-10-13
Ok guys.  I'm partitioning my drive right now.  Right now it looks like this:

hda1 /
hda2 swap
hda3 /home

Should I put swap on hda3 instead?

---

