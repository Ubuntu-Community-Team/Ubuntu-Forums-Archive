---
title: "Why I wont be switching from Windows ..."
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by georgevl on 2007-06-02
So I read about Ubuntu, saw videos and got excited.
Installed under VMWARE (Windows) and I liked it so much that I even installed Dev environment (used to be a developer some years back).

So convinced about it wanted to see Beryl and the desktop effects in actions and considered switching all together from Win using VMWARE from Ubuntu instead.

Downloaded both distros (AMD64 and i386) and both failed to get me up and going. No errors, simply a blank screen during boot (never got into the gui to start the install).

I assume it has something to do with my config, but I have been booting in and out of Windows for a whole day trying to get some help on the web... so, no offense but its like hitting your head against the wall. Honestly I had all the will to switch... just wish that a clear instruction or a message was shown directing me on what to do next.

For those interested, here is the rel info:

Ubuntu ver: 7.04 (tried both AMD64 and i386)
Motherboad:  Gigabyte GA-K8NXP-SLI (latest BIOS)
CPU: AMD64 Athlon 3500+
3 x SATA Drives on NVidia motherboard controller
2 x Gainward 6600 VGAs (PCIe)
3G RAM
2 x Dell 19" TFT (both connected on one VGA card)

Symptoms: Boot of CD, choose Install/Start, loads, swicthes to blank screen.

Other failed attempts (all for AMD64 ver only, for i386 I only tried simple install): 
  Safe mode
  noapic nolapic
  noapic nolapic pci=noacpi acpi=off
  Alt+F1, dpkg-reconfigure xserver-xorg, selected vesa and left all other options to default. tried startx kept complaining that another one was running elsewere (how do you kill it?).
  Tried above with noapic nolapic option and without quiet splash options. Didn't complain (I think) about other session running but still bank screen

Wasted enough time already but if someone knows what to do I might try again. I am guessing it has to do with the nv driver, but for both distros? It would have been nice to warn or test instead of locking into blank screen, especially by the fact that I read somewhere that there is a known issue with nv 6600 (only for AMD64 however).

Sorry, simple user... forgive the negativeness ...

(btw, worked great in VMWARE ... great distro! - if only it worked the same way on my machine...)

---

### Post by peebly on 2007-06-02
Must be the graphics card, look at my computer spec, its almost the same as your's.

My computer has always worked with Ubuntu and every other distro I have tried.

My last card was a 6800GT which also worked fine.

---

### Post by georgevl on 2007-06-02
So what do you propose... changing my video cards?!

From what I am reading in other forums,... I might have chosen the wrong time to switch as there seem to be bugs with this version...?

---

### Post by peebly on 2007-06-02
> **georgevl said:**
> So what do you propose... changing my video cards?!

From what I am reading in other forums,... I might have chosen the wrong time to switch as there seem to be bugs with this version...?

If possible I would try and borrow one to test, or even buy one from the shop If it works keep it, if not take it back and just ask for a refund.

I know what your think though, you don't really want to be spending money trying to get Linux to work.

---

### Post by georgevl on 2007-06-02
> **peebly said:**
> If possible I would try and borrow one to test, or even buy one from the shop If it works keep it, if not take it back and just ask for a refund.

I know what your think though, you don't really want to be spending money trying to get Linux to work.
....!

you serious? Surely not. Anyway, stuck with Win for now till I can get Ubuntu running on machine.

---

### Post by peebly on 2007-06-02
> **georgevl said:**
> ....!

**you serious? Surely not**. Anyway, stuck with Win for now till I can get Ubuntu running on machine.

Yes, whats the problem ?

---

### Post by georgevl on 2007-06-02
> **peebly said:**
> Yes, whats the problem ?
Cause simply put that is not something I am interested in doing, and I think most ppl would be the same.

---

### Post by hessiess on 2007-06-02
is the graphics card ati or gforce8, ati cards have verry poor support under ubuntu, gforce8 laks proper drivers

---

### Post by georgevl on 2007-06-02
> **hessiess said:**
> is the graphics card ati or gforce8, ati cards have verry poor support under ubuntu, gforce8 laks proper drivers
its gforce 6600 
from ur msg I guess if you have either ur F**D

