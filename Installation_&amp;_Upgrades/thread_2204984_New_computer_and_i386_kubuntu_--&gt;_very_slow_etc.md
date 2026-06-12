---
title: "New computer and i386 kubuntu --&gt; very slow etc.."
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by bjngchn on 2014-02-11
I'm replying myself. Anyway here is the beginning of the story. [http://ubuntuforums.org/showthread.php?t=2204172](http://ubuntuforums.org/showthread.php?t=2204172)  Bought a new laptop and tried to install an alternative CD version of kubuntu with amd64. Many attempts failed, asked here. Noone can help. Then I decided to help myself by trying i386. Everything seems to work now, except that it is extremely slow. I was able to get firefox and other programs with sudo comand without problem, and it was not slow. Also did sudo apt-get update without problem (but when restarting the computer I get DRDY UNC ..Emask...error whatever it is, so maybe updates are not installed correctly?).......................... Now the main practical problem is, although sometimes it works at normal speed sometimes it freezes for no reason. ... I do a sudo job,...it has problems and can't do it. While waiting computer is frozen. Also I start firefox, I see a shadow icon ofit, but not the program itself. Eveything frozen. When I have a chance to use command line I try to kill it. Yes, it is killed according to ps ux, but shadow on the panel stays there. Computer still slow. ....... I disabled all desktop efects to increase speed. Still it almost freezes because of a very small thing. What now?  I will only use a few programs, like firefox, pdf, image, sound,  viewing/editing.. So I can uninstall any program which is not absolutely necessary. BTW, can't remove kopete or kontact....Will linux die completely soon because of all these. Someone hate linux, because it is good.

---

### Post by bjngchn on 2014-02-11
None of thesudo commands which worked once (15 minutes ago) works now. For example I do sudo apt-get update. I get a long list of errors. Couldn't resolve extras.ubuntu.com  (whose fault is this?) .....then Failed to fetch ................., then some index files failed to download. .. Then E: Read Error -Input/output error.... then E: The package list or status file couldn't be parsed or opened. ................ 2 weeks wasted with this already. I don't understand why I have to spend so much time trying everything learning nothing, getting crazy, noone helping. I hate windows but there is no linux anymore.

---

### Post by jdeca57 on 2014-02-11
The question is of course what hardware and why an alternate CD. Did you try a live image on usb (any modern computer can boot from usb).
Is the problem related to UEFI? Simply disactivate it. UEFI boot is not neccessary in order to use Ubuntu. (It's even not necessary for Windows 8, but that's another story)

---

### Post by bjngchn on 2014-02-11
I don't understand hardware much but it is samsung and has corei5. Must be much more powerful than the laptop I'm using right now (where I was able to install a recent kubuntu without problem)....Why alt-cd, because it is encrypted. No encryption means no protection... Tried uefi and alternatives (CMS, uefi and legacy OS). new bios is very uncomprehensive. When you change something, it is not clear what happens, and new options arise. When you click something you can't go back. Such nonsense. Some stuff can't be modified, then why are they there. .... There was a windows inside it, probably windows8, but I didn't try to install it. Immeadiately put kubuntu disc to format the whole disk. But got many problems and everytime (different versions of kubuntu) there is a different problem.

---

### Post by mastablasta on 2014-02-12
first off new computer i would try AMD64 image and latest version (13.10).

secondly what do you mean alt-cd is encrypted? there is no encrpytion on it. if you mean to encrypt your disk then you can do that with normal desktop disk during instalation. alternate CD was there for those that had old mashcines with low ram that couldn't do graphical install. instead mini-iso (netinstall or barebones install) is now used in those cases.  i suggest not to use those if you are not versed in linux.

md5sum is there so you can check if the downloaded image is exactly the same as the one on the server. ot make sure the download is good. and there are md5sum hashes for desktop images as well as for server and so called mini.iso images.:
about: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
hashes: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

secondly your post is confusing. if you want help you will need to give at least some basic information about hardware as well as at least some informaiton how you installed on the disk (default options, manual configuration...). 
the slowness can be due to bad graphics card drivers. hard to say as you don't provide any data on system. see this: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

more on the slowness check the ksysinfo monitor and see what is hogging the CPU. you can also use top command.

furthermore your error does not mean that sudo is not working, but that apt-get can't reach the repository server. this can be caused by bad internet connection with server - check network connection, change repository server and see if that helps. or the local server could be down. happened to me once as i couldn't connect to local server. i changed to server from neighbouring country and it works well.

