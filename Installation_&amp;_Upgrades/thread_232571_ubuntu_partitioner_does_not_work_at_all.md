---
title: "ubuntu partitioner does not work at all"
date: 2006-08-08
forum: Installation &amp; Upgrades
---

### Post by talledega500 on 2006-08-08
Having installed almost every major  flavor of linux in a dual boot scenario with windows going back 7 years, I am shocked at the partitioner in Ubuntu on the standard and alternate install image.

It simply **does not work** in a windows dual boot situation.  ***_Dont try it or you will be sorry_***.  If you are a masochist and you have part magic + other recovery tools and you just dont care that much about your windows installation then go for it you will have a great time biting your nails and...

You will screw up your disks. 

Someone show me the option in either ubuntu install that lets you choose what partition to install to.  Also when you get caught in the partitioner loop which you will on the GUI or the dossy if you are attempting to dual boot windows tell me what you did (besides give up or use another tool to undo what ubuntu did).

Even if you dont touch your primary partition and only mess with partitions you create away from your windows partition, the partitioner will (if you are stupid enough to give it the chance), stomp your master boot record and make your windows part unbootable.

If thats **ALL** that happens to you then you are lucky as even experienced linux geeks who have much more experience than me have run into the exact same problems or worse and had to do serious system recovery in dual boot windows scenarios to get their systems back.

I wouldnt care enough about this distro to even report it as a bug since no other distro from mandrake to knoppix to redhat to suse to debian... **to anything** has ever choked so easily in so many different ways on my box or all of my linux experienced friends boxes on plain jane windows boxes.

Also forget manual partitioning...**use most contiguous free space will screw you even harder**.

forget it guys.  Fix it or forget it.  This partitioner is broken, it sucks and your pretty gui is irrelevant. Im not buying a dedicated box for your slick GUI when you are ***_7 years behind the pack in install_***.

---

### Post by hopstah on 2006-08-08
wow, so angry.  this completely contradicts my experience.  > 
Someone show me the option in either ubuntu install that lets you choose what partition to install to. 
choose to manually edit the partition table, and then assign whichever partition you want ubuntu to be installed on to be mounted as root (/).

honestly, i didn't read any further in your post than that, because it shows a lack of effort on your part, and you sound all too excited to rant.

---

### Post by talledega500 on 2006-08-08
R-i-g-h-t.  Thats why everyone I know who did the same thing ended up using part magic or something else to recover their primary windows part.

---

### Post by talledega500 on 2006-08-08
Ah the ones who install on empty disks or dont have problems teach us so00000 much since it didnt happen to them when it can be reproduced on multiple machines with nothing special on them.  As if the install wizard is beyond all of us who have done linux 10 times over

---

### Post by talledega500 on 2006-08-08
I didnt have problems installing Windows 95 either by the way

---

### Post by talledega500 on 2006-08-08
> **hopstah said:**
> wow, so angry.  this completely contradicts my experience.  
choose to manually edit the partition table, and then assign whichever partition you want ubuntu to be installed on to be mounted as root (/).

honestly, i didn't read any further in your post than that, because it shows a lack of effort on your part, and you sound all too excited to rant.

Saying something does not work is not an expression of anger.

---

### Post by hopstah on 2006-08-08
> **talledega500 said:**
> Saying something does not work is not an expression of anger.

no, but the periodic statements in bold, as well as the blanket statements that it "does not work at all", "will screw up your discs", and that it "sucks" sure convey anger.

---

### Post by talledega500 on 2006-08-09
> **hopstah said:**
> no, but the periodic statements in bold, as well as the blanket statements that it "does not work at all", "will screw up your discs", and that it "sucks" sure convey anger.

Sorry for the italics and the bold.  I should have instead listed all the articles in this forum about partitioning probs and then list itself might be considered "anger".

My kids routinely say this sux and that doesnt work and my friends tried it too.  Its not anger its a fact. 

I hope anger doesnt get in the way of it being fixed.  Because its broken.  

Thats "broken" in minitext, unbolded, un-underlined so the extremely sensitive people responsible can feel good enough about themselves to fix it and so you can feel good enough about yourself to admit it might not work in alot of scenarios.

