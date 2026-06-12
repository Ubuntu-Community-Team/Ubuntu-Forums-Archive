---
title: "Installing Ubuntu for the first time in my life log"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by jorges on 2007-05-01
** This is my own experience with Ubuntu, Im not saying it is bad, Im not saying it is good. I wrote this while i was installing... **

Installing Ubuntu for the first time in my life log
Im also installing linux for the 1rst time in my life
I want to learn PHP and i want to do it in its native platform, I've been an ASP developer for a long while.

Armed with SwitchingToUbuntu/FromWindows as documentation.
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

Armed with Ubuntu 7.04 Server Edition CD

Installing in a reasonable new more than average Intel Motherboard, Intel P4 2.8 Processor, 120GB 

SATA HD, 1GB RAM, No Audio - it used to be a very stable production IIS server but homemade.

- I want to try the LiveCD option that will let me "...try Ubuntu without installing it, or modifying your computer in any way" according to SwitchingToUbuntu/FromWindows documentation.
- Insert the CD and it boots very fast to Ubunto menu
- Unable to find the LiveCD option - 1st ANNOYMENT
- Search Google for discussion groups for a while with no luck - 2nd ANNOYMENT
- Take out my HD and insert my handy 120 SATA "erasable HD"
- Start over
- Selected Option 1: Install to the hard disk (maybe LiveCD option will come a few steps further)
- Auto detect keyboard layout wizard, it works perfect (i guess) [1 for linux, 0 for Windows]
- Configure the network, asking hostname: jsblinux
- Partitioning a disk: Use entire disk (other options looks unfriendly)
- Configure LVM ... YES (whatever it is)
- (At this point i know i will never be asked for liveCD option)
- Select my time zone .. ok (it knows it because i provided my country) [2 for linux, 0 for Windows]
- Configure the clock .. set to UTC .. yeah wharever
- Full name: jorge s
- username for the account: jorge (the default, i will live it this way) ... thought for a second about the difference between jsblinux and jorge but forgot inmediately.
- Password for the user jorge: ********
- Software Selection: DNS Server (yes), LAMP Server (No) whatever it is.
- Installing for several minutes
- Finish the installation (that was quick in average), half a windows install. My Cd was ejected and 

here comes the first reboot.

Ok, let's see what happens ...

Starting up ...
Loading please Wait ...
unable to read config index 0 descriptor/all
can't read configurations, error - 84
kinit: name_to_dev_t (/dev/mapper/jsblinux-swap_1) = dm-(254,1)
kinit: trying to resume from /dev/mapper/jsblinux-swap_1
kinit: No resume image, doing normal boot...

- will wait for a while ... 2 minutes ... (thinking about rebooting again) ... 5 minutes - 3rd 

ANNOYMENT
- just before i press RESET on the machine, more text appeared (lucky me that i did not reboot?) ... port failed, exception emask 0x0, 0x2 frozen, blah blah blah ... 2 minutes ... 4 minutes ... 4th ANNOYMENT (thinking about rebooting again) ... 7 minutes ... now screen is full of exception emask's
- black screen! (something is still going on, is it?) ... 2 minutes ... 5th ANNOYMENT ... 4 minutes ... the HD is moving so i guess i'll just wait a little more ... 10 minutes and the screen is still black but hard drive light is on and the hard drive is making noise similar as the sound it does when deleting large amount of data ... let's wait a little longer ... hd light blinked for a second .. it gives me hope ... fans are working at maximum capacity ... 
- 15 minutes (going for coffie) ... 17 minutes ... Googling for "exception emask" found Sata1.00 : exception Emask 0x0 sAct 0x0.... - LinuxQuestions.org ... lets's see .. it talks about "fairly old hard drives" .. um ... Is it my HD? .. let's wait a little longer ...
- Ok. patience is over .. power off!

- Power on ...
- Starting up ...
- (trying to remember where did i put some old Hard drives)
- 5 minutes 
- remember it
- Exception emask again
- Power off.
- Found 2 dusty n old HD's in the dark side of my closet

Hardware Configuration Change

Installing in a reasonable new more than average Intel Motherboard, Intel P4 2.8 Processor, *** OLD M40GB MAXTOR ***, 1GB RAM, No Audio - it used to be a very stable production IIS server but homemade.

- Power on
- Strange HD noises, computer restarts several times
- Power off
- Flag MAXTOR HD for destruction

Hardware Configuration Change

Installing in a reasonable new more than average Intel Motherboard, Intel P4 2.8 Processor, *** OLD BARRACUDA ATA III HD ***, 1GB RAM, No Audio - it used to be a very stable production IIS server but homemade.

- Power On
- Ubuntu Menu
- Option 1: Install to the hard disk
- Keyboard wizard
- Hostname: jsblinux
- Partition: Use entire disk
- Format partitions: yes
- (starting to think i did not select yes for formating partitions last time and maybe my 120GB SATA 

is not faulty ... hope so)
- Clock to UTC: yes
- Name of new user: jorge s
- username: jorge
- password: ********
- installing ...
- Software Selection: DNS Server (yes), LAMP Server? ... this time Google?q=what is lamp server
- Wikipedia (L)inux (A)pache (M)y SQL (P)hp ... Oh god .. **** yes!
- Installing for several minutes
- While Im waiting ...  Google.com?q=what is UTC
- Coordinated Universal Time (UTC) is the international time standard ... I knew it ;)
- Finish the installation (again, it was quick), longer than before but quicker than windows (up to this point i must say). 
- My Cd was ejected and here comes the first reboot. The CD tray did not auto close on rebooting .. i like that...

