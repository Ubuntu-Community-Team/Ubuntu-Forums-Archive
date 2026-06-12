---
title: "Need help &quot;Forcing&quot; Ubuntu 12.04 LTS to Newest build"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by datfireflyfan on 2012-05-22
I am trying to get my current build from 12.04 LTS i386 to either the newest build (don't necessarily need LTS, not a business application) or 12.04 LTS in the amd64 flavor.  

Let me explain, I downloaded the "recommended" version back on version 11.10, even though i had a 64-bit board and processor, with >4GB ram.  i would like to get to amd64 without reloading the machine if possible.  not sure what upgrade path to take.  

i have some knowledge of terminal commands, however step by step instructions would be best.  If this upgrade is not possible, and i have to re-image the machine than so be it, but i had just gotten my stuff installed and cozy here, and would prefer to update the moving bits while leaving file structures intact.  

maybe this can't be done, but i thought i would check with people first.

---

### Post by jmore9 on 2012-05-22
12.04 LTS means long term support.  The next " newest " version will be 12.10 which is under development now.  The 12.04 LTS goes for i think i may be wrong but about 5 or 6 years of support,  thats why called LTS.

My own experience is if i want to get to 64bit i always have to do a reinstall.  Never been able to change the 32bit to 64bit .

Hope that helps a little.

---

### Post by fantab on 2012-05-22
> **datfireflyfan said:**
> 
Let me explain, I downloaded the "recommended" version back on version 11.10, even though i had a 64-bit board and processor, with >4GB ram.  i would like to get to amd64 without reloading the machine if possible.  not sure what upgrade path to take.  


You can't. You have do a clean install of 64bit version.

---

### Post by jadtech on 2012-05-22
here is something few realize if you  set up a ubuntuone account and go to system setting  click back up make a full back up that store on ubuntu one  and you have a google account and use chrome web browser even if you didnt set up a home partition once you reinstall you can run back up  from ubuntu one and it will restore any configuration  you will have to reinstall programs and updates frist but your config file photos documents music will all be restored  if you use chrome  all you bookmarks and even account user names and passwords that you store will be down load  with the new browser ..

you are really not going to notice any difference using 64bit amd  over the 32bit it will be the same ram  and from reading its is even the same shared library because they choose to use the 32bit lib files  for ubuntu 12.04 64bit so that  things are more interchangeable ..

unless your computer will hold globs more ram you plan on installing  it will make no difference   its a 5 year lts support ask your self will you even still have the same machine 5 years from now or will would you most likely be getting something new between then and starting over any way ..

---

### Post by jocko on 2012-05-23
> **jadtech said:**
> here is something few realize if you  set up a ubuntuone account and go to system setting  click back up make a full back up that store on ubuntu one  and you have a google account and use chrome web browser even if you didnt set up a home partition once you reinstall you can run back up  from ubuntu one and it will restore any configuration  you will have to reinstall programs and updates frist but your config file photos documents music will all be restored  if you use chrome  all you bookmarks and even account user names and passwords that you store will be down load  with the new browser ..

you are really not going to notice any difference using 64bit amd  over the 32bit it will be the same ram  and from reading its is even the same shared library because they choose to use the 32bit lib files  for ubuntu 12.04 64bit so that  things are more interchangeable ..

unless your computer will hold globs more ram you plan on installing  it will make no difference   its a 5 year lts support ask your self will you even still have the same machine 5 years from now or will would you most likely be getting something new between then and starting over any way ..

You are right that 32 bit ubuntu with a pae kernel is able to use all of the datfireflyfan's ram, but that does NOT mean he gets all the other benefits of 64 bit.
For web browsing and other simple tasks there may be no noticeable difference, but for more demanding things [64 bit easily outperforms 32 bit in almost all cases]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1"). And [memory >4Gb is slower with a 32bit pae kernel]("https://help.ubuntu.com/community/32bit_and_64bit#Memory") compared to a 64 bit kernel.
So please don't say datfireflyfan won't notice the difference. It depends completely on what datfireflyfan does with his computer.
It's NOT true that 32 bit and 64 bit uses the same shared libs. On 64 bit ubuntu every 64 bit process uses native 64 bit libs, but in addition it is also possible to install 32 bit applications that uses separate 32 bit libs.

---

