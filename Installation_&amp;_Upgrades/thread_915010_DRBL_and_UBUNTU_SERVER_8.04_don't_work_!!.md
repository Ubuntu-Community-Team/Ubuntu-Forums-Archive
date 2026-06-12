---
title: "DRBL and UBUNTU SERVER 8.04 don't work !!"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by BingoBilly on 2008-09-09
I have downloaded fresh installs of Hardy 8.04 server and workstation.... followed the instructions and DRBL does not work with Hardy.   The only way I can get DRBL and CLonezilla working is on an old Gutsy install- where DRBL and clonezilla work fine for about a week then stop.

I had Hardy working with DRBL earlier in the year but it stopped working after one update or another( I made the mistake of allowing Hardy to update) and any reinstalls failed on DRBL install while running /opt/drbl/sbin/drblsrv -i stating the following before terminating the program:

[FONT="Courier New"][COLOR="Red"]Package linux-image-2.6.24-20-386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-image-2.6.24-20-386 has no installation candidate
linux-image-2.6.24-20-386 can NOT be downloaded!!! Something went wrong!
Maybe you should check /etc/sources.list or remove the unnecessary kernel block
in /var/lib/dpkg/status so that apt-cache pkgnames linux-image can
get the downloadable kernel! Then try to run this program again.
Program terminated!!!
[/COLOR][/FONT]
 

Anyway, I have been trying to resolve this ... finally going back to gutsy install ( not updating) and running old installer of DRBL - which all works....... but now, after following install instructions repeatedly I can say there is a definite bug- and that 8.04 and current DRBL/CLonezilla are not happy together.   Too bad!   When they work together it rocks!

Sad.

---

### Post by BingoBilly on 2008-09-10
HAPPY!!!

I should now change my title to DRBL and Ubuntu server 8.04 WORK!!

I am so impressed- who ever performed the work and made the changes over night please take a bow.

Issues at the big $$$$ software companies never get resolved this quickly!!

Anyway, without fanfare it appears the DRBL installer has been updated to address the issue I was citing.

A new option has been added to choose the kernel during the install and it appears to be fixed.

I am finishing the install as I type.

Again, wow!!!!

..... and thank you!!!!!!!!!!!!!!!!

BB

---

### Post by OfMacandMen on 2008-09-11
I have the same issue but still can not install. I have used both the following install commands

./drblsrv -i -o
and 
./drblsrv --install --client_kernel_from

but I still get the same error. 

How do you get around this issue

Thanks

---

### Post by OfMacandMen on 2008-09-12
I solved this by adding the following to my /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-proposed main restricted universe multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-proposed main restricted universe multiverse

---

### Post by nirmalraj on 2008-09-19
i am trying to install DRBL in ubuntu 8.04 hardy, i got error message as...

Package linux-image-2.6.24-20-386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-image-2.6.24-20-386 has no installation candidate
linux-image-2.6.24-20-386 can NOT be downloaded!!! Something went wrong!
Maybe you should check /etc/sources.list or remove the unnecessary kernel block
in /var/lib/dpkg/status so that apt-cache pkgnames linux-image can
get the downloadable kernel! Then try to run this program again.
Program terminated!!!

can u help me to solve this one!

regards
Nirmalraj D

---

### Post by captinkid on 2008-10-07
> **OfMacandMen said:**
> I solved this by adding the following to my /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-proposed main restricted universe multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-proposed main restricted universe multiverse

Solved the problem.

Thanks!

Matthew Wallace
Encore High School

---

