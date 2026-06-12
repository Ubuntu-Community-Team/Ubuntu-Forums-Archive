---
title: "problems installing the Ubuntu Desktop Edition"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by red40y on 2010-08-13
[SIZE=2]**[FONT=Arial]im new here and had a question on the installation on the[/FONT]**[/SIZE][SIZE=2][B][FONT=Arial] Ubuntu Desktop Edition. when i go to choose the os to boot from after restart, i choose ubuntu. it says completing install process and stops. it doesn't let me do anything. can some one figure this out for me? 
[/FONT][/B][/SIZE]

---

### Post by mörgæs on 2010-08-14
Hi, welcome to the forum.

> **red40y said:**
>  can some one figure this out for me?

No, not until you give us a detailed description. Which Ubuntu version? Does it run as a live CD? Did you have wired internet access while installing? Which hardware? Especially, which graphics card do you have? Is it a solitude Ubuntu, or is it installed with Wubi?

---

### Post by red40y on 2010-08-17
hello, 
i downloaded the latest version i=of the 64 bit program(figured, 64 bit windows7, 64 bit ubuntu would work.) i have the AMD Turion(tm) II Dual-Core Mobile M500 2.2GHz processor--- 4 gig ram--- AMD M880G with ATI Mobility Radeon HD 4200--- i created a img to disc with Wubi with it aswell. i get all the way to the end of step 3 on the download and install page (After your computer restarts, choose '**Ubuntu'** from the boot menu.) and i get a bunch of lines i dont understand. and it dosnt go any further, so i have to do a hard shutdown.

im using a wireless network with excellent connection to the router. (Verizon fios.)

---

### Post by MrLowEnd on 2010-08-17
I believe we have the same problem. I'm trying to install Ubuntu inside Windows, since I need Windows for school (for compatibility's sake), and run it as an application. When I try to boot it from the boot menu, it gives me a screen with several lines of text, which consist of terms like "child_rip". If someone could help, it'd be awesome.

By the way, I'm using Windows 7 on a system running the same AMD processor. Are you possibly using the Toshiba Satellite L505?

---

### Post by red40y on 2010-08-18
the l505-D. yes. we both have the same problem then, like you said. im hoping i can get this resolved with as little pain as possible, lol.

---

### Post by mörgæs on 2010-08-18
There have been some problems with Toshibas and Ubuntu. I can't give an exact solution, since I have never had a Toshiba, but googling the machine name + Ubuntu (or + Wubi) gives plenty of hits.

Radeon HD also can cause some trouble:
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

Does the machine boot with a 9.10 live CD, 32 bit?

---

### Post by red40y on 2010-08-18
no go with the 32 bit. so far there dosnt look to be any practical solution the the issues im having... im not experienced enough to make the changes that are required to get this particular software to run. for now, it looks like its just going to have to wait for toshiba users. i will keep this in mind the next time i buy a new computer in the future. 
unless someone has a noob solution to the toshiba l505-d problems, im just going to call this quits for now. 

---------------------------------------------------------------------------------------------------------

---

### Post by mörgæs on 2010-08-19
There is some advice here: 
[http://ubuntuforums.org/showthread.php?t=1464170](http://ubuntuforums.org/showthread.php?t=1464170)

Did you have wired internet access while installing? 

In general I guess Dell is a better option for Ubuntu: 
[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

---

### Post by MrLowEnd on 2010-08-19
perhaps using a virtualization program could help. maybe virtual pc 2007, or even virtualbox? i'll try these and see if maybe that will help.

---

### Post by MrLowEnd on 2010-08-19
OK....while using VirtualBox (latest edition) inside Windows 7 Home Premium 64-bit, install was successful. Unless anyone else has a solution, that's the only way to work around this issue. 

By the way, I installed Ubuntu 10.4 Lucid in a 10GB VDI file. It works flawlessly.

---

### Post by mörgæs on 2010-08-20
> **red40y said:**
> . 
unless someone has a noob solution to the toshiba l505-d problems, im just going to call this quits for now. 


I take it that you don't like playing with commands and changing the system too much.

If you want an easy test, you could try another Linux. Just boot as a live CD and see if it works better than Ubuntu.

---

### Post by red40y on 2010-08-20
im giving virtualbox a go real quick, let you know how it goes.

---

### Post by red40y on 2010-08-20
im not qualified enough to be doing anything too complicated. but im learning! its a work in progress. 

i used virtualbox  to boot Ubuntu and install! very nice suggestion. the only issue i see is if someone wanted to run Ubuntu solo with out windows. im happy though. 

i will continue to research the isues with toshibas, one day i want to dump windows!

---

