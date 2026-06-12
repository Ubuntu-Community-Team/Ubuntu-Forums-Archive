---
title: "Unable to install"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by Nemion on 2006-12-23
Hello everyone.

I really want to try Ubuntu, and I have tried many times now doing it, but I simply just can’t get to install it. I have a laptop where the installation went smooth, but I spend more time on my home desktop computer, so I would like to install Ubuntu on it, and then force myself to get used to it. Maybe it’s a good start to enter the specs of my system so you know:

AMD64 3000+
ASUS A8N-SLI Deluxe
1 GB Corsair PC-3200
Primary [Operating System] Disk, WD Raptor 36.7 GB (currently holds only one partition with Windows XP SP2 on it)
GeForce 6600 GT

I have tried both the Ubuntu Edgy 6.10 x86 and x86_64 with the same result:

When I boot up the Live Disk, it boots fine, and I select ‘Start or Install Ubuntu’ in the menu. The boot loader is fine, and loads it all, but then I get a very weird picture which looks like some heavy graphics problem… [See Link/attachment – roughly made in Paint]

[IMG]http://img175.imageshack.us/img175/6686/ubuntubootupsw1.png[/IMG]

I have tried to start the install using the ‘Save Graphics Mode’ in the menu, but the exact same happens – the weird picture which I think should be the desktop appears :-/

What do I do? I can’t even get to the installation of this fine system…

Please let me know if you need more info, and I hope someone has a solution.

---

### Post by taurus on 2006-12-23
I strongly recommend you use the alternate CD to install it on your machine!  I just replaced my machine with a new nVidia graphic card and a new monitor and the alternate CD installed like magic...

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

p.s.  Don't forget to burn it at slow speed like 4X (although my machine didn't have any problem reading it at 8x...)

---

### Post by meng on 2006-12-23
Perhaps boot with the safe graphics option, but otherwise I second the suggestion of Alternate CD.

---

### Post by Nemion on 2006-12-25
Hello again!

Thanks for your possible solutions, but sadly none of them worked :-/ I'm starting to loose faith I'm afraid, it sucks... :confused: 

I've tried:
Ubuntu x86, x86_64
Ubuntu Alternate x86
Kubuntu x86

All of them I've tried running with Safe Graphics Mode also, but it's still the same: after everything has loaded, and the desktop should show, I get my screen filled with vertical lines in many colors - looks just like when my old Amiga encounters an error or the disk is damaged so it just displays a colorful screen... ](*,) 

I don't know if Safe Graphics Mode is the same, but I've tried the boot option "vga=771" also, still the same...

Could someone please tell me why this happens, and why it wont even run with Safe Graphics? My system isn't *THAT* special is it? Known bugs with some of my hardware?

