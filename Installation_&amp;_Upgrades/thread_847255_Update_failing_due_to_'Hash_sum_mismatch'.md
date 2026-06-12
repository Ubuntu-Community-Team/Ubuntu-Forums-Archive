---
title: "Update failing due to 'Hash sum mismatch'"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by Vyoma on 2008-07-02
I have been trying to get my Ubuntu to run the update manager. All other packages seem to go fine, except for two of these:

> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-2.6.24-19-generic_2.6.24.13-19.44_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-2.6.24-19-generic_2.6.24.13-19.44_i386.deb)
  Hash Sum mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx_96.43.05+2.6.24.13-19.44_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx_96.43.05+2.6.24.13-19.44_i386.deb)
  Hash Sum mismatch




I tried switching between US Servers and Main Servers but the results are identical.

Any thoughts?

---

### Post by cll2001 on 2008-07-02
I have been having the same problem this morning. Up until about 20 min. ago. The update servers might just be busy.

---

### Post by VOLKOV9 on 2009-07-19
I am also having a hash sum mismatch for Cairo dock on hardy, amd64.

There are several dead ends to be found on this forum and google.  Apparently for some people, switching servers in system>administration>softwaresources to main helped.  For me, US and main have the same error.

---

### Post by LinkedITS on 2009-12-16
I had the same exact problem. I tried Ubuntu, Mint 7, Mint 8 and every single time I would get the Hash Sum Mismatch Error when I try to install anything. Because I spent so much time searching for the answer to my problem, I am going to try to post this anywhere I see someone having problems with Hash Sum Mismatch.

But after seeing breaker's post (he mentions the problem might be with bad RAM), I realize it could be a problem with my RAM because I remember that my machine used to have Windows 7 OS on it and it failed to install anything because it kept getting corrupt files error. Originally I thought the problem was because my computer was unable to support Windows 7. But one of the symptoms of bad RAM is having corrupt files and bad disk. Another symptom is having distorted graphics on the web pages which i notice was another problem I had. 

My computer had ordered a couple of the same computer, so I did a test and installed Mint 8 on a computer of the same model. I was able to install everything I wanted on the new computer without any of the Hash Sum Mismatch errors.

So that led me to conclude that I kept getting the Hash Sum Mismatch errors because i had a bad RAM. (OR at the very least it is a hardware problem isolated to that specific computer). I am going to change the memory in my problematic computer and see if that fixes the problem. I'll post an update within the week with the results.

---

### Post by LinkedITS on 2009-12-16
As I mentioned in a earlier post, the Hash Sum Mismatch might be caused by bad RAM so i devised a experiment to test out my Hypothesis. In the "experiment" that I performed, I took the RAM out of the "Good Machine" and put it into the "Bad Machine." Then I booted into the "Bad Machine with the Good RAM" and tried to install the ntp package. However the installation failed with Hash Sum Mismatch once again. 

Then I put the "Bad RAM" into the "Good Machine" and booted into it. The "Good Machine with the Bad RAM" was able to install properly without any problems at all.

This leads me to the conclusion that the problem is NOT the RAM. I hypothesize that the problem, although not with the RAM, is still related with the memory in some way. I will continue to look into this and post any updates I have.

---

### Post by wcorey on 2010-04-04
While your last post was some time ago, I have had this problem for a few weeks now and on multiple machines. One of them did have Windows 7 on it. I, too, checked memory...just in case. and it tested fine. Memory on one machine would not cause an issue with another machine. A problem with the ISP would cause ALL TCP traffic to die as there are checksums there as well. I, too, tried multiple sources, and all of them fail. I, too, tried apt-get clean and clean all etc, and still not a clean update mgr run or apt-get run. So did you give up or did you resolve this or did it clear up on its own?

---

### Post by gtandon on 2013-01-24
Got the same error when I was trying to install apxs (sudo apt-get install apache2-threaded-dev). Fixed it by adding the following mirrors in the sources list: [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/)

Steps are:
1. Add the following line all the way at the bottom in /etc/apt/sources.list
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) precise main

2. update packages
sudo apt-get update

3. Now try whatever you were trying!

BTW, my ubuntu is running on a VM :: Linux ubuntu 3.2.0-23-generic x86_64

Hope this helps.

Thanks,
GT

---

### Post by oldos2er on 2013-01-24
Old thread closed.

---

