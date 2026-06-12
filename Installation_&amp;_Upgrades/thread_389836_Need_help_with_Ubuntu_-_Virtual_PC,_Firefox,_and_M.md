---
title: "Need help with Ubuntu - Virtual PC, Firefox, and More"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by Thanh-BKK on 2007-03-19
Hello :)

I am very new to Ubuntu, yet not to Linux - have used SuSE 10.0 before. Right now i am running Ubuntu 6.06 in a virtual machine (Virtual PC 2007 under Vista Ultimate), i just installed it last friday and now i have a few quirks that i need answers to.

First, how come i can't upgrade Firefox? It's version 1.5. It's "check for upgrade" option is not available, "greyed out". So i went to the Firefox website and downloaded the 2.0.0.2 gz.tar file, and now that's sitting there. What to do with? I googled the issue, and found i need to install it to /etc or /opt. Fine... if Ubuntu would let me do that? Aparently i have "no permission to install to those two directories". Thanks for taking control off me, this is MY computer and i want to install them there, damn it!

So i gooled again for the "root" issue. Ebnabled the root account with password, and tried logging on to that. If Ubuntu would once again at least me do THAT? No! "The system administrator can not log on this way" or similar is the excuse Ubuntu gives me. WTF..??

So i unpacked the Firefox files to some random place where Ubuntu generously allowed me access to, and clicked the Firefox executable - and to my surprise, even tough i had downloaded a 2.0.0.2 version, it still opens as 1.5! And because i saved a couple of bookmarks, those were there too, so i see that Ubuntu flatly ignores what i just downloaded (and clicked!) and gives me the old version instead. What a crap.

Then next. I need some files from my Windows drives. As the internet works fine, the ethernet definitely should too - as that's where the internet comes from. So i created a folder and shared it. It never asked me to set any passwords or whatever. Then, from within Windows (host OS), i saw that folder there, double clicked it - and was prompted to enter a user name and password! I tried my Ubuntu user name and password, and they were rejected. So where should i get the password from? Ubuntu default something? 

Then i tried it the other way round, and, surprise surprise, it prompted for a password too..... again i never had been asked to create one in the first place, so how please do i transfer files between the two OS? 

Next thing. Why can't i set a screen resolution any higher than 1024x768? My monitor is 1280x1024 and it's an LCD, so why can't i just use that? I have SuSE 10.0, Windows XP and even Windows 95 (no joke!) running in virtual machines, and all of them allow me to go fullscreen. Why won't Ubuntu? When i shift to fullscreen, i got a large amount of "black" around the small Ubuntu "window" in the middle of the screen. Or is that for Ubuntu users to stick those yellow notes with quirk-workaround notes there? 

Then why won't my mouse wheel work in Ubuntu? No such problem in the other Linux (SuSE), and remember, they are running in virtual machines, ergo - identical "hardware" (which is exactly why i run them there - to compare different OS's under exactly identical circumstances without having to mess with a n-boot setup).

But most important are the first two issues - how does one upgrade Firefox as a non-root user, and if that is impossible, how does one log on as root (and please, no "command lines"..... if i want to use last-century stuff, i get a second-hand c64 and play with that.. i'm no geek, i just want to use a computer!) And what's with those passwords that i am never asked to create but that are required to get LAN access? 

Other than that, respect for an absolutely great looking Linux - Ubuntu's desktop has the best look of any OS that i've seen so far (it's simple beauty beats Vista's "Aero" by lengths!) and it was so far the easiest-to-install Linux i ever had in my hands (and i had quite a few). 

Kind regards.....

your Thanh

---

### Post by Thanh-BKK on 2007-03-21
Hello :)

I truly hope that someone can help me here.... nothing life-threatening but very annoying for me, and wasting tons of my time. So here goes:

I am running a relatively new computer with Windows Vista as it's OS. I am open to learning new things and i love to play with different OS, so i got Virtual PC and went thru a few tests with Ubuntu in there, which weren't all that good in results - various restrictions from Virtual PC and quirks in Ubuuntu itself made the experience worth to forget. if it wereb't for the stunning beauty of this  Linux version!

