---
title: "Dual boot installation problem (Vista Installed first)"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by love_gnu on 2008-09-12
Hi Friends,

       This is my first post to this forum. So i am not sure where to post problem regarding installation. At last I am posting here.

  Yesterday I bought Sony vaio- SR90S, 32-bit, SATA drive, intel centrino 2(Vista loaded).But I am dying to install ubuntu on it. As I am really a newbie to linux I ve no idea how to handle this. Please need help.

I shrink the the original partion of Vista. So now almost 100Gb is absolute free with no partition. 

I follwed the steps from this URL
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3)


My problem is i m trying to install Ubuntu (8.04) with dual boot( vista installed first ). But It goes well at the time of boot up until selecting language , then after clicking install Ubuntu, then it process for some time the screen goes black/dark nothing happens after that . Also I checked the CD with the Ubuntu option [ to check the CD for defects] , it detects no error.

I tried Fedora-7 it goes well no problem in installation . 
Also I tried with another Ubuntu Live CD it shows which I got from Ubuntu . it displays me the following error.
 
```
 
[!!]Detect and mount CD-ROM
No common CD-ROM drive was detected.

You may need to load additional CD-ROM drivers....

```



Please help me to get it work.

Regards,
Prady

---

### Post by ubuuntu9897 on 2008-09-12
must be missing cd rom drivers then:(

---

### Post by love_gnu on 2008-09-12
> **ubuuntu9897 said:**
> must be missing cd rom drivers then:(

If CD ROM drive is missing then how does the first screen comes i.e, the the installation screen. And as I told no problem in installing Fedora-7.

Also I checked the Ubuntu CD with the inbuilt option it gives me no error. Only it hangs in the time of installation.

The live CD is of version 5.10 , I think its too old thats why its not detecting my dvd rom driver.

I want to send to some screen shots too but did not get any options here.

Regards,
prady

---

### Post by zvacet on 2008-09-13
>  I think its too old thats why its not detecting my dvd rom driver.

It looks like you detected your problem.Another reason not to install 5.10 is because it is unsupported.Download Hardy and try with it.It should work.Good luck!

---

### Post by love_gnu on 2008-09-18
> **zvacet said:**
> It looks like you detected your problem.Another reason not to install 5.10 is because it is unsupported.Download Hardy and try with it.It should work.Good luck!

Thanks for your reply zvacet. Nope Dear, I ve not yet find any solution to this.

First of all I downloaded Ubuntu 8.0 (Hardy). It goes well upto selection of language then the main screen [B]"UBUNTU"
[/B] comes then it hangs , displays nothing.As I said earlier.

  Thats why I tried the older version of Live Ubuntu 5.10 which I am having earlier,(Its works in IBM thinkpad). Here it won't detect the dvd driver also.

Regards,
Prady

---

### Post by skozzy on 2008-09-18
Backup your drive before you push it with installs. Or make sure you have a recovery cd ready.

The CD-Rom interface is probably SATA not IDE, in my minimal experiance with Ubuntu and my computers at home Ubuntu and SATA don't mix to well. I can only get Ubuntu 7.10 to work with the SATA devices I have, I can't get Ubuntu 8.04 to detect SATA at all.

Check if your bios has Legacy support (IE: Visable in DOS as a drive), I enabled that to get at least part of my computer visable with Ubuntu. Even though that option is mostly for USB, but I think some SATA is based on the same chips for USB2.0

---

### Post by Sef on 2008-09-18
1) When using the Live CD (not installing) are there any problems?

2) Did you use Vista's partitioner to shrink the Vista partition?

---

### Post by love_gnu on 2008-09-18
> **Sef said:**
> 1) When using the Live CD (not installing) are there any problems?

2) Did you use Vista's partitioner to shrink the Vista partition?

*1)* Live CD is also giving me the same problem..

  I burnt Another CD ( thinking the previous burnt CD might be corrupted ), but it also gives me the   same problem.
First it show me Loading Linux Kernel , then it goes to Ubuntu window with the scroll bar moving..Then after sometime the blank screen comes. Then it hangs...

*2)* Yes, I shrinked the the original partion of Vista using the following instruction .

[http:////apcmag.com/how_to_dualboot_vi...rst.htm?page=3]("http:////apcmag.com/how_to_dualboot_vi...rst.htm?page=3")

So now almost 100Gb is absolute free with no partition.

I guess partition is not a problem , as I told earlier I can install fedora -7 with no problem..


Regarding SATA/IDE , if I changed the it IDE is it a problem to vista..If so my warrenty will be void. As SONY only recommends Vista..Anyway How to change my cdrom Driver to IDE ?

Regards,
pradyu

---

### Post by love_gnu on 2008-09-21
> **love_gnu said:**
> *1)* Live CD is also giving me the same problem..

  I burnt Another CD ( thinking the previous burnt CD might be corrupted ), but it also gives me the   same problem.
First it show me Loading Linux Kernel , then it goes to Ubuntu window with the scroll bar moving..Then after sometime the blank screen comes. Then it hangs...

*2)* Yes, I shrinked the the original partion of Vista using the following instruction .

[http:////apcmag.com/how_to_dualboot_vi...rst.htm?page=3]("http:////apcmag.com/how_to_dualboot_vi...rst.htm?page=3")

So now almost 100Gb is absolute free with no partition.

I guess partition is not a problem , as I told earlier I can install fedora -7 with no problem..


Regarding SATA/IDE , if I changed the it IDE is it a problem to vista..If so my warrenty will be void. As SONY only recommends Vista..Anyway How to change my cdrom Driver to IDE ?

Regards,
pradyu

Dear Friends,

   I tried my best to install to explore ubuntu in my sony vaio notebook. But still can't figure out what exactly the problem is.

   I burnt twice (one CD & one DVD) And tried it from now USB stick using wubi & another tool UNetbootin tool.

They all seem to be the same problem as in CD/DVD,
i.e, After selecting language.
Then it shows loding linux kernel(100%)..Then the main install screen comes ,i.e the scroll bar moving in the screen(left to right<->right to left ). Then it hangs..

For a newbie like me, It really painful. 

Atlast I installed Vmware and now I am running it live.

Again When I tried to install(ubuntu) that to my hard drive(vmware Ubuntu) it goes well but at 96% it hangs(searching for packages).

Now I almost out..Please need ur helps.

Regards,
Prady

---

