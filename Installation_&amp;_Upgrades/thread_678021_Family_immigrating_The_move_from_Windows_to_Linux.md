---
title: "Family immigrating: The move from Windows to Linux"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by BXA121 on 2008-01-25
hi there, im BXA121, ive just joined tihs forum with the intention to migrate from windows xp sp2 to linux. in particular to the gtusy gibbon of ubuntu.

There seems to be plenty of people out there who want to move from windos to linux, but have no knowhow or way to do it. how do you tell a fish its meant to swim in water if its been lying on the ground all its life? This is where i intend to come in.

This is a migration journal: i wish to show how a novice to linux moves not only himself, but his whole family over to linux.
i do this so that others can follow me and see the help i get from a community which prides itself on support.

i have AMD and intel computers, i have wired and wirless internet to solve. i have old comps like amd k6 to quad core intels to migrate. 
my task wont be easy but ill learn a hell of a lot about linux and i hope beginners will too.

heres what i intend to do:

download ubunto - gutsy gibbon version.
my computer will be the first primer - ill make a dual boot system and eventuall on every computer ill do the following:

install it on each computer
setup drivers and what-not. 
install microsoft office - ( not because open office is crap, simply because all our study work and documents are in office format)
install open office - all new documents will be made using this eventually.
install a pdf programme, a media player and maybe a few games if i can! 

right now im downloading ubuntu, ill burn it on my computer and start a dual boot, once i know i can get all the bits working from here, ill implement it for the rest of the family.

ill try to post screenshots if i can.
ill learn as igo and ihope other will do so too.

thank you

---

### Post by jeffus_il on 2008-01-25
Good Luck!

Open Office Writer reads and writes Word .doc format, So does AbiWord.

You see, you're being harassed already!

---

### Post by ubuntu27 on 2008-01-25
Good luck mate! Go slowly, don't rush :)

Also, like the previous post indicated, OpenOffice.org can open and save Microsoft Office's file formats like doc.
It also has an option to export to PDF, so anyone with any Operating System can view your documents.

See my signature for tips for OpenOffice. :)

---

### Post by Lord Illidan on 2008-01-25
> 
install it on each computer
setup drivers and what-not. 
install microsoft office - ( not because open office is crap, simply because all our study work and documents are in office format)
install open office - all new documents will be made using this eventually.
install a pdf programme, a media player and maybe a few games if i can! 

You'll find that Ubuntu includes all these - except MS office, of course, out of the box.
Open Office is compatible with Microsoft Office .doc format. It can also make pdfs.

Feel free to refer to the links in my signature, there are some very helpful tips in there.

---

### Post by rosegarden78 on 2008-01-25
You could also look into using [this]("http://ubuntuforums.org/showthread.php?t=385981") article with an Xfce session instead of Gnome or Kde for a cleaner look.

---

### Post by ubuntu27 on 2008-01-25
If you really need to install Microsoft Office, then you might be interested in [CrossOver Linux]("http://www.codeweavers.com/products/cxoffice/") from [CodeWeavers]("http://www.codeweavers.com/"). It will let you install Windows application in Linux. :)

[http://www.codeweavers.com/](http://www.codeweavers.com/)

---

### Post by bwtranch on 2008-01-25
Anybody that has been reading my posts knows that I am against dual boot machines. They cause a lot of problems. I know there are naysayers out there that say this isn't true. But, I have plenty of experience to know. Put on a queenie in her own house and you will be better off. After a while, you can get rid of the other bitch, I mean dog.

Microsoft means very, very tiny software.

---

### Post by rosegarden78 on 2008-01-25
I thought dual-boot was a safety net if one wireless driver fails you can go online with the other.

---

### Post by ubuntu27 on 2008-01-26
I don't know if it is true, might be a myth. I've read and heard that when the computer dual or triple-boots. The "life-span" of the computer is lessend.

---

### Post by jeffus_il on 2008-01-26
Nonsense, The lifespan of the owner may be shortened if he messes up and doesn't know how to manage it. It someone makes such a claim, ask for detail, how does it actually work, i.e. the mechanism that damages the computer.

---

### Post by linux phreak on 2008-01-26
> **ubuntu27 said:**
> I don't know if it is true, might be a myth. I've read and heard that when the computer dual or triple-boots. The "life-span" of the computer is lessend.

I really hope that this is just a MYTH.

---

### Post by K.Mandla on 2008-01-26
> **ubuntu27 said:**
> I don't know if it is true, might be a myth. I've read and heard that when the computer dual or triple-boots. The "life-span" of the computer is lessend.
Can you link to something that explains that? That's definitely the first time I've heard it, and I have trouble believing it.

---

### Post by Lord Illidan on 2008-01-26
I have trouble believing it too. There is no logical connection.

---

### Post by PmDematagoda on 2008-01-26
I cannot believe it myself without some solid proof, I am currently triple-booting three different Ubuntu releases, one in development, and I do not face any problem at all, except that I realise that 280Gb of total hard disk is not enough for me;).

