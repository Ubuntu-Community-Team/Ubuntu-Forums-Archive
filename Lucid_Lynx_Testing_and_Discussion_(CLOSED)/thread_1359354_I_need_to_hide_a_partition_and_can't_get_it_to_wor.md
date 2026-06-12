---
title: "I need to hide a partition and can't get it to work"
date: 2009-12-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-12-19
I installed CentOS on my test platform.  Now I want an install of A1 that will be converted to Lxde as I can't get the Lubuntu installer to work right.

So, with the great migration assistant instead of an install page asking if you want to migrate anything, it decided to get stuff from Cent for some reason.  Can't handle it for some reason (ext3?).

I figure "hide the sucker" as I have heard you can do this.  So I look at gparted and there is the flag manager.  Tried to do this from the LiveCD.  Click on "hidden" and the box goes grey and then comes back with the box unchecked.  Hit close and it goes through the reading stuff and there is no new flag.  Tried this mounted and unmounted.  No joy at all.

So I boot to Karmic on my internal and try it from there.  Same deal.

So, I boot to Jaunty on my other internal and try it from there.  Same deal.

What is a poor boy to do?

---

### Post by phillw on 2009-12-19
> **ranch hand said:**
> I installed CentOS on my test platform.  Now I want an install of A1 that will be converted to Lxde as I can't get the Lubuntu installer to work right.

So, with the great migration assistant instead of an install page asking if you want to migrate anything, it decided to get stuff from Cent for some reason.  Can't handle it for some reason (ext3?).

I figure "hide the sucker" as I have heard you can do this.  So I look at gparted and there is the flag manager.  Tried to do this from the LiveCD.  Click on "hidden" and the box goes grey and then comes back with the box unchecked.  Hit close and it goes through the reading stuff and there is no new flag.  Tried this mounted and unmounted.  No joy at all.

So I boot to Karmic on my internal and try it from there.  Same deal.

So, I boot to Jaunty on my other internal and try it from there.  Same deal.

What is a poor boy to do?

No idea on CentOS or hiding partitions, but this boy, did this for 9.10

>  				 				**LXDE + ubuntu** 			
 			 			 		   		 		 		I heard that in 9.10 there will be a Lubuntu (Ubuntu with LXDE on it), but currently I have it installed... and to say that it was nice is an understatement. It feels just like KDE, but without its bloatedness, and I seldom hear the fan even rev up on my virtualBox installation on my laptop. Everything is... smooth, simply say.

So, I'd go for 10.04, and stick lxde onto it.

I'm not sure how the upgrade scripts from 9.10 --> 10.04 is going just yet - I seem to recall you tried it & it borked on you.

There's a 9.10 with lxde on it over here --> [http://www.linuxquestions.org/questions/linux-general-1/script-driven-ubuntu-9.10-builds-featuring-e17-svn-and-lxde-ready-for-download-776855/#post3797857](http://www.linuxquestions.org/questions/linux-general-1/script-driven-ubuntu-9.10-builds-featuring-e17-svn-and-lxde-ready-for-download-776855/#post3797857)

As the wiki for lxde is timing out on my system, I can't go have a look (read as 'play') with it.

REgards,

Phill.

---

### Post by ranch hand on 2009-12-19
It is the 10.04A1 (or yesterdays daily) that I am not being able to install because of "migration assistant" insisting on "migrating" my information from CentOS an it can't.

I am thinking that I may need to just format the Cent partitions and install right there.  They are bigger anyway.  I think I may have to hold off on trying CentOS.  My son told me I should try it.  And I will but not on this drive anyway.

I am not fond of this "improvement" in the installer at all.  Saves one page and one or two (at the most) clicks.  It also fails.

I get a message that the information could not be "all migrated but installation will continue".  Then the installer just disappears from the screen a few second after you click OK.

Really sucks.

Lubuntu is not ready to be excepted by Ubuntu as an official offshoot like Xubuntu or Kubuntu.  That is the goal.  The Lubuntu 9.10 was what I tried to install first but it didn't work.  The installer on the CD (from sept 8 so well before 9.10 was released - latest CD) is buggy.

You have to run "sudo ubiquity" to get it to load in the first place.  It failed for me at the 88% point.  I may try installing it again after getting rid of CentOS, that may have something to do with it.

