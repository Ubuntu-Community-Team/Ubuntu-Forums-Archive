---
title: "Help With Installing 6.10 on Windows XP machine."
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by ChocoSnake on 2007-03-22
Hey, 
I really want to get Ubuntu on my machine as my main OS, but I'm pretty much a total newbie on the whole thing. I know one of the basic things I have to do is install Ubuntu on a partition on my HD, but I really don't have that much of an idea how to make one. I'm pretty sure I only have one, or none at all, assuming that multiple partitions would show up as having more than one HD in My Computer. The only thing showing up is Local Disk (C). 

I only have one HD and it's only a 40 gig. Sucks, yes, but I barely manage. Right now there are about 5.12GB free, and I intend to use at least 4.5GB for Linux. 

I already have a burned LiveCD, so that's set. What I really need are step by step, easy to follow instructions that will end up letting me dual-boot Windows XP or Ubuntu.

Some questions I have:
- Is there a way to install Ubuntu Linux on my HD along with Windows XP *and* share the same file system? Basically letting me access all my files that I would normally use on Windows, on Ubuntu.

- Are there chances that I could totally screw the installation/partitioning up that I would have to reformat? Or lose all my files on my HD any other way?

                                    -Thanks a lot.

---

### Post by ffxr on 2007-03-22
5.12GB spare space is really too little space to be messing around resizing partitions..

can't you get your hands on a cheap 2nd hard disk from somewhere..?

---

### Post by ChocoSnake on 2007-03-22
I'm really flat broke, even if I did have a second HD, it'd still be a hassle. I have a cheap Dell Dimension 3000, with really crappy expansion abilities. I don't even have a second bracket for another HD. Along with no PCIx16 or AGP slots, and no SATA ports, ha.

---

### Post by shavenlunatic on 2007-03-22
well, i'd suggest one of these

1) Delete half your windows crap and have a 20/20 split

2) Ditch windows completely, its the way forward :)

---

### Post by ffxr on 2007-03-22
ok; if i was in your situation, 

i would do something like this:

delete as much of your C: drive as possible.. 
use CCleaner as well to clear any other unnecessary crap offa it
defrag your C: drive a few times
partition the drive with a decent tool in xp.. like partition magic..
-> create 4gb ext3 partition for ubuntu
-> create 256mb linux-swap partition

then install into these partitions from the ubuntu cd.

the ubuntu install should  automatically create a dual boot option for you


[no disk partioning tool is 100% reliable btw]

---

### Post by adewale on 2007-03-22
i also have  a similar problem, i had ubuntu and windows on my pc so now i removed ubuntu  using gnome partitoning hoping that i will be able to reinstall. then i tried rebooting and it said grub error so then i tried reinstalling and all went well till it reached 86% and said failed to install grub to /target. plz what can i do i need to use my pc urgently

---

### Post by ffxr on 2007-03-22
adewale, if u have an xp disk, boot of that.. then select recover and inspect boot enviroment.. 

also i think there is another way to fix it by issuing a dos command to restore the normal windows boot order something like fix /mbr .. i cant remember it the exact command tbh..

also maybe u shouldve started a new thread for ur issue.. looks like ChocoSnake could do with a few more general tips tbh...

---

### Post by adewale on 2007-03-22
thanks i just started a new thread but no reply yet. isn't there a way i can install ubuntu and still have windows back grub should be aable to find it

---

### Post by upbeat.linux on 2007-03-22
Fixmbr:

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

Recovering MBA:

[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

---

### Post by upbeat.linux on 2007-03-22
ChocoSnake, as for your request I'd recommend clearing up all the unnecessary apps and files that currently reside on your Windows partition. Clear your cache and temporary internet items for all browsers you use in Windows XP.  

Next, find a good hosted disk space service similar to:

[http://www.box.net/home/2/](http://www.box.net/home/2/)

[http://www.xdrive.com/](http://www.xdrive.com/)

[http://storage.vmn.net/](http://storage.vmn.net/)

[http://www.mediamax.com/](http://www.mediamax.com/)

You'll have to read the FAQ's and EULA's.  Upload/download access might be capped. For instance, some services offer 5GB of space; you can fill that to capacity, but you may only be able to access 1 GB of data at a time.

If you have a friend at a university or who owns there own web server see if you can SSH or FTP some of your file up there in the interim. Or you can just burn a DVD or CD of all necessary files. Backups never hurt.

After this is complete run a system scan and then the defrag utility.  This will prep your drive partitioning and the Ubuntu install.

After installing Ubuntu get rid of all the fluff. Go through Synaptic and permanently remove/delete everything you don't need or aren't willing to use. This will give you a better idea of what Ubuntu has to offer and what you can plan to use once you have the disk space.

Happy brewing...

---

### Post by ChocoSnake on 2007-03-22
I've got a 30GB iPod, I think I'll use that for backups.

---

### Post by shavenlunatic on 2007-03-29
> **ChocoSnake said:**
> I've got a 30GB iPod, I think I'll use that for backups.

sell that, buy a sensibly priced mp3 player and use the remains to upgrade ya pc :)

---

### Post by ahlandberg on 2007-04-05
Hi!

I want to install Ubuntu 6.10 on my computer on which I have Win XP running at the moment.

I have two partitions, 50GB each. One of the partitions has got Win XP on it, the other one just my user data.

I have the following questions:

1. Can I simply install Ubuntu 6.10 on the machine and it will be okay with Win XP (I still wanna use Win XP, too)?

2. When installing Ubuntu 6.10, will I have the option of creating an additional partition or should I rather clean up my current second partition and use that for Ubuntu 6.10?

Thanks for all help!!

Anders

---

### Post by junkman on 2007-04-09
> **ChocoSnake said:**
> I'm really flat broke, even if I did have a second HD, it'd still be a hassle. I have a cheap Dell Dimension 3000, with really crappy expansion abilities. I don't even have a second bracket for another HD. Along with no PCIx16 or AGP slots, and no SATA ports, ha.

This is for everyone, especially if in this situation. 
[www.wholesaleauction.com](www.wholesaleauction.com)
It is a part of [www.evertek.com](www.evertek.com), which is for wholesale dealers only. The auction part is more limited, (In quanities and such) but does not have the same minimum dollar amount for orders, and does not require a resellers liscense, (IE: The general public can use it)
I have been using both parts for years. They are very good at what they do, but are no non-sense types. (If you can't/won't pay instantly, forget it, they have ZERO tollerance for that sort of thing!) 
You get what they say you will get, no more, no less. You will have to set up your account to get started, but the prices absolutly can not be beat, anywhere. (Unless you have a rich friend who loves giving away his/her "old" stuff!) 
BTW: I have NO connection with Evertek, or any subsidaries, beyond that as stated, a customer of some years. (I own First PC, LTD., a not-for profit group that refurbs old, used, or donated computers to give to disabled Vets. Price is EVERYTHING)
It pays to check the site often, as inventory changes almost daily. Auctions now run for much shorter times than they used to. you can find almost anything you might need, if you are paitent. They have a wide range of stuff at any one time, (We use a lot of older equipment, such as PIII's even, gasp. yes, PII's K6's, and so on) And they have a limited supply of such things as well. Example: A PIII (pull, or used, even new) 850mhz flipchip might go for 5 dollars! Now, you can laugh at that, sure, but it's plenty to get some poor bloke stuck in a wheelchair, who's been stairing out the window like some potted plant, onto the WWW via dialup. Which is our focus. 
As for hard drives, a 80 gig brand name "refurb" (IE: Cleared of all data, tested, and packaged up) can go for as little as $20.00 USD, depending. Depending on what? Type, (IDE, vs Sata, spindle speed, cache, etc) and how many on on offer, and how many people happen to be wanting one (or a dozen) that particular day. Point is, if you are willing to do a little bit of work, you CAN have a bigger hard drive for very little money, skip a movie and popcorn, and you CAN afford one! 
Hope this helps someone. (I have mixed emotions about sharing this, as more competitors in bidding are bad for us, but the UBUNTU motive in me wins out) Use this info wisely, don't be spreading it around to greedy types, and post your successe(s) for others to see, I wasn't pulling your leg.  
BYW, I have a TON to learn about all things Linux flavoured. I have UBUNTU 6.10 running dual boot on an WinXP machine, and, other than not being able to 'see' the one partition from the other, (either way, from Win to Unbuntu, or Unbuntu to Win) and not being able to use my dialup connection, (All I have, all I can get here in this rural area) I love it. My KIDS love it, and I am a believer now. I got my disk out of a magazine. (Downloading a full CD worth over dialup never works, I tried, a few bits always go missing somewhere along the way. And, tieing up the phone line for 6 hours isn't cool either) 
If anyone can tell me how to get the blanking ^&(*$# modem working, ANY modem (other than cable or dsl)  I would be very grateful! (I know about the 14.4 driver for conextant chipset modems. That is just not going to work for us) 
Keep the faith:
Junkman

---

### Post by junkman on 2007-04-09
> **ChocoSnake said:**
> I'm really flat broke, even if I did have a second HD, it'd still be a hassle. I have a cheap Dell Dimension 3000, with really crappy expansion abilities. I don't even have a second bracket for another HD. Along with no PCIx16 or AGP slots, and no SATA ports, ha.

This is for everyone, especially if in this situation. 
[www.wholesaleauction.com](www.wholesaleauction.com)
It is a part of [www.evertek.com](www.evertek.com), which is for wholesale dealers only. The auction part is more limited, (In quanities and such) but does not have the same minimum dollar amount for orders, and does not require a resellers liscense, (IE: The general public can use it)
I have been using both parts for years. They are very good at what they do, but are no non-sense types. (If you can't/won't pay instantly, forget it, they have ZERO tollerance for that sort of thing!) 
You get what they say you will get, no more, no less. You will have to set up your account to get started, but the prices absolutly can not be beat, anywhere. (Unless you have a rich friend who loves giving away his/her "old" stuff!) 
BTW: I have NO connection with Evertek, or any subsidaries, beyond that as stated, a customer of some years. (I own First PC, LTD., a not-for profit group that refurbs old, used, or donated computers to give to disabled Vets. Price is EVERYTHING)
It pays to check the site often, as inventory changes almost daily. Auctions now run for much shorter times than they used to. you can find almost anything you might need, if you are paitent. They have a wide range of stuff at any one time, (We use a lot of older equipment, such as PIII's even, gasp. yes, PII's K6's, and so on) And they have a limited supply of such things as well. Example: A PIII (pull, or used, even new) 850mhz flipchip might go for 5 dollars! Now, you can laugh at that, sure, but it's plenty to get some poor bloke stuck in a wheelchair, who's been stairing out the window like some potted plant, onto the WWW via dialup. Which is our focus. 
As for hard drives, a 80 gig brand name "refurb" (IE: Cleared of all data, tested, and packaged up) can go for as little as $20.00 USD, depending. Depending on what? Type, (IDE, vs Sata, spindle speed, cache, etc) and how many on on offer, and how many people happen to be wanting one (or a dozen) that particular day. Point is, if you are willing to do a little bit of work, you CAN have a bigger hard drive for very little money, skip a movie and popcorn, and you CAN afford one! 
Hope this helps someone. (I have mixed emotions about sharing this, as more competitors in bidding are bad for us, but the UBUNTU motive in me wins out) Use this info wisely, don't be spreading it around to greedy types, and post your successe(s) for others to see, I wasn't pulling your leg.  
BYW, I have a TON to learn about all things Linux flavoured. I have UBUNTU 6.10 running dual boot on an WinXP machine, and, other than not being able to 'see' the one partition from the other, (either way, from Win to Unbuntu, or Unbuntu to Win) and not being able to use my dialup connection, (All I have, all I can get here in this rural area) I love it. My KIDS love it, and I am a believer now. I got my disk out of a magazine. (Downloading a full CD worth over dialup never works, I tried, a few bits always go missing somewhere along the way. And, tieing up the phone line for 6 hours isn't cool either) 
If anyone can tell me how to get the blanking ^&(*$# modem working, ANY modem (other than cable or dsl)  I would be very grateful! (I know about the 14.4 driver for conextant chipset modems. That is just not going to work for us) 
Keep the faith:
Junkman

---

