---
title: "Install hangs at &quot;configuring apt&quot;"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by renzokuken on 2005-10-15
im having some seriously irritating problems installing Breezy.

im trying to set up a dual boot (with XP). XP is installed on my SATA harddrive and i created a new partition on my SATA drive using PartitionMagic. put the ubuntu cd in and rebooted. install starts of fine until i reach the point of the installation which says

"Configuring APT - setting up primary instalation repos"
(just after u choose username and password)

it always (i mean always!!) hangs at 25% completion of this stage.

ive tried both amd64 and i386 of ubuntu (and kubuntu) hoary and breezy and they all do the same.....i even tried to install it on one of my IDE storage harddrives but no luck

i'm installing on a box with :

AMD64 3500+
Asus A8V deluxe
1 x SATA drive with XP
2 x IDE drive used for storage

i just installed ubuntu successfully on one of my old computers with no problems whatsoever......why doesnt it work on this computer though???

please help.......

would it make a difference that im creating partitions with partitionmagic in XP and not using the Ubuntu partitioning tool to resize the disk?

---

### Post by drew_t on 2005-10-15
I'm having the same problem.

I had a working dual-boot XP/Hoary system, Athlon XP2400+, one IDE hard drive.  The last time I updated the Hoary, the X11 file somehow got messed up, and also the Windows entry (once again) disappeared from the GRUB screen.  Since Breezy just came out, I opted to not bother trying to fix the Hoary installation, and instead to just install Breezy from a CD.

I used the partitioner in the Breezy installation disc to delete the two linux-related partitions, and selected the "automatic" option to set up the two new partitions in the newly-freed space.

As the poster above reports, the installation gets to the 25% stage of "configuring apt . . . setting up primary intallation repository" and stops cold.

Any help would be appreciated.

---

### Post by alainhenry on 2005-10-16
I got that too, but tried again a few hours later (i.e. an hour ago) and everything went fine.  I'd assume it's the servers that are busy, I mean overloaded with install demands.  

Alain

---

### Post by renzokuken on 2005-10-16
so its actually connecting to the net at this stage of the install........

so if i did an offline install (chose to configure the DHCP at a later date in one of the earlier options) it might work

thanks......

perhaps thats why it installed fine on my other computer cos that wasnt connected to the router

---

### Post by tymek666 on 2005-10-16
The same problem here, but i stuck at 50%. The same was yesterday, the same is today. I've tried at different hours, without positive results :(

---

### Post by alainhenry on 2005-10-16
I was doing a CD install, what you'd call an offline install I assume.  At some point, the install process connects to configure apt, default repositories, etc.  That's where it hangs as far as i understand.  

Maybe it uses your location to select a default server, and lucky me :smile: , the Belgian one is not that busy?  This is a pure assumption from my part, I actually do not know what install does.  ;) 

Alain

[QUOTE=renzokuken]so its actually connecting to the net at this stage of the install........

so if i did an offline install (chose to configure the DHCP at a later date in one of the earlier options) it might work

thanks......

perhaps thats why it installed fine on my other computer cos that wasnt connected to the router[/QUOTE]

---

### Post by drew_t on 2005-10-16
The thing is, it just ***dies.***  The CD stops, there is no hard drive activity, there are no error messages or other dialogue, and the system is unresponsive to any keyboard inputs other than Ctrl-Alt-Delete.  I can't believe they would have intentionally written the installer to just stop dead in its tracks if it can't connect to a server.

---

### Post by renzokuken on 2005-10-16
yep, i have exactly the same problem as u then drew

a mystery

---

### Post by alainhenry on 2005-10-17
I agree when it stops, everything stops.  Only reboot will work.  :confused:

---

### Post by dmallery on 2005-10-17
more of the same:

i had the exact problem... 25% "setting up primary installation repository"
then hard hang.

so i removed the ethernet pcmcia card.  no outside world.

started over and got the SAME problem.

any more ideas??

machine is a latitude CPx.
thanks

