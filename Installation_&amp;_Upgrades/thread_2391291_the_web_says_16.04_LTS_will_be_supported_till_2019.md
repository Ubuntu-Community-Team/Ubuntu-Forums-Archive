---
title: "the web says 16.04 LTS will be supported till 2019"
date: 2018-05-08
forum: Installation &amp; Upgrades
---

### Post by oneleded on 2018-05-08
i dont believe the web. never the less, if i need my upgrade now, i'd rather do it an be done. i need the command line, to update 16.04, if it need to be done. 16.04 seems to be different than 14.04, as far as update notification's..  just in case,, whats the command line in 16.04 to update to 18.04. i didnt think of this approach till tonight. i'm trying to do this on my own. sometimes it works, sometime it dont.  //ed](*,)

---

### Post by kerry_s on 2018-05-08
make sure you back up & have a live installer ready just incase. 18 uses gnome-shell, while 16 is using unity.
sudo do-release-upgrade

---

### Post by PaulW2U on 2018-05-08
From the [18.04 Release]("https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes") notes:
> Upgrading from Ubuntu 16.04 LTS

Upgrades from 16.04 LTS will not be enabled until a few days after 18.04.1's release expected in late July.

As far as I am aware, you can upgrade to 17.10 now if you are set to display notifications of any new release rather than the next LTS. If you are set to receive notifications of the next LTS release then you will have to wait for the 18.04.1 as the release notes advise.

Using the command line won't make any difference. Install 18.04 now or upgrade in late July.

---

### Post by dino99 on 2018-05-08
If you prefer less trouble, then wait for the first 18.04.1 fix release in a couple weeks.

---

### Post by Impavidus on 2018-05-08
Regular Ubuntu 16.04 is supported until April 2021, but the light flavours, including Lubuntu, are only supported until April 2019. A direct upgrade from 16.04 to 18.04 will be supported from July 2018 or thereabouts, which gives a 9 month window to upgrade.

---

### Post by oneleded on 2018-05-09
i want to say thanks to all of you people for the help. i think i will wait 9 months, to give any bug correction to take place. good advice all around. that also gives me time to do any research, that i've been neglecting.:)
i'll mark this solved. got to restudy that research.

---

### Post by oneleded on 2018-06-18
not quite sure i can wait for update.. anywho.. i been getting a massage, when i log onto 2nd hard drive. /usr/lib/xorg/Xorg,, is causing a problem. it has a bit to do with Uname Linux 4.4.0 -128-generic i686.   i also copied,  i386 = PackageArchitecture in part of the problem. i know im closer, if not, to i386..  32 bit XP, from an age ago. i wonder if lubuntu can get past everything moving up to 64 bit, an T-bytes,  just saying. i might need a 64/32 inverter, for its all over. switching to Linux, not so much.:)  //Ed

---

### Post by mörgæs on 2018-06-18
If you want to know your options we need to know the hardware. Please copy and paste ```
sudo lshw -sanitize > lshw.txt
``` into the terminal, run it and post lshw.txt in CODE tags.

---

### Post by oneleded on 2018-06-20
i haven't for got this. i run a bit slow. i'll get back soon. [ Reply last made] thanks

---

### Post by wildmanne39 on 2018-06-20
Hello oneleded, please do not create duplicate posts.

Thanks!

---

### Post by oneleded on 2018-06-29
> **mörgæs said:**
> If you want to know your options we need to know the hardware. Please copy and paste ```
sudo lshw -sanitize > lshw.txt
``` into the terminal, run it and post lshw.txt in CODE tags.
i did try this. however, i made a copy of this with windows. it translated to, sudo 1shw-sanitize > 1shw.txt.  it took me a bit to get it to work in lubuntu 16.04 LTS on 2nd HD ... then when it did i got a page, with what looked like commands, i couldnt figure out how to record it. a storm was coming in, an i had to revert to my 1st hard drive. when i got back to my 2nd HD with linux,  sudo lshw -sanitize > lshw.txt no longer worked. it did let me log in, cept it got in a cycle after that, where nothing happened, though i didnt have to log in. 
perhaps i should just download 18.04 LTS. i would hate to lose some things, i have on 16.04. i suppose it wouldnt be that great of a loss. 
these older renditions of windows, are failing fast. everything seems to migrate to 64bit. seems the best thing to do. ;~}

