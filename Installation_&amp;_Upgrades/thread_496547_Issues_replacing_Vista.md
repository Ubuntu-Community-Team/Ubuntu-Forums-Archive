---
title: "Issues replacing Vista"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by taffy-nay on 2007-07-09
I wonder if anybody could help me with this at all.

About two months ago I bought a shiny new Vaio laptop. The down side of this laptop is that it came with Vista Home Premium pre-installed. Before I continue I would like to make it clear that I am NOT a Windows "basher". I moan because I was forced to buy it. 

I have been happily using Vista since I bought the Laptop, however I'm not prepared to put up with the annoyances of the OS anymore.

I have decided to install Ubuntu 7.04 after trying out the live CD and being rather impressed buy the fact that everything JUST WORKED (especially the 3D desktop and Wierless).

The issue I am having is that, during the install process, the Migration Assistant doesn't seem to pick up the files and settings from Vista. Is this a known Issue. If so, are there any sucessfull solutions?

I also do not wish to delete the recovery partition for Vista seeing has how I have paid the money for it after all.


In an ideal scenario, I would like to have Ubuntu installed as the only OS on the machine, with others in VM's if needed. All my current media inplace and view/listenable. And the Vista recovery partition intact, in case I sell the Laptop on.

I would appreciate any help at all. Although, please bare in mind that I am NOT a technical user.

---

### Post by Gremlinzzz on 2007-07-09
Sounds like you would like to dual boot vista with ubuntu. If so in vista click start right click computer choose manage from the list.Then choose disk manager .then right click the window that shows your c drive choose shrink volume make the partition at least 15gbs or more.then right click the partition you made and delete it making it free space.shut down put your live ubuntu cd in when desktop appears click install follow directions.when it gets to the partition part choose largest countinous free space .thats it ubuntu does the rest.

---

### Post by Gremlinzzz on 2007-07-09
If you want to clean your hard drive completely i always use this program.
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)
:guitar:

---

### Post by stchman on 2007-07-09
> **taffy-nay said:**
> I wonder if anybody could help me with this at all.

About two months ago I bought a shiny new Vaio laptop. The down side of this laptop is that it came with Vista Home Premium pre-installed. Before I continue I would like to make it clear that I am NOT a Windows "basher". I moan because I was forced to buy it. 

I have been happily using Vista since I bought the Laptop, however I'm not prepared to put up with the annoyances of the OS anymore.

I have decided to install Ubuntu 7.04 after trying out the live CD and being rather impressed buy the fact that everything JUST WORKED (especially the 3D desktop and Wierless).

The issue I am having is that, during the install process, the Migration Assistant doesn't seem to pick up the files and settings from Vista. Is this a known Issue. If so, are there any sucessfull solutions?

I also do not wish to delete the recovery partition for Vista seeing has how I have paid the money for it after all.


In an ideal scenario, I would like to have Ubuntu installed as the only OS on the machine, with others in VM's if needed. All my current media inplace and view/listenable. And the Vista recovery partition intact, in case I sell the Laptop on.

I would appreciate any help at all. Although, please bare in mind that I am NOT a technical user.

The migration assistant seems to be hit or miss.

As far as "I paid for Vista", about $25 of the total PC cost is Vista.  Unless you have specific Windows apps ro play games there is not much of a need for Vista.

---

### Post by Firemage1026 on 2007-07-09
I want to know if the Vista Partition Recovery Drive is really that important?? What exactly does it do? I have a HP Pavilion with Vista that I just recently purchased. I tried to install Ubunutu on it and had it crash on me so I want to know if setting up another partition will fix the problem?

---

### Post by Mark Phelps on 2007-07-09
Welcome to the Linux forums -- you ask a simple question about Windows, and you get a bunch of comments about how you don't "need" it, and how Ubuntu is great, etc.

I'm new to Linux myself, struggling with migrating over from years of Windows work (including Vista).  I've found these forums to generally be very helpful -- you just have to get by the usual load of MS-sucks and other such useless garbage.