- Starting Up ...
- Lots of [OK] tests :)
- 2 minutes ...

/// 1rst conclusion ///
You must have another computer connected to the Internet while atempting to install linux

- 5 minutes ...
- Lighting a cigar
- 10 minutes it is still stucked on: * Running local boot scripts (/etc/rc.local)
- Black screen!, and HD working like crazy
- Waiting ... (wondering that maybe in my first installation was just a metter of waiting more?)
- 7 minutes - 6TH ANNOYMENT
- 10 minutes ... double check the screen to see if there is a prompt hidden in the corner ... nope.
- 15 minutes, screen is still black, HD is still working, fans are at full speed ... waiting
- its extreemly ANNOYING NOT HAVING A PROGRESS BAR!!! [Linux: 2, Windows 1]
- 20 minutes and counting ...
- Google.com?q=installing ubuntu black screen
- Found people that have been waiting for more than an hour to the black screen to disapear [http://www.ubuntux.org/black-screen](http://www.ubuntux.org/black-screen)
- Start to loose hope
- 30 minutes ...
- Enaugh!
- Power Off!

- Last try ...
- Power on
- Stuck on * Running local boot scripts (/etc/rc.local) [ OK ]
- 10 minutes ...
- 15 minutes
- Black screen!
- No hope
- Power off
- Insert old windows 2003 server HD
- Power on
- It works.

It will be until a next time

---

### Post by tgm4883 on 2007-05-01
Why are you using the server cd?

---

### Post by PilotJLR on 2007-05-01
Agreed - try the desktop install CD. You have the wrong media.

---

### Post by jorges on 2007-05-01
Im using the server cd because I need PHP, My SQL, DNS, FTP, APACHE, etc... and it says that the server version come with all this pre installed ( LAMP Server is called ) .. since I am new to linux I didn't wanted to have problems installing each of this server software and instead i wanted to run Apache and try some php code asap.

Jorges

---

### Post by PilotJLR on 2007-05-01
A "server" install is meant to be headless, so it will NOT install a graphical environment at all.

Just install the desktop version... then you can very easily add apache, mysql, php, etc through a single apt-get command. (Or graphical synaptic, if you prefer).

Same kernel, same security... only in Windowz does server = graphics   :-)
Good luck!

---

### Post by PilotJLR on 2007-05-01
Unless you WANT it to be headless... so you do developing and testing elsewhere, and make this box a pure server only. I just assumed you didn't want that.

---

### Post by jorges on 2007-05-01
I posted this log in the hope Ubuntu developers have a detailed user experience, from what i saw in this installation i would suggest:

1. Provide a method to check the HD and alert if it is damaged.
2. Provide a constant progress bar during the installation
3. Do not forget about the fact that newbys doesnt know anything about linux and avoid using terms like "LAMP server"  without an explanation of what it is.
4. Dont forget that most of the users does not read and even the ones that read (like me) can easily get overhelmed with all this enormous amount of help avaliable for this OS.

jorges
PS. I will try the desktop version as you suggested but i'm afraid it will be a long way until i can get Apache, Mysql, Dns, ftp installed....

---

### Post by jorges on 2007-05-01
I want just a server, I will not use the computer for anything else than server tasks.
Jorges.

---

### Post by jorges on 2007-05-01
by the way, i never complained about lack of graphical stuff.. im pretty compfortable with a prompt ... the problem is i never got there, if you are refering to the progress bar, it doesnt need to be graphical ... but is fair to think that a black screen for more than 30 minutes plus unlimited threads about "black screen of death" indicates malfunction.

---

### Post by serialdae on 2007-05-01
Did you test the media after download to insure it was ok?

MD5sum or anything?

---

### Post by tgm4883 on 2007-05-01
Well you want to test the media from the cd boot screen.

Also, if you want the developers to actually see this then good luck, as most do not frequent these forums.

---

### Post by jorges on 2007-05-02
I didnt tested the media, i will... i dont spect anything at all, i just posted my story, that's all.

---

### Post by Munya2007 on 2007-05-02
Okay, I downloaded Kubuntu 7.04 (MD5 Hash is okay) file size about 699MB . I have burned an ISO image to a regular CD-R disc to be used for installation.

1 Question: I am new at Linux, especially Kubuntu 7.04 and would like to learn about Kubuntu 7.04. For first timers which Linux version would be better Kubuntu 7.04 or Mepis 6.5?

2 Question: Can I install both versions of Linux: Kubuntu 7.04 and Mepis 6.5 as a dual boot?

3 Dumb Question: Can either Kubuntu 7.04 or Mepis 6.5 be installed indiviually as a clean install on a brand new hard drive in a new PC that I have just finished building?

---