Even though I'm VERY disappointed in the whole Linux thing now, because it officially hates my system, I'm still open to suggestions, because I really want to learn this - tired of Windows... [-( 

Hope there's something to do!

---

### Post by taurus on 2006-12-25
Let's go back to the alternate CD for a second.  Did it install at all?

---

### Post by Nemion on 2006-12-25
Yes, it installed okay I guess, a bit slow though.

But on bootup it failed like they all did, and then I did something in my frustration:
I got pretty mad, that it didn't work, so I ran the installation again, deleted the Ubuntu partitions and merged all the free space together for Windows again. I thought I could fix the MBR by running FIXMBR or FIXBOOT in the Recovery Mode, but it failed, so I had to reinstall Windows yesterday also.

In total this has been some **** [-( 

What would you like me to try? Still open for suggestions. I hope I can make some test with the Live CDs first though, can't even get them to work.

---

### Post by hhtuer on 2006-12-25
i got the same problem exept from that my screen was purple with black lines :D we have the same video cards GeForce 6600 gt  (so its definitly something up with that) but i wonder what ? and how to fix it ??

---

### Post by Nemion on 2006-12-25
Hey hhtuer!

My screen can get multicolored bars too. The drawn picture was from my first attempt and it was with Ubuntu 6.10 x86. Within Ubuntu 6.10 x86_64 the bars was more like purple, white, yellow... many colors! When I tried Kubuntu 6.10 x86 the bars were all orange. 

Maybe it really is a big problem with GeForce 6600 GT, because not even Safe Graphics Mode works...

---

### Post by hhtuer on 2006-12-25
i will try to install the Alternate install CD, but im hopeless...if you'll sort this out, please email me on [email]hhtuer@yahoo.ie[/email], give me your email and i'll email you if i find out anything ..

---

### Post by gerkin on 2006-12-26
...this is from memory so bear with me...

(firstly i have the same Nvidia 6600 graffics card - and similar speced machine)

the problem seems to be a change between Ubuntu 6.06 and 6.10 with the default video driver (the old/original version 6.10 worked but the latest download now doesn't)

This is what worked for me:

1.  download and burn the alternative install CD .iso (whichever version you want, currently I'm using 6.06 primarily as I've found it more stable.... I have been unable to install it satisfactorily with the Live 6.10 CD

2. install it as usual (you'll notice the CD works fine up until the "eject the CD and reboot" stage, then it turns to crap and you get the weird screen when it boots up??)

>>>> the problem is no Nvidia driver has been installed for your card <<<

3.  go to this site and download the "envy" .deb script

[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb)

4. copy/save it to your ~/home directory in the new installation

5.  use the alternative install CD to to run a terminal (sorry I can't remember what the option is called)

6. then navigate to the ~/home (wherever you saved the "envy" .deb, install it with:

           "sudo apt-get install "envy_0.7.5-0ubuntu1_all.deb"

7. see the envy homepage but basically just run the "envy" script

8.  when it's finished doing its thing and you reboot you should get the Nvidia splash screen
and your away 

9.  couple of things if you upgrade you kernel, you'll lose the Nvidia driver and have to repeat the steps 4-8 again.  & Linux Mint (also Ubuntu based) has the same issue, but other distros like eg. PCLinuxOS still have a fall back nvidia driver which works out of the box

I hope this helps... if not let me know and I'll do a bit more digging

---

### Post by gerkin on 2006-12-26
ALSO

make sure you read and follow the "envy" instructions at:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by hhtuer on 2006-12-26
hope , this will work, i will install it tomorrow, and post what i got ...

---

### Post by Nemion on 2006-12-26
hhtuer I will wait for your reply before I try it too then, but maybe I will try it anyway tomorrow also.

More bad news, though this was pretty expected: tried Xubuntu Live CD today, loads fine just like the other, but when it should be displaying the desktop it just showed green/purple vertical bars...
Just to be sure there's no misunderstandings, all CDs work on my laptop, and I've checked them for errors in the menu before use, no problem.

Back to the new suggestion:

I must admit I'm VERY surprised about this, if this really is the thing. I can't understand this. Maybe I'm a newbie in the Linux universe, but tell my why a complete operating system choose not to include a working driver for such a normal card as mine? I just don't get it...

---

### Post by hhtuer on 2006-12-27
i wanted to install it, but i havn't got a clue how to partition my disk , im new to linux i know that i need to have the three partion / ,swap and home but i only got my partition on my hard drive ,and i dont want to loose any data thats on it, and the patitioner is telling me that its going to erase the partition... have no clue how to do it....

---

### Post by Nemion on 2006-12-27
It's the Alternate Ubuntu you're talking about right? I managed to select some setting so it reduced the size of my Windows partition and then used the newly created free space to set up the partitions for the installation. You can select what the new size of the existing partition should be.

---

### Post by hhtuer on 2006-12-27
yes, alteranate. well, i got 2 partition , the main one, and the second one with the installation of windows ( it was like that since i bought it ) so it wont allow me to partition the main partition (its telling me that there is not enough memory ( 200 gb wonder why ?:/ ) and if i choose the whole hard disk ,its telling me that all partition will be lost ( does that mean that, i will loose all the data, or what ?? ) linux drives me bananaz at this stage , and  i didnt even installed it yet ( but still im sick of windows ) anyway, did you get it working properly ??

---

### Post by Nemion on 2006-12-28
If this can help further troubleshooting, I tried Knoppix Live CD today, and it worked nicely. Everything seemed to work, and my hardware was detected and worked - it could also read my hard disks. 

Duo to exams I haven't got that much time for experiments, and the suggestion with manual driver install is too much to handle just now - I need a stable system I can work with to get up and running with my exams.

---

### Post by xtknight on 2006-12-28
Safe graphics mode does not change anything in Edgy.

[http://www.ubuntuforums.org/showpost.php?p=1941036&postcount=19](http://www.ubuntuforums.org/showpost.php?p=1941036&postcount=19)

---

### Post by riven0 on 2006-12-28
> **hhtuer said:**
> yes, alteranate. well, i got 2 partition , the main one, and the second one with the installation of windows ( it was like that since i bought it ) so it wont allow me to partition the main partition (its telling me that there is not enough memory ( 200 gb wonder why ?:/ ) and if i choose the whole hard disk ,its telling me that all partition will be lost ( does that mean that, i will loose all the data, or what ?? ) linux drives me bananaz at this stage , and  i didnt even installed it yet ( but still im sick of windows ) anyway, did you get it working properly ??

Before installing it's always good practice to do a disk defragmentation on windows. Also doing **chkdsk** is a good idea. Depending on how XP was installed on your system, Windows will set aside a small hidden partition that prevents the rest of the hard drive from being messed with. This will, of course, prevent it from being repartitioned. I know; I had a long experience with it. :rolleyes: 

Anyway, try those two things first and then try re-partitioning.

---

### Post by hhtuer on 2006-12-28
i defragmented with powerdefragmenter already. ( much faster then the windows one, and more effective ) i will do the check disk , but i dont think it will do any good, i will try anyway...

---

### Post by hhtuer on 2006-12-28
i might actually try the Knoppix , looks nice , and if it works go on my machine , it will do me...

---

### Post by gerkin on 2006-12-31
Hi hhtuer

sorry to hear that you are having so many problems

firstly I would have to say I'm a real Ubuntu fan (and I've tried many distros), Ubuntu is my primary OS

What annoys me is that the latest versions of the Live CD doesn't work "out of the box' on my Nvidia 6600  card either 

Earlier versions of Ubuntu worked fine (and had a fall back driver as I previously posted and the Live CD worked great ... obviously something has been changed to effect this)

I could be wrong and hopefully someone will correct me if so but unless you install one of
the NVidia drivers you do no have accelerated 3D graffics etc. (despite the screen now working etc.)

It can make life seem very difficult to install Ubuntu with the problems you are having.

I'm pleased you are liking Knoppix, it's great and I always keep a knoppix CD around for system recovery tasks etc.

Also I would strongly recommend PCLinuxOS for anyone new to Linux, I have found recent converts from the other $OS$ find it very comforting as it looks quite windozy and I have had no problems installing it on my hardware in the past.

Chess Griffin has a section on it in his excellent Linux Reality Podcast here:
[http://www.linuxreality.com/2006/04/](http://www.linuxreality.com/2006/04/)

You can find PCLinuxOS here:
[http://www.pclinuxos.com](http://www.pclinuxos.com)

If your going to install Ubuntu 6.06/ 6.10 from the alternative CD you may need to do a bit more reading on this site to answer all your questions


cheers...........gerkin

---

### Post by spockrock on 2006-12-31
have you guys after installing from the alternate disc, boot into single user mode from the grub menu, you may have to hit esc to see it.  Then you should have a black screen white text, and you should enter these commands

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
nano /etc/X11/xorg.conf
```

find a line that resembles, Driver "nv"
change it so the "nv" is now "vesa"
save, then reboot.

then you should atleast have a gui..... and from there use the envy script, or use automatix, or go to ubuntuguide.org and follow the steps on how to install the nvidia driver.

---

### Post by lulabob on 2007-01-09
I have nearly same machine, and get the same picture on screen, when trying to install ubuntu 6.06. have 2 nvidia 6600gts in sli. will try some of the suggestion listed in the replys to nemions post. what about trying the linux driver for these cards from the nvidia web site? how would I get it configured properly?
lulabob

---

### Post by lulabob on 2007-01-10
ok so now i'm hosed. i could always see the splash screen, and tried safe graphics option. that brought me to the desktop using live cd. clicked install, and it went through the install routine. on reboot i get the bios, then "error loading operating system". can't do anything but pull the plug. any ideas?   Anyone.   Please!

---

### Post by sxturbo on 2007-01-18
well looks like the 6600GT card just sucks ***.

I'm having the same issue installing 6.10 Live CD. I installed it on a work computer today and absolutely loved Ubuntu. I'm pretty new to Linux , so i figured I'll install it at home too and play around and learn as much as I can.

I've been fighting this graphical problem for 4 hours now. Searching on here like  crazy, trying different things. Damn this just sucks. 

I'd love to drop in a new videocard, but another AGP at this point in time is stupid. Time to get a new CPU, PCI-E card, DDR2, etc.   Let the $$$ roll I guess ](*,)

---