dave mallery

---

### Post by renzokuken on 2005-10-17
ok.....that was gonna be my next step, fortunately u saved me the trouble dmallery

can i ask....how did u all burn ur installation CDs?

---

### Post by dmallery on 2005-10-17
hi

probably time to repeat the download...

i use cdrecord on command line.

dave

---

### Post by renzokuken on 2005-10-17
i used Alcohol in XP.......

just curious really, i'm sure its not the CD cos it installed fine on my old computer.......

where are all the experts who are supposed to be helping us with this?

---

### Post by dmallery on 2005-10-17
i don't know.

i am trying a post to the mailing list.  the x-chat ignored me.

i am zero for three with breezy... have another problem with scsi device names that i have posted to death.

later

dave

---

### Post by renzokuken on 2005-10-18
ok guys......i found this thread in the forum

[http://ubuntuforums.org/showthread.php?t=19408](http://ubuntuforums.org/showthread.php?t=19408)

**quote**

Looks like I found the work around.

I took the Debian installation approach . At the installation boot prompt, I chose 'server' to install bare minimum packages. My installation was successful. When I got the command prompt, I just did following:

# sudo aptitude update
# sudo aptitude install ubuntu-desktop

I am hoping that 'ubuntu-desktop' with its dependencies installed every thing that installation was suppose to install.

I still do not know why regular install failed on apt config
  	
**end quote**

havent tried it yet but gonna give it a go and see what happens in the next day or so

let u know how it goes

---

### Post by james4e on 2005-10-19
Haha. It is very easy to solve it.

You should switch to console by pressing "Ctrl+Alt+F2". Then you can use "ps ax" command to list all the processes and find "http" process. What you should do is kill this proess. 

The next step also is a long time wait. You can solve it in the same way.

---

### Post by renzokuken on 2005-10-19
awesome.....thanks for the answer james.......

i'll have a go tonight if i get time

EDIT: just had a thought, how are we supposed to do "Ctrl+Alt+F2" when the keyboard locks out during the hang/crash

---

### Post by dmallery on 2005-10-19
hi

work-around works.  i am still downloading ubuntu desktop, but i got past the breaking point when configuring apt.

i worked around my other scsi naming problem, filed a bugzilla and now have breezy running on two production machines.  amd64 is next.  breezy is well worth the effort.  audio is great (first time it EVER worked on this machine.)  OO2.0 comes right up.

thanks for your help!  this one needs a bug report too.  will you do it?

dave mallery

---

### Post by renzokuken on 2005-10-19
dave......which workaround worked?....

james' one or the one i found......??????

i'm so happy it worked, tomorrow im getting rid of xandros and getting stuck into some ubuntu action

as for the bug report....if u were asking me if i'd do it (as opposed to james) then yeah mate i will......as long as u tell me how, hehehe !!!! (n00b remember)

>_<

---

### Post by flower on 2005-10-25
check out also this post : 

[http://ubuntuforums.org/showthread.php?t=79963#7](http://ubuntuforums.org/showthread.php?t=79963#7)

---

### Post by Lod on 2005-12-05
[QUOTE=renzokuken]ok guys......i found this thread in the forum

[http://ubuntuforums.org/showthread.php?t=19408](http://ubuntuforums.org/showthread.php?t=19408)

**quote**
# sudo aptitude update
# sudo aptitude install ubuntu-desktop

I am hoping that 'ubuntu-desktop' with its dependencies installed every thing that installation was suppose to install.[/QUOTE]
I had the same problems with my 'new' computer. Strangely enough it worked well last weekend with my first installation. Sunday I decided to change the partioning of my hd and then the troubles started.
I've tried this workaround and it worked. I'm sharing your hope of the 'ubuntu-desktop' being the same.

---

### Post by Lod on 2005-12-09
Small update: I tried to get my tv-card working. As it happens it wasn't even recognized by Ubuntu. So I opened my case and it appears that the card wasn't inserted correctly in it's slot. After I fixed it I decided to reinstall Ubuntu and this time it didn't hang on configuring apt.
I'm not sure if it is related to each other but who knows :)

---

### Post by 484 on 2008-01-07
I recently tried to install "Gutsy Gibbon" (Ubuntu v 7.10 I think) and I had a similar problem, but it hangs at 82 per cent (configure APT) the italic text says "examining mirror..." I think. I decided to install Ubuntu after receiving a new motherboard, RAM, and Processor as a Christmas present. The installation went fine, but I decided to reinstall my OSes (XP and Gutsy) in order to partition my hard disks better. The first time I installed I used one 40 Gb Maxtor HDD, this second time I attempted to install Windows on the 40 Gb drive, and Ubuntu on a 20 Gb drive connected to a RAID card (3ware's Escalade 6410). Linux recognized the new HDD (as well as another 4 Gb HDD) as being SCSI drives, and I assumed there wouldn't be any problems, however the installation hung at 82 per cent of "Configuring APT." I tried different configurations of HDDs, such as connecting the HDD I wanted Ubuntu installed on directly to my IDE as a master, but it still hung at 82 per cent.
If the other posts here are any indication, the problem is that I had an active internet connection the first time I installed Ubuntu, but currently the Ethernet ports in my dorm room are down. I shall try to install again later, and I will let you guys know how it goes.

Ironically I am trying to use Ubuntu so that my computer will be kosher with Valparaiso's network without having to download all of the windows updates, naturally this is irrelevant if the network is down anyway...:lolflag:

---

### Post by Partyboi2 on 2008-01-07
> **484 said:**
> I recently tried to install "Gutsy Gibbon" (Ubuntu v 7.10 I think) and I had a similar problem, but it hangs at 82 per cent (configure APT) the italic text says "examining mirror..." I think. I decided to install Ubuntu after receiving a new motherboard, RAM, and Processor as a Christmas present. The installation went fine, but I decided to reinstall my OSes (XP and Gutsy) in order to partition my hard disks better. The first time I installed I used one 40 Gb Maxtor HDD, this second time I attempted to install Windows on the 40 Gb drive, and Ubuntu on a 20 Gb drive connected to a RAID card (3ware's Escalade 6410). Linux recognized the new HDD (as well as another 4 Gb HDD) as being SCSI drives, and I assumed there wouldn't be any problems, however the installation hung at 82 per cent of "Configuring APT." I tried different configurations of HDDs, such as connecting the HDD I wanted Ubuntu installed on directly to my IDE as a master, but it still hung at 82 per cent.
If the other posts here are any indication, the problem is that I had an active internet connection the first time I installed Ubuntu, but currently the Ethernet ports in my dorm room are down. I shall try to install again later, and I will let you guys know how it goes.

Ironically I am trying to use Ubuntu so that my computer will be kosher with Valparaiso's network without having to download all of the windows updates, naturally this is irrelevant if the network is down anyway...:lolflag:
when it stops at 82% leave it for 15-20 mins eventually it should time out and continue to install. This has worked for me in the past.
Just means that when it has finished installing you will need to enable some repo's that it was not able to verify.
To do that you would on you new install go to 'Software Sources" (System>Admin>Software Sources) on the first tab (Ubuntu Software) tick all of them except "Source Code" and then click on the 3rd tab (updates) and tick the first 2 then close.

---

### Post by Gsus on 2008-02-07
Just popped in to say thanks for this forum post, I thought waiting would be sufficient but killing the process as recommended by **flower** did the job.

(By the way my test machine is on a closed network so cannot access the repo)

---

### Post by FutureIsLinux on 2008-03-11
to bypass this you simply disconnected your computer from the internet, it 'freezes' because its trying to download ubuntu security updates. You will get an error, but it won't hurt your computer, simply run an update when you get into ubuntu as some of the security updates are important.

---

### Post by PmDematagoda on 2008-03-11
This thread is very old and I see no point in trying to revive it.

This thread is closed.

---

