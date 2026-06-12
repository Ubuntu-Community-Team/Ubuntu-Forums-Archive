---
title: "FF Makes me not want to switch to Ubuntu..."
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by pdusen on 2007-04-20
Okay, maybe that's harsh, but I'm having a major problem with it. I'm new to Linux, but I've had an install of Fedora that I've been messing around with for a while, and that supported all my hardware just fine. 7.04 came out, so I decided to give it a shot. So I downloaded the AMD64 LiveCD, booted from it, and as soon as I selected the first option my monitor lost signal... 

okay, so it's a video driver problem, I suppose. So on the advice of someone in #ubuntu, I downloaded the alternate and gave it a shot. Okay, it's all text, I get through the install with no problems. I reboot and go to load Ubuntu and... the same thing happens. So I go online and discover that this is apparently a common problem with ATI cards... I go to the linux ATI wiki on installing fglrx in 7.04, and reboot into Ubuntu's recovery mode to try and fix the problem. It is at this point that I discover that I apparently also don't have drivers for my onboard network adapter.

I am not sure what to do now. On the asrock site are Linux drivers for my chipset, but I think they are targeted toward i386 systems...

My specs:
[LIST]
[*]Video: ATI x800xl
[*]CPU: AMD Athlon 64 3200+
[*]939Dual-SATA2
[/LIST]

My setup isn't really uncommon, so I can't understand why the support for those parts (especially the ATI) seems to be nil... can anyone help?

---

### Post by rich.bradshaw on 2007-04-20
Haven't used it myself but there is a script called Envy that installs ATI drivers automagically. I'm sure there is a lot about it on this site.

ATI don't support Linux, so there is a lack of "official" drivers by them. That might help you though.

---

### Post by greymongrey on 2007-04-20
Envy worked fine for me. I highly recommend it.

---

### Post by RawMustard on 2007-04-20
Not just ATI, My Nvidia 8800gtx does the same thing.  Black screen can't do a damn thing!
64bit Ubuntu Feisty final relese is screwed!

---

### Post by orb9220 on 2007-04-20
> My Nvidia 8800gtx does the same thing.

Yes when you try adding a card that is TOO new and hasn't had time to be upgraded in the linux nvidia drivers yet.

And Ati have always sucked and are a bear to config.

---

### Post by pdusen on 2007-04-20
I really need to figure out what to do about my networking drivers before I can do anything about the ATI drivers.

> **orb9220 said:**
> And Ati have always sucked and are a bear to config.

I like my ATI card fine in windows.

---

### Post by anachreon_ on 2007-04-20
> **pdusen said:**
> I really need to figure out what to do about my networking drivers before I can do anything about the ATI drivers.



I like my ATI card fine in windows.

Yeah he means in linux.  The ATI linux driver / support seems pretty spotty.  I'd definitely recommend using the Envy script for proprietary driver installs, at least with nVidia - though I hear it works well with ATI as well.

---

### Post by bagadonitz on 2007-04-20
I was having the same issues with 64bit 7.04 with both alternate and desktop CDs (a few days before final release mind you).  I could get lucky and get the nvidia driver installed and it still would interrmitedly lock up/reboot/crater.

I installed 32 bit and haven't had a hitch since.

---

### Post by pdusen on 2007-04-20
I'm glad that fixes for my video situation are around, but until I find a way to activate my networking, it is all nil.

32-bit, huh? Why should I go back to 32-bit Ubuntu when 64-bit Fedora 7 can run all of my hardware just fine, and it's still in Beta?

I'm just saying to look at this from an end-user standpoint: Why use one distro that won't utilize the full capabilities of my hardware, while another one will?

I'm willing to make the switch if I can find a fix for this, maybe.

---

### Post by bagadonitz on 2007-04-22
This is my very first forray into Linux and I'm comfortable with Ubuntu and it was recommened to me by many as the easiest to learn.

