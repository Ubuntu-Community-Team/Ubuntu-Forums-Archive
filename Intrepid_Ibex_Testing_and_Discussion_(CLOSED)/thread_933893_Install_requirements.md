---
title: "Install requirements"
date: 2008-09-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by solitaire on 2008-09-29
What are the requirements for the "LiveCD" install?

I'm currently have an old Dell Inspiron 8200 with
P4m (2Ghz)
512Mb Ram
16Mb Video
120Gb Disk

I'm trying to install the latest Alpha 3 build (Desktop) but when i run the "Install to Disk" (Think that's the option name.) it runs through the basic install then drops to: 
```

Ubuntu@Ubuntu:~$

```
I think it's an issue with available ram when running the install using the LiveCD.

Anyone know the requirements for the LiveCD?

*Note* 
LiveCD session runs ok (excessive CD thrashing though!)
Install in the LiveCD using Ubiquity fails when trying to start the partition software (known issue:  [Bug# 226187]("https://bugs.launchpad.net/ubuntu/+source/parted/+bug/226187"))

I'll D/L latest build of the latest Alternate Disk and try that.

---

### Post by alphacrucis2 on 2008-09-29
> **solitaire said:**
> What are the requirements for the "LiveCD" install?

I'm currently have an old Dell Inspiron 8200 with
P4m (2Ghz)
512Mb Ram
16Mb Video
120Gb Disk

I'm trying to install the latest Alpha 3 build (Desktop) but when i run the "Install to Disk" (Think that's the option name.) it runs through the basic install then drops to: 
```

Ubuntu@Ubuntu:~$

```
I think it's an issue with available ram when running the install using the LiveCD.

Anyone know the requirements for the LiveCD?

*Note* 
LiveCD session runs ok (excessive CD thrashing though!)
Install in the LiveCD using Ubiquity fails when trying to start the partition software (known issue:  [Bug# 226187]("https://bugs.launchpad.net/ubuntu/+source/parted/+bug/226187"))

I'll D/L latest build of the latest Alternate Disk and try that.

Not sure of the minimum requirements but I installed 8.10 alpha 4 on a 256mb PIII machine with no problems. What was happenning immediately prior to dropping to the prompt? Any other messages.  BTW alpha 6 is the latest with the 1st beta about to appear.

---

### Post by perlluver on 2008-09-29
The recommended memory, is 320MB, so your memory is fine, could be your video, or the disk.  The first beta will be Oct. 5th, with release on Oct. 30th.

---

### Post by solitaire on 2008-09-29
Thanx for the replys.

@ [alphacrucis2]("http://ubuntuforums.org/member.php?u=648132")

If i remember correctly the top of the screen has "Starting Install" (or something like it) then the screen is filled with a welcome message of some sort, It does not look like an error message! then it has the "Ubuntu@Ubuntu:" user logged in at the bottom. (I'll have to grab a screen shot with a camera) I get a "no avalible space" message when i try to install things using "sudo apt-get" at this point. 

This is why i was thinking it's a memory issue if it's using a ram disk for the inital install....
 (Inspiration just hit me!) OR an issue with the partition manager failing! The partition manager under LiveCD session fails aswell!. see   [Bug# 226187]("https://bugs.launchpad.net/ubuntu/+source/parted/+bug/226187")

@ [perlluver]("http://ubuntuforums.org/member.php?u=395609")
I may wait for the Beta release later this week. But I'll try they Alternative install disk sometime today.

---

### Post by solitaire on 2008-09-30
*Update*

Woo :D

Downloaded the latest LiveCD alpha build.

Ran the install and it worked i'm currently typing form 8.10 Alpha :)

So far so good. only issue is with my ancient nVidia card in this laptop not liking the restricted drivers. but default drivers work fine!

---