Oh yes, one more thing, all three releases do not use the same FS, one uses ext3, another JFS and the last(development one) on ReiserFS.

---

### Post by ubuntu27 on 2008-01-27
I have read that two years ago somewhere. I cannot recall the URL. 

As for my position, I do not believe it myself.  

Their supporting detail is that "Every time you reboot, you damage your hard drive" if I remember correctly.

---

### Post by BXA121 on 2008-01-27
I burned the iso image of gutsy gibon onto a cd.

guides i used:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://www.oneafrikan.com/archives/2005/06/15/dual-booting-ubuntu-linux-with-xp-tutorial/](http://www.oneafrikan.com/archives/2005/06/15/dual-booting-ubuntu-linux-with-xp-tutorial/)
[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)


i used partition magic, but you can use any free paritioning tool to make the appropriate hard drive space - if you download "system rescue cd for linux" and boot from that, you can use qtparted to make the space - i have partition magic and i made 20GB of space for linux. 
heres my partitions as they stand. i dafragged each partition.

see per-install1 attachment

i use a seperate NTFS partition already ( cos windows sometimes needs a clean install and i dont usually want to move my stuff, so i keep it in a seperate partition). 
i converted this to fat32 and allocated 20GB of space as thus:

see post-formatting attachment.

i tried to install ubuntu as a multiboot system. bad news.

the intallation pathway was good enough, the partition manager threw me off totally. (the bit where it asks where you want to install ubuntu ) i wasnt familiar with this so i tried to third option ( manal installation). i got totally confused - there was no help function. i had space i just want it installed there. so i tried the second option - "install where there is the most continuous amount of space"
i rebooted - ubuntu worked great. :)
i rebooted to windows - computer said "no" HAL.dll was missing - looking this up suggested it was the boot.ini that was buggered - i copied the details onto my boot.ini from another computer - no joy.
:(
ubuntu installed GRUB - its a program which manages your booting process - the windows equivilant would be the vista program to manage booting processes - dunno the name. 

i guessed the booting process was wrong- so i used the super GRUB disc - a bootable GRUB cd. 
here: 
[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)

this didnt work. i decided "im trying to fix a windows problem using linux - this is dumb" so i tried the recovery console - fixmbr - no good -i thought "screw this"- fixboot - noting. i was at a loss. 

i hadnt saved my stuff or backedup anything - i was too optomistic. thoughts of overhauling my computer ran through my brain - was liunux worth it?

i had downloaded multiboot cd2.0 from here: [http://thepiratebay.org/tor/3558083/Multiboot_2.0_Final_Release_(Bootable_CD](http://thepiratebay.org/tor/3558083/Multiboot_2.0_Final_Release_(Bootable_CD))

its on piratebay.

booting from this,  i deleted the unbuntu partitions. and made my windows partition active. rebooted. i used the partition magic program that comes with this.

voila! it worked. winxp was back. ok so fixed. :)

that cd is a keeper.

went back into multiboot cd and using partition magic - i setup my own partitions the way i wanted them.

i set the ext3 partition where linux would install as 23GB and i used 2GB for the swap partition.

windows worked fine now - so i tried again. 
installing ubuntu...
this time when at the partition manager section. i chose manual and pointed it to the ext3 partition. 
in mount partition i put "/" thats all.
it worked. 
rebooting from grub was fine. no problems! :guitar:
windows and ubuntu both work. 

heres what my partitions look like now:
see Finally1 atachment.

* my advice - if your starting to get worried about installations - dont worry. if you have multiboot - you can use that to manage your partitipons before you do installation. so do this: sort your partitions out before installation - even setup the partitioon where you want linux to go and allocate a swap partition. this way, you just tell linux where you want it to go*

next: ill try to install my wireless network


bxa121

multiboot complete.

---

### Post by steveneddy on 2008-01-27
> **ubuntu27 said:**
> I don't know if it is true, might be a myth. I've read and heard that when the computer dual or triple-boots. The "life-span" of the computer is lessend.

That is funny. I would like to see some facts about that. 

**Don't install extra software! It is dangerous!**

ROTL LMAO

l33t haxorz will cum 2 ur houz n st33l leet warez

Myth.....busted.

:popcorn:

---

### Post by BXA121 on 2008-01-27
I used the following guide to help get my wireless card up and running. 
"WIRELESS CARD HOWTO: ANY DISTRIBUTION OF LINUX (DESKTOP OR LAPTOP)"
by HokeyFry
[http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)

i have an asus wireless g card - ( thank God it runs) 
tip: just check if your card is recognised you can use this in command - i mean terminal ;)