Once I get more comfortable with it, if I can't get 64 bit to run on my platform, I'll consider switching to Fedora.

That said, when I initially tried wiht the 64 bit version, I was battling memory issues as well.  Once that is straightened out, I might give 64 bit another spin.

---

### Post by SunnyRabbiera on 2007-04-22
> **pdusen said:**
> I really need to figure out what to do about my networking drivers before I can do anything about the ATI drivers.



I like my ATI card fine in windows.

yeh but thats windows...
ATI is really a thorn in our sides, i suggest not using it.
but you might also want to stick to an older version of ubuntu, I am only a few days in with feisty and i am thinking of downgrading to either edgy or dapper as they were more stable on my system, feisty is alright but I have had issues with it.

---

### Post by Mongoose on 2007-04-22
Feisty Fawn isn't ready for prime time.  If you want to try Ubuntu I suggest using Edgy.  It's pretty simple -- try a Feisty live disc.  If you have problems just install Edgy and enable backports.  Due to the new kernel and several policy changes sata / 64bit / nvidia nforce boards / native wireless drivers / etc that worked fine with edgy don't work with Feisty.  Like most people I got tired of the bullshit and started making my own patches.  A great example is the gaim / nm bug where if you try to IM a gtalk user the application hangs if you have network manager removed.  Why would you remove network-manager?  To get networking working again.  

All the reports of unbootable installs and input devices like PS/2 and usb kb and mice not working...  it's an embrassment quiet frankly.  Feisty runs fine on my old PIII with a closed driver for wifi, but on my dual core system it would be unusable if I used the feisty packages for kernel, some libraries, and applications.  I can't stress enough you should use a live cd to test if you have these issues first.  It's not so easy to downgrade, but upgrading is near trival.

---

### Post by zorkerz on 2007-04-22
If feisty is ready for prime time or not i suppose is a subjective opinion. The fact of the matter is that as of the 19th feisty is a full blown out of beta final release. As with every release new people have problems and many old people stop having problems. Some things get fixed and others have new problems. In my experience there appears to be many many people happily using feisty. I have been for a couple months.

Sorry im off topic. As for the proprietary graphics cards drivers have always been a problem. The restricted drivers manager in feisty is a neat new addition. I have no experience with 64 bit ubuntu but the 64 bit realm is new and will undoubtedly take some time to be as full fledged as 32 bit. 

If you decide to use edgy for a while there will be more developed documentation and support but if you are willing to spend some time at it i bet a feisty how to can be found.

Are you getting an x error when it crashes? or any sort of error that could help.
cheers

---

### Post by mhansen on 2007-04-22
I had this problem too with the 64bit, and resolved it by specifying a resolution to use with vga=XXX where XXX is the mode you want to run and editing /boot/grub/menu.lst accordingly.  Here is an example from my GRUB menu:

kernel          /boot/vmlinuz-2.6.20-15-generic ro quiet splash vga=795


I added the vga=795, 795 being 1280x1024.  792 is 1024x768.  There are more, but I don't know them offhand.  You can Google them.

I hope this helps.


Regards,
Mike

---

### Post by Mongoose on 2007-04-22
I guess you were replying to my comment.  I'm saying Feisty is not deployable on many hardware configurations as of this release.  If you can't imagine how bad this is then picture Windows Vista shipping with kernel bugs disabling mouse and keyboard and not booting due to policy changes that weren't tested on enough.  That's just what Feisty did.  Sure it doesn't affect everyone, but then again if your system runs fine now on your hardware and breaks with the new release you should be pissed.  I personally don't have crashes, etc because I'm using older kernels or newly built kernel modules/libs/applications from source to workaround the broken packages.  Some things are easy to fix -- just remove the Ubuntu patches and rebuild.  

