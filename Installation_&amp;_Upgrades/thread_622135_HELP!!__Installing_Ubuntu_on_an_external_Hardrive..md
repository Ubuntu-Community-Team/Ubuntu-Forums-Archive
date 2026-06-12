---
title: "HELP!!  Installing Ubuntu on an external Hardrive."
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by Khaor on 2007-11-24
Hi everyone! First of all I would like to say that I ran Ubuntu out of the cd and WOW I am amazed!!

I am 19 years old and ive been my whole life a Windows user but to no ones amazement I am sick and tired of it and want a change.

I would like for someone to please tell me how to install ubuntu correctly on my external hardrive (WD 160GB).

	](*,)I already installed it in that hardrive but in another computer but there seems to be something wrong because it doesent boot with ubuntu, it always boots with XP even when I select to boot from the external drive.

I would apreaciate i someone could help me ASAP, it will be well apreciated!

---

### Post by adramalech on 2008-01-21
I am trying to do the same thing with the 320gb one too:lolflag:...

***THIS MIGHT WORK ON YOUR WD 160GB***

i believe that you would have to first use a partitioner to partition space on the external hard drive...using this partitioner which will detect your wd 160gb [ http://www.sysresccd.org/Main_Page ]( http://www.sysresccd.org/Main_Page ) 

you then will take boot rescuecd from cd or dvd to partition your space...then you can use some options to be able to make it bootable...

when you put in the ubuntu install cd....you will have the option while the external hd is on and connected to the computer be able to select the partion u created on your external....then from there it is a matter of tweaking your system to use the external to boot ubuntu from it....

***HERE IS SOME LINKS TO OTHER PAGES THAT SHOULD WORK ON INSTALL AND GETTING THE BIOS BOOT WORKING***

[ http://ubuntuforums.org/showthread.php?t=80811 ]( http://ubuntuforums.org/showthread.php?t=80811 )

NOTE: the reason I say to partion before install, i know that it comes with a partitioner but it is difficult to not erase the whole thing if u have info on there u want else just install on whole thing using the guided install...


:guitar:

good luck! and post your results so I can see if it helps...

---

### Post by dreblen on 2008-01-21
I too have wanted to install ubuntu on an external drive, this is my ubuntu answers post,
[https://answers.launchpad.net/ubuntu/+question/15421](https://answers.launchpad.net/ubuntu/+question/15421)
I successfully installed both ubuntu and kubuntu on my drive, and the above link might help you,
also note the pendrivelinux part, which might be what you want if you want to use your drive on multiple computers

---

### Post by louieb on 2008-01-21
[COLOR=Red]**Caution: **[COLOR=Black]The guides are good. Pay attention to what they say about installing the boot loader GRUB. If you accept  the default of installing the GRUB pointer  to the MBR of the hard drive you will have to have the external drive pluged  in every time you reboot.   [/COLOR][/COLOR]

---

