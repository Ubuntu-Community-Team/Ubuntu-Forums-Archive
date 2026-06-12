---
title: "[SOLVED] Problem With Firsit Installation"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by yazuki101 on 2008-01-28
I am a first time user of ubuntu, but am very eager to get on board with open source. Unfortunately I can't seem to get past the installation process for ubuntu 7.10 Gutsy Gibbon. I find that after I boot off the live cd I can get to the main menu well enough. I run an errors check on my disk and it is good. But after about 1-2 mins after I hit Install Ubuntu (the first option) it freezes up. Specs as follows:
-AMD x64bit 2.01GB processor 
-3GB DDR2 RAM
-xFx nVidia 8600GT GeForce GPU (512MB)
-ubuntu 7.10 i386 (it was conscious desicion to go with the 32bit version as I heard it was better supported than the 64bit)

I have yet to try the alternate cd because I have noticed that alot of people have had this issue using the AMD x64 bit processors. Unfortunately I am such a newbie that none have been dumbed down enough for me to fully understand. I am a quick learner, I just a nudge. A plain english step by step nudge lol. 

yazuki101--- "School is a place where former 'A' students teach mostly 'B' students, how to work for 'C' students." --- Guess which one I was?

PS- explanations as to what each step is actually doing in term of what is being modified appreciated but by no means neccessary Thank you in Advance and long live free and open innovation

---