"sudo lshw -C network"

it will list all your network hardware and tell you the status. 
by the time you have finnished with the above guide you should have a "recognised network drive" it should say at the bottom

" configuration: broadcast=yes **driver=ndiswrapper+bcmwl5 **driverversion=1.51+ASUS,02/11/2005, 3.100.64.0 ip=192.168.1.5 latency=64 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g"
the important bit is in bold. if it doesnt have that bit in bold (with your driver name with it) youve done something wrong. just go back and try to guide again - it worked the second time for me.

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
"How To: Troubleshoot your Wireless Network Connection - Connecting at Command Line by kevdog"

the above guide helped me to get my network running stable. though i never got to the end of it. i got to: "Setting the Wireless Interface to Connect at Boot " and realised it wouldnt give me a guide for an encrypted network. by then ubuntu had picked my network! 

i installed wifi radar ( google it and download it) forget about terminal line messin' i just left clicked it and selected install. worked a  treat. 
i configured wifi radar and now i can scan networks and select what i want.

woohoo! 

now ill try and sort out my ati 9800pro grafix card.

wish me luck (!)
BXA121

---

### Post by Achetar on 2008-01-28
nm-applet works better than wifi-radar. You can download it through Synaptic, or from packages.ubuntu.com. I believe the package name is "gnome-network-applet" or "gnome-network-manager".

---

### Post by BXA121 on 2008-02-09
> **Achetar said:**
> nm-applet works better than wifi-radar. You can download it through Synaptic, or from packages.ubuntu.com. I believe the package name is "gnome-network-applet" or "gnome-network-manager".

i have nm-applet, works fine with the system. sometimes its more helpful than wifi radar.
only trouble it that i cannot seem to be able to 'tweak" my network settings - to make then more agressive in finding my network. This is something i can do easily in windows - since im far away from my broadcasting router, i have to tweak my card to rad only in g mode or else it wont work if it goes into default b mode. 
any ideas?

---

### Post by BXA121 on 2008-02-09
Installing grafics drivers ATI.
the generic ones that come in with Ubuntu - are ok, but not fast and not really capable of doing what the proprietary ones are able to do. so i used this guide to help me get the right drivers and to set it up right. 

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

also used this , but to a lesser degree [http://ubuntuforums.org/showthread.php?t=515573&page=25](http://ubuntuforums.org/showthread.php?t=515573&page=25)     HOWTO: Install the ATI driver on ANY stable version of Ubuntu by tseliot

i enabled the restricted ati driver and i also allowed the universe and multi verse repositories in the software sources program.

i have installed the fglrx driver and it works with my system - however, i am unable to use the #D effects that ubuntu comes with -it simply says unable to enable - or someit like that. 

any ideas on how to fix this?
the drivers installed - it works fine - but 3d effects are not working. and i hope in the future to install beryl on my system. 

any help would be great.

---

### Post by ubuntu27 on 2008-02-09
I cannot help you on this but, I have a tip fro you. Create a new thread for each _different_ problem that you encounter. People see this thread has three pages and might conclude that whatever the problem was, it might be solved already.

Another thing is the title of this thread, it does not look like it is asking for support. Few people will see it. ^^

Just my two cents. :)

---

### Post by BXA121 on 2008-02-10
> **ubuntu27 said:**
> I cannot help you on this but, I have a tip fro you. Create a new thread for each _different_ problem that you encounter. People see this thread has three pages and might conclude that whatever the problem was, it might be solved already.

Another thing is the title of this thread, it does not look like it is asking for support. Few people will see it. ^^

Just my two cents. :)

