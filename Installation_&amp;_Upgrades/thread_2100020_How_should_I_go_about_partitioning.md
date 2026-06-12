---
title: "How should I go about partitioning?"
date: 2012-12-31
forum: Installation &amp; Upgrades
---

### Post by gas0line on 2012-12-31
I have a MacBook Pro currently running only OS X. I would like to dual-boot to Ubuntu 10.04.4 LTS. 

Should I partition my HD before booting off of the live CD, or will the debian-installer partition it?

---

### Post by raja.genupula on 2012-12-31
Ubuntu Live OS have in-built partition system. so no problem you can do partition there.

If you want to know install process you can see this link 

[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/#.UOG-6vnNWJM](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/#.UOG-6vnNWJM)

---

### Post by TheFu on 2012-12-31
> **gas0line said:**
> I have a MacBook Pro currently running only OS X. I would like to dual-boot to Ubuntu 10.04.4 LTS. 

Should I partition my HD before booting off of the live CD, or will the debian-installer partition it?

The default partitioning scheme is lacking, IMHO. It is fine for trying out Linux for a few months, but probably not good enough for someone who will be using Linux more and more.  There is an "advanced" option during install, but it assumes you know what is necessary and will set that up yourself.

For example, I like 4 partitions.

[LIST]
[*]/boot
[*]/
[*]/home
[*]swap
[/LIST]

[LIST=1]
[*]/boot is where non-encrypted boot files are located. Size: 500MB
[*]/ is where most of the OS and apps go. This and /boot can be upgraded easily. Size: 10-15GB
[*]/home is where end-user files go. My settings and my small, local data. Large data is stored on the network - in other places. Size: 3-4GB, more if needed
[*]swap is needed just like with other OSes. By using a different physical HDD, performance can be enhanced too. Size: 2GB or less. The old 2x RAM is outdated.
[/LIST]
Others will have different suggestions, but I think the most important aspect is to keep MY data (/home) separate from the apps and OS. Every time I do not, I regret it later.


Good luck and happy Linuxing!

---

### Post by dino99 on 2012-12-31
here is how to do a standard installation:

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

note: the "manual" install is called now "Something Else" installation by the installer.

---

### Post by gas0line on 2012-12-31
Thanks for everyone's answers! I will go ahead and install now.

---

### Post by gas0line on 2012-12-31
Hmm, I seem to have run into a problem. When I select "Use continuous free space", I get an error message saying:

> [color=red]**Failed to partition the selected disk**[/color]
This probably happened because the selected disk or free space is too small to be automatically partitioned.

_I have over 450 GB of free storage on my Hard Drive, is that not enough?_

TheFu: I didn't use the advanced option since... well, I'm not advanced. :p

Raja: That article says "These instructions apply for Ubuntu 12.04 and may cause serious damage to other versions." I am trying to install Ubuntu 10.04.4 LTS.

---

### Post by gas0line on 2012-12-31
--bump--

still need help here, guys

---

### Post by gas0line on 2013-01-01
--bump-- 

please help meh!!

---

### Post by TheFu on 2013-01-01
You really should not install 10.04. It is almost out of support and doesn't include some important updates for new partitioning methods.

12.04 has those.

I don't think there is anyway to avoid the "advance" partitioning. Sorry.

---

### Post by gas0line on 2013-01-02
thank you

---

