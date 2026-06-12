---
title: "Samsung netbook - ?HyperSpace"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by drspikes on 2010-04-02
Hi,

I'm about to take delivery of a Samsung n210 with Windows 7 Starter installed.

1) I intend to duel-boot with full Ubuntu rather than Netbook Remix as I would like to migrate to 10.04 as soon as it comes along. (any comments on this plan would be welcome.)  

2)Also although pretty news to Linux, I am toying with the idea of going for the 64 bit edition - am I going to fail?  (am upgrading memory to Max (2Gb)anyway).  

3) Will it fail more because I am running it alongside Win 7 32bit?

From reading the reviews, the netbook comes pre-installed with an instant-on Linux derivative called HyperSpace that you installing after the first boot into Win7 ?as an option.  From what I hear it's pretty slow to load and pointless so was planning to disregard it but just wanted some pointers.

4) Am I right that HyperSpace is only installed as an option or is it there right from the start?   

5) If HyperSpace is already there, is it on it's own partition... how can I get rid of it safely?

Many thanks,

---

### Post by tommcd on 2010-04-03
> **drspikes said:**
> 
I'm about to take delivery of a Samsung n210 with Windows 7 Starter installed.
... I am toying with the idea of going for the 64 bit edition - am I going to fail?  (am upgrading memory to Max (2Gb)anyway).  

