---
title: "Abandoning Ubuntu for Fedora! :("
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by drbongo on 2007-11-16
If someone had told me a month ago that I would be moving from Ubuntu to Fedora I would have thought they were crazy - but the unbelievable has happened!

This is all down to the number of serious bugs in Gusty!

I have been using linux for several years and have tried all of the major distributions. Since Ubuntu 6.04 I have always found Ubuntu to be the most reliable and easiest to use distro and even though I was a devoted Ubuntu user I still tried new editions of other distros but they never matched Ubuntu. 7,04 was brilliant with some great features and very stable, but Gutsy has been a disaster, at first I could not even get it to boot on any of my ATI equiped computers although it worked on my laptops. I eventually got it to run in safe graphics mode and adjust the screen resolution but the Xorg was still messed up and very unstable etc.

I have spent the best part of a month scouring forums for a fix but none worked and to add insult to injury there has been no official recognition or resolution of the problem from Ubuntu. And it seems a large number of people have had similar or equally serious issues.

I don't how long it will take for a fix for this or whether it will ever be fixed - and I don't want to be stuck on an older version which won't be supported for that long even though Feisty was great. So after considering Sabayon 3.4F, OpenSuse 10.3 and Fedora 8 I opted for Fedora. 

Why? Because it works out of the box, offers remastering of CDs through Revisor and has a simple install to USB Pen script. It is not as easy to use as Ubuntu out of the box. I had to add tsclient to get access to a windows terminal, evolution-exchange to get evolution to talk to a microsoft outlook account then enable the livna repository to get access to ATI drivers (for dual monitors) , HP and Minolta Printer drivers and MP3 codec support etc. The only thing that was tricky was enabling samba support to access a windows network - this involved downloading samba-clkient and samba-suite and then enabling it in services and then allowing samba through the firewall. 

The Yum package manager has improved considerably and although there are not as many packages in the fedora as ubuntu/debian all of the major packages are available though fedora, livna or other third party RPM repositories.

I wonder how many other people will be tempted to try out a new distro because of the "Bugsy Gibbon"?

I will check out the Hardy Heron though and hope that everything is sorted out by then!

drbongo

---

### Post by Dunrobin on 2007-11-16
> I wonder how many other people will be tempted to try out a new distro because of the "Bugsy Gibbon"?
I've been tempted, although I haven't tried any of them yet.  (Well, I *did* try Mandrake Linux before, but that was a few years ago, and I didn't cared for it back then.)

I have never had a single problem with the video drivers that came with Ubuntu 7.04.  The 7.04 Live CD boots up just fine, and I never had to touch a video setting after I installed 7.04.  "Gutsy Gibbon" on the other hand has been nothing but headaches.  I originally upgraded through the Update Manager, which went fine until I had to restart the computer - then OY!  I tried downloading the ISO, but the 7.10 Live CD would not load for me either.  

I was eventually able to get Ubuntu to start using the vesa driver, but the max screen resolution available was only 800 x 600, and frankly the display sucked.  I finally said the hell with it, deleted the partition and reinstalled 7.04, since my personal data files were all on a separate partition anyway, and the experience kept me from getting rid of Windows as I had originally considered doing.

I'll probably stick with 7.04 at least until the "Hardy Heron" version comes out.  If I don't see a ton of complaints about it, as I have with Gibbon, I might give it a try, but after my Gibbon experience I'm not going to hold my breath.

---

### Post by kast on 2007-11-16
I don't understand why so many people feel the need to jump to 7.10 right out of the gate? if you have a working Linux system then why not wait? I know i wait for some time before i will upgrade, and upgrade isn't the word because i do a full backup then a reinstall. 
This has helped me avoid some issue when upgrading. 

Who's to say that you install Fedora, then when the next version comes out you upgrade right away and still have issue's? 

I have tried at least 12 different distributions so I'm not telling anyone whats the best for them, but don't jump ship because the newest version inst playing as nice as what you currently had. Unless its From XP to Linux because of Vista  :-)