finnaly if you installed on UEFI mashcine i believe there is more explanation in link in my previous response to your question. boot partition should be unencrypted. you would normally enrypt only home.
more on encryption here: [https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)
and here: [https://help.ubuntu.com/community/FullDiskEncryptionHowto](https://help.ubuntu.com/community/FullDiskEncryptionHowto)
and some more info here: [http://askubuntu.com/questions/366749/enable-disk-encryption-after-installation](http://askubuntu.com/questions/366749/enable-disk-encryption-after-installation)

depending on why and how you want to encrpy your data choose the correct option.

---

### Post by bjngchn on 2014-02-17
{I don't understand everything. and I don't want to learn anything because I can't learn: it means getting a degree in computer science.  I'm trying to save time, not to lose time. of course if I'm born again I will start learning computers early in life, so I can save years later. } So I have a new question. There is no alt-CD in new versions(?) I read here:  [https://www.eff.org/deeplinks/2012/11/privacy-ubuntu-1210-full-disk-encryption](https://www.eff.org/deeplinks/2012/11/privacy-ubuntu-1210-full-disk-encryption) something like this: new versions (like 13.10)  of kubuntu have an option for full disk encryption. Is this correct? I don't want to worry about encrypting boot. It must be arranged by kubuntu.  I want the best (most encrytpted) version possible; so I won't need to worry about data leaks in the future  (even if that data is not important).   If 13.10 has FDE option, I will try this too. Maybe this time it will work.

---

### Post by mastablasta on 2014-02-18
if you are not wiling to learn then why are you asking to be tought a thing?

no there are not alt-cd in new versions. only minimal install iso (so called net install that is text based)

normal desktop verison can do encryption as well. read the provided links.

alternative version was ment for users that had weak mashicnes (not enough RAM, since all system loads into ram on boot) and couldn't boot into graphical interface but could then use text instaler to install the OS to disk and then boot into graphical interface. [B]it had/has nothing to do with disk encrpytion. 

[/B][I]for example: i have an old notebook with 256 MB ram of which 32 MB is taken by GPU. while i can boot into graphical interface when i try to install the installer would crashes as it ran out of RAM. however using text based installer in alt-cd i can perform the instal and then boot into the OS form hard disk as i could before from CD.

[/I]if you do not trust default encrpytion that is offered to you during install you can always use trucrypt or similar.

beware that if critical section of disk gets corrupted you will loose all your data. so make sure you have a good backup policy.

---

### Post by bjngchn on 2014-02-20
I was able to install 13.10.  it worked for a few days. Now I cant use firefox because it doesnt open for no reason. Previously I used remove and then  install commands to fix this problem although it was not really removed when I requested and it was not reinstalled and preferences were kept as before. ANYWAY MAIN PROBLEM now seems to be that any sudo apt-get .. command doesnt work and ends with : E: Read error - read (5: Input/output error)E: The package lists or status file could not be parsed or opened.WHAT NOW.Can the source of problem be modifying firefox preferences (and about:config ). Things work well and suddenly everything is screwed.  Computer is new. Update and install worked soon after installing kubuntu. But now it just doesnt. Maybe there is a trial period for something and it ended(!)

---

### Post by mastablasta on 2014-02-21
nope. hard to say what you did. i hope you didn't uninstall some crucial packages or something like that. it seems one of the updates didn't finish propperly. i would say open a new thread and describe the problem as best as you can. with all error messages. 

a non working apt-get is rare and since it is such an important part of the OS the error should be resolved.

---

### Post by fdrake on 2014-02-21
in the terminal try
```
sudo rm /var/lib/dpkg/status
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo rm -rf /var/lib/apt/lists/*
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install -f
sudo apt-get install --reinstall firefox
```

---

### Post by bjngchn on 2014-02-26
Thanks for replies above. It worked (but not at the first attempt). btw aptitude command is not understood by the system. Anyway things work.... ............Computer is a little bit noisy,  so I wanted to remove some unnecessary programs. I never use kmail, so I decide to uninstall it. It says, 300MB will be freed. This is great. Then I realize instead of removing kmail, all programs are being removed including dolphin. What a nonsense. If I don't use email, I also can't use anything else. A similar problem created before with firefox. If I edit firefox, whole system will be screwed, not only firefox..This reminds me the connection between windows and IE. they can't be separated. .. sudo apt-get update works, but any other thing doesn't work, maybe because I tried ctrl C and ctrl Z to stop removing essential programs.  What now, remove kmail..ok changed mind. But can't reverse things as easily. ..... i mean, if bad things are likely to happen with uninstalling a program, I should be informed about it. ..maybe if I didn't stop the removal, I wouldn't be open this computer again, because everything would become unworking.

---

### Post by mastablasta on 2014-02-27
> **bjngchn said:**
>  Then I realize instead of removing kmail, all programs are being removed including dolphin. What a nonsense. If I don't use email, I also can't use anything else. A similar problem created before with firefox. If I edit firefox, whole system will be screwed, not only firefox..This reminds me the connection between windows and IE. they can't be separated. ...

well yes and no. the programs in linux share libraries. windows programs do that as well only in windows porgrams often bring their own version of libraries (which might be the same as windows version) with them. this makes them a lot bigger compared to linux progams. however even in windows you will find that it is difficult to remove some programs that come with it by default and are part of the OS.

in this case the Kmail itself is probbaly only a few MB big (4 or 5) and then shares libraries with other programs. i too wanted to remove it and came to same conclusion. so i just don't use it as it is part of the whole desktop package. it's integrated. note you can actually remove it but then somethign else willnot work proppely, so you will have to remove that and when you remove than something else will work strange etc.
 
in linux you can run program separatelly from others i believe by putting all necessary libraries/dependencies together for them to run. but they are never completelly separated. this makes them smaller, faster to run as well as brings some other benefits.

there is an experiemntal version of one linux distribution that will try to do just that. install each program into it's own folder with all dependencies and such inside.

similary there is a version of BSD operating system called PC-BSD that also uses this method via PBI packets. they include all libraries and dependencies. as a result they can be quite big.

if you want a smaller system you can do it in reverse by adding the minimum KDE and then add only applicaitons you want.

changing firefox should mess up the OS, since firefox settings and such are in your /home folder.

---

### Post by bjngchn on 2014-02-27
Thanks for info. I can't open the computer now (a topic of another thread). I wonder what would be securit(privac)y implications of this. For example can a firefox crash/heaIth report, or updates can be an opportunity to steal user data related to all these applications. ... Western system can't allow true securit(privac)y , because then not everything would be under totaI controI. I wonder how this affects normal linux users. Maybe computers have hidden hrdware, or what we believe to be encrytpn has a backdoor key etc. .. I shouldn't have to worry about this more than many other people, but it costs me a lot of time already.

---

### Post by mastablasta on 2014-02-27
> **bjngchn said:**
>  Western system can't allow true securit(privac)y , because then not everything would be under totaI controI. .

what do you mean?  you can see the code and if you see any holes or anyhting that is reporting to someone form your system you can notify or patch it. this is different in windows where code is closed an can't be seen. any backdoors in windows can't be patched as we do not see the system code.

you can also build ***Linux from scratch ([http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)) ***if you are paranoid and have some time on your hands...

that leave the internet and data tranfers - but you can lock encrypt your data for those transfers.

---

### Post by bjngchn on 2014-02-27
I read many years ago from somewhere that Germany wanted to use gpg, or pgp, and US was angry about it... I read recently somewhere western system tries to add something (cIipper?) to hrdware (chips?) something (electronics?) which spies on everything...Many years ago I read from somewhere one of the founders(?) of moziIIa was angry about disrespect of the company for user privacy, and left (?);... My memory might be lying. But there is an effort to control every data. Even Ggl officially says they are trying to index all data in the world. I trust linux more than most things in life, but I don't know enough to justify this myself... All these are general stuff, not about me in particular. So I'm not paranoid, but too much power in the wrong hands (or in any hand) is dngerous... In this particular case, i just don't understand why I can't uninstall kmail safely. Even windows doesn't allow such a thing (either uninstall is made possible safely or not allowed).... Opensource is much more trustable, but this doesn't mean in my opinion  it can't do bad things without many people being aware of them.

---

### Post by SeijiSensei on 2014-02-27
It seems like you've been spending a lot of time reading about Linux on sites full of people with extremist views on computing.  Personally, I'd suggest investing that time figuring out how to install and use Ubuntu and less time worrying about the NSA.

The primary reason why open source software is considered safer is the "many eyes" theory.  Open source code makes it difficult to hide malicious activities from savvy reviewers.  Now obviously this only works if informed people actually read the source code, but the Linux kernel developers certainly qualify.

---

### Post by mastablasta on 2014-02-27
you are confusing many things. even if chip could captre your data what does it help the entity if data is encrpyted with strong encryption?
kmail - if you really want to understand whyx you can't remove it then i suggest to read up upon desktop environments (DE).
idea of DE is, among others, to package all the most commonly used things together. since Kmail is packaged in KDE that Kubutnu provides it can't be easilly removed without removing other components. as i said you can actually remove them but since other parts of the DE use parts of Kmail they will miss Kmail and will report that as an erro.
why are they integrated - let's say you receive an email invitation to important meeting, you accept it, then you turn off your mail program. but the calendar pogram that will tell you the hoolidays, time etc is still on. well it should show the meeting as well. so you can see it there. 
[http://userbase.kde.org/KMail](http://userbase.kde.org/KMail)
> KMail is the email component of Kontact, the integrated personal information manager from KDE.
now
> Kontact is the integrated Personal Information Manager of KDE, but can be used with other systems as well. It supports email, address books, calendars, tasks, news feeds and much more. 
 

and then:
> Components
KDE Kontact supports various groupware servers. When using these servers your workgroup has access to features like shared email folders, group task lists, calendar sharing, central address books and meeting scheduling. 
Kontact consists of the Kontact PIM back end and the graphical applications connecting to the back end. Special 'agents' (say a facebook agent) are employed to get new data in and merge it in the existing data set (for example contacts, news). Due to the clean infrastructure new agents are easy to develop. 
These programs together form Kontact: 
&#8226;Akregator - Read your favorite feeds
&#8226;KAddressBook - Manage your contacts
&#8226;KJots - Your ideas organised in a Notebook
&#8226;KMail - Mail client
&#8226;KNode - Your usenet mail reader
&#8226;KNotes - Sticky notes for your Desktop
&#8226;KOrganizer - Calendar and scheduling, Journal
&#8226;KTimeTracker - Track how much time you spend on various tasks
&#8226;Summary - Summary screen in Kontact

So as you can see Kmail is only a subcomponent of a much larger part fo the whole desktop environmet . as mentioned you can install the oS with no desktop environment and then only install minimim components that are needed. however the user experience will not be the same.
and to answer why you are allowed to remove it all -- because it is a free system in every way. it frees the computer. you can do anything you want with it. even remove the whole kde and replace it with icewm for example. you can also remove part from kernel you do not need and create your own OS that will run only on your mashcine.

---

### Post by bjngchn on 2014-02-27
Ok it looks like joining kmail with other things may be completely legitimate. But there should be warning in red saying, you computer might stop working after this operation, and you should type "n" unless you are sure what you are doing.. ........ I don't spend much time on conspyracy stuff, and it is difficult to learn linux. But sometimes I get useful info on this forum, and internet search; when there is a problem. It would be much better if we get linux education in early life, worldwide.

---

### Post by bjngchn on 2014-02-27
Anyway let me type the current problem here too: I type encryption pw, then the next screen, instead of showing graphical login screen it says:   The disk driver for /dev/mapper/kubuntu--vg-swap_1 is not ready or nor present. Wait, Skip, or Manual recovery. None works..... This happened after I tried to uninstall kmail, and then ctrl+C to stop it. After this, in that session, firefox continued to work , but other programs, like terminal, dolphin, kaffeine,... didn't work anymore... most sudo actions were problematic too. This was yesterday, and today ** I can't open the computer graphically. I can only  do command line login by typing CTRL+ALF+F1, and act like root using command line using sudo command, install/uninstall with apt-get etc; or wait to see the usual login screen but instead it gives the error:   The disk driver for /dev/mapper/kubuntu--vg-swap_1 is not ready or nor present. Wait, Skip, or Manual recovery...  ** So I need to know , how to fix this with command line, root access, and internet connection. ......................... If this problem happens because of trying to reove kmail and asociated things (unintentionally), there must be a fix by adding them back.... Maybe remove them and add back?? Aren't install and uninstall opposite of eachother.

---

### Post by bjngchn on 2014-02-27
**Update** Ok, currently I can login graphically (after some help in another thread), but there are problems related to display, kwin etc. It looks like just one more thing missing to make things work... and it may be ok to use the computer with errors showing up all the time. .. I don't understand why, sudo apt-get install doesn't fix problems by repairing what is missing or problematic. Any other magic commands, similar to  sudo apt-get install command, which might accidentally fix a problem(?) What do I to fix kwin for example.

---

### Post by mastablasta on 2014-02-28
if i was at your place i would remove the whole desktop like so (MAKE SURE YOU SELECT THE CORRECT VERSION FOR YOUR OS): [http://www.psychocats.net/ubuntu/pureubuntuprecise](http://www.psychocats.net/ubuntu/pureubuntuprecise)

and then reboot - should throw you into Command line only. then log in and install kubuntu-desktop metapackage using apt-get command. alternately you could install only base KDE and then add the things you want/need. 

there should be a fix command for apt get but i am not sure exactly how it works. but you can read it in man page. just type > man apt-get into console.

you may also wait for a better advice. perhaps there is a way to solve this in an easier way.

---

