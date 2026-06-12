---
title: "Noobee needs Help"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by Amit182 on 2008-03-21
Hi Fellows,

I have an AMD Sempron 3000+BXBOX that&#8217;s supposedly a 64 bit processor, 256 MB RAM & two HDD's, One 80GB & One 10GB..The 80Gb was the Master & 10Gb the slave .. I was running XP & was irritated by how often I had issues with malware & updates & how slow Windows was. So.. I thought of moving over to Linux. 
Did some research & found that I could use the Ubuntu 7.10 Live CD & see if everything works fine, any driver issues etc & I did just that. Everything worked beautifully. So , still in an experimental mood, I (thankfully now) backed up all my data on the 80Gb drive (& now I have just 3Gb on it)& then moved the 80GB drive out, made the 10 GB the master & booted with LiveCD.. It booted just fine & I started the install process & something went wrong after it asked if I wanted to go for a guided complete install to which I said yes.. About 40 seconds in the install, the screen went kaput about 5-6 times & I got an error message that said that my video driver had been shut down 6 times & this normally means something bad is going on, please try after 2 minutes. I said ok to that & left. I came after 6-7 minutes & saw that the screen was still the same (Half Brown & half static).. I waited another 10 minutes or so & still nothing.. The keyboard lights were out & my HDD activity light on the 
tower was solid lit. So I shutdown the system & re booted again with the live CD.. No luck. I could not boot into the desktop. It would freeze before that. This happened several times. SO I put the disk back as slave & booted with the 80Gb disk as Master. Xp loaded but did not detect the 10 GB drive. I used CompuServe&#8217;s SWISNIFE partition tool & it did show me the drive as did my BIOS, but when I tried to access it the program terminated every time... I tried to boot with the Ubuntu LiveCD with this 
configuration & it boots better than it ever did before.. I mean the boot was faster, the programs seemed to run faster... & yes it did detect the 10 Gb drive, however I could not access it, & whenever I tried the system froze up. 
So the net result is that I have a 10 BG drive that&#8217;s not any good, an 80GB drive that&#8217;s got just 3GB on it, Windows that i initially wanted to remove, & no Linux:( .
I looked up the other threads & its majorly geek lingo to me.. even though I have some tech background with Windows... can anyone help me out please?
PS: The graphics card is Savage S3, although I don't think that should be causing any problems as LiveCD works fine.

Thanx in advance
Bye

okay friends, I was reading the threads & saw something about checking the disks.. that made sense to me & i checked the integrity of BOTH the Ubuntu Cd's I had (Regular & 64 Bit versions) & after that I won't even get to the desktop with either CD.. things have gone progressively downhill. One interesting thing I noted was that this time when the computer froze up, I could actually eject out the Live CD. that is something I haven't been able to do before...

---

### Post by gaurdianAQ on 2008-03-21
you said you downloaded the 64 bit version........ and you only got 256 megs of ram I doubt its a 64 bit computer what kind of processor is it and try increasing your ram I believe it is reccomended to have 512 that or try xubuntu although i cant get it installed right now I have previously had it installed also the reason I dont think you have a 64 bit processor is because I have a top of the line vista computer with 2 gigs of ram that is still 32 bit so try the other version currently I am trying to get linux to work on mine but with no luck and no one has responded to my post :lolflag:

EDIT: doy I didnt see the processor you mentioned ya thats definitly not a 64 bit processor, the only 64 bit processors are probably only on servers considering my processor is better than that and still a 32 bits also get some more ram that will make a world of difference

---

### Post by swudee on 2008-03-21
You do need more than 256 meg of ram with 7.10. I believe about 300 meg is recommended, so do try another 256 meg, or maybe if you can afford it another 512 meg for a bit of future proofing.

---

### Post by Amit182 on 2008-03-23
Thanks for the help buddies,

I don't think RAM is the problem, LiveCD which works from the RAM works fine,its only when HDD access comes in play that it hangs up.... & yes I am a firm believer of the Quote : there's a MYTH called going around known as "Enough RAM"
anyways as I was searching for solutions to my woes i saw this : [URL="http://www.techsupportforum.com/hardware-support/hard-drive-support/194492-have-you-lost-hard-drive-partition-files-your-computer.html"]
XP Sees HDD in Device manager, not in my computer.[/URL]
& it seemed to make sense as I think the messages started coming when the partition tables were being formatted. SO I tried what in the thread.. That did not work for me.. But I then Downloaded Gparted ([http://www.download.com/GParted-Live...html?tag=lst-1](http://www.download.com/GParted-Live...html?tag=lst-1)) & that fixed my problem. i was able to install Ubuntu for all of 15 minutes before my computer started acting up again though..& on reboot Grub error 15 started coming up ..So I have used Gparted again, & now using the 10 GB drive under Windows..

:popcorn:Problem Solved:popcorn:
I must admit though, this experience has made me realize no matter how much i cuss Windows.. its still the only thing that I am comfortable with.

& as per AMD [My Processor]("http://products.amd.com/en-us/DesktopCPUDetail.aspx?id=166") does support 64 bit Operating Mode.

---