---

### Post by tech9 on 2007-11-16
I have used 7.10 since it was release, with no problems... I am not sure why people say it's buggy. Maybe the upgrade process is buggy, but I have had no problems from a clean install

---

### Post by lavinog on 2007-11-16
> **drbongo said:**
> Gutsy has been a disaster, at first I could not even get it to boot on any of my ATI equiped computers although it worked on my laptops. I eventually got it to run in safe graphics mode and adjust the screen resolution but the Xorg was still messed up and very unstable etc.

I have spent the best part of a month scouring forums for a fix but none worked and to add insult to injury there has been no official recognition or resolution of the problem from Ubuntu. And it seems a large number of people have had similar or equally serious issues.

I don't how long it will take for a fix for this or whether it will ever be fixed - and I don't want to be stuck on an older version which won't be supported for that long even though Feisty was great. So after considering Sabayon 3.4F, OpenSuse 10.3 and Fedora 8 I opted for Fedora. 

Can you at least fill us in on what your issues are?
I have installed/Upgraded to Gusty on two ATI machines (ATI radeon express 200m, and 200) These two cards have no 3d support with the open source driver, but 2d worked fine. I used the new and improved proprietary ATI driver and everything worked great, including compiz.

So what are the bugs that you are referring to that you need resolved.
is there a link to a post that better explains the issue.
are there logs posted?

If Fedora works fine then by all means use it.

---

### Post by lavinog on 2007-11-16
Quoted from:[http://ubuntuforums.org/showthread.php?t=586344]("http://ubuntuforums.org/showthread.php?t=586344")
> The problem is that after the live CD boots the screen goes blank and nothing else happens. I can get them to work with a safe graphics start, but once booted the resolution is set to 1280x1024 and if I change it the screen just gets messed up. This is true from the live CD and a full install even from the Alternate CD! I will try an update and see if that works. I have also tried setting the resolution at boot time and editing Xorg.conf and usplash.conf but this has not helped!

what resolution are you trying to switch to?
if you are in safemode you are going to have problems if you go above 1280x1024

The question is why are you going into safemode? Are you choosing safemode?
When the Screen goes blank during boot up have you tried ctrl-alt F1 to pull up a console?

There was an issue with ubuntu not displaying the splash display for widescreen monitors, but it should have still booted up to the GDM...did you wait long enough for it to finish booting?
If you fall into this category there is a fix for the usplash resolution issue.
EDIT: Did you use ```
sudo dpkg-reconfigure usplash
```after you made changes to usplash.conf?

---

### Post by tweston on 2007-11-17
I think you need to relax and remember a couple of things. First off, both Ubuntu and Fedora are free, so we end users really should only offer constructive suggestions. We should mostly be thankful to the folks that put all this together for us. Second of all, the very fact that there are good alternative distos is one of the best things about Linux.

---

### Post by luvr on 2007-11-17
I'm using Ubuntu 7.04. I tried to boot up a 7.10 Live CD, but it booted into a black screen instead of a desktop. A friend of mine installed 7.10 onto his laptop, but doesn't seem to be able to get wireless networking to work; under 7.04, it worked just fine.

Since we're having these issues with 7.10, we will be sticking to 7.04 for the time being. We're both perfectly happy with Ubuntu 7.04, so we don't consider that too much of a problem.

It **is** a pity that Ubuntu 7.10 doesn't work better than it does, but no real harm done; we will likely try out the *next* release when it arrives, and see if that works any better for us. Or else, who knows, we may run into some other distro that we prefer--no harm done either (and that won't even mean that we necessarily abandon Ubuntu...)

I've been hearing some quite positive comments on Fedora lately; earlier Fedora releases didn't quite cut it for me, but I may give the latest one a try, and see what gives.