---

### Post by oneleded on 2018-06-29
Hello wildmanne39;  thanks for bring this to my attention. hope its in regard to posting on a solved thread. i was trying to post linear, as to keep things in line. if not, would you mind telling me a bit where i messed up. i didnt want to post every problem i have, not related to what i have done so far. 
i think asking a question in a solved thread is what you are referring to, an have wondered about doing that. Keep me informed, if you dont mind.  ed

---

### Post by mörgæs on 2018-06-29
> **oneleded said:**
> i did try this. however, i made a copy of this with windows. it translated to, sudo 1shw-sanitize > 1shw.txt.

Then you didn't copy and paste the command as I suggested but tried to write it. Don't! Copy-paste every time you have the option.


> **oneleded said:**
> then when it did i got a page, with what looked like commands

Then something is wrong. The results should be a text fine describing your hardware.

> **oneleded said:**
> 
these older renditions of windows, are failing fast. everything seems to migrate to 64bit. 

Chances are that you have a 32 bit Windows running on 64 bit capable hardware. The lshw.txt file will tell.

---

### Post by oneleded on 2018-06-30
> **mörgæs said:**
> Then you didn't copy and paste the command as I suggested but tried to write it. Don't! Copy-paste every time you have the option.
i seem to be having a problem with copy and paste. though linux is on my second hard drive, i suspect the mother board i have is 32 bit. PC is dell optiplex 270, an probably made about 2002.
on another thought, 1st, why not just download 18.04 lts, an be done with it. i do have firefox bookmarks, and have a way to save them. 2nd, just a question. when you go from 16.04lts to 18.04lts. does it save any data?
if i got 64bit download, its most likely, i messed up.  i was having trouble with 16.04lts, download, when i put it on disk. i had a copy of 17.04. i upgraded from that to the next LTS version, which was 16.04lts. you might say i downgraded. how i did that, i cant remember, but so i did. appreciate the help i get and then some  //ed

---

### Post by oneleded on 2018-07-01
> **wildmanne39 said:**
> Hello oneleded, please do not create duplicate posts.

Thanks!
i read 'marking threads solved' from your post, and do understand. thanks again.

---

### Post by oneleded on 2018-07-03
> **mörgæs said:**
> Then you didn't copy and paste the command as I suggested but tried to write it. Don't! Copy-paste every time you have the option.




Then something is wrong. The results should be a text fine describing your hardware.



Chances are that you have a 32 bit Windows running on 64 bit capable hardware. The lshw.txt file will tell.
my last post on this thread. what ever i did, when i typed it seemed to render copy-paste ineffective. never after did LXterminal work the way it was supposed to after that including copy-paste. i did learn how to copy-paste. i'm going with a fresh install of 18.04LTS. i appreciate your help. and have but 1 more question. how do you get those 2 dots over the o?, in your name, or the ae stuck together.:)

---

### Post by oneleded on 2018-08-26
> **mörgæs said:**
> If you want to know your options we need to know the hardware. Please copy and paste ```
sudo lshw -sanitize > lshw.txt
``` into the terminal, run it and post lshw.txt in CODE tags.
 for some reason, when i right click. to copy, i get nothing..

---

### Post by oneleded on 2018-08-26
> **oneleded said:**
> i been getting a massage, when i log onto 2nd hard drive. /usr/lib/xorg/Xorg,,..
i have to start a new thread on this problem. however, to copy an past in this thread, dont work..   while i am typing reply, i can copy what i write, with no problem..

---

### Post by oneleded on 2018-09-12
> **dino99 said:**
> If you prefer less trouble, then wait for the first 18.04.1 fix release in a couple weeks.
i still have much to learn from this thread. i decided to go with 18.04.1, after i resolved another issue.  thanks for all the help everyone

---

