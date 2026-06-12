---
title: "What is wrong with Ubuntu 6.10 install?"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by AAM on 2007-01-05
I have come to the conclusion that the Ubuntu team may have stuffed up the installation routines of Edgy 6.10.

I have a similar problem to many posters - namely that after loading the LiveCD and rebooting, the cylon progress bar starts and then everything disappears. 

Lots of posts say this occurs with LCD screens and ATI cards, although there are many posts blaming nVidia cards too, so I don't believe its ATI. LCD screens seem to be much more commonly the problematic denominator. 

Through a series of unfortunate incidents to do with chipset support, my functioning Ubuntu Dapper sits on a the small 'experimental' partition and I want to move it to replace the large MEPIS 'stable' partition, but wanted to use Edgy 6.10 because I can get it stable before the transition.

BUT ....in goes the LiveCD (i386 or AMD64) with a large variety of the fixes described in the forums, including various screen specifications (xdriver=vga, vesa; res=1440x900) but all result in the same outcome. Also tried no acpi and such like, always the same. I'm sick of downloading, burning and MD5sum checking isos to find that they are all good.

THE ERROR HERE IS NOT ME! (yes, I am shouting, I'm frustrated)

I put in an old Dapper 6.06.0 disk last night and I got the LiveCD desktop no trouble. Resolution is a bit wonky (16:9 > 4:3) but otherwise OK. So what gives? Same hardware, so it isn't me! The 1440x900 LCD is detected enough to work (SATA isn't but that was why I had to use MEPIS in the first place while waiting for 6.06.1). Yes, I am sure that it was working!

Unfortunately, there is no Ubuntu announcement to acknowledge a problem and suggest a fix. Why are there so many install problems? Is it LCDs? LCDs are very common, and 1440x900 is also common enough. 

So what is the conclusion? If my hardware were so crazy, MEPIS would not work (it does!), Knoppix 5.0 wouldn't work (it does!) and Dapper 6.06.0 would not work (it does!). Only Edgy 6.10 doesn't. THE ERROR HERE IS NOT ME! (that shouting is to try to get attention).

Ubuntu is failing in my estimation as a 'user friendly' distro. Ubuntu firstly needs to be friendly to my previously supported hardware, then me!

---

### Post by userundefine on 2007-01-05
I agree that there were some problems with the latest livecd.  However, the old method of installing Ubuntu, from an older Debian-style GUI, exists on the alternative CD and is quicker, IMO, with the same questions.  It doesn't require X.

I suggest you try that.

Edit: Here, this is the description you'll get at all mirrors.  Regardless of the "following situations", you can install it in place of the desktop livecd.

> Alternate install CD

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installing GRUB to a location other than the Master Boot Record;
    * installs on systems with less than about 192MB of RAM. 

There are three images available, each for a different type of computer:
[URL="http://ftp-mirror.internap.com/pub/ubuntu-releases/edgy/ubuntu-6.10-alternate-i386.iso"]
PC (Intel x86) alternate install CD[/URL]
    For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows. Choose this if you are at all unsure.

---

### Post by Morkalin on 2007-01-05
Hi Aam,

I also had this problem and today after searching through the forums I finally found a solution which worked for me.  Thanks whoever it was, I'm not sure who posted it initially.  My specs:

Acer 5024 WLMi notebook aka Acer Aspire 5020
- 1GB RAM
- 100GB HDD
- ATi Mobility Radeon X700 graphics chipset