On another topic, I am beginning to find the GNOME interface somewhat limiting, so when I migrate from Ubuntu 7.04 (to either a higher Ubuntu release, or a different distro altogether), I think I will be looking at KDE-based systems first, and see if I can learn to prefer that.

---

### Post by AgentZ86 on 2007-11-17
Hi all,

I would like to add my 2 cents to this thread.

I'm a multi distro user and I must say that the most important thing for your linux experience; and to accurately test the distro is to be sure you have compatible hardware. Most of the times I see complaints it's usually due to hardware compatibility problems.

It's not an accurate evaluation to test something and then conclude that it does not work or that there is problems simply because the hardware you are trying to force the OS onto is not compatible or perhaps the drivers for that hardware are in development stages in linux.

I understand it's very fustrating to pop in the old live CD and you get nothing and figure it don't work.

But I must say that I could not jump to Fedora because of a few compatibility hardware issues.

I would have to I switch I guess if I had no other choices, but I've chosen to get compatible hardware so that my linux experience can be accurately evaluted.

I hope this makes sense to all. In other words it would be like trying to test out the latest cool car that runs on gasoline, and you want to put diesel in it ?

Well your experience is going to be very negative with this car. I can tell you this in advance before you even drive it that it will leave you hanging and broke down very quickly, but you can't blame the fuel, you have to blame the fool for putting the diesel into the gasoline driven car.

Same with Ubuntu or any other disto.
Typically if I have compatible hardware that is known to work on that distro, or perhaps I will actually go and find/buy hardware that will be compatible with that distro, Almost all distros of linux have worked out really well for me.

There have been a few that I've not been able to get my webcam working, but the printer, and scanner worked well, etc. And others the webcam and usb hub worked great, but printing would not work properly.

However after researching this over the years I've found that if I get proper hardware for my distro I have the best trouble free computing you could possibly ever want from an OS.

I mean this really, I've have compatible hardware, and recently started to sell used computers that would normally take windows 2000, however the windows 2000 is no longer supported by MS so you can't run IE 7 or the latest plugin stuff either. So I installed Ubuntu which seems to really like IBM computers and all hardware seems to work great so far on my last 4 installations and updates. Currently sold a few local and a few ebay Ubuntu systems and they love them. Also they have never even used linux before, however they have the proper hardware and no complaints at all.

Anyhow I understand and sympathize with this topic because I myself have experience in this matter.I hope this can help with your linux experience as it has with mine.
:)

:guitar:

---

### Post by starcannon on 2007-11-17
Gutsy has been my favorite release to date.
I never do "upgrade" installs though, I keep my /home on its own partition, which makes my life easy, just do a clean install of the latest stable release, no worries, and for me, the first time ever, all of my various wireless nic's work without me doing anything, just click on the network I want to join, give it the password and it just works, wep to wpa2 no problems, a/b/g all no problems.

/shrug works for me, I did have to use an alternate install cd to install to my wifes HP Pavillion dv2600 but that wasn't a big deal it worked fine.

---

### Post by Laserbeast on 2007-11-17
If you think Ubuntu is "severely buggy", I dare you to try almost anything else. Arch being a good example. Hell, Gentoo 2007.0 is another.

Most of the bugs on 7.10, atleast in my experience, have been minimal and fixable through this huge community.

---

### Post by Ooht on 2007-11-17
Gutsy has some annoying issues, but so does evey distro I've tried -and I've tried a few (Ubuntu and I have an understanding :)). Before I got my new computer I had to manually edit my xorg.conf for every distro I tried, and enabling 3D acceleration was a nightmare with some of them. ATI tends to suck with Linux no matter what in my experience. I never got  Beryl to work properly with Feisty on my old ATI X1300 Pro, but when I got my Nvidia card it just sort of worked once I installed the drivers.

That said, have you tried Xubuntu? I tried my Gutsy LiveCD in my mom's laptop (which should be plenty powerful) and it booted to a black screen, but Xubuntu Gutsy boots just fine. The few annoyances I've had with Gutsy on my system (namely the theme-chooser not working) seem to be Gnome specific as well.