---

### Post by talledega500 on 2006-08-09
> **hopstah said:**
> no, but the periodic statements in bold, as well as the blanket statements that it "does not work at all", "will screw up your discs", and that it "sucks" sure convey anger.

And what is the word for "broken" in an african dialect that also means "togetherness" and "your system wont boot"?

---

### Post by hopstah on 2006-08-09
maybe i was off-base with angry, but bitter is definitely coming mind....

---

### Post by -deadcats on 2006-08-09
Hmm. Works for me, no problem. Must not be your lucky day.

regards,
-dc

---

### Post by talledega500 on 2006-08-09
> **hopstah said:**
> maybe i was off-base with angry, but bitter is definitely coming mind....

I dont care if you think Im angry.  but dont dismiss what is an obvious problem that should be fixed which affects alot of people by saying it didnt **happen to me** and your *JUST *angry and dont know how to install linux.  

I clearly made the case that I do and I have and that Im not the only one I know affected who have superior skills to myself.

If you cant count high enough to find all the partitioner issues on this forum and others then so can the ubuntu team.  Its time to fix it.

Sometimes **emphasis** gets attention to something which would be all too politely discussed as "user issues" and this is a distro issue.  Im looking for some remedy before I touch dapper with a ten foot pole and Im not the only one.

---

### Post by skirkpatrick on 2006-08-09
I think you've obviously mistaken a forum for an IRC channel.  11 posts and most of them are yours, some not even being more than a minute or two apart.

I am wondering, since you pointed out how many partitioning problems appear in the forums, just how many people have had no problems and didn't likewise post that they were successful.  Must have been only 2 or 3 of us.

I just love how people come into the forums and post some nonsense about how "This is so screwed up, I am a demigod when it comes to computers/Linux, and the developers have obviously made such a bad program that nobody in the thousands or tens of thousands of people who attempted to use it succeeded".

I have installed Dapper on 2 WinXP laptops turning them into dual-boot machines, 1 desktop with two drives for a dual-boot (swapped drives so Linux is the primary), 1 desktop with two drives for a dual-boot (WinXP drive is the primary), and 2 desktops with fresh harddrives and no dual-boot and never ran into a partitioning problem, even when having to resize a Windows partition.  Obviously, I do not know what I am talking about and I bow to your superior wisdom, Oh might computer guru!

PS
I probably won't check this topic again for several hours so be sure to leave me about 20 posts, quoting each sentence I have just typed.
:-({|=

---

### Post by hopstah on 2006-08-09
ohhhhhh - snap!!!1one

---

### Post by unisol on 2006-08-09
why dont you try the alternate installcd or with the livecd opt for installing in text mode the partitioner is much simpler to use good luck

---

### Post by Snowmayne on 2006-08-09
Throughout all your commenting, the only thing you really said was that the partioner was 'broken', not ubuntu. I'd just like to point out that the partition app is based on gparted, so if you have any beef about it, take it up with them.

---

### Post by talledega500 on 2006-08-10
I beieve I said I tried the alt install

And if I am so off base why are there something like 20 new posts today about how he partitioner does not work and has put people in a corner?

I dont have to list the links just look at the fresh meat.  

Its the same as yesterday and the day before.

---

### Post by unisol on 2006-08-10
there is a version of ubuntu, ubuntu 606.1 which you can get at linuxcd.org for a small fee or you can download it from ubuntu site the updated version has over 300 fixes including the installer why dont you give it a try

---

### Post by djheadley on 2006-08-10
Right now I'm running a triple boot system: WinME, Ubuntu 5.10, and Ubuntu 6.06.  I had NO trouble with the partitioner and I "split" one partition into 2 for the 6.06 install.  Yes, I have used Ubuntu since 4.10 but that doesn't make any difference since the installer is new to 6.06.  Instead of geating angry, why don't you just ask for help?

BTW, my machine is now a P4 with 256M RAM and 2-40G hard drives and both a cdrw and dvd drives.

---

### Post by djheadley on 2006-08-10
Oops, 512mb Ram.

---