I am on the Lubuntu "team" so I can get the list.  All I am skilled enough to do is testing and it bugs me that I can't do that as I have had one problem or another with the CD.

There are only a couple of developers involved and they have to have a pretty nice OS to be approved by Ubuntu.  May happen for 10.04.  I am sure that if not it will by 10.10.

The LiveCD works very well and looks great, except the installer.  We really do need another CD released.

---

### Post by Shazaam on 2009-12-19
From the documentation it looks like the SuperGrubDisk can hide partitions.

---

### Post by ranch hand on 2009-12-19
I will look into that.

Thanks.

---

### Post by phillw on 2009-12-19
> **Shazaam said:**
> From the documentation it looks like the SuperGrubDisk can hide partitions.

Doesn't support Grub2 ?

> Hi,I have released Auto Super Grub Disk 1.9 alternate which it is only available at mirror #0.Auto Super Grub Disk is a windows application that lets you recover your Grub boot (Grub legacy not Grub2, i.e. it does not work for Ubuntu Karmic Koala ...


Phill.

---

### Post by Shazaam on 2009-12-19
Yeah, *sigh* after reading up on it it seems that hide/unhide isn't implemented in grub2 yet like it was in grub-legacy so SGD2 won't have it either.

---

### Post by ronacc on 2009-12-19
must be a regression in yesterdays daily . When I installed 10.04A1 it allowed me not to "migrate" anything .

---

### Post by phillw on 2009-12-19
> **ronacc said:**
> must be a regression in yesterdays daily . When I installed 10.04A1 it allowed me not to "migrate" anything .

I only have the RC for A1 to go back to, if I need to do a re-install.... So far, only one re-install, and that wasn't 10.04's fault.

I've not been putting the dailys onto my system - just the updates (NOT the  partial ones).

Phill.

---

### Post by ranch hand on 2009-12-19
SGD would not work for what I need.  That only hides the partition from grub not a partitioning tool.

I installed 10.04A over CentOS.

It was interesting in that I had the page for migration back when Cent was not there.  The only RH based OS I have found that plays nice with other Linux OS' is Mandriva.  The rest you have to watch like a hawk or in this case, they just mess with the poor computers head.

I am going to mark this solved.

Cent can wait and be the last thing installed somewhere else, someday.  At this point I am in no hurry.

Thanks for the support and tips.  I still want to knowhow you get gparted to give you a "hidden" flag but that is just for educational purposes now.

---

### Post by Gemu on 2010-01-08
> **ranch hand said:**
> SGD would not work for what I need.  That only hides the partition from grub not a partitioning tool.

I installed 10.04A over CentOS.

It was interesting in that I had the page for migration back when Cent was not there.  The only RH based OS I have found that plays nice with other Linux OS' is Mandriva.  The rest you have to watch like a hawk or in this case, they just mess with the poor computers head.

I am going to mark this solved.

Cent can wait and be the last thing installed somewhere else, someday.  At this point I am in no hurry.

Thanks for the support and tips.  I still want to knowhow you get gparted to give you a "hidden" flag but that is just for educational purposes now.


did you try 
entering grub as root type
grub> hide (hd?,?)       the hard drive you need to hide then reboot.
quit

type sudo fdisk -l to verify that it is hidden. I can't wait to try it. 

I read you could hide (hd0,0) drive in this manner and install windows on the (hd0,1) second partition from the install cd.

---

### Post by ranch hand on 2010-01-08
Are you talking about grub1.97 or grub0.97?

I take it that you are talking about some grub command when you have the grub menu screen up.  I am not sure how to do that in grub but will look into the commands.

I do know that if you enter sudo grub in terminal on an installed OS it will not do it (command unknown).

---

### Post by Gemu on 2010-01-08
> **ranch hand said:**
> Are you talking about grub1.97 or grub0.97?

I take it that you are talking about some grub command when you have the grub menu screen up.  I am not sure how to do that in grub but will look into the commands.

I do know that if you enter sudo grub in terminal on an installed OS it will not do it (command unknown).


 Yeah I was talking about grub legacy. I'm also looking for a way to do something similar. My knoppix usb keys won't boot in my desktop unless I unplug my two hard drives in which each have Knoppix booting on them. I bet grub2 will do it somehow.

Herman has a slew of good info on grub2 here:

[http://http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html]("http://http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html")

It looks like you can do all kinds of things with grub2 like run hdparm. It looks like you can put a hard drive on standby for a set amount of time with hdparm. 

I'm still trying to learn grub2.
I never new everything there was to know about grub legacy for that matter. LOL

---

### Post by ranch hand on 2010-01-08
I prefer grub2.  If you check my sig you will see that I also am familiar with hermans stuff (first link I give).

I hope you are studying drs305s stuff too.  He has gotten the documentation going.

---

### Post by ronacc on 2010-01-09
I don't think you can hide a partition from a partitioning tool , if you could how would you ever be able to unhide it ? I know gparted finds and will manipulate hidden windows partitions , I've used it to delete them .

---

### Post by VMC on 2010-01-09
> **ranch hand said:**
> I installed CentOS on my test platform.  Now I want an install of A1 that will be converted to Lxde as I can't get the Lubuntu installer to work right.

So, with the great migration assistant instead of an install page asking if you want to migrate anything, it decided to get stuff from Cent for some reason.  Can't handle it for some reason (ext3?).

I figure "hide the sucker" as I have heard you can do this.  So I look at gparted and there is the flag manager.  Tried to do this from the LiveCD.  Click on "hidden" and the box goes grey and then comes back with the box unchecked.  Hit close and it goes through the reading stuff and there is no new flag.  Tried this mounted and unmounted.  No joy at all.

So I boot to Karmic on my internal and try it from there.  Same deal.

So, I boot to Jaunty on my other internal and try it from there.  Same deal.

What is a poor boy to do?
A little confused. What's A1. Cent A1. Whose A1?

You think that installing another distro tried to find stuff for Cent, is that it? Now I'm confusing myself.

Here, do this. Clone Cent. Then format Cent partition. Now you can install whoever A1 is and once its done re-image the formated partition with the cloned Cent.

---

### Post by ranch hand on 2010-01-09
That is what I decided.  Cent is not worth the effort.

I just wanted to look at it but it is another pain in the butt like every other rpm based OS I have fooled with (even Mandriva and I kind of like it).  I am just not going to fool with any of the many more.  More trouble than they are worth.

---

### Post by ronacc on 2010-01-09
I was a Suse user for years and spent many an evening trying to get something to install that wasn't part of the default install, it often made me wan't to do something violent to my box,My blood pressure is down several points since switching to Ubuntu .:lolflag:

---

### Post by Gemu on 2010-01-09
> **ranch hand said:**
> I prefer grub2.  If you check my sig you will see that I also am familiar with hermans stuff (first link I give).

I hope you are studying drs305s stuff too.  He has gotten the documentation going.


Oh yeah I see your sig now. I think Herman gives links to your page and drs305's as well. I read drs's stuff first when I realized Ubuntu 9.10 installer had put grub2 in place of grub legacy while I was getting coffee. At first I wasn't to excited about grub2 but am starting to like it. 

It looks like parttool in grub2 does the hide function.

Here is a link I just found that is interesting:  


[http://www.keneks.net/]("http://www.keneks.net/")

---

### Post by VMC on 2010-01-09
> **Gemu said:**
> Oh yeah I see your sig now. I think Herman gives links to your page and drs305's as well. ... Just like Ubuntu's logo, a circle of friends. :)

> **Gemu said:**
> It looks like parttool in grub2 does the hide function.

You can run, but you cannot hide ... Like Ronacc said, if a partition tool was able to hide electively you wouldn't be able to unhide it. It least not like what Ranch hand is wanting.

---

### Post by Gemu on 2010-01-09
> **VMC said:**
> Just like Ubuntu's logo, a circle of friends. :)



You can run, but you cannot hide ... Like Ronacc said, if a partition tool was able to hide electively you wouldn't be able to unhide it. It least not like what Ranch hand is wanting.

 I wonder if Ranch could temporarily rename the offending file so it doesn't get picked up on. I had some luck with this idea on a different occasion with renaming the KNOPPIX folder on my HD so my USB knoppix would boot.

---

### Post by ronacc on 2010-01-09
I think he wants to hide the whole partition from the installer . You might have an Idea there though , if he can find out where the installer looks on the partition(s) to find importable things he might be able to rename that folder within the partition so that the installer can't find it . for example his cent /home  to /some , if that is how the installer works , that should spoof it . Note ! I'm just guessing here .

---

