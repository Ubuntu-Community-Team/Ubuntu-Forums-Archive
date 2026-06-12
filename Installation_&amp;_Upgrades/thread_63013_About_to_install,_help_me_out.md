---
title: "About to install, help me out"
date: 2005-09-06
forum: Installation &amp; Upgrades
---

### Post by Orion2014 on 2005-09-06
Ok, heres the scoop. Im almost done DLing Hoary and im thinking about doing a dual-boot with my main desktop. heres my current setup.


Hard Disk (2)

main-WD 40GB with Windows 2000 Pro on NTFS

secondary-WD 2.5GB with just BU Files and NTFS

What i want to do is put hoary on my secondary HD, so its easy to wipe, and then i can remove it quite easliy from my system if i wish to.


Will my 2.5GB hdd hold hoary? 

And once installed, what do i do about my V.92 modem, will it be compatible? Its a Conexant SoftV.92 modem.

---

### Post by Orion2014 on 2005-09-06
Anyone gonna help me out, im dyin here!!! ](*,)  ](*,)  ](*,)

---

### Post by wvslkr on 2005-09-06
The hardrive will work, but you won't have much space left over.  About 2 gig used by install.  You will then be able to free another 200-300M by dumping the apt-cache.

Sorry I can't help with modem.  Try a forum search on  conexant and see what turns up. 

Hope that helps you.  GL :)

---

### Post by Orion2014 on 2005-09-06
That helps alot, thanx. Really, if it takes 2GIGS then thats fine, as i keep my windows disk SPOTLESS (capacity is 37.999999GBs, free space is 33.789564GBs) and i can designate a folder on my windows disk for linux  to use.


so that should work.

---

### Post by John.Michael.Kane on 2005-09-06
linux archive-copier/copy=flase should help you save some space. 

wvslkr wow did not know that was their  ](*,) 

however i will still give azz credit for the posting of the comand as he did bring it to light atleast for me lol.. ;-)

---

### Post by wvslkr on 2005-09-06
The link [https://wiki.ubuntu.com/forum/installation/DiskSpace](https://wiki.ubuntu.com/forum/installation/DiskSpace)

---

### Post by rafakl on 2005-09-06
You will love ubuntu, and quickly find that 2.5 gigs are very, very small space for the things you will wanna do.

What about using a livecd instead??

---

### Post by Orion2014 on 2005-09-07
I do like ubuntu, alot!

Well, im going to use it strictly on the laptop that i havent yet recieved. I finished my beta-testing of it and now i wish to uninstall it from the dual-boot.


how do i do this? i want to remove ubuntu and the little start-up screen from the dual-boot thing it installed.

---

### Post by jabb0 on 2005-09-07
hey dude from what i can gather modems and Ubuntu (or any other flavour) just dont go that well together.
I have a conexant adsl modem, and it did look as if it was possible tog et it to work, from all the research i done.
However it sure as hell is nowhere near easy.
 
So i deceided to bump the buying of a router up my list of "Things To Buy".
 
Sorry this isnt exactly gonna be much help - but i thought id get my pennys worth in here :-\"

---

### Post by Orion2014 on 2005-09-07
Trust me, i know. NO linux version ive ever tested EVER worked with ANY dial-up modem i had. And mine is a very expensive Conexant V.92 (allows me to recieve phone calls while online)


So im just going to save Ubuntu for my laptop which will be strictly for HotSpots, which i hear wifi works great with ubuntu.

so someone PLEASE  tell me how to remove this from my dual-boot system. ](*,)

---

### Post by bogoliubov on 2005-09-07
I'm going to disappoint you. I don't know how to remove the dual-boot. If you don't have anything you need on the Ubuntu partition you can use some partition program in windoze I guess. About the boot loader, find out what type you are using and google aroun a bit...

When it comes to modems, Linux may work OK with "real" modems, eg not the so-called "win-modems". The latter ones are basically and interface and needs a specialized driver to work; drivers that the modem companies don't make for linux. I had problems with one such modem; finally I got hold of an older modem and that one "just worked"...

---

### Post by Orion2014 on 2005-09-07
*bump*

---

### Post by wvslkr on 2005-09-07
Just reformat the drive with whatever you used to get it ready for Linux.  To get rid of Grub run fixmbr from win.

---

### Post by Orion2014 on 2005-09-07
fixmbr....is that from the command prompt?

---

### Post by wvslkr on 2005-09-07
Yes, I am not sure if it will run from windows.  If not do it from the install cd.  If you have an old win95 or win98 boot disk you can also do fdisk /mbr  from the command prompt.

---

### Post by Orion2014 on 2005-09-07
[QUOTE=wvslkr]Yes, I am not sure if it will run from windows.  If not do it from the install cd.  If you have an old win95 or win98 boot disk you can also do fdisk /mbr  from the command prompt.[/QUOTE]


didnt work, says its not a recognized command. im running windows 2000 pro


will it work in command prompt, or do i actually have to REBOOT into DOS

---

### Post by wvslkr on 2005-09-07
I have never actually used it other than from the install cd,  but I would assume it would run from win2k as well.  You will no doubt have to do it as admin.  If you have too much trouble just google for a dos boot disk and run fdisk /mbr that will work just as well.

---

### Post by Orion2014 on 2005-09-07
Ok, i was able to get everything fixed. I had to boot from my Windows 2000 Pro installation CD, then go to repair (press r) then go to console (press c)

now, i had to go in and set a password for my admin account to do this, which made things a little complicated. (my admin account had no password, it just booted straight into the account.


then i pressed help to get the list of commands.

the proper command was "FIXMBR"


it ran its course, and in about 10 seconds, i had a new, fresh MBR. I then deleted the Linux partition in windows and its gone!

that simple.

they should sticky this, as i know others have had this problem as well.

---

### Post by wvslkr on 2005-09-08
Happy to hear you got it fixed up.

---

### Post by Orion2014 on 2005-09-08
[QUOTE=wvslkr]Happy to hear you got it fixed up.[/QUOTE]



thanx, and alot of credit should go to the technical support here. i had alot of help, and the community should be commended. in fact, as a member of microsoft (just cuz im a member of the MS IT Academy and a liscensed MCSE dosent mean i like them :wink: )

i have to say that the technical support here is faster and more friendly than microsofts, plus i can understand you guys, lol!

(microsoft outsources their technical support to afghanistan and pakistan, and i ca hardly understand them)

---