3) Will it fail more because I am running it alongside Win 7 32bit?
You can install 64bit Ubuntu alongside 32bit Windows. I have 32bit Windows XP, 32bit Ubuntu 9.10, and 64bit Slackware 13 on my desktop. 
> **drspikes said:**
> 
4) Am I right that HyperSpace is only installed as an option or is it there right from the start?
It seems that the Hyperspace thing is included. According to these reviews you access it by pressing F6 as the machine boots:
[http://www.laptopmag.com/review/laptops/samsung-n210.aspx?page=2](http://www.laptopmag.com/review/laptops/samsung-n210.aspx?page=2)
[http://www.zdnet.co.uk/blogs/zdnet-uk-first-take-10013312/samsung-n210-netbook-10015114/](http://www.zdnet.co.uk/blogs/zdnet-uk-first-take-10013312/samsung-n210-netbook-10015114/)
> **drspikes said:**
>    
5) If HyperSpace is already there, is it on it's own partition... how can I get rid of it safely?

This review refers to it as "Phoenix Hyperspace":
[http://www.liliputing.com/2010/03/samsung-n210-review.html](http://www.liliputing.com/2010/03/samsung-n210-review.html)
and says it is similar to Splashtop that was included on some Asus motherboards:
[http://www.phoronix.com/scan.php?page=article&item=869&num=1](http://www.phoronix.com/scan.php?page=article&item=869&num=1)
So it may be on the motherboard of N210, and not on the hard drive. This is how Slashtop was. If so, you will not be able to remove it. But it will not interfere with Ubuntu in any case.

See this about the wireless on the N210 if you have problems:
[http://ubuntuforums.org/showthread.php?t=1391750](http://ubuntuforums.org/showthread.php?t=1391750)
Hope this helps. I learned a thing or 2 looking this up!

And welcome to the Ubuntu forums!

---

### Post by drspikes on 2010-04-04
> **tommcd said:**
> You can install 64bit Ubuntu alongside 32bit Windows. I have 32bit Windows XP, 32bit Ubuntu 9.10, and 64bit Slackware 13 on my desktop. 

It seems that the Hyperspace thing is included. According to these reviews you access it by pressing F6 as the machine boots:
[http://www.laptopmag.com/review/laptops/samsung-n210.aspx?page=2](http://www.laptopmag.com/review/laptops/samsung-n210.aspx?page=2)
[http://www.zdnet.co.uk/blogs/zdnet-uk-first-take-10013312/samsung-n210-netbook-10015114/](http://www.zdnet.co.uk/blogs/zdnet-uk-first-take-10013312/samsung-n210-netbook-10015114/)

This review refers to it as "Phoenix Hyperspace":
[http://www.liliputing.com/2010/03/samsung-n210-review.html](http://www.liliputing.com/2010/03/samsung-n210-review.html)
and says it is similar to Splashtop that was included on some Asus motherboards:
[http://www.phoronix.com/scan.php?page=article&item=869&num=1](http://www.phoronix.com/scan.php?page=article&item=869&num=1)
So it may be on the motherboard of N210, and not on the hard drive. This is how Slashtop was. If so, you will not be able to remove it. But it will not interfere with Ubuntu in any case.

See this about the wireless on the N210 if you have problems:
[http://ubuntuforums.org/showthread.php?t=1391750](http://ubuntuforums.org/showthread.php?t=1391750)
Hope this helps. I learned a thing or 2 looking this up!

And welcome to the Ubuntu forums!

Thank you very much for your clues Tommcd. I got my Samsung N210 yesterday and thought I would report back what I've learned in case it helps others.

First time it booted into Win 7 setup.  This took about 40 min to configure.  It then went straight into a Samsung program loader, which I assume loaded everything else.  There was no selection or imput allowed at this stage.  (15 min). It then booted to Samsung Restore which insisted on making a Restore image (19min). Finally into windows.  The next thing is it asks to partition the C: drive into C: and D: and describes this is a one time opportunity.   Fear not, just drag the C: drive to the right eliminating D: - you will need that partition yourself later.  If you don't do this, there is nothing final about it, you can easily change this.  

At this point, program after program will try to install itself.   Hyperspace install pops up in a dialogue box that gives you 30 seconds to turn it down otherwise it will start to install itself.  After some reading, I've decided it gives no advantage so stopped the install and have not heard from it since!   

I followed the instructions from [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

A couple of points though.  When using Gparted I found it had already got 3 physical partitions (Restore, ?Boot, and Windows).  Therefore as you can only have one more physical partition, you much make all the free space remaining into an "Extended partition" and then put up the partitions for /, a 4Gb Swap, then the rest as NTFS for duel storage.

I don't agree with the lifehacker article fully for the final part in terms of shared storage. Instead follow [http://ubuntuforums.org/showthread.php?t=1337628&page=1](http://ubuntuforums.org/showthread.php?t=1337628&page=1)

Now both OS are fully set up, this is my first proper Linux install and I am amazed at the difference in speed and simplicity compared to Windows 7.  I can't quite bring myself to go for a Ubuntu only build but I doubt there will be many occasions when I boot to Windows 7.

Hope this helps.

---

### Post by tommcd on 2010-04-05
> **drspikes said:**
> 
First time it booted into Win 7 setup. ... 40 min to configure.  
It then went straight into a Samsung program loader, ... 15 min. 
It then booted to Samsung Restore ... 19min ...
 Finally into windows.
Geez, a total of 74 minutes just for configuring and loading Windows for the first time!
In contrast, I can do a clean install of Ubuntu in about 20 minutes. This includes manual partitioning to set up my partitions the way I want them.
Anyway, glad you got it all sorted out. Did you have any trouble at all getting the wireless connected and online?
Also, any trouble with using grub2 to control the MBR and dual boot Windows and Ubuntu? I have read reports around here about Windows 7 not wanting to load with grub on the MBR. In these instances Windows 7 insists on fixing the MBR to get it back under Windows control. Did you run into any problems with this at all?

---

### Post by drspikes on 2010-04-06
> **tommcd said:**
> Geez, a total of 74 minutes just for configuring and loading Windows for the first time!
In contrast, I can do a clean install of Ubuntu in about 20 minutes. This includes manual partitioning to set up my partitions the way I want them.
Anyway, glad you got it all sorted out. Did you have any trouble at all getting the wireless connected and online?
Also, any trouble with using grub2 to control the MBR and dual boot Windows and Ubuntu? I have read reports around here about Windows 7 not wanting to load with grub on the MBR. In these instances Windows 7 insists on fixing the MBR to get it back under Windows control. Did you run into any problems with this at all?
 
I'm still having major trouble with wifi - as documented towards the end of this thread...[http://ubuntuforums.org/showthread.php?t=1391750](http://ubuntuforums.org/showthread.php?t=1391750)  Any help appreciated!
 
Grub2 is working fine.  There is a bit of wierdness that I have read seems to be a general issue with Samsung netbooks.   When you reboot and switch OS the computer - GRUB OS selection page then reboots back to POST screen 3 seconds after GRUB hands over controle.  On second run through Grub the OS completes fine.  If you are loading into Win7 it comes up with a screen reporting failure to start last time and would I like to run recovery(recommended).  Everyone I have read says just select normal boot and this has worked fine for me.  Naturally Ubuntu does not complain and runs as if nothing bad happened.  If you have shut down the computer and then run the same OS next time, you don't get the reset post-grub and both OS load normally.
 
This is my first real linux experience and find it superior to Win7 in every way (except wifi which I am not yet tearing hair out over).  I doubt I will boot to Win7 much now..  ;)

---