So i got myself the VMware "server" thingy, and set up new virtual machines there (much better hardware emulation, CD/DVD burning and USB support!) Got Ubuntu to run there after MUCH hassle - VMware is a b!tch compared with Virtual PC, the mouse jumping all over the place as long as the "tools" or "addons" aren't installed, and nobody ever replied to my last thread here "how to install things in Ubuntu". So with a lot of trial-and-error i finally got the thing installed, and enjoyed Ubuntu for a full 24 minutes in full resolution. 

Then i set the auto-login, like i did in the Virtual PC VM. And rebooted. 

And now it boots all the way to that point where the little round thingy comes up and normally the login screen would appear. At that point it freezes up for a couple of seconds (the animation in that round thingy stops) and then the virtual machine just closes, equal to a crash on a "real" computer. I get no login screen and no GUI and not even a command prompt. 

Now i would need some instructions on how to fix that? I believe my only chance is a command line, but how to get one? I need to press some keys during boot, yes? Which ones.... please, i'm normally a Windows guy :)

And what command do i need to type, once i GOT a command line, to fix the login? Or reset the default settings, as the auto-login is the only thing i changed. 

Please, Ubuntu users, help a Ubuntu newbie who fell in love with the most ebautiful Linux ever...... i really want it to work, if it satisfies me function-wise it'll be the standalone OS on my next computer... therefor i need to "test drive" it in the VM first........ 

Kind regards.....

your Thanh

---

### Post by Thanh-BKK on 2007-03-22
Hello once again.

I am still surprised why i never get a reply to my questions i post here, but maybe noobs are just ignored.... ok, can live with that. I am giving Ubuntu a g\final chance and if it screws up again i throw the disks in the bin and stick to Windows. 

Ubuntu 6.06.1 "Dapper": Installed it like SIX times already. Either it doesn't work right from the reboot (usually no GUI), or it stops working 1) after upgarding Firefox, 2) after setting it to "auto-login", 3) after attempting to install things like "gcc" and "kernel headers" which are required for the VM additions to install (and are NOT included on the CD and also not downloadable, and the versions on the 6.10 "Edgy" DVD are only partly compatible!) or 4) after making any ever-so-slight change to anything related to the GUi (resolution, theme). Always after reboot i get no GUI with various error messages or simply a resetting VM (system crash). 

Ubuntu 6.10 "Edgy": Starts fine from "Live  CD", when installing, goes to 24% and stalls. Can still move mouse, but clicking anything does not yield any effect, System basically stopped at that stage. Can't shut down either, have to "power off" the VM. Tried that four times already, always the same no matter what options i boot the live CD with (normal, safe Graphic, VM with IDE or SCSI drive). Also no difference if i attempt from the ISO image or the actual burned CD or DVD (Dapper = CD, Edgy = DVD). 

How can i disable the "update software packages" prompt? It's sitting there annoying me (Ubuntu working at that stage!) untill i let it update, downloading 200+ MB on my rather slow connection, and no longer working after update completed. I only found options to check "daily, weekly" etc but no such option "never". 

Please, i just want to enjoy Ubuntu as a working OS that actually allows me to do some work in... so far i wasted a combined four straight days in trying to INSTALL it! Plus another straight day in downloading the two versions (5 GB combined, thanks god i have no cap on my internet connection)! And the "no-matter-what-you-change-we-will-****-up-the-gui" thing is exactly what prevents 90% of the world's computer users to go Linux..... 

And not getting any replies in "help" forums doesn't "help" much either.......... 

Thanks anyway.

A frustrated Thanh

---

### Post by ffxr on 2007-03-22
i believe ""gcc" and "kernel headers"" are on the CD; add the build CD to your software sources list

have you tried installing with alternate CD? its a more robust installation method.

you can turn of automatic updates by going into software sources applet and untick the checkbox for automatic updates in the Internet Updates tab.

---

### Post by mahy on 2007-03-22
Please try to install Ubuntu 6.10 Edgy using the alternate installation CD. If it really doesn't work, chances are it's your hardware that needs some serious overhaul.