i understand. 
I'm a NOOB like many that are moving from windows - this is just to catalog my progress for others in future. 
ill post another separate thread for this issue im having. 
thanks man.

---

### Post by BXA121 on 2008-02-19
ok so the above became unresolved. 

i had to uninstall ubuntu. 

but i reinstalled it! 

since then, using the guide for wireless, my wireless was setup  - it was much faster and less frustrating than before ( i guess im learning something!)
i decided not to upgrade my ATI drivers and started fooling around with compiz - i figured out the advanced settings manager with this guide:
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

on my searches, i found another help file for compiz installation. it gave me a REALLY SIMPLE WAY TO INSTALL PROPRIETRY ATI DRIVERS! 
here it is! 

[http://www.ubuntu1501.com/2007/12/installing-newest-ati-driver.html](http://www.ubuntu1501.com/2007/12/installing-newest-ati-driver.html)

So simple! install Envy and it will complie and install the right driver! 

so there you go! 
wireless, good 3D acceleration and compiz ready to be fooled around with! 

for my next trick:

ill be installing Office and also trying to create a virtual windows environment to make Ms Office work.
please note: this is something i have never done so i may make a HELLA lot of mistakes.

im kinda enjoying this now!

---

### Post by BXA121 on 2008-02-23
so far i have used crossoveroffice to install ms office 2000. 
it was really simple to install crossover and to install office after that, a doddle!

man, im really beginning to enjoy doing this stuff!

sing the mac4lin project, i was able to follow the instructions and setup my linux to look like a mac with leopard os! cool huh?

i have a large ntfs HD that i had trouble loading up, i used automatix and also the ntfs configuration thing that in the repository and i was able to read and write onto my hd! 

i guess the next thing is to try and emulate windows xp - this way ill be free completly from windows xp. 

i guess ill be able to move the rest of the family to ubuntu and then set them up...

---

### Post by ubuntu27 on 2008-02-24
> **BXA121 said:**
> so far i have used crossoveroffice to install ms office 2000. 
it was really simple to install crossover and to install office after that, a doddle!

man, im really beginning to enjoy doing this stuff!

sing the mac4lin project, i was able to follow the instructions and setup my linux to look like a mac with leopard os! cool huh?

i have a large ntfs HD that i had trouble loading up, i used automatix and also the ntfs configuration thing that in the repository and i was able to read and write onto my hd! 

i guess the next thing is to try and emulate windows xp - this way ill be free completly from windows xp. 

i guess ill be able to move the rest of the family to ubuntu and then set them up...


Good JOb mate! Keep it up :)

---

### Post by luvr on 2008-02-24
> **ubuntu27 said:**
> Their supporting detail is that "Every time you reboot, you damage your hard drive" if I remember correctly.
Hahahahah! That means that running **Windows** will seriously reduce the lifespan of your computer!

---

### Post by ubuntu27 on 2008-02-24
> **luvr said:**
> Hahahahah! That means that running **Windows** will seriously reduce the lifespan of your computer!

True enough! One star :KS point to you ;)

---

### Post by luvr on 2008-02-24
> **bwtranch said:**
> Anybody that has been reading my posts knows that I am against dual boot machines. They cause a lot of problems.
They can cause problems, if you don't know what you're doing. And you won't really know what you're doing until you run into the problems and make a serious attempt at resolving them, and understanding what causes the problems and why the solution works.

> I have plenty of experience to know.
So do I. However, I considered the problems, and their solutions, part of the learning curve. It's not like dual- or multi-boot will never create any problems ever again for me; it's just that I have learned enough to understand what goes wrong, and how I can recover.

I have plenty of experience to know that there's no real reason to be afraid of multi-booting. In fact, these days, **all** my computers are multi-booting (some even have *two* Windows XP systems installed, in addition to two or more Linux systems). I install a GRUB version that I compiled myself, into a separate, small boot partition, and no matter how often I install or reinstall any Operating System, as long as I leave my boot partition intact, I can recover. Worst case scenario, short of accidentally zapping the boot partition, is having to boot from a Slackware CD and reinstall GRUB onto the Master Boot Record. In fact, even if my boot partition gets damaged, I'll boot from a Slackware CD, copy the GRUB files back onto the boot partition again, and reinstall GRUB.

---

### Post by BXA121 on 2008-03-04
ok so so far ive updated my drivers and im using the new ntfs driver to read/write to my ntfs drive. 
i decided to reinstall win xp. however, when i installed - it didnt boot! and my grub was dead ( which i expected).

