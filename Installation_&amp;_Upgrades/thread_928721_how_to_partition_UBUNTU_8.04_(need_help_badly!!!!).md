---
title: "how to partition UBUNTU 8.04 (need help badly!!!!)"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by uglybastard0 on 2008-09-24
hey guys,

i'm new to ubuntu...i'm currently running on windows xp sp2 and i plan to dual boot using UBUNTU 8.04 LTS (you know, test the water first before plunging in)...

as a backgrounder, i have partitioned my 250GB hard drive into three (3) partitions (80GB each) using windows...my windows XP is installed in the 1st partition; the 2nd is where all my media (mp3s, pictures, applications, etc.)...the 3rd is left empty (i've read from a magazine (Linux Format) that you should install Linux (ubuntu, for that matter) to a separate partition if you plan to dual boot -- besides the fact that it may cause conflict if installed in the same partition as that of windows)...

i already burned the image to a CD and have tried to install ubuntu (almost)...

anyways, i'm having problems on partitioning...i tried to use the 3rd option (manual partitioning) but i'm having second thoughts (in short, nervous coz i might %&$#-up my computer)...the window showed me the 3 partitions...i opted for the 3rd partition (assuming that it's the empty partition)...it then asked me to partition it (root something)...and that's where my mind flew away (i really don't know what to do)...

could you guys help me out? pls. send me a step-by-step procedure (i've read the procedure from softpedia.com but i'm still having problems specifically on partitioning ubuntu)...

i already tried contacting the philippine linux users group (PLUG) though...

thanks a million

my email add: [email]ugly_bastard6@yahoo.com[/email] :confused:

---

### Post by Elfy on 2008-09-24
Welcome to the forum.

You need 2 partitions - 1 for / (root) and 1 for swap. Swap should be equal or greater than ram if you need to hibernate. If not for ram less than 1Gb then swap = 1.5xRAM, for more thna 1Gb I have found 512Mb of swap sufficient (I have 1Gb swap and never use it all).

I've not used the manual option so am not sure of the steps. Instead use partition editor in the system admin menu.

In the empty space create an extended partition using all of the space available. In that extended partition create 2 logical partitions

swap - however big you decide
ext3 - remainder of the space.

Go back to the install and when you reach the partitioning again pick manual - select the ext3 partition you made with the editor. Edit partition - in the Use As drop down menu - pick ext3 , in the mountpoint dropdown menu pick / close that window and carry on

Ask more if you need to :)

Make sure you have backups if there is information you can't afford to lose.

---

### Post by uglybastard0 on 2008-09-24
btw,are you saying that i have to allocate the 2 partitions (out of the 3 that i already mentioned) to cover the 2 partitions needed for  ubuntu (i.e. 1 for root and 1 swap)...

is it possible to use the 3rd partition that i left empty (70GB) for the 2 partitions for ubuntu?

---

### Post by uglybastard0 on 2008-09-24
btw,are you saying that i have to allocate the 2 partitions (out of the 3 that i already mentioned) to cover the 2 partitions needed for ubuntu (i.e. 1 for root and 1 swap)...

is it possible to use the 3rd partition that i left empty (70GB) for the 2 partitions for ubuntu?

---

### Post by Elfy on 2008-09-24
Sorry, obviously not clear - you make the extended partition where your 3rd partition is and then the 2 logicals get made inside that.

You can only have 4 primary partitions on any drive - so using an extended and logicals oercomes this, then if later you wanted to do something else you could if necessary make another primary.


You don't need to do anything to, or with, either of the 2 other partitions at all.

---

### Post by uglybastard0 on 2008-09-24
nope,i haven't partitioned my drive yet using ubuntu 8.04...see,i'm planning to dual boot...

as i've said,i've partitioned my 250GB drive into three (3) when i installed windows XP...i've cleared the 3rd partition (70+GB) in the hopes of installing ubuntu 8.04 in it...the 1st two partitions were for my windows xp,etc.

would it be possible to use that empty partition for my ubuntu?

---

### Post by JohnFH on 2008-09-24
Alternatively you could safely ignore what the Linux magazine had to say and install the WUBI version of Ubuntu: [https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide").  This installs it alongside Windows, but in a safe way even to the extent that you can move it to its own partition(s) later.  Have a read of the documentation in the link above - it is very easy to read and very helpful.

---

### Post by uglybastard0 on 2008-09-24
thanks a million for the link...try to check it now

---

### Post by fourthofjuly on 2008-09-24
> Alternatively you could safely ignore what the Linux magazine had to say and install the WUBI version of Ubuntu: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide). This installs it alongside Windows, but in a safe way even to the extent that you can move it to it's own partition(s) later. Have a read of the documentation in the link above - it is very easy to read and very helpful.

very true, JohnFH...

for starters, go with the wubi method or you might risk losing precious data...

[http://wubi-installer.org/]("http://wubi-installer.org/")

---

### Post by Elfy on 2008-09-24
> would it be possible to use that empty partition for my ubuntu?YEs - make an extended partition and then 2 logical partitions inside it to install ubuntu.

You can indeed use wubi to install, as has been pointed out you can later transfer to it's own partition.

There is a wubi forum here spefically for wubi, if you use other forums pleas elet people know that you are using wubi - it can make a substantial difference at times toi the information received and asked for.

Good luck

---

### Post by uglybastard0 on 2008-09-24
thanks a million guys...

---

