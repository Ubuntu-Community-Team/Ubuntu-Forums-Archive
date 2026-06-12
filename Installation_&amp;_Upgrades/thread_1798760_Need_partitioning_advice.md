---
title: "Need partitioning advice"
date: 2011-07-06
forum: Installation &amp; Upgrades
---

### Post by Awes0meSauce on 2011-07-06
[SIZE=2]So today I attempted to install Ubuntu 11.04. My computer has three hard drives and I allocated an entire drive for the install. Here is some info on that HDD:

[/SIZE]>  [SIZE=2]
WDC WD25 00KS-00MJB0 SCSI Disk Device             
Manufacturer             Western Digital             
Business Unit/Brand   Enterprise/WD S25             
Interface                   ATA             
Capacity                   244GB             
Real size                   250,059,350,016 bytes                 
S.M.A.R.T                  not supported
[/SIZE][SIZE=2]
I made sure that I deleted all partitions so that the drive is just free space. For some reason, there is no option to use the entire drive, or free space for the install. Maybe that option was only available in past Ubuntu versions, or I'm just getting confused with an entirely different distribution install altogether; but what I need is some help setting up partitions on this HDD. While I am a bit of a noob, I do understand the basics of partitioning. I would like some help in setting up partitions as effectively as possible. I would like to use EXT4 as it uses journaling for my data, however, I would like to use a different partition and maybe another file system for the /var directory, for example. I do not think I need journaling for a bunch of log files because it is a waste of  space and processing. I hope that makes sense, but if someone could help me chose the right sizes and file systems for the different directories so that Ubuntu can run effectively, I would really appreciate it. Thanks for you time.[/SIZE]

---

### Post by Quackers on 2011-07-06
During an attempted installation does the installer "see" the empty hard drive?

---

### Post by Awes0meSauce on 2011-07-06
> **Quackers said:**
> During an attempted installation does the installer "see" the empty hard drive?
Sorry for not getting back sooner, but yes, the installer did see the empty hard drive. However I have to chose the option "Something Else" in order to see it. The other two options will not use the empty drive. Whenever I chose install along side Windows it just starts installing right away, to where I have no idea, but it doesn't give me any options to chose the drive. And the option, replace Windows is out of the question. So I have to use the "Something Else" option. Am I missing something? Well anyways, I figured this would be a good time to manually mess around with partitions and files systems. Was hoping I could learn a little something in the process. Any help would be appreciated.

---

### Post by haqking on 2011-07-06
an example:

/boot 100 Mb ext 2 (dont need journalling overhead on boot

/ (root) 1 to 2 gb

swap (usually at least size of ram, some say twice the size debatable depending on whether you use hibernation)

/home as large as necessary

/tmp 1 or 2 gb depends on what you do and use tmp for

/usr depends on software packages you plan to use (this can be ext2 aswell as data dont change much

/var min of 500...lot bigger if using server services (daemons)

but you could put the whole lot on /

or / and /home

or / /home /boot

etc etc

---

### Post by psusi on 2011-07-06
There is little to no reason to create a separate partitions for anything other than /home ( and swap of course ).  There is no overhead saved by putting /boot on another fs and you will just fill it up and run into problems when it is out of room.

Unless you are planning on installing multiple different linux distros, just go with the default partitioning scheme: one for swap, and one for everything else.

---

### Post by Awes0meSauce on 2011-07-06
> **haqking said:**
> an example:

/boot 100 Mb ext 2 (dont need journalling overhead on boot

/ (root) 1 to 2 gb

swap (usually at least size of ram, some say twice the size debatable depending on whether you use hibernation)

/home as large as necessary

/tmp 1 or 2 gb depends on what you do and use tmp for

/usr depends on software packages you plan to use (this can be ext2 aswell as data dont change much

/var min of 500...lot bigger if using server services (daemons)

but you could put the whole lot on /

or / and /home

or / /home /boot

etc etc

> **psusi said:**
> There is little to no reason to create a separate partitions for anything other than /home ( and swap of course ).  There is no overhead saved by putting /boot on another fs and you will just fill it up and run into problems when it is out of room.

Unless you are planning on installing multiple different linux distros, just go with the default partitioning scheme: one for swap, and one for everything else.
Interesting. Thanks for the input. I like what psusi said about creating two partitions for swap and /home. But what does hagking mean by putting the "whole lot on /"?

---

### Post by haqking on 2011-07-06
> **psusi said:**
> There is little to no reason to create a separate partitions for anything other than /home ( and swap of course ).  There is no overhead saved by putting /boot on another fs and you will just fill it up and run into problems when it is out of room.

Unless you are planning on installing multiple different linux distros, just go with the default partitioning scheme: one for swap, and one for everything else.


well i listed lots of options including everything on /  and /home

however if you seperate data that changes alot like /home and /var from /boot and /usr which dont change much then you can reduce fragmentation (little i know) and depends on your system, for a desktop then yeah probably overkill but he is looking to play with partitions.

and /boot wont get filled up quickly especially if he makes it something like 100 or 200 mb and uses a non journalling FS unless he is installing lots of OS

plus seperating /usr can be useful if he wants to export it to another machine at a later date.

there are also arguments for /opt.

just options, for most dekstops then yeah a / and /home is fine but a little tweaking here and there if he wants to play wont harm too much.

---

### Post by haqking on 2011-07-06
> **Awes0meSauce said:**
> Interesting. Thanks for the input. I like what psusi said about creating two partitions for swap and /home. But what does hagking mean by putting the "whole lot on /"?


I meant that some people choose to put the whole thing under /
or use entire space and mount it as /

which makes recovery a pain, it is better for a / and /home as a minimum

---

### Post by psusi on 2011-07-06
> **haqking said:**
> 
and /boot wont get filled up quickly especially if he makes it something like 100 or 200 mb and uses a non journalling FS unless he is installing lots of OS

/boot easily reaches 100mb these days with just a handful of kernel updates.  200mb might be ok, but why chance it?  That is just one less headache to worry about.

> **haqking said:**
> plus seperating /usr can be useful if he wants to export it to another machine at a later date.

Why would you want to share /usr?  And you can share a directory without it being on its own partition.

> **haqking said:**
> there are also arguments for /opt.

What uses /opt?  The only thing I have ever seen using it is the occasional proprietary software package.

---

### Post by haqking on 2011-07-06
> **psusi said:**
> /boot easily reaches 100mb these days with just a handful of kernel updates.  200mb might be ok, but why chance it?  That is just one less headache to worry about.


Why would you want to share /usr?  And you can share a directory without it being on its own partition.


What uses /opt?  The only thing I have ever seen using it is the occasional proprietary software package.

like i said unless he has lots of OS which i meant as kernel updates, i  never said he should, i was giving him options which are viable, i have  mine set up this way no issues, and there are plenty of resources online  which discuss the same, not a definitive but arguments for and agasint

i never said share, i said export to another machine or build

not alot  use /opt (like i said optional) just like the directory itself ;-) but i know a few people who use /opt for tarballs then create symbolic links

some examples on the ubunut wiki
[https://help.ubuntu.com/8.04/installation-guide/i386/apcs03.html](https://help.ubuntu.com/8.04/installation-guide/i386/apcs03.html)

---

### Post by YesWeCan on 2011-07-06
```
~$ ls /opt
Adobe  google  jre1.6.0_25  thinkTDA

```

---

### Post by haqking on 2011-07-06
> **YesWeCan said:**
> ```
~$ ls /opt
Adobe  google  jre1.6.0_25  thinkTDA

```

I have openoffice in mine ;-)

---

### Post by YesWeCan on 2011-07-06
> **haqking said:**
> I have openoffice in mine ;-)
I think we should form a secret society for /opt users. The adepts will put /opt on a separate partition.

---

### Post by haqking on 2011-07-06
> **YesWeCan said:**
> I think we should form a secret society for /opt users. The adepts will put /opt on a separate partition.

yeah but we should make joining /optional ;-)

---

### Post by psusi on 2011-07-07
> **haqking said:**
> 
i never said share, i said export to another machine or build


What do you mean?

You could "export" /usr with rsync or tar without it being on its own partition.

---

### Post by Awes0meSauce on 2011-07-07
*Nods head in agreement, pretending to understand*
Thanks everybody. I'll use a little from both and see what I come up with.

---