The main issue for me is now I have to wave people off Ubuntu onto a better distrobution as an upgrade path if this process failure isn't fixed soon.  It is a production failure when cricital bugs are waved off to push a release out the door.  It doesn't matter if they have it fixed for the next release if they plan to start doing this every release.  You can't keep people on 6.10 LTS forever.  Not having working PS/2 and USB keyboard/mice support in a release is unacceptable for a desktop OS.  Franky, I also don't care for your opinion if you haven't even tested the issues involved on more than your home PC on one architecture.  You should be aware this is an issue for many people.  Most people will just install another distrobution to fix it.  

In all my years I haven't had a software transistion break so many working systems at the same time.  I'll just reiterate -- Feisty will either work ok or you won't be able to boot / use kb or mouse / have networking.  You're better off telling new users to test a live cd on every system they plan to install on or turn them away from Ubuntu when it fails.  "It works for me" quips with a pat on the head won't help them learn how to repair an install the hard way for the first time.  Not warning people about possible issues only makes it worse.

---

### Post by zorkerz on 2007-04-22
I guess we are just coming from different set of experience mongoose. Ive feel as if every release of ubuntu has caused hell for some people and i have not hit the point where i feel that feisty is worse than any of the others have been. If anything im still leaning in the other direction I have a few friends who decided to switch over during feisty beta and none have had the problems that i have witnessed with old releases.

The unfortunate state of Linux at the moment is still one where hardware and software is mostly designed for windows and the FOSS community plays catch up.

As for a live cd i would never recommend someone install a distro without testing a live cd and searching the net for their hardware if possible. Thats why they are there. 

What distro are you recommending to people these days? 

I have some free time lined up this summer and im collecting a list of distros that i would like to try. If there is something easier for first time switch overs than ubuntu i would love to see it in action.

Sorry all i should not hijack this thread. I am quite off topic and will now silence myself                                               :~)

---

### Post by killjoy45 on 2007-04-22
I just want to get this clear, is there any way to get ubuntu 6.10 or 7.04 working with my 8800GTX graphics card or is it just not possible? ive tryed running the LiveCD of 6.10 but it gives me an error saying that my graphical interface is not correctly configured and i cant even get into the desktop or do anything for that matter. Ive been reading in alot of other forums and they say to type this and that in some command line but i dont even get a command line or im just really stupid and just dont know what im looking at.
  Can some one please help me, and fyi ima noob to Linux so yea.....Help Please.

---

### Post by pepsi_max2k on 2007-04-22
> **anachreon_ said:**
> The ATI linux driver / support seems pretty spotty.

*ahem* sure, may not work so well, but...

[http://ati.amd.com/support/drivers/linux/radeonprevious-linux.html](http://ati.amd.com/support/drivers/linux/radeonprevious-linux.html) - one release a month, every month, for the past year.

[http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html) - a couple in december. nothing for 3 months. one at beginning of march. nothing for 2 months. one a couple days ago.

i dunno what your idea of spotty is, but that nvidia release table looks pretty spotty to me :) i won't complain about their drivers when they do release em though, they're great. well, their linux ones are. they haven't released one for win XP for 6 months, and there's plenty of people with problems after that much time :(

---

### Post by Mongoose on 2007-04-23
Yes, the 8XXX series works great under Linux.  If you have one of the mid/lower end 8XXX cards you MUST use the newly released driver from Nvidia.  Visit there website and install their driver package.  I know people that have been running 8800s before that new driver release, but like I said if you have newer model you can only use the 1xx series of drivers.  Drivers for new hardware isn't even the issue -- a PS/2 mouse?  Come on.  It's funny I got working GLSL in Linux way before OS X for example, and in fact good GLSL still hasn't come to OS X yet.  The problem here wasn't reverse engineering hardware -- it was shitty QC from Linus' upstream on down.   This kernel has been a setback in quality for many, but the last minute tacked-on policy changes and packaging made it worse.  

Right now I recommend LTS, or Feisty if you don't mind building your own kernel/libs and fixing all the bugs and packaging yourself.    Also Debian is always a good choice for stability.

---