---

### Post by Arthur Archnix on 2007-11-17
Glad you found a distro that works for you. Fedora is very nice. Be seein' ya8-)

---

### Post by wsx123 on 2007-11-18
I could not get my USB hard drive to work in Ubuntu 7.10, Open Suse 10.3 or Fedora8. I like the fact that Fedora 8 has a firewall but wireless works better with Ubuntu or Open Suse 10.3.
Why isn't the Ubuntu installed firewall discussed more? I never knew it had one.

---

### Post by scemmine on 2007-11-18
As someone has correctly stated, there's no reason to switch to a completely new revision of an operating system if you're happy with the previous one(s)! Maybe what you need is just a couple of minor version updates of your favourite programs, or the desire to follow the common behaviour of the "**I MUST upgrade to be cool!**" philosophy...?

---

### Post by duncanyoyo1 on 2007-11-18
The only think I don't like about Gutsy is Compiz, it does not let me use the 3D windows plug in, while Beryl on 7.04 did. Other then a few window manager crashes ( because of Compiz ) I have had absolutely no problems.

---

### Post by bsmith1051 on 2007-11-19
> **scemmine said:**
> As someone has correctly stated, there's no reason to switch to a completely new revision of an operating system if you're happy with the previous one(s)! 
... except that all the latest versions of important programs -- the Linux kernel, Gnome, OpenOffice, Sun Java, etc -- are only available on the new OS.  Yes, I realize that some people know how to manually upgrade/replace the included copies on 7.04 but most people don't.  Personally, I've loved every version of Ubuntu until this latest 7.10 which IMO has been a disaster.

---

### Post by luvr on 2007-11-19
> **bsmith1051 said:**
> ... except that all the latest versions of important programs -- the Linux kernel, Gnome, OpenOffice, Sun Java, etc -- are only available on the new OS.
True--But as long as you're happy with the older versions, and there's no compelling reason why you absolutely, positively **must** upgrade, all those latest versions may be [I["nice to have,"[/I] but they're not essential.

You can keep using the older version of the OS just fine, at least until it reaches its end-of-support date. Which Ubuntu 7.04 has clearly not reached yet--as I'm typing this, for example, there are 6 updates available for it. The update manager kindly reminds me that there's a new distribution release '7.10' available, and invites me to hit the *"Upgrade"* button, but no thanks--I will stick to 7.04 for now. (And if, one day, I do decide to upgrade, I will perform a fresh install anyway.)

---

### Post by steveneddy on 2007-11-19
I wish I had stayed on the LTS version long ago.

When the next LTS comes out I'm sticking with that for a while.

I've tried Fedora and it leaves a lot to be desired at this time.

I have OpenSUSE installed on the second partition and it is getting better, but I have to say that I still like Ubuntu better.

---

### Post by Mithrilhall on 2007-11-19
Good luck with Fedora. I've never had a good experience with an RPM based distro.

Why not go with Debian. It's extremely stable and you'll feel right at home coming from Ubuntu.

---

### Post by ThomasMarkas on 2007-11-19
I started with Fedora and liked it. But not for the home network. Of the 6 computers I have so far upgraded to Gutsy,  2 ok, 2 had problems with network and 2 had to be re-installed.

Now this is better than my 2 Fedora machines that have never upgraded, I always try, But so have always had to re-install and fight the drivers.

The only problem left with Gutsy is that none of the computers will mount my USB 2.5" hard drives and did previously.

---

### Post by xineizer on 2007-11-21
I moved from Fedora 7 to Ubuntu Gutsy Gibbon last month, and I'm very happy with Gutsy.  So far no serious problems, except that I was disappointed with the OpenOffice application that came with the distribution -- I had to uninstall it and install the one from OpenOffice.org.

What I love about Ubuntu is that everything nearly worked out-of-the-box, except for my built-in webcam.  I was about to upgrade to FC8 from FC7, but I wanted to try out Ubuntu first, and guess what?  I'm sticking to my Ubuntu!

Now... if I can only get ipwraw to work properly....

---

### Post by stoodleysnow on 2007-11-21
Come back soon, drbongo!):P

---

### Post by AgentZ86 on 2007-11-21
About once every six months or so I try download a bunch of new distros from the distrowatch.com just to see how things are moving along.

I was initially a Suse user for a short time, then instantly found Lycoris which I loved even though it's an RPM based. Then convinced I needed Linspire for compatibility, and used Lycoris for about a year, then Linspire with CNR for about a year, and Mepis for about year, and while using those I tried many others PClinuxOS was nice enough but their forum was just negative and a bad experience in my opinion. I've recently loaded Ubuntu and have been really happy with Lycoris,Linspire,Mepis,PClinuxOS,Slax,Slackware,Debian etc. I've installed various others as well, Fedora,LinuxXP etc. I must say that Ubuntu has been my most pleasant experience so far both the OS and the forums.

No one moving forums around and saying they don't belong here or there etc. Or if that does happen at least it's with pleasant explanation etc and not rude.

I know with all distros there are some issues for different reasons, but Ubuntu 7.10 just works well with all my stuff, and all the computers I've been loading for reasale, and wireless stuff just happens on it's own I don't really have to do anything. So for me I have to chalk it up to The OS and mostly compatible hardware.

If people have compatible hardware and they plugin the OS and it just works. What could they possibly complain about. I know I'm restating this but if your hardware is compatible with the distro of choice I bet you will be happy with just about all distros out there now, especially Ubuntu for it's ease of use and installing packages. 

It just keeps getting better with linux I'm looking forward to watching the emergence of the new stuff.

:):popcorn:

---

### Post by BoardDWorld on 2007-11-22
I'm considering mac, something truly solid. I should have gone mac in the first place, I spent enough on my laptop to go for one of their high end systems. I'm just about to trial the hacked OSX 10.5 Leopard(works on most Duo2core intel based computers). All going well next years system is going to be an Apple.

I just can't believe the amount of bugs in Gutsy considering how well Feisty worked. How do you make such a giant leap backwards? To be honest it's exactly like when I change to my Vista system from my old XP system. It's unbelievable and as with "many" it's tarnished my love for Ubuntu.

---

### Post by drbongo on 2007-11-22
It has been interesting reading everyone's comments to my original rant! The reason I was so frustrated is that for the last couple of years Ubuntu has been excellent, everything just worked out of the box and never had any serious problems. It is true that no versions are perfect, they all have strengths and weaknesses but Ubuntu always seemed to come out on top overall and this probably gave me very high expectations. This is why I was so frustrated! It seems the vast majority are managing fine with Gutsy but 20-30% have had problems according to the polls and this is unheard of with Ubuntu. 

It is true that these are cutting edge releases and there is no reason why I could not stick with Feisty which did everything I wanted out of the box. 

I am also a cheapskate when it comes to hardware - I realise I will have to buy a new PC one of these days!

I realise that all of this software is free and I can't give enough praise to the people and companies that produce it. My frustration is actually a symptom of admiration for Ubuntu - like a jilted`lover :(

It doesn't look likely that these issues will be fixed in Gutsy, and other distro's based on it cause the same problems.

I am sure I will give Hardy Heron a try!