### Post by zvacet on 2008-01-28
If you still have iso on your HDD chek [md5sum](https://help.ubuntu.com/community/HowToMD5SUM).If that is correct boot with safe graphic mode ( I think it is under F6).if all of this doesn´t help download alternate CD from [here](http://releases.ubuntu.com/gutsy/).

---

### Post by yazuki101 on 2008-01-28
I am having some real trouble getting any version of gutsy gibbon to successfully load on my pc. This is my first linux experience so I am have to learn everything as I go. I have looked over these forums for about 5 hours now and I cannot find anyone having my problem that provides a solution I can honestly say I know 100% what to do.

I have managed to finally get 7.10 i386 loaded to the GRUB boot loader using the alternate cd. I tried adding "vga=791" as well as "nosplash" at the edited line of the boot loader. first the vga, which did nothing ( I simply added to the end of line, after the 'quiet splash': "splash vga=791). to no avail. next I changed the splash to nosplash. It looked like things were going great, until it froze loading the manual drivers and the kernel modules. 

That translates into my experience using both liveCD and alternate, 32 bit and 64 bit, (with the added benefit of blank monitors when I use the 64bit alt)

My Specs are:
AMD Athelon 2.01GHz x64bit processor
XFX Geforce 8600GT nVidia GPU (512mb)
3GB DDR2 RAM
320GB SATA HDD
80GB SATA HDD (contains the ubuntu partition) 

I am rather new to this and I would appreciate any help I can get, thanks in advance

---

### Post by ibizatunes on 2008-01-28
i386 is 32 bit
have u installed 32bit or 64 bit?
Have u enable restrict drivers?

---

### Post by yazuki101 on 2008-01-28
i have the alternate disk and am currently staring at the GRUB menu after having got it this far. But now I  cant load the actual GUI. I tried replacing splash with nosplash, but to no avail. Any other help would be appreciated ( i check the cd before i did anything with it. as well i have no other OS on my hard drives, so it all or nothing lol)

---

### Post by yazuki101 on 2008-01-28
restrict drivers? thats new to me...how does one go about that? and in regards to your other inquiry am running 32 bit because its more widely supported than the 64bit)

---

### Post by PmDematagoda on 2008-01-28
Installing Ubuntu using the Alternate CD means that you will have to configure the X-Server manually.

First boot Ubuntu in Recovery Mode and do the following steps:-

Install the Nvidia driver using:-
```
sudo apt-get install nvidia-glx-new
```

Then enable the driver using:-
```
sudo nvidia-settings --config enable
```

After the above have been done, configure the X-Server using:-
```
sudo dpkg-reconfigure xserver-xorg
```

After the X-Server has been reconfigured, restart the system using:-
```
sudo restart
```

See if you get your GUI now.

---

### Post by yazuki101 on 2008-01-28
i tried booting it in recovery mode and it when great until this line of code:

[      12.848000] Uniform CD-ROM driver Revision: 3.20
[      13.076000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ22
[      13.076000] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [LAZA] -> GSI 22 (level, low) - > IRQ 17

then it hung there for about 10 mins and then   [fail] just appeared in the bottom right corner 
at no point was I given a chance to input anything.

---

### Post by Perfect Storm on 2008-01-28
> **yazuki101 said:**
> restrict drivers? thats new to me...how does one go about that? and in regards to your other inquiry am running 32 bit because its more widely supported than the 64bit)

By whom/what/which?


You know you posted in the Ubuntu 64-bit area.

---

### Post by hajk on 2008-01-28
The OP probably experiences problems with the splash screen not showing, this is a known problem  with AMD64 and 8xxx series nVidia GeForce cards, see e.g. bugs #140759 and #179642. The problem seems to be with using the framebuffer, no easy solution in sight AFAIK. Replacing the splash boot option by nosplash at least gives a black Linux screen with boot messages, so avoiding that uncertain feeling about the gdm login screen starting or not...

---

### Post by zvacet on 2008-01-28
Alternate CD doesn´t have graphic installer.It have text based installer,and if you see it just proceed with installation.Can you see [this](http://users.bigpond.net.au/hermanzone/p14.htm) and what happened i you select **install in text mode** ?

---

### Post by yazuki101 on 2008-01-28
i am making progress, currently i cannot resolve  'ca.archive.ubuntu.com' after inputing the command to download the nvidia driver. any suggestions?

---

### Post by yazuki101 on 2008-01-28
exact line of text i put in was 

sudo apt-get nvidia-glx-new

it came that it was unable to fetch some archives

---

### Post by zvacet on 2008-01-28
System>administration<software sources>chek all boxes under Ubuntu software tab and under updates tab.Reload.Try again to install driver.

---

### Post by PmDematagoda on 2008-01-28
Could you please provide some details as to how you connect to the internet.

---

### Post by PmDematagoda on 2008-01-28
> **zvacet said:**
> System>administration<software sources>chek all boxes under Ubuntu software tab and under updates tab.Reload.Try again to install driver.

zvacet, this may be rather useless since the OP does not have a GUI, so he would have to use the CLI to solve his problem:).

---

### Post by yazuki101 on 2008-01-28
zvacet- i cannot do that as i am unable to load the GUI, and can only act within the recovery mode

As for how I connect to the internet, I use an onboard network card on an ASUS M2N mobo. I have a wired connection to a siemens gigaset se567 router/modem. and finally the connection itself is a High Speed ADSL provided by Telus (the computer i am typing this on is the same, only wireless)

---

### Post by PmDematagoda on 2008-01-28
Ok, now this next step may require a fair amount of typing, but it would help greatly.

Post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by yazuki101 on 2008-01-28
some of it scrolled above the screen so i cant relay that. most of what is visible is information describing the other parts. the actual *content* of it is as follows:
(Disclaimer stating software from this repository may not have been tested and other various CYA statements)

# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

(some text explaining the next two lines explain how its software that is not part of ubuntu but is offered by canonical)

# deb [http://arcive.canonical.com/ubuntu](http://arcive.canonical.com/ubuntu) gutsy partner
# deb-src [http://arcive.canonical.com/ubuntu](http://arcive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main multiverse

---

### Post by zvacet on 2008-01-28
Try with [this](http://easylinux.info/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories) one.

---

### Post by yazuki101 on 2008-01-28
sorry for the late reply, i was busy simultaneously 'frankenstein-ing' a pc together for my fiancee and completely reformatting both my 320Gig SATA HDD and my 80Gig SATA HDD completely (*bows head in moment of mourning for all the lost information, a tragic waste.) So needless to say, my situation deteriorated drastically after i got it in my head i should reinstall win xp and update my BIOS and try loading unbuntu again. I got as far as windows first boot, well almost, while trying to load windows some terrible error about tabling or something. Anyway I now have to fresh SATA HDD's ready for a clean dualboot with windows. And where do I start now? lol

---

### Post by zvacet on 2008-01-29
Install Windows first,and after that install Ubuntu from alternate CD.If you still have troubles with graphic go to the recovery mode and type

```
dpkg-reconfigure xserver-xorg
```

and when you come to the drivers step select vesa and continue with reconfiguration.Restart and you should have basic grapfic.When you have that you can search for your video card driver.

---

### Post by yazuki101 on 2008-01-29
Currently reinstalling i386 with the alt, will post one way or the other

---

### Post by yazuki101 on 2008-01-29
Heres the deal for anyone whos looking at this thread for the first time:  I have the following hardware:

-AMD x64 Athlon Processor (2.01 GHz)
-XFX nVidia Geforce 8600GT GPU
-3.0GB RAM
-320GB Serial ATA (Primary Physical) (50GB partition for windows all rest is currently still raw from having to wipe all HDD)
-80GB Serial ATA (Sec Phys) (entirely devoted to ubuntu, with a 3GB swap file)
-ASUS M2N mobo
-LG 48x DVD Burner
-DVI- Gateway FPD2275LCD 22inch w/s LCD
-Analog- Lenovo 17 inch flat-screen CRT
-everything else is basically on-board

I have ubuntu installed once again on my 80GB SATA, but I can only load up in recovery mode. When I try normal mode I get a cursor blinking in the top left corner. I havent updated my BIOS since my last format. I figured I will start at scratch and let myself be advised and learn everything I can. (lets put my newbie-ness this way, until yesterday I had no idea what the sudo command was). I am at your mercy FOSS, do your thing.

---

### Post by yazuki101 on 2008-01-29
So I have updated my BIOS and I am gonna give it another go. This time I am using to 64 bit alternate cd. The integrity test was ok and am currently setting the partitions. fingers crossed

---

### Post by digc16 on 2008-01-29
Can anybody help? Please!  Install 7.10 and it has worked one time. I restarted the system in anticipation and it has yet to come up. I thought ok its a new system. No problem.  I will reinstall over my initial instilation and note any errors. I cannot get it to reinstall off of the disk. Iit hangs there as well and there is no activity from my processor and my keyboard flashes incessently, but its only the cap and scroll locks and not all three. Any ideas? I just want to use Ubuntu.

I went to the recovery kernel and backed over quiet and splash then it seemed to hang at the restricted drivers line. Is this any help?

---

### Post by yazuki101 on 2008-01-30
no such luck with the reinstall of the 64-bit, I am having the same problem as before. I am unable to resolve [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com)

---

### Post by digc16 on 2008-01-30
Have you tried fdisking it then re-installing?

---

### Post by Riffer on 2008-01-30
Heyas.

[QUOTE]# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse [QUOTE]  

I went back to your sources list and noticed that you had these 2 lines hashed out (its the #) try unhashing them and trying again (remember to save the file.

Question, when you do a graphical install does it hang around the time of installing language packs?

---

### Post by yazuki101 on 2008-01-30
i am not sure where it hangs in graphical install. it hangs one the load screen after you hit enter on the menu

---

### Post by Riffer on 2008-01-30
> **yazuki101 said:**
> i am not sure where it hangs in graphical install. it hangs one the load screen after you hit enter on the menu

Well I'll throw this out.  I've been installing Ubuntu on a couple of machines at school and in the beginning the install would hang forever.  I found it was because we were behind a "gateway", which prevented connection to the internet unless you enabled the network proxy.

If you're behind a gateway boot up your "LiveCD" and before you install go to the drop down menu "system-->preference-->network proxy".  In there put in the tcp address and port number of your gateway.  Then start your install.

I wouldn't worry about getting you nVidia drivers just yet, just get you basic install up and running.  By default Ubuntu uses the open source (vesa) driver for nVidia which works ok, just no 3D.  Also if the install again hangs see where abouts it does.  I've had a couple of disks that hung around the 94% mark and I had to re download the iso and reburn.  If thats the case try burning at a slower speed.

Kinda an after thought here.  Does your LiveCD boot up and get you to a desktop?  If it doesn't its a good indication that there are some hardware issues with Ubuntu and your system.

Hope this helps.

---

### Post by yazuki101 on 2008-01-31
Riffer- I cannot even get into the GUI with the liveCD, it hangs somewhere in between the initial menu (choose which install, memory test, test cd for defects etc...) and the GUI. I think it has something to with my AMD x64

---

### Post by Riffer on 2008-01-31
> **yazuki101 said:**
> Riffer- I cannot even get into the GUI with the liveCD, it hangs somewhere in between the initial menu (choose which install, memory test, test cd for defects etc...) and the GUI. I think it has something to with my AMD x64

[SIZE="2"]Which is surprising as we have very similar hardware.  

AMD64 dual core 5000
nVidia 7300 gs GPU
MSN-E SLI    motherboard

A question, have you loaded another OS using the same hardware?  I've been following your posts and wasn't sure if you had.                                                            [/SIZE]

---

### Post by yazuki101 on 2008-01-31
Aside from MS Windows XParasite, I have yet to successfully intall an OS on this particular machine. I have tried Ubuntu 7.10 (both 32 bit and 64 bit), Fedora 8, and Zenwalk 5.0 and none of would load (ZW would load with the FOSS 'nv' driver, but when I tried the 'nvidia-glx-new' drivers my 'X' server would error all over the place). I know that the problem does not exist between the screen and chair, as I am currently using my other box to communicate (one I just slapped together today with a P3 board I got my hands on). For some reason though, my main box does not want to let put and GNU/Linux based OS's on it.

About the only things I can think in terms of hardware that I havent mentioned yet is that I am using the AMD processor on an ASUS M2N mobo (with an NVIDIA nForce 430 MCP), i am using the onboard network adapter, and my internet connection is a wired line to a SIEMENS Gigaset SE567 ADSL Modem/Router

Finally I am currently taking another "kick at the cat" at installing the 64 bit 7.10

---

### Post by Riffer on 2008-02-01
[SIZE="2"]At this point it looks to me that its your nVidia GPU.  I had a heck of a time getting Gutsy working with my card, I finally did a fresh install and used ENVY to remove all traces of the nVidia driver that could have been installed, then did a manual install through ENVY to use the latest drivers (169.07 I think).

One of the things that I learned is that if you can't run the LiveCD there is probably a hardware issue and not necessarily a problem with Ubuntu.  And over the years I've learned that just because its new doesn't mean that its working perfectly.  I would think about taking you GPU back and getting another one, just because its working for the few minutes that your on XP doesn't mean that you may not have issues with it when graphics become intense.

I just reread your post and I'm convinced there's a hardware problem somewhere , and like I said I think its the nVidia card, but I did had to return my ASUS m2n-E SLI because of some issues.  If I were you I would think about returning everything and get an exchange for them and try again.

If I may ask where abouts in Canada are you?                                                                          [/SIZE]

---

### Post by yazuki101 on 2008-02-01
Unfortunately most of hardware is a year old, except my GPU which I get just after xmas, so its this or bust. As for canada, i live in calgary

---

### Post by Riffer on 2008-02-01
[SIZE="2"]Damm.  Well if you have another GPU  try using that , or maybe using the onboard one, either way if it works you know its your GPU.  If not I hate to say it you may just have to use XP which would be a drag.

Oh another thought, try your GPU in another slot, your MB should have 2 pci-e slots and 3 maybe 4 pci slots.  Been more then a few times that I got sound and video cards working by just switching slots.  Also You may have pulled a dumb move like I did (I forgot to take off the plastic shield on the cpu so I had overheating problems) so check your install just in case.

If none of those works, I'm sorry I'm out of ideas  , I hope you can get it figured out.

P.S. I'm in PG BC.                                                                                                           [/SIZE]

---

### Post by yazuki101 on 2008-02-01
> **Riffer said:**
> Heyas.

[QUOTE]# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse [QUOTE]  

I went back to your sources list and noticed that you had these 2 lines hashed out (its the #) try unhashing them and trying again (remember to save the file.

Question, when you do a graphical install does it hang around the time of installing language packs?

what was it you meant by this?

---

### Post by yazuki101 on 2008-02-01
I think my problem might just be I cant access the internet for some reason. ubuntu is the only OS i have been unable to even download the drivers let alone install them

---

### Post by Riffer on 2008-02-01
> **yazuki101 said:**
> [QUOTE=Riffer;4234535]Heyas.

[QUOTE]# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse 

what was it you meant by this?

In your source.list file those 2 lines have the # in front of them.  That prevents those lines being read.  If you remove the # then your system will load those lines.  This is in hopes that you'll then be able to fix the "unable to resolve ca.archive.ubuntu.com" issue that you had.

---

### Post by Riffer on 2008-02-01
> **yazuki101 said:**
> I think my problem might just be I cant access the internet for some reason. ubuntu is the only OS i have been unable to even download the drivers let alone install them

Could be.  By default Ubuntu sets the system for roaming IP addresses, but a lot of home setups have a static IP.  How is it setup on your XP?

---

### Post by yazuki101 on 2008-02-01
ahem um static ip...I have my SEIMENS Gigaset port forwarded for utorrent to get things i "shouldnt" have, faster

---

### Post by Riffer on 2008-02-01
Unfortunately I can't help you.  I too have set my router for static IP, yet Ubuntu works fine for me with the default settings.  Mind you I use guard dog to disable the default firewall in Ubuntu.

You could try as I said before, to set Ubuntu to have a network proxy, you could try that.

---

### Post by yazuki101 on 2008-02-01
for now I would settle with knowing how to confirm my connection status while in recovery mode

---

### Post by zvacet on 2008-02-01
Read [this](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html).

---

### Post by yazuki101 on 2008-02-01
okay, so I have finally managed to successfully install a LinuxOS with a working nvidia-glx-new driver. The OS is Zenwalk 5.0, and I was able to use the nvidia-configx command after I downloaded the nvidia-glx-new driver. All this was done in the CLI.

As for whether or not this will solve my Ubuntu issues, I am doubtful. At least until I can figure out why Ubuntu is the only OS i cannot even access the mirror to get the 'nvidia-glx-new' driver. After I can get past that, and have the driver, I will post my results

---

### Post by yazuki101 on 2008-02-01
> **Riffer said:**
> [QUOTE=yazuki101;4247032][QUOTE=Riffer;4234535]Heyas.



In your source.list file those 2 lines have the # in front of them.  That prevents those lines being read.  If you remove the # then your system will load those lines.  This is in hopes that you'll then be able to fix the "unable to resolve ca.archive.ubuntu.com" issue that you had.
Riffer:
I dont know how this post slipped past my attention the first time. But I have since edited those line in '/etc/apt/sources.list'. And am currently awaiting to see if the drivers will install now (seems to be hanging at 0%, while connecting to ca.archive.ubuntu.com, but even that is more progress than I have ever made). Again, will post results

---

### Post by yazuki101 on 2008-02-02
Well I am happy to report to anyone still with me after this marathon thread, that I am currently typing this on a 100% ubuntu dedicated machine. thats right, despite NVIDIA's best efforts, as well as bad mirrors, I am running gutsy's GUI off of my HDD! YAY. Sigh of relief everyone...small round of applause for everyones fruitful effort perhaps? 

Anyway, I am currently organizing every agonizing step of what I went through, as well as all  the information I gathered from the various threads I have begun, in all the various forums I have utilized in an effort to get Gutsy to run on my rig.

Once I have a comprehensive guide as to my issue as well as the solution (including all explanations of what the commands mean and what is being affected, as to the best of my knowledge), I will post a new thread, so as to have all the information in one place in a manner that even the mightiest newbie will understand.

Also I am interested in any other sites that may benefit from this posting, Suggestions welcome.

Once again, thank you to everyone who has helped me with this problem. My level of understanding has been exponentially increased in the few days since I first posted this misspelled thread, in the hopes of an easy fix. One thing I definitely learned, when dealing with ignorance, there is no such thing as an easy fix.

---

### Post by zvacet on 2008-02-02
I´m glad you fixed your problems,and decide to stay with Ubuntu.If you want to read and learn something about linux here are few links

[http://linuxcommand.org/]("http://linuxcommand.org/")

(You can also look all links [here](https://help.ubuntu.com/community/HowToGetHelp) under **General Linux links** and [this](http://www.cutlersoftware.com/ubuntuinstall/) one.

---

### Post by yazuki101 on 2008-02-02
thanks for the tips, I have them all bookmarked and ready for new issue, getting my twin view to work and get desktop effects. Hopefully this goes easier. Well wish me luck.

---