Now the solution in a nutshell:
- Boot with normal live CD / Installation CD, no alternative needed in my case
- Press F6 at the very first Ubuntu menu to get extra boot options
- In editing the line that comes up delete the word "splash" from the boot line
- After the "--" add a space and "break=bottom"
- Press enter to boot Ubuntu
- Once you get to the prompt type "chroot /root"
- cd to X11 and edit the xorg.conf file with nano
- in the xorg.conf file find your graphics device section and change "ati" or whatever is selected as the driver for your card to "vesa"
- Save the file
- Once back at the command prompt type exit and enter twice and this will hopefully now be able to start the Ubuntu installation with safe graphics ("safer" than the safe mode option which didn't work for me)

I hope this works for you too.

Regards,
Morkalin

---

### Post by AAM on 2007-01-05
This is very user-friendly!

(not having a go at you, Morkalin, but really hardly the stuff that you expect a Windows killer to do!

Few people install Windows from barebones start, so Ubuntu has to be flawless ... and this is just so far from flawless, its not funny.

AAM

---

### Post by userundefine on 2007-01-05
Linux is not Windows.  If you aren't "convinced" enough to judge Linux on its own merits, Linux is probably not for you.  By "convinced", I mean you have multiple reasons for wanting to use Linux.  And, rarely does the first try to switch to Linux take.  It didn't take for me, doesn't take for most people.

---

### Post by justin whitaker on 2007-01-05
AAM,

I never use the live or desktop CD, only the Alternate. It seems that every live-CD batch gets a host of hardware related errors and the attendant posts....it's not worth it if you are familiar with the text install. 

I'd say download the Alternative CD, and give that a shot. The whole process is fairly painless. 

And you are right: if you want to make things user friendly, then "it just needs to work." User friendly does not necessarily mean easy tho'. ;)

Mateo

---

### Post by sdowney717 on 2007-01-05
I have some problems with system admin update manager.
After I run thru some updates and restart, I lose Xwindows.
just a blank screen.

So far Fedora core 6 seems to be better. But on that install I have to fix recheck grub for every computer I have put it on. seems FC6 does not write the grub properly at install time.

---

### Post by justin whitaker on 2007-01-05
> **sdowney717 said:**
> I have some problems with system admin update manager.
After I run thru some updates and restart, I lose Xwindows.
just a blank screen.

So far Fedora core 6 seems to be better. But on that install I have to fix recheck grub for every computer I have put it on. seems FC6 does not write the grub properly at install time.

There have been a bunch of issues with Xorg updates lately (hence all the sticky threads). Not the first time this sort of thing has happened with Ubuntu, although you would think that they would have their QA down by now. 

That said, I do not know of any Linux, Windows, or BSD release that runs 100% on all hardware all the time. 

Ubuntu is way better than most, but not as stable as, say, Slackware. Price of living on the edge, I'm afraid.

---

### Post by sdowney717 on 2007-01-05
Also, build-essentials package from the cdrom install ought to be installed by default!
Otherwise you cant 'make' compile anything.

---

### Post by macogw on 2007-01-05
> **justin whitaker said:**
> There have been a bunch of issues with Xorg updates lately (hence all the sticky threads). Not the first time this sort of thing has happened with Ubuntu, although you would think that they would have their QA down by now. 

That said, I do not know of any Linux, Windows, or BSD release that runs 100% on all hardware all the time. 

Ubuntu is way better than most, but not as stable as, say, Slackware. Price of living on the edge, I'm afraid.

I would just like to say that I installed a video update in Windows and went for 32-bit 1024x768 to 16-bit whatever's-less-than-800x600.  Eventually figured out how to roll-back the driver and make it work again.

sdowney, the reason build-essential is not there is that most home users probably don't care to learn all that development building stuff.  Nerds build from source.  If you're a nerd, get the package.  If you're not a nerd, you probably don't need it anyway since there's tons of stuff in the repos and you probably won't be writing and compiling code.

---

### Post by sdowney717 on 2007-01-05
thing about that is, when you need it to be there and expect it to 'make' and it does not do what you assumed it should do, it will cause some stress.

I dont see any reason why it should not be installed by default.
IMO, It is more nerdy to have to go searching for why something does not work.

In my own situation, I had to install an agere modem. There were a lot of web pages I had to run thru and questions to ask and lots of wondering why until I finally got martian to work.

I got it down now, except I cant use the winmodem except when running as root in Xwindows.
If I log in as scott, gnome-ppp does not see the modem.
How do I fix that?

---

### Post by Morkalin on 2007-01-05
Hi AAM,

Sorry I thought you just wanted to get up and running so I thought I'd post my solution to help you out.  I would be interested to know if that does work for you if you're willing to give it a try.  It's definitely not a "beginner" solution by any means and IMO the Ubuntu people are simply trying to make the installation / Live CD part too pretty hence loading Ati / Nvidia drivers etc at startup which is what breaks it.  I think they should just split the installation and live CDs again and it will solve most of these installation issues.

Regards,
Morkalin

---

### Post by rbhigday on 2007-01-05
> **Morkalin said:**
> Hi Aam,

I also had this problem and today after searching through the forums I finally found a solution which worked for me.  Thanks whoever it was, I'm not sure who posted it initially.  My specs:

Acer 5024 WLMi notebook aka Acer Aspire 5020
- 1GB RAM
- 100GB HDD
- ATi Mobility Radeon X700 graphics chipset

Now the solution in a nutshell:
- Boot with normal live CD / Installation CD, no alternative needed in my case
- Press F6 at the very first Ubuntu menu to get extra boot options
- In editing the line that comes up delete the word "splash" from the boot line
- After the "--" add a space and "break=bottom"
- Press enter to boot Ubuntu
- Once you get to the prompt type "chroot /root"
- cd to X11 and edit the xorg.conf file with nano
- in the xorg.conf file find your graphics device section and change "ati" or whatever is selected as the driver for your card to "vesa"
- Save the file
- Once back at the command prompt type exit and enter twice and this will hopefully now be able to start the Ubuntu installation with safe graphics ("safer" than the safe mode option which didn't work for me)

I hope this works for you too.

Regards,
Morkalin

How far after entering in the -- break=bottom will the prompt appear, I getting stuck in different places this time, it saying Kernel Panic - not syncing: vhs; unable to mount root fs at this time and froze.

---

### Post by rbhigday on 2007-01-05
> **Morkalin said:**
> Hi Aam,

I also had this problem and today after searching through the forums I finally found a solution which worked for me.  Thanks whoever it was, I'm not sure who posted it initially.  My specs:

Acer 5024 WLMi notebook aka Acer Aspire 5020
- 1GB RAM
- 100GB HDD
- ATi Mobility Radeon X700 graphics chipset

Now the solution in a nutshell:
- Boot with normal live CD / Installation CD, no alternative needed in my case
- Press F6 at the very first Ubuntu menu to get extra boot options
- In editing the line that comes up delete the word "splash" from the boot line
- After the "--" add a space and "break=bottom"
- Press enter to boot Ubuntu
- Once you get to the prompt type "chroot /root"
- cd to X11 and edit the xorg.conf file with nano
- in the xorg.conf file find your graphics device section and change "ati" or whatever is selected as the driver for your card to "vesa"
- Save the file
- Once back at the command prompt type exit and enter twice and this will hopefully now be able to start the Ubuntu installation with safe graphics ("safer" than the safe mode option which didn't work for me)

I hope this works for you too.

Regards,
Morkalin

Thanks for this between this and other I was able to gain access but I had to do it a bit different

the chroot /root did not work this is what I did
cd to bin i think i not sure as i went into several directories looking for the nano file
find nano 
then type nano /etc/X11/xorg.conf

make the changes stated above and the save which is ctrl +o and then exit which is ctrl +x

hope this helps someone, remember the help people give may work or you may have to tweak it, for it to work on your system.

---

### Post by AAM on 2007-01-05
Thanks for the help guys. Unfortunately it is Saturday here and I have to mow and weed!

Morkalin, thanks for the help, I'll post the results when I've had a chance (?8 hours time).

I'm not a recent user, I have been using Linux since Mandrake 9.1 (?2001). I run Ubuntu on 4 machines at home, one at work, and one on my son's laptop (until he defected to the dark side!). I have managed wine use, ndiswrapper use, ATI hardware acceleration and XGL installation. I am not a high level tweaker. but I can read the HOWTOs and forums ... But that LiveCD has me beat!

Given the abilities of Knoppix, Kanotix, Ubuntu, MEPIS, etc I really can't understand how there isn't more talking.

AAM

---

### Post by Morkalin on 2007-01-05
rbhigday: I'm glad you managed to get it working now - as you asked the first time the prompt would be quite recogniseable under normal circumstances, it should definitely not give you a kernel panic or anything - that would probably indicate a different issue.

AAM: I definitely appreciate that this new release should have done better - I think they are just trying to put too much into an installer that worked fine for most people in the last release.  I would be keen to see if this solution works for you too.

Regards,
Morkalin

---

### Post by AAM on 2007-01-06
Well, Ubuntu giveth and Ubuntu taketh!

Morkalin, your instructions worked just fine (I used sudo nano /etc/X11/xorg.conf) but otherwise it was fine.

BUT ....

then I tried to install and no go! No hard drive recognized! This was the same problem with 6.06.0 that was fixrd with 6.06.1 (no recognition of VT chipset). So I am installing 6.06.1 now as it is all too difficult. I'll think about the AlternateCD when my equilibrium is re-established.

AAM

---

### Post by AAM on 2007-02-09
An update .....

I have tried everything to get 6.10 working - 6.10-386, 6.10-AMD64, text install, -break=bottom ... EVERYTHING! 

Everything breaks. Took about 4 disks to get something to even install (was successful with text installer), altered xorg.conf (it has recognised the monitor), but on reboot monitor just says "out of range".

So I am back to 6.06. Mind you I can configure my wireless card in my sleep! NDISwrapper is my friend!

---

### Post by daller on 2007-02-11
Have you tried 7.04 Feisty Fawn?

---

### Post by Irony on 2007-02-12
Edgy doesn't work for me, Hoary, Breezy and Dapper I had no problems. Updating to Edgy and I had a frozen mouse (standard ps2 mouse). Live CD doesn't work so I did a fresh text based install, installed fine but on boot up just get a progress bar then a blank screen.

I'll try that ati to vesa thing next. Maybe have to wait for the next stable LTS release or use PCLinuxOS.

---

### Post by Irony on 2007-02-13
It worked! I changed ati to vesa in my xorg.conf file - not sure why it should have ati in the first place.

I've just installed the radeon accelerators as described in the wiki and will see if this speeds up the graphics.

---

### Post by AAM on 2007-03-02
An update!

I received a Feisty DVD today and tried it ......... SAME PROBLEM! It installed easily on the Athlon1500 with 19 inch CRT, but no go on the 1440x900. Not standard and not 'safe graphics' AND not text install! 

I'll try Morkalin's instructions again.

---

