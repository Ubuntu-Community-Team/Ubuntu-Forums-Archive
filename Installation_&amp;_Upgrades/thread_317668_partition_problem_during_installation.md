---
title: "partition problem during installation"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by atarileaf on 2006-12-12
Hello all. So I've gotten a little further on my installation journey. My current problem is now that I can't seem to get Ubuntu to create a partition.

Using this site: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I followed the instructions and since I'm a newbie, I chose the first method for resizing and partitioning my drive automatically. I have an 80 gig drive with just a shade under 40 of that used by Windows XP. I want to set up a dual boot with about 20-30 gig for Ubuntu.

I've tried using the slider, which gives me a minimum of 39.7 gig at 55%, but after 4 tries using different precenteges from the minimum to the maximum and a couple spots in between including the default of 77%, I keep getting an error that Ubuntu can't create the free space (not sure of the exact wording of the error message). 

Again since I'm a newbie I don't want to try the manual option. Too confusing. Am I missing something? This should be easy right? Tell the computer how much space for windows and ubuntu and away it goes?



Before I did any of this, I did a defrag and error check on my drive. Everything is fine.

---

### Post by atarileaf on 2006-12-13
Nobody knows or should I be asking this in the newbie forum? :???: 

Sorry, I'm still pretty new here and am not sure which questions should be asked where.

---

### Post by HoTseChu on 2006-12-13
I got the same problem trying to install Ubuntu on a laptop. I couldn´t resize the unique partition in it, I don´t know why still. I tried also with Gparted CD, but it didn´t work.
Finally, I remove win totally and install only Ubuntu. Sorry, I know this is not a solution, but I don´t know if you are using a laptop. In that case, perhaps in the forum of "Hardware & laptops" you could find something more useful than my answer.

---

### Post by atarileaf on 2006-12-13
Thanks for the reply. I am using a desktop machine though, not a laptop. I'm just not comfortable manually partitioning my machine. If I had two computers, I'd just install Ubuntu on the second but I only have the one and don't want to lose Windows until I know that I can do everything I currently do with Ubuntu.

How would it work if I used a second hard drive for Ubuntu? Could I format it and use it just for Ubuntu? If so, how would that work with the boot process?

I wonder if there's a website detailing the installation of Ubuntu to a secondary drive?

---

### Post by unisol on 2006-12-13
maybe you should try to boot in safe graphics mode it is a text-mode installation i found partitioning eaiser for novices. give it a try.

---

### Post by HoTseChu on 2006-12-13
If you have two hard disks in your desktop, I think that in "step 6 of 7" of the installation should appear both hard disks, I mean, at least two options like:

Erase entire disks: IDE1 ...
Erase entire disks: IDE2 ...

and then, of course, choose the correct one :p  (Check the size, for example). 

Don´t be afraid if you fail, the "step 7 of 7" confirms before install.:cool:

---

### Post by atarileaf on 2006-12-13
> **HoTseChu said:**
> If you have two hard disks in your desktop, I think that in "step 6 of 7" of the installation should appear both hard disks, I mean, at least two options like:

Erase entire disks: IDE1 ...
Erase entire disks: IDE2 ...

and then, of course, choose the correct one :p  (Check the size, for example). 

Don´t be afraid if you fail, the "step 7 of 7" confirms before install.:cool:

Thanks, I'll try that. I have an older 20 gig drive just lying around that I could use. Is 20 gig enough do you think?

---

### Post by HoTseChu on 2006-12-13
I think 20 Gb it's enough. At the end of the installation the hard disk use would be more or less of only 4 Gb.

---