---

### Post by georgevl on 2007-06-02
anyone with some suggestions? (ie install a previous ver)

---

### Post by georgevl on 2007-06-02
For anyone else who might be lost as I am:

I went to #ubuntu IRC where **SlimeyPete** and **mneptok** where kind enough to point out that I should try the [COLOR="Red"]Alternate Istall CD[/COLOR]!

Downloading now, plus looking at this post: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I will post an update of how I go.

---

### Post by hessiess on 2007-06-02
try a erler version if you want, couldent hert anything

---

### Post by SmoshySmosh on 2007-06-02
Or the problem is you burned it to a cd using Nero, or something like that. Or you have an ATI video card in which you would have to do something different while it is booting the live CD (happen to me while installing on a friends PC with a ATI video card.)

---

### Post by fsando on 2007-06-02
Could be something with feisty or your bios too. A bios upgrade may be a good idea.

Also, there have been A LOT of issues with the kernels in feisty which could also be the problem.

I just tried to get feisty onto an older laptop without success (it runs edgy like a charm - actually it needed a bios upgrad to run edgy)

you could try the earlier 6.10 just to test if that one works (it takes less than an hour to go through a full install). And there is not that big a difference - especially if it's a desktop and not a laptop.

Older versions can be had from here: [http://cdimage.ubuntu.com/releases/](http://cdimage.ubuntu.com/releases/) 

As for ATI: I'm running Beryl on one of the 'unsupported' X1000 series cards. ATI releases a new updated linux driver every month - they release windows and linux drivers at the same time. So i think they are really getting their act together.

---

### Post by DaBigUA on 2007-06-02
I have an ATI board and have no luck with the standard install since the Live CD came out.  I always use the "alternate cd" with a text based installer.  You might try that.

---

### Post by iqag1060 on 2007-06-02
You got the right advice on IRC.The Live CD can be troublesome - the alternate CD is nearly always easier (but uglier) for installation. Generally, even if you need proprietary drivers you should be able to get into Gnome or KDE (maybe with resolution off or image distorted) and install the drivers you need. 
Just in case, it might be better if the wiki instructions included command line equivalents. It looks (from the wiki) like you need to install two packages, the restricted modules for your architecture (which should be installed by default) and nvidia-glx either old or new, which you should determine first from [the list.]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html") When the installer is done, if it seems to boot, but then the graphical environment never comes up, hit CTRL-ALT-F1, and log in to the console. Then use apt. The great thing is that apt has tab completion, so you can type "sudo apt-get install linux-res" and hit tab and you'll get a list of all the available versions. Do the same for "nvidia-glx-" Then once both are installed run "sudo nvidia-xconfig". The easiest thing would then be to reboot: "sudo shutdown -r now". I'm guessing that would solve your problems, based on vague memories of past experience and the wiki page you linked to. 
By the way, if you or anyone were to install an old version, install Dapper rather than Edgy, as it is the Long Term Support version. 
Hopefully you've already solved your problems and on to more productive things.

---

### Post by georgevl on 2007-06-03
> **iqag1060 said:**
> You got the right advice on IRC.The Live CD can be troublesome - the alternate CD is nearly always easier (but uglier) for installation. Generally, even if you need proprietary drivers you should be able to get into Gnome or KDE (maybe with resolution off or image distorted) and install the drivers you need. 
Just in case, it might be better if the wiki instructions included command line equivalents. It looks (from the wiki) like you need to install two packages, the restricted modules for your architecture (which should be installed by default) and nvidia-glx either old or new, which you should determine first from [the list.]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html") When the installer is done, if it seems to boot, but then the graphical environment never comes up, hit CTRL-ALT-F1, and log in to the console. Then use apt. The great thing is that apt has tab completion, so you can type "sudo apt-get install linux-res" and hit tab and you'll get a list of all the available versions. Do the same for "nvidia-glx-" Then once both are installed run "sudo nvidia-xconfig". The easiest thing would then be to reboot: "sudo shutdown -r now". I'm guessing that would solve your problems, based on vague memories of past experience and the wiki page you linked to. 
By the way, if you or anyone were to install an old version, install Dapper rather than Edgy, as it is the Long Term Support version. 
Hopefully you've already solved your problems and on to more productive things.

Hello to everyone from my (finally) working Ubuntu!

Although I didn't follow those steps exactly I can definitely that it was neither obvious nor did I get any help during the install. You dont have internet? Dont touch this.

Anyway, The process I followed is this (as much as I can remember):

Used Alternative CD instead of Live (although considering the steps below I might have been able to find a way through Live as well).

Booted and followed all the prompts. Indeed not that difficult (except the part of the partition management which gave me a fright cause it did not state anywhere the free space or size of the partition I was choosing, worrying I would wipe out my work in Windows. Choosing the "Partition with most continuous free space" did exactly as it states and installed in the partition I had created with PartitionMagic under Windows).

So once the whole thing installed, to no surprise Xorg still gave me the "blank screen". Did eventually figure out the Cntrl-Alt-F1 (btw what does F2 do ? seems to open a new terminal) which got me to the command prompt. In principal I tried everything with no luck but then bumped onto a blog somewhere mentioning Envy. Downloaded that and used the text script to install the drivers... still Xorg wouldnt start (something about the NVidia kernel version)... kept on fighting and went to the site (thank God I have a laptop and I could do this side-by-side) of the developer who also attempted to fix that kernel error. In the end I still couldn't get the damn thing showing anything.

The got to another site on how to get Xorg running with nv basic setup. It was at this point in time that I got the full instructions on how to configure the drivers through the text prompt. The part I was missing: Dont let it autodetect the monitor and force it to be set to 1024x748@60. This allowed me for the first time after a whole day to actually see the login screen!! (on one monitor only but who's complaining?!)

Logged in and headed straight to the Restricted Hardware Manager to attempt the Umuntu way of installing the driver. Wishful thinking in short. Ended up wasting 3 hours rebooting all the time till I decided to use the GUI side of Envy... problems solved!

I now had nvidia geforce 6600 both working !!!

Had to go through similar steps to get the audio playing only to find out in the end that I had to choose a different manager under sound preferences.

So I am happy to be here.... but PLEASE PLEASE PLEASE: consider improving the whole process. Simple things like prompting the user for the video mode: 

ie. do you see/hear this? no? revert to other setting or try something else?

I would think that the goal is to be able to get things going without internet connection and not having to know linux commands from the word Go. Even Dos didn't expect that much from you back in those days.

Anyway, I wish I have all the urls I visited to thank everyone but too many to keep track. Thank you anyway.

BTW: I even managed to get Beryl running and got rid of that blackwindow nvidia bug (thanks to an nv forum) !

---

### Post by Cloud22 on 2007-06-03
try 6.10 then try to upgrade from there

---

### Post by fsando on 2007-06-03
> **Cloud22 said:**
> try 6.10 then try to upgrade from there

Not necessarily - that's what I tried. If the problem is with 7.04 (Feisty) this will not help.
As I experienced: [http://ubuntuforums.org/showthread.php?t=461219](http://ubuntuforums.org/showthread.php?t=461219)
To quote myself ;)
> Xubuntu 6.10 installed without a hitch
I then upgraded to xubuntu 7.04 with kernel 2.6.20-16, which resulted in the laptop constantly rebooting (without any user interaction).

---

### Post by fsando on 2007-06-03
> **georgevl said:**
> Hello to everyone from my (finally) working Ubuntu!

<snip>
[...]
</snip>

I would think that the goal is to be able to get things going without internet connection and not having to know linux commands from the word Go. Even Dos didn't expect that much from you back in those days.

Anyway, I wish I have all the urls I visited to thank everyone but too many to keep track. Thank you anyway.

BTW: I even managed to get Beryl running and got rid of that blackwindow nvidia bug (thanks to an nv forum) !

I do agree with you, there should be very clear indications what is going on and what you could do about it.

But there are some serious issues at play too. The question of proprietary drivers is not trivial at all.
Some smaller distros will deliver those drivers out of the box, problem is that this is illegal somewhere around the world - or the legal status of distributing them is very unclear (most notably the US).
This is in general not a problem for a small distro, noone will go after them for a lot of reasons: there is no mony to be had, it's problematic to figure out who exactly to sue, suing the little guy is bad publicity.
But in the case of Ubuntu the situation is entirely different (just think of youtube before and after Google bought it).

As it is now, you may or may not be breaking the law when installing proprietary stuff. It may in fact be legal if you do it on a personal basis but illegal if it is done as part of the distro itself - and in addition this may be very much dependent on where you live posing difficult problems for a world wide reach like ubuntu's, etc. etc.

So Ubuntu is forced to stay out of legally dangerous waters if it wants to succeed in the long run. This means difficulties for the end user. But I believe (after seeing the development on the driver front for the last 6 months) that this decision on the part of Ubuntu has been very wise. The blame has quite largely been put on the vendors rather than on Ubuntu (and rightly so) which has affected a change in attitude on the part of the vendors. Good support for Linux is increasingly becoming an important market parameter.

Therefore I expect those issues to disappear over time. You are experiencing the early adopter's pain right now.

And congrats to you that you succeeded in the end :)

---

### Post by lazyart on 2007-06-03
First of all, I'd like to say thank you to you for trying where others would have just said "Screw this, Ubuntu sucks."  And it looks like you were real close to that.

I had the same exact problem migrating from 32 bit to 64 bit yesterday as well, and I'm only using a nVidia FX5200.  My fix was go install the updated driver from the command line[sudo]sudo apt-get install nvidia-glx-new[/code]but I've been on the boards hear for about 8 months... certainly not obvious to a newbie.  The Live CD worked for me but the install gave me the white screen.  A conversation with the developers is in order here.

---

### Post by t2000kw on 2007-06-03
If you were concerned about things in the current version needing fixed, you could install the LTS vertsion (Dapper) and that might do the trick.

As for the graphics card, you probably won't need the latest, greatest, so if you have an older one or an Nvidia card (seems to be well supported here), pop it in and see what happens. 

Or, if you're patient, try SuSE Linux and see if you get the same black screen.

Now, I'll pass this along but I doubt if it's your problem.

I have a 2-year old system that has some hardware problems that was starting to show up a couple of months ago. Windows would crash unexpectedly or I would get a sudden reboot. I installed Ubuntu and thigs were better for a wile, then the problem got worse again.

When I would reboot, sometimes I would see the BIOS splash screen and it would boot to the GRUB menu (to allow a chose between Linux or Windows), and sometimes the screen would go black but it appeared that the system was still booting. If I shut off the system for half a minute or so it would book OK, I would see the BIOS splash screen, etc. Also, what led me to believe it was RAM related was that I had problems with Linux recognizing a partition, and failing RAM can make it look like you have a hard drive problem. 

It acted like failing RAM and/or video card, but I can't afford new RAM right now (maybe in a month or so). Really bad timing for this to go bad. So I tried raising the voltage supplied to both the RAM and the video card and it fixed the problem for now, at least I rarely have a program crash except for Firefox web browser. 

I doubt if this is related to your problem if it is working under Windows, but if you were switching because you were having problems in Windows, perhaps it might have ben a hardware problem.

---

### Post by cantormath on 2007-06-03
The people that write these comments, day in and day out, must be employed by Microsoft or some affilate.

---

### Post by wpshooter on 2007-06-03
> **georgevl said:**
> Hello to everyone from my (finally) working Ubuntu!

Although I didn't follow those steps exactly I can definitely that it was neither obvious nor did I get any help during the install. You dont have internet? Dont touch this.

Anyway, The process I followed is this (as much as I can remember):

Used Alternative CD instead of Live (although considering the steps below I might have been able to find a way through Live as well).

Booted and followed all the prompts. Indeed not that difficult (except the part of the partition management which gave me a fright cause it did not state anywhere the free space or size of the partition I was choosing, worrying I would wipe out my work in Windows. Choosing the "Partition with most continuous free space" did exactly as it states and installed in the partition I had created with PartitionMagic under Windows).

So once the whole thing installed, to no surprise Xorg still gave me the "blank screen". Did eventually figure out the Cntrl-Alt-F1 (btw what does F2 do ? seems to open a new terminal) which got me to the command prompt. In principal I tried everything with no luck but then bumped onto a blog somewhere mentioning Envy. Downloaded that and used the text script to install the drivers... still Xorg wouldnt start (something about the NVidia kernel version)... kept on fighting and went to the site (thank God I have a laptop and I could do this side-by-side) of the developer who also attempted to fix that kernel error. In the end I still couldn't get the damn thing showing anything.

The got to another site on how to get Xorg running with nv basic setup. It was at this point in time that I got the full instructions on how to configure the drivers through the text prompt. The part I was missing: Dont let it autodetect the monitor and force it to be set to 1024x748@60. This allowed me for the first time after a whole day to actually see the login screen!! (on one monitor only but who's complaining?!)

Logged in and headed straight to the Restricted Hardware Manager to attempt the Umuntu way of installing the driver. Wishful thinking in short. Ended up wasting 3 hours rebooting all the time till I decided to use the GUI side of Envy... problems solved!

I now had nvidia geforce 6600 both working !!!

Had to go through similar steps to get the audio playing only to find out in the end that I had to choose a different manager under sound preferences.

So I am happy to be here.... but PLEASE PLEASE PLEASE: consider improving the whole process. Simple things like prompting the user for the video mode: 

ie. do you see/hear this? no? revert to other setting or try something else?

I would think that the goal is to be able to get things going without internet connection and not having to know linux commands from the word Go. Even Dos didn't expect that much from you back in those days.

Anyway, I wish I have all the urls I visited to thank everyone but too many to keep track. Thank you anyway.

BTW: I even managed to get Beryl running and got rid of that blackwindow nvidia bug (thanks to an nv forum) !

Georgevl:

I am a fan of Ubuntu/Linux **BUT** I sort of agree with you.  Getting this done should not take all of this effort.  I believe that Linux has enough hurdles to overcome already without having these types of problems just getting the O/S installed.

---

### Post by cantormath on 2007-06-03
> **wpshooter said:**
> Georgevl:

I am a fan of Ubuntu/Linux **BUT** I sort of agree with you.  Getting this done should not take all of this effort.  I believe that Linux has enough hurdles to overcome already without having these types of problems just getting the O/S installed.
  
Then you should by a preinstalled box from dell.  Remember, just because you are an awesome point-click engineer on windows does not make you a leet Linux user.  Actually, the better you know windows, the more often then not you are a Linux hater and the less likely to learn new and better things.

Next time you get stuck on an install
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

---

### Post by georgevl on 2007-06-03
> **cantormath said:**
> Then you should by a preinstalled box from dell.  Remember, just because you are an awesome point-click engineer on windows does not make you a leet Linux user.  Actually, the better you know windows, the more often then not you are a Linux hater and the less likely to learn new and better things.

Next time you get stuck on an install
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

cantormath I think you misunderstood my comments and in general your posts are quite aggressive. I don't know what your line of work is but I can confirm that I do not work for Microsoft or an affiliate. That said however, as it has been a long long time since I was fed from my parents, I need to make a living. I have been infront of the PC since the age of 12 developing and I have also followed the IT industry as a carreer.  As a professional I have been developing under MS for over a decade and never never ever have I hated Linux! It is ridiculous to say that and forgive me for saying so, but quite immature. 

These days, as part of the management team, I am concerned about being able to perform my day-to-day tasks in an easy and friendly way (and financially viable). Once that is satisfied I will look at being able to have a nice environment and final in the list is the ability to learn new things.

I do not get why Linux lovers are so aggressive on the MS side. I work under with MS as my customers drive the market. However, not once have I come across an "MS guy" that doesn't show some sort of respect or envy for the Linux/Unix front. 

Fact is that the last battle was won (if it was even won) on the marketing side and the user friendliness of the OS. MS put down a strategy and managed to pull it through. I personally dont agree with their strategy but I will give them this much:

* They opened the IT market to novices and the every-day user
* They did stugering good work in marketing (doesnt necessarily reflect quality btw)
* They diversified to stay at the top.

Dont take this in the offensive way, but if the Linux side of the world decided to stop winging about MS and put their efforts in user-friendliness I guess it is a no-questions asked answer: everyone would switch! (gamers would need some attention as well btw)

I for one, will try hard to keep Ubuntu running and up to date. It is the first time in years that I installed Linux and dont feel limited in doing my job (still using vmware to keep the MS side of things working, nothing I can do on that front).

Even today when some friends came over I was happy to show off Ubuntu. They liked it quite a bit, kept asking questions and so on, but you know what ... I did not give them the CD. Why? Cause they are family people with little to no knowledge of PCs... can you imagine their horror if they were to undertake the task of installing it?! So yes, thats were things are wrong right now and have always been wrong in the Linux front.

Simply put: Put some error handlers, some instructions, full guides and assume nothing about the user's knowledge. Coming from MS environments they are used to having things crash but even then they don't need to know everything to get things going again. 

I love Linux cause it doesn't hide anything from me.
I hate Linux because it expects everything from me.

Finally, does anyone know how I can run everything with root privileges? I am tired of having to go to the prompt each time I need to install or run a sys utility (ie. nvidia-settings cant save the conf file if I dont run it with sudo.)

Oh, and one last thing (not that anyone who matters would listen).... give files and products meaningful names! You are not DOS with an 8 char limit.

Other than that, again thank you to Ubuntu team and all the rest. I promise to make a serious effort ... I hope you will too...

Regards

George

---

### Post by MentholLite on 2007-06-03
Too much to read there for me at this hour. 

Anyway u install the i386 version on your vmware?
What about the physical machine? I presume its 64bit u are using, since your h/w is 64bit.

How about doing a md5sum check on your 64bit ISO to ensure its integrity. :-k

---

### Post by georgevl on 2007-06-04
> **MentholLite said:**
> Too much to read there for me at this hour. ...

It shows by ur queries

---

### Post by hessiess on 2007-06-04
in turmes of actualy using linux, not geting it to work. it is far easer than windows is and it looks alot better. the problem,s with geting it to work are not linux folt, thay are the folt of the hardwere companys who refuse to make drivers for linux, or make poor drivers for it.

---

### Post by georgevl on 2007-06-05
> **hessiess said:**
> in turmes of actualy using linux, not geting it to work. it is far easer than windows is and it looks alot better. the problem,s with geting it to work are not linux folt, thay are the folt of the hardwere companys who refuse to make drivers for linux, or make poor drivers for it.

Agreed, however, as before, this is not the user's fault either.

---

### Post by slashdot87 on 2007-06-05
maybe you could try another distro and see if that would work for you.  I am assuming that you are using 7.04 'Feisty Fawn'  Maybe you could try an older version 6.10, perhaps.  I have Feisty Fawn running on an old 1.0 Duron machine with a 40 gb hard drive and its clipping along rather nicely.  I dual boot on my main machine with XP and openSuse 10.2 and it took a little work to get it going.  But, once you get it going, you will have fewer problems with Windows.  I am still dependent on Windows, but I am getting better with Linux...

Edit:  Sorry, a bit tired and did not read down to the end of the thread.  Glad you got it working...

---

### Post by Wherdgo on 2007-06-06
> **cantormath said:**
> Then you should by a preinstalled box from dell.  Remember, just because you are an awesome point-click engineer on windows does not make you a leet Linux user.  Actually, the better you know windows, the more often then not you are a Linux hater and the less likely to learn new and better things.

Next time you get stuck on an install
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

How mighty white of you.  Glad you have such friendly and positive things to contribute from your infinite wisdom.  Hopefully you feel bigger by belittling others with a lesser knowledge than your own.

Anyone who objects to things that need improving in Ubuntu *must* come fromM$, because they couldn't possibly object to self-righteous personalities like yours in our community.

Lighten up, Francis.

---

### Post by #Reistlehr- on 2007-06-15
for your video driver problem, best bet i found, was, add the getautomatix.com repo to your sources list, and apt-get install automatix2, then install the nvidia drivers. only way i could get nvidia installed. the .run script from nvidia.com didnt work, nvidia-glx, and envy didnt work for me either. eveyrhting else, lol, no help, sorry.

---