I just wanted`to see if there were other people feeling the same!

drbongo (I'll be back):lolflag:

---

### Post by AgentZ86 on 2007-11-22
> **BoardDWorld said:**
> I'm considering mac, something truly solid. I should have gone mac in the first place, I spent enough on my laptop to go for one of their high end systems. I'm just about to trial the hacked OSX 10.5 Leopard(works on most Duo2core intel based computers). All going well next years system is going to be an Apple.

I just can't believe the amount of bugs in Gutsy considering how well Feisty worked. How do you make such a giant leap backwards? To be honest it's exactly like when I change to my Vista system from my old XP system. It's unbelievable and as with "many" it's tarnished my love for Ubuntu.

I've also considered a mac, however the hardware topic is the same topic as any other OS compatibility and compatibility, and of course the cost.

Anyhow Gutsy has no bugs I can't believe people say it has bugs I install anything I want and use my computer everyday all day for my main home business computer and I install it on used computers and selling them on ebay and craigs list. No bugs here.

I use the updates daily for all the latest stuff never a problem there either.
It's unbelievable to me how stable and perfectly this thing is working for me on several computers in the house and office and also resale.

It's all relevant really; If a computer won't run Ubuntu either get another computer that will, or get another OS that will work with your hardware thats about all you can do.
I prefer to get hardware that is compatible with the OS I would like to use.
I usually do this before installing the OS not after. This save much aggrevation and fustration.
I must say that Gutsy 7.10 has been the most pleasant experience ever thus far. 

Well I know I've said this before but I just can't make it clear enough if your hardware is compatible you will not complain at all. In fact I wish everyone would know the same experience I've been having with what I've learned about compatible hardware.

Well, thats all I know thanks for reading
:popcorn:

---

### Post by AgentZ86 on 2007-11-22
> **drbongo said:**
> It has been interesting reading everyone's comments to my original rant! The reason I was so frustrated is that for the last couple of years Ubuntu has been excellent, everything just worked out of the box and never had any serious problems. It is true that no versions are perfect, they all have strengths and weaknesses but Ubuntu always seemed to come out on top overall and this probably gave me very high expectations. This is why I was so frustrated! It seems the vast majority are managing fine with Gutsy but 20-30% have had problems according to the polls and this is unheard of with Ubuntu. 

It is true that these are cutting edge releases and there is no reason why I could not stick with Feisty which did everything I wanted out of the box. 

I am also a cheapskate when it comes to hardware - I realise I will have to buy a new PC one of these days!

I realise that all of this software is free and I can't give enough praise to the people and companies that produce it. My frustration is actually a symptom of admiration for Ubuntu - like a jilted`lover :(

It doesn't look likely that these issues will be fixed in Gutsy, and other distro's based on it cause the same problems.

I am sure I will give Hardy Heron a try!

I just wanted`to see if there were other people feeling the same!

drbongo (I'll be back):lolflag:

I agree and understand this myself as I also had high hopes for Linspire,Mepis,PClinuxOS(i pronounce Piclinuxsauce lol).
I really wanted to use Mepis at the time prior to their conversion to the Ubuntu kernel etc. And I used it, however there was always seeming to be some glitch.
Either my webcam didn't work, or not properly, or my sounds was not working I had to edit the sound conf files etc to make it work right. But it was mainly due to compatibility. I just had in my mind that I like Mepis and wanted to make it work because I see all the stuff it could do for me. But after much effort I never really did get it working right on my system at that time. Firefox fonts were strange and I couldn't get that worked out. I chalked it up as a buggy piece of crap. But I was still sort of new to linux at that time and just wanted ease of use. I was determined to use linux and get off the MS products once and for all.
I finally decided that I would get hardware that will work with my OS just like I would for my MS products. And it was the most important thing I ever did on linux.And now I pretty much load any distro out there when it comes time and things just work. Some easier then others. but basically they all work well. I mean that even the newest ones that are not as popular work well if the hardware is compatible.
It would even be better to get an older computer that is compatible if needed. But your overall experience will be great compared to incompatible hardware.
But anyhow I do understand the frustration as I've said I've been there.
In fact I'm getting ready for a new computer myself and am currently researching compatible Motherboard,sound,vid etc. and FYI IBM systems like linux most distros.
Well, anyhow happy hacking and good luck on your next OS
:guitar:

---