So, back ON TOPIC, I would be very surprised if the migration assistant did a really great job, especially with Vista.  An alternative would be to install without using it, then load your Windows partition read-only, and see what you can copy over and re-create in Linux.  This link has some instructions for doing a "manual" migration by loading your Windows partition after installation.  Perhaps this will help a bit:

[http://ubuntuforums.org/showthread.php?t=420477](http://ubuntuforums.org/showthread.php?t=420477)

---

### Post by stchman on 2007-07-09
> **Firemage1026 said:**
> I want to know if the Vista Partition Recovery Drive is really that important?? What exactly does it do? I have a HP Pavilion with Vista that I just recently purchased. I tried to install Ubunutu on it and had it crash on me so I want to know if setting up another partition will fix the problem?

The Visa recovery partition on your laptop is for just that recovery.  If you hose your system you can launch the software for partition recovery and turn your OS back to the day when you first turned it on.

---

### Post by stchman on 2007-07-09
> **Mark Phelps said:**
> Welcome to the Linux forums -- you ask a simple question about Windows, and you get a bunch of comments about how you don't "need" it, and how Ubuntu is great, etc.

I'm new to Linux myself, struggling with migrating over from years of Windows work (including Vista).  I've found these forums to generally be very helpful -- you just have to get by the usual load of MS-sucks and other such useless garbage.

So, back ON TOPIC, I would be very surprised if the migration assistant did a really great job, especially with Vista.  An alternative would be to install without using it, then load your Windows partition read-only, and see what you can copy over and re-create in Linux.  This link has some instructions for doing a "manual" migration by loading your Windows partition after installation.  Perhaps this will help a bit:

[http://ubuntuforums.org/showthread.php?t=420477](http://ubuntuforums.org/showthread.php?t=420477)

Do people go on to Windows forums asking questions about Ubuntu?  Probably not, they would get a bunch of I don't know, Linux sucks, Linux is for geeks comments.

---

### Post by Gremlinzzz on 2007-07-09
No big deal just dual boot see which system you like best and use it. i find myself using ubuntu most.I still keep vista but mostly as a game emulator.

---

### Post by taffy-nay on 2007-07-09
Thanks for all you help everyone.

As it stands, I have 10Gig spare on my laptop which I can partition off for Ubuntu as a TEMPORY dual boot.

My ultimate goal is to switch TOTALLY to Ubuntu and have a Windows install in a virtual machine only (I work for a comany that produces propriatory software which is dependant on a perticular Windows protocol)

If I install on said 10Gig partition, could I essentially "Bleed" the two partitions together over time? I'm aware that might not make sense, but it's the only way I can think to verbalise what I mean.

---

### Post by ozPATT on 2007-08-14
Gremlinzzz, I just used the DBAN thing on my dads computer as he is having trouble installing ubuntu, and was happy for everything to be wiped. I am wondering now though, how do I get ubuntu on it? When I start teh computer, the screen is just blank now, so I guess DBAN did its job? But when I put the ubuntu disc in and boot, it still doesnt do anything. Any ideas? 

Thanks

Patrick

---

### Post by limoral on 2007-08-15
I also have the problem as you. 

I wanna buy a new lap computer and I am in China. As you know, all the lap computers in sale in China are all been installed Vista.

Therefore, I also wanna clean my new future computer, and I need some suggestion indeed.:popcorn:

---

### Post by ozPATT on 2007-08-15
well i got it displaying again, I removed the battery and then put it back in and started it,and the bios started happening again. 

i then tried to install linux but keep getting a tty error. so i have re-installed vista to try and get the dual boot thing happening, but it will only allow me to shrink the drive by less than 10 Mb... 

So no joy on any front at the moment. The dban thing didnt seem to work at all. i tried 2 different versions, and both errored out immediately. 

Cant be that hard to install over vista, can it?

Patrick

---