Does windows work on your current box? If yes, stop whining and try the Live CD elsewhere to see if it's faulty or not.

EDIT: in case you didn't know it, Ubuntu comes in a CD version too. <700 MB for one version.

---

### Post by bollix47 on 2007-03-22
If you really want someone to reply to your post(s) you must supply more information.  

In particular for the above problems you need to specify your hardware specifications.

What motherboard?
What processor?
How much RAM?
How much Disc Storage?
What video display adapter?

---

### Post by wpshooter on 2007-03-22
First thing I always ask is - have you checked the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by floke on 2007-03-22
Ok, so you 'never' get a reply? You have only made two posts prior to this, and the first one was only 3 days ago, so you're being a bit melodramatic. Also, your posts contain many questions so you might be better addressing one issue at a time to attract help. And also, many of the issues you raise have been addressed before. There's a search box in the top right hand corner of the screen that many people find useful. Maybe you would too.

Anyway, AFAIK...

* Firefox 1.5 can't be upgraded via the official repos since the upgrade has to be checked out to ensure it won't screw up the system. 

* For permissions to install you might have to use the 'sudo' command. That you didn't seem to know what this was indicates that you haven't done much reading on Ubuntu/Linux prior to trying to install it. Maybe you should do this before ranting in the forum. Sorry if using the command line seems so-last century to you, but most people don't seem to have any trouble with it. Maybe you should stick with Windows, since this is clearly the OS of the future.

* To install a new version of Firefox you might be advised to completely remove the previous version.

* I don't know anything about VM so can't help there. But if you want to test-drive then maybe try a LiveCD rather than a VM?

* If you have trouble with the LiveCD, try F6 from the menu and enter 'noapic' as the boot option (i think it's this - there are others too, search for forum for non-loading LiveCDs and you'll find loads of stuff). BTW: Some LiveCD's just don't work. Make sure you verify the integrity of the disc first (option on menu).

As you can see, several people have already offered their assistance, so please try to be more polite and you'll find that this is a very helpful and useful community.

Good luck

---

### Post by Jonne on 2007-03-22
You don't *need* to install all the vmware stuff to be able to run it in vmware. Sure, it sucks to have to use ctrl - alt every time you get out, but i haven't gotten the vmware stuff to work either.

autologin seems to give problems too, as it seems like some stuff isn't loaded when it does autologin. A workaround is using 'timed' login (set it to 10 seconds or so).

And, since you're running in vmware, it's trivial to create a snapshot right before you're about to mess with vital system settings. (or just copy the whole vmdk file).

