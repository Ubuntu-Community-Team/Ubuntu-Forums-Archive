---
title: "I want to install in my 64bit PC the Kubuntu 9.04 64bit"
date: 2009-03-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lse123 on 2009-03-22
I want to install in my 64bit PC (vista 64bit one partition + vista 32bit anather partition) Kubuntu 9.04 64bit when get released the full dvd version ... Well when it will be released the full version exactly in April ? I must install to 64 bit partition ? There are Linux software runs **only **with Kubuntu(I mean Linux) 32bit ? May install alone , is it easy , I am web developer/designer ? I must first find install STEPS (Where?) print them, and follow them STEP-BY-STEP ? I have a textbook about "Fedora & XP ISBN:978-1-4188-3725-9 /E:05/19/2006" from course.com, STEPS to install kubuntu are similar to fedora ?

---

### Post by 3Miro on 2009-03-22
Kubuntu 8.10 is somewhat unstable, so 9.04 is a good choice.

Linux uses at least 2 partitions, one for swap and one for data. Make two partitions (you can do that from under windows) make one at least the size of your ram (if you have <1GB of ram make it bigger) and one at least 15GB. Then point the small partition for the swap (i.e. make it swap) and the other one /. If you can, it is better to have another partition for /home, but it the hard drive is too small keep them just two (/home if it exists should be much bigger than /, /home is where most of your data would be).

Any Linux 32-bit app works under Linux 64-bit, the only exceptions are the drivers.

Ubuntu install is the easiest of all that I have seen. It is no harder than Windows, if you understand partitions, then it is trivial If not, then you might run into some trouble).

---

### Post by cariboo on 2009-03-22
Jaunty will be released April 26th, see the [thread=971232] Release schedule[/thread]. All software is available for both 32-bit and 64-bit, the software is located in the repositories.

The installation if you use the LiveCD/DVD consists of 7 steps, and is pretty self evident, just follow the instructions.

Jim

---

### Post by lse123 on 2009-03-22
steps installing/make-partitions of kubuntu 64bit are similar to fedora ?

---

### Post by cariboo on 2009-03-23
Ubuntu has created their own installer called ubiquity, I'm not sure how the Fedora installer works.

Partitioning is the same no matter what OS you are using, there are just different gui interfaces.

Jim

---

### Post by lse123 on 2009-03-23
after make the partitions installing/setting up/configure kubuntu 64bit , is it easy ?
where find the step for print, to follow ?

---

### Post by 3Miro on 2009-03-23
> **lse123 said:**
> after make the partitions installing/setting up/configure kubuntu 64bit , is it easy ?
where find the step for print, to follow ?

8.10 came with KDE 4.1 and that was somewhat unstable. I had to follow the instructions on the kubuntu web-page to get KDE 4.2. Other than that, there is no need for complicated setup, adjust the menus and effects the way you want them, but that is straight forward. (well hardware drivers might have to be installed, just follow the instructions in the hardware manager)

---

### Post by ken78724 on 2009-03-23
This be a discussion thread, let me ask a question.

I run U8.04.1 AMD64. What are benefits of Kubuntu 9.04 64bit & assuming there are good ones, will Kubuntu 9.04 64bit do a direct upgrade without risking docs created by U8.04.1 in the same partition where the update would be made? :popcorn:

---

### Post by 3Miro on 2009-03-23
> **ken78724 said:**
> This be a discussion thread, let me ask a question.

I run U8.04.1 AMD64. What are benefits of Kubuntu 9.04 64bit & assuming there are good ones, will Kubuntu 9.04 64bit do a direct upgrade without risking docs created by U8.04.1 in the same partition where the update would be made? :popcorn:

I would recommend a clean install, if possible. The KDE benefits (for me) are smoother effects (with kwin) and generally more customizable desktop. Also, media programs like Kaffein and Ktorrent run better under KDE (Gnome doesn't quite have the same analogs, you can do the same things, but not in the same way)

---

### Post by Tony_photoplus on 2009-03-23
I uninstalled Kubuntu 64 bit the other day.  Collapsed within the hour and it is very unstable.  So we wait until stability and software stabalise.  I am having probs with most things, I only had the comp a week and its going to be a year or so before I see the benefits of using the 64bit

Tony

---

### Post by lse123 on 2009-03-28
I have a textbook about "Fedora & XP ISBN:978-1-4188-3725-9 /E:05/19/2006" from course.com, STEPS to install&setup kubuntu 64bit 9.04, are _similar_ to fedora ? Or there are big changes ?

---

### Post by lse123 on 2009-03-28
fedora core 4 redhat

---

### Post by ken78724 on 2009-03-28
permit me to break in with a related Ubuntu 8.10 desktop 64AMD live CD install question

> **lse123 said:**
> I want to install in my 64bit PC (vista 64bit one partition + vista 32bit anather partition) Kubuntu 9.04 64bit when get released the full dvd version ... Well when it will be released the full version exactly in April ? I must install to 64 bit partition ? There are Linux software runs **only **with Kubuntu(I mean Linux) 32bit ? May install alone , is it easy , I am web developer/designer ? I must first find install STEPS (Where?) print them, and follow them STEP-BY-STEP ? I have a textbook about "Fedora & XP ISBN:978-1-4188-3725-9 /E:05/19/2006" from course.com,
 
 Please guide me on this.
  am amidst manual 8.10 install to dev/sda3 ext 3 having 8.1 giB and
271.56 mb used on gparted 750 Maxtor HD/ have five partition. Yes, I
have backed up data made with ubuntu 8.04.2 found in
dev/sda1 Ext 3     62.5 giB with 16.8 Gib used
fdev/sda2 extended with 2.85 GiB unused
dev/sda3 ext 3 having 8.1 giB with 271.56 mb used
dev/sda4 jfs       625.4  giB with zero used
dev/sda5 linux swap with 2.81 GiB unused

tried this from live CD install, going to the loader and specifying
want to load only to dev/sda3 ext 3 but stopped after being prompted
to designate dev/sda3 ext where I could verify the 8.1 giB was there.
Immediately it scanned the partition and then it asked "Designate a
mount point and gave me a drop down menu with 6 options. in first
trial, I selected /opt and message said "you cannot do this"; so I
backed up and I selected another option and got the "you can't do
this" so I backed up and set it to "/" and the installer automatically
reset the selected gpart to I believe dev/sda1 jfs 8.1 giB and fore
warmed me that I would write over and delete data & program files in
all partitions; 

so, I packed my bag so I could learn a correct selection which won't delete/lose the U 8.04.2 OS &/or data files on the gparted 62 gig as noted above. 

Clarifying? what manual install decisions should I executive. :popcorn:

---

### Post by ken78724 on 2009-03-29
> **3Miro said:**
> I would recommend a clean install, if possible. The KDE benefits (for me) are smoother effects (with kwin) and generally more customizable desktop. Also, media programs like Kaffein and Ktorrent run better under KDE (Gnome doesn't quite have the same analogs, you can do the same things, but not in the same way)

immense loses would arise... please review/respond to the new thread under my name... need your help.... ended up blocking use of Ubuntu 8.04.2 which I need so I can keep working... :(:confused:

---

### Post by ken78724 on 2009-04-10
> **3Miro said:**
> I would recommend a clean install, if possible. The KDE benefits (for me) are smoother effects (with kwin) and generally more customizable desktop. Also, media programs like Kaffein and Ktorrent run better under KDE (Gnome doesn't quite have the same analogs, you can do the same things, but not in the same way)

thanks 3Miro! have been swamped. so, I'll wait for the Apr 26th release or longer so I can do a clean install. under pressure it's not feasible for one working alone on many tasks. ;)

---

### Post by PGHammer on 2009-04-13
> **Tony_photoplus said:**
> I uninstalled Kubuntu 64 bit the other day.  Collapsed within the hour and it is very unstable.  So we wait until stability and software stabalise.  I am having probs with most things, I only had the comp a week and its going to be a year or so before I see the benefits of using the 64bit

Tony

If you were running Kubuntu 8.10, I can see the issues, as KDE 4.1 had its share of pain-causers.  Kubuntu in 9.04 is a much better-behaved environment all around (that's what I'm entering this from, in 64-bit Wubi flavor, while Amarok is playing  the "Fire Engine" (Farenheit 451) from the Bernard Herrmann Film Scores (Los Angeles Philharmonic, Esa Salonen conducting) 2 CD set converted to MP3 on my Windows partition).

---

### Post by dasme on 2009-04-13
> **Tony_photoplus said:**
> I uninstalled Kubuntu 64 bit the other day.  Collapsed within the hour and it is very unstable.  So we wait until stability and software stabalise.  I am having probs with most things, I only had the comp a week and its going to be a year or so before I see the benefits of using the 64bit

Tony

I am also using Kubuntu 9,04 64bit from the day it was released as beta without any problems. ;)

and IMO it's the most stable Linux Distro. :)

---

### Post by SpreadFirefox on 2009-04-21
I have upgraded Kubuntu 8.10 32 bit to Kubuntu 9.04 in the office. At home I have 64 bit station and there is no update available neither via update-notifier or Adept. Should I wait until official release?

---