i tried the numerous ways to fix the damn thing ( using the recovery console in winxp) to no avail. 
i got so frustrated that i used my ubuntu live cd and deleted my win xp partition for good! 

thats right i dont have windows anymore. well, kinda, well read on...

i expanded my linux and my work stuff partitions to fill the space. 

using the vitual box program i installed winxp as a virtual drive - ok so i out winxp in a jar for use when i need it..

i got ms office 2007 on it and i also downloaded knoppix, damn small linux and also vixta - ill try them out using the virtualisation engine. 



the next thing is to get everyone elses computer running linux.

---

### Post by ubuntu27 on 2008-03-04
> **BXA121 said:**
> ok so so far ive updated my drivers and im using the new ntfs driver to read/write to my ntfs drive. 
i decided to reinstall win xp. however, when i installed - it didnt boot! and my grub was dead ( which i expected).

i tried the numerous ways to fix the damn thing ( using the recovery console in winxp) to no avail. 
i got so frustrated that i used my Ubuntu live cd and deleted my win xp partition for good! 

thats right i dont have windows anymore. well, kinda, well read on...

i expanded my linux and my work stuff partitions to fill the space. 

using the vitual box program i installed winxp as a virtual drive - ok so i out winxp in a jar for use when i need it..

i got ms office 2007 on it and i also downloaded knoppix, damn small linux and also vixta - ill try them out using the virtualisation engine. 



the next thing is to get everyone else's computer running Linux.


You're cool :guitar: fast learner, and an adventurer. Those are good qualities (and a must for Linux user :P ) . :)

Good luck with trying to put linux on your families or friends computer. Don't push them too much.

---

### Post by jahvascriptmaniac on 2008-03-08
> **ubuntu27 said:**
> You're cool :guitar: fast learner, and an adventurer. Those are good qualities (and a must for Linux user :P ) . :)

+1 :KS ! I like people who learn fast and (because ?) are ready to spend a small amount of time googleing about their issues :-).

As long as you handle tha maintainance job, your family should be ok migrating, mine didn"t have any problem, even if they're far from being geeks :-)

If you want to (greatly) improve your compiz experience, try this :
[http://ubuntufromscratch.wordpress.com/2007/12/24/compiz-fusion-update-ubuntu-710/](http://ubuntufromscratch.wordpress.com/2007/12/24/compiz-fusion-update-ubuntu-710/)

It expplains how to install compiz with unofficial pluggins, and also the default config of their compiz package is MUCH better. I just followed the steps, exept that when uninstalling the old compiz, I checked that I hadden't any extra compiz package I would have added manually and that would conflict. You'd better do that If you installed extra stuff.

---

### Post by BXA121 on 2008-03-09
hey guys, thanks for your help! 

im pretty happy with the way my 3d desktop is working right now - i still havent fooled around with all the different plugins. 

i guess i can do that later. 

right now im on holiday - we plugged my computer into my bros new hd tv - works a dream - its so cool getting 3d desktop running for everyone to see. 
i guess my family will warm up to it soon.

---

### Post by mimada on 2008-03-09
Hi There,

If you have the hard drive space I recommend you try out VirtualBox (VirtualBox.org). You can install Windows XP (or most other operating systems) within Linux (it's really cool to see it booting inside of a window). This is if you have a few windows apps you still need to use. VirtualBox is naff for Windows 3D games but it runs a lot of stuff I couldn't get going on Wine. It does run a lot of older windows games (like Starcraft or Diablo).

Another advantage of VirtualBox is that you can clone your virtual hard drive. If something goes horribly wrong with your virtual machine, dump the old virtual hard drive and make a new one from the backup. It saves me hours from having to reinstall everything from scratch.

The disadvantage of using the virtual machine is that it is slower than a direct install and it can use up a lot of hard drive space. I'm currently playing with different linux distros for kicks.

Have fun,
Mike

---

### Post by BXA121 on 2008-03-12
> **mimada said:**
> Hi There,

If you have the hard drive space I recommend you try out VirtualBox (VirtualBox.org).... I'm currently playing with different linux distros for kicks.

Have fun,
Mike

I have installed this and fiddled with winxp and also knoppix as well as DSL. Installed Office 2007 so i can reproduce this for the rest of the family if they moan.
All very interesting - tried to get usb drivers on and a way of communicating with the virtual os's with no avail - oh well ill just keep going till I break something lol.

---