I'm running Feisty and a server running dapper in vmware,, and I don't get any issues. (and I'm using Edgy as my desktop).

---

### Post by mouseboyx on 2007-03-22
It is possible that the CD is messed up or you have are running a x64 copy on and x86 machine or x86 on a x64 machine. OR PEBKAC [http://www.google.com/search?hl=en&q=PEBKAC&btnG=Google+Search](http://www.google.com/search?hl=en&q=PEBKAC&btnG=Google+Search)

---

### Post by leeley on 2007-03-22
> **Thanh-BKK said:**
> Hello once again.

I am still surprised why i never get a reply to my questions i post here, but maybe noobs are just ignored.... ok, can live with that. I am giving Ubuntu a g\final chance and if it screws up again i throw the disks in the bin and stick to Windows. 

Ubuntu 6.06.1 "Dapper": Installed it like SIX times already. Either it doesn't work right from the reboot (usually no GUI), or it stops working 1) after upgarding Firefox, 2) after setting it to "auto-login", 3) after attempting to install things like "gcc" and "kernel headers" which are required for the VM additions to install (and are NOT included on the CD and also not downloadable, and the versions on the 6.10 "Edgy" DVD are only partly compatible!) or 4) after making any ever-so-slight change to anything related to the GUi (resolution, theme). Always after reboot i get no GUI with various error messages or simply a resetting VM (system crash). 

Ubuntu 6.10 "Edgy": Starts fine from "Live  CD", when installing, goes to 24% and stalls. Can still move mouse, but clicking anything does not yield any effect, System basically stopped at that stage. Can't shut down either, have to "power off" the VM. Tried that four times already, always the same no matter what options i boot the live CD with (normal, safe Graphic, VM with IDE or SCSI drive). Also no difference if i attempt from the ISO image or the actual burned CD or DVD (Dapper = CD, Edgy = DVD). 

How can i disable the "update software packages" prompt? It's sitting there annoying me (Ubuntu working at that stage!) untill i let it update, downloading 200+ MB on my rather slow connection, and no longer working after update completed. I only found options to check "daily, weekly" etc but no such option "never". 

Please, i just want to enjoy Ubuntu as a working OS that actually allows me to do some work in... so far i wasted a combined four straight days in trying to INSTALL it! Plus another straight day in downloading the two versions (5 GB combined, thanks god i have no cap on my internet connection)! And the "no-matter-what-you-change-we-will-****-up-the-gui" thing is exactly what prevents 90% of the world's computer users to go Linux..... 

And not getting any replies in "help" forums doesn't "help" much either.......... 

Thanks anyway.

A frustrated Thanh

Well as you were already told if you tell us what machine you are trying to run Ubuntu on you might get some help. It is pretty hard to help some one if you do not know what they are trying to on what machine or format (32 or 64 bit), video card, processor, etc.

---

### Post by raul_ on 2007-03-22
How come you never get answers if you only have 2 more posts?

---

### Post by Thanh-BKK on 2007-03-22
Hello :)

Now i am indeed happy, having gotten some useful answers :) Please, guys, undestand me too - i am indeed completely new to Ubuntu (previously used SuSE) and as of yet i still could not enjoy it - but i spent a whole week's freetime (which is several hours every morning as i work in the afternoon) trying to get Ubuntu to work, so far without any success. So here comes some information.

My "Hardware" is a virtual machine, created by VMware Server (it's the latest version.... don't know what number as i am still at the office now). I use 512 MB of RAM, 4 GB of hard disk, 2 CD drives as "auto detect", sound standard adaptor, LPT and USB enabled. 

The physical machine this runs on has a AMD Sempron 2800+ CPU, 1.5 GB of actual RAM installed (that's DDR 400) and the physical harddisk that runs the host OS is a 120 GB Maxtor IDE, the one where the virtual machines are stored is a separate 40 GB Maxtor (also internal IDE). One DVD burner, onje DVD drive are present, either one can boot in the virtual machine, plus the option of mounting the iso image as an additional CD "drive". The host OS is Windows Vista Ultimate (32 bit). 

I have one virtual machine set up (Windows XP SP2) which works 100% perfectly. My plan is to get Ubuntu (either Edgy or Dapper) in a second such machine, SuSE 10.0 in a third and Windows 95 (yes...) in a fourth. I also have Virtual PC installed and there i got a Ubuntu "Dapper" working, however that won't support USb or CD/DVD burning, which is why i changed to VMware. After i got all four VM's done, i would uninstall the VMware server (hogs a lot of resources actually) and use VMware "Player" to run the VM's. 

However i don't get anywhere because the Ubunto won't let me!

About the Kernel-Headers, if i try to get those from the CD (or iso image), there is no version available. If i try to get them from the internet, a version is listed but won't download - (Error, could not fetch....) and when i try it from the Edgy DVD, the version is different and won't be accepted (different kernel? Sorry i don't know much about kernels....)

Same with gcc, there are several versions of it but regardless which one i chose, VMware's additions setup will complain that it (some component in my system) was created with a different gcc version, the closest i got was (i think i remember correctly) 4.03.4 when it asked for 4.03.1, the exact version it asked for was neither on the CD nor on the DVD nor on the internet. The strange part is that in a previous try it installed all those things right during the initial install, because THAT time the VMware additions installed straight without even asking for those extra things (i liked that with SuSE - it allowed me to chose packages befroe install even started).

About Firefox - sorry, i had no idea that i need to remove it first before installing the new version............. but i am afraid that when i remove it, again X will not work after, as seemingly everything i do will break the GUI. 

About SUDO - yes, i knew that, but my problem is that i don't know waht to put after sudo - the actual command :) As i said, i am a Windows idiot or "mouse pusher", and no geek in any way - i can build systems that outperform anything in the market but when it comes to software, i leave that to the software guys. I only want a standard Ubuntu working and usable, i don't need any fancy stuff on it - i'd even stick to the live CD if it would not need half an hour to boot :) 


Cd integrity - sorry, had no idea about that. Will try, but i am sure that at least the Dapper one works as it does definitely install a working system... just any customisation later, no matter how small, will break it.......... 

CD vs. DVD: When i downloaded it, Edgy (6.10) was only available as a DVD iso image, no CD. Otherwise i would have gotten the CD, believe me....... This too works fine as "live" but when installing, as mentioned, it stalls at 24%. That one would not work in Virtual PC at all (messed up graphics due to limitation in Virtual PC, sure not Ubuntu's fault there!) which is why i got the Dapper in first place as i read on the net that it (6.06) would work - and it does indeed.  

Auto login - i can live without it, but would have been nice if it worked. Will try "timed" as an alternative, maybe i'll set it to 1 second if possible :)

Alternate CD - well, as i have no actual "install" trouble with the Dapper i have, i think it should be fine....... it is usually the updates that break it (or the stuff required for the additions). I will definitely use the here mentioned way to disable the update prompt once i actually get a working system. 

And finally, yes i do need the VMware additions because without them, the mouse is jumping all over the place, almost completely useless. Also when typing something, i get a dozen letters instead of one....... 

I apreciate any advise i can find here, and again, please do understand my situation, i have spent a lopt of time on this issue and didn't get anywhere as of yet, of course it is frustrating.......... and three days response time ("only three days ago...") is, in my opinion, plain horrible. I thought there were thousands of users here that have the knowledge and powers and my questions were not that difficult... again, i could be wrong.... may i ask you all to forgive me for ranting?

sudo ./ rantmode-off.pl 
sudo ./ happy-user-mode-on.pl
reboot

Kind regards.....

your Thanh

---

### Post by rayj00 on 2007-03-22
I have Ubuntu 6.10 as host and a VMware workstation WIndows XP.
They work flawlessly......

---

### Post by Thanh-BKK on 2007-03-23
Hello again :)

Thanks guys for your support.... i am typing this from within a perfectly running Firefox in a just-as-perfectly running Ubuntu 6.06 in a virtual machine under Vista :)

And yes, it has all the latest updates (and update prompts now disabled), it has the VMware additions installed (with correct kernel headers and gcc version) and it even has auto-login enabled and functioning! And Firefox, tough the 1.5 version (i am way too scared to try upgrading that again) has my favourite theme, all my extensions and some of the plugins (can't get RealPlayer to download, neither Quicktime, which doesn't seem to have a Linux-version on that website).

Now a couple more questions. Why is it that Firefox becomes extremely sluggish when running for a while? Meaning websites load fast but when trying to scroll down in thgem (specially when there are pictures on the page) it goes very slow. Is that because i run in a virtual machine (but everything else is fast and very responsive) or because Firefox, which has also gotten some updates during the system update process, is somehow about to screw up again? It wasn't that sluggish before that update, this time round i have made backups of the virtual machine as advised, before every "next step" so that i don't need to install from scratch again should something fail.

Is there an alternative web browser (i know Konqueror from SuSE) which installs EASY on Ubuntu (please without damaging something in the GUI) so that i could copmpare? If that's sluggish too, it must have some other reason. 

Also, is there an easy way to upghrade from 6.06 Dapper to 6.10 Edgy? Since i could use one of the backups i don't need to screw around with my now-working installation, but i have the Edgy DVD and maybe an upgrade would, as opposed to a new install, actually work. I understand it's probably not as easy as it was from Windows 2000 to XP and recently from XP to Vista, but as long as i don't need to study a 300-page manual on CLI commands before attempting it... anyone able to advise me? 

With kind regards.......

your Thanh

---

