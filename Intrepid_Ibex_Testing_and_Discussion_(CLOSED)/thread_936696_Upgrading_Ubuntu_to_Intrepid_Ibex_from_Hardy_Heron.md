---
title: "Upgrading Ubuntu to Intrepid Ibex from Hardy Heron"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sef on 2008-10-03
First, before upgrading read these:

a) run the update manager to make sure that all the updates have been applied to your system.

b) read the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/810").

c) Read the other stickes in this forum.  

d) **Back up** all your data.   There is no guarantee that all will go well.

e) **Backing up with rsync** - tutorial links.  ([see post #20]("http://ubuntuforums.org/showthread.php?t=936696&page=2"))

f) Remember that this software is still beta at this time. It is not for production machines.

g) For more information about upgrading to Intrepid Ibex, click [here]("https://help.ubuntu.com/community/IntrepidUpgrades").

h) Test the Live CD for a while to make sure that your hardware will work with it.   Use all the applications that you will use when you install it.

i) Have a copy of Hardy Heron, in case the upgrade or clean install fails.   That way you can reinstall it and have a working system.
____________________________________________________________________________________

Second, this upgrade only applies to **Ubuntu** and **Xubuntu** Hardy Heron, 8.04.

- Only [upgrade]("https://help.ubuntu.com/community/IntrepidUpgrades") this way:

>  To upgrade from Ubuntu 8.04, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '8.10' is available. Click Upgrade and follow the on-screen instructions. ____________________________________________________________________________________


Third, this [upgrade]("https://help.ubuntu.com/community/IntrepidUpgrades") only applies to Kubuntu Hardy Heron, 8.04:


> Open the *Run Command* dialog by pressing *Alt+F2*.


 Type kdesu "adept_manager --dist-upgrade-devel" in the command box and press the *OK* button. _____________________________________________________________________________________



Fourth, this [upgrade]("https://help.ubuntu.com/community/IntrepidUpgrades") applies only to the alternate cd:


> 


[LIST=1]
[*]Download and burn the **alternate** installation CD.
[*]Insert it into your CD-ROM drive.
[*]A dialog will be displayed offering you the opportunity to upgrade using that CD.
[*]Follow the on-screen instructions.
[/LIST]
_____________________________________________________________________________________


Fifth, for a network upgrade, click [here]("https://help.ubuntu.com/community/IntrepidUpgrades") and go to network Upgrade for either Desktops or Servers.

____________________________________________________________________________________


Sixth, to do a clean install instead of an upgrade, click [her]("http://releases.ubuntu.com/8.10/")e.

---

### Post by perlluver on 2008-10-03
Just wanted to say that Intrepid Is very stable, no problems other than with Epiphany webkit.

---

### Post by anuban on 2008-10-03
Thanks a lot.
I m doing a clean install and the 'New Human' theme looks really good.:D

Cheers
Anurag Bansal
[http://www.knowliz.com](http://www.knowliz.com)

---

### Post by jdong on 2008-10-03
Sef, I should also say, **Test an Intrepid LiveCD first** to make sure all your hardware still works in this beta release. I'd hate to apply 3 hours of irreversible upgrades to find out that my hard drive no longer gets detected and I get stuck at a boot panic :)

---

### Post by Sef on 2008-10-03
> Sef, I should also say, **Test an Intrepid LiveCD first** to make sure all your hardware still works in this beta release. I'd hate to apply 3 hours of irreversible upgrades to find out that my hard drive no longer gets detected and I get stuck at a boot panic

Added.  Thank you for the excellent suggestion.

---

### Post by WiFi Ed on 2008-10-03
I'm ready to plunge in to Intrepid Ibex but I have a minor concern about the ethernet "corruption" issue.

Has the kernel in the beta release been updated to fix this yet? My hardware may or may not be affected by this, but I'd like to be sure before diving in...

Thanks in advance!

---

### Post by jdong on 2008-10-03
In the beta, the affected driver was disabled. It will not load on systems susceptible to this problem, but that also means no wired networking. A kernel update arriving VERY SOON that you can apply to Intrepid via Update Manager will turn the driver back on, with a fix incorporated.

---

### Post by WiFi Ed on 2008-10-03
> **jdong said:**
> In the beta, the affected driver was disabled. It will not load on systems susceptible to this problem, but that also means no wired networking. A kernel update arriving VERY SOON that you can apply to Intrepid via Update Manager will turn the driver back on, with a fix incorporated.

Thanks for the info! I'm downloading the beta now, so I guess I'll know if I'm affected when I boot the LiveCD. If ethernet works, no problemo, if not, I wait for the new kernel.

I'm downloading directly from the server at about 100 KB/sec and torrenting at the same time. Transmission seems to have stalled on the download after getting about 100 MB (shows "none"), but I have 12 connected peers being seeded at 48KiB/sec.

Update: Bummer...no ethernet with the beta LiveCD. Guess I have the vulnerable chipset.

---

### Post by Fazer2 on 2008-10-03
> **WiFi Ed said:**
> Thanks for the info! I'm downloading the beta now, so I guess I'll know if I'm affected when I boot the LiveCD. If ethernet works, no problemo, if not, I wait for the new kernel.

I'm downloading directly from the server at about 100 KB/sec and torrenting at the same time. Transmission seems to have stalled on the download after getting about 100 MB (shows "none"), but I have 12 connected peers being seeded at 48KiB/sec.

Update: Bummer...no ethernet with the beta LiveCD. Guess I have the vulnerable chipset.
Or maybe you have to reinstall your drivers?

---

### Post by jdong on 2008-10-03
> **WiFi Ed said:**
> 
Update: Bummer...no ethernet with the beta LiveCD. Guess I have the vulnerable chipset.

The fixed/re-enabled driver was already uploaded yesterday; should be a matter of hours before it is available as an update. Of course that doesn't help if you only have ethernet.... :)

---

### Post by WiFi Ed on 2008-10-03
It looks like I'll have to wait for the RC. Sigh...

---

### Post by Sef on 2008-10-04
> It looks like I'll have to wait for the RC. Sigh...


It should be in sooner than that.  It is already available as [source]("https://launchpad.net/ubuntu/intrepid/+source/linux/2.6.27-5.8").  I would expect a few days at the most.  The kernel number is 2.6.27-5.8

---

### Post by WiFi Ed on 2008-10-04
What would be the easiest way to get the new kernel into the Ibex beta without an ethernet connection (when booted to Ibex)? Could I download it in Hardy or Windows and then integrate it into Ibex somehow?

---

### Post by jdong on 2008-10-04
You can download the first "daily" ISO spin after the build systems wake up.

---

### Post by Gina on 2008-10-04
Or update the ISO you already have using rsync - saves downloading the whole file, rsync only downloads the changes, making a significant saving.

---

### Post by jerrylamos on 2008-10-04
Dual Boot has saved me big time again and again.  

A number of the Alpha's and Beta's have failed to run on my stock IBM Thinkpad R31 or my Compaq Presario.

I either download from the Alpha or Beta announcement, or much more commonly rsync from Daily Build of Ubuntu, Xubuntu, Kubuntu.

1.  If CD Live doesn't work, chances are an install will not!
2.  Right now, the Beta won't boot to Gnome Desktop at all on this IBM Thinkpad R31.  What saved me is dual boot.  The other image is an Alpha 5 NOT UPDATED which does work.
3.  Beta and Alpha 6 both boot to "black screen" frozen keyboard at the point Gnome should load the desktop.  Dead.  Launchpad bug 277344.
4.  What I had to do to get Beta to limp along was to install, which worked since it doesn't use the Gnome desktop, boot in recovery mode, do "fix broken packages", then install Xfce4 which does work.

An upgrade or update without dual boot would have wiped me out several times.

Jerry

---

### Post by uflieven on 2008-10-04
Has anyone tested the Xubuntu live-CD daily image 4th October?
Still no ethernet on live-cd, thought it was going to be fixed :(

---

### Post by gg234 on 2008-10-04
check this simple upgrade guide [http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibex-beta.html](http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibex-beta.html) including screenshots.

Hope this helps someone

---

### Post by jlh68 on 2008-10-04
**Gina**:  What is the process of using "resync"?
A short how-to would be helpful.

---

### Post by Sef on 2008-10-04
> **Gina**:  What is the process of using "resync"?
A short how-to would be helpful.     [Rsync Howto]("http://ubuntuforums.org/showthread.php?t=639979") Tutorials and Tips or [Rsync Howto]("https://help.ubuntu.com/community/rsync") Community Documents

**What is rsync?**

From the Rsync Howto Community Documents (in part):

> **rsync** is  a program that copies file from one location to another, with it you can make **backups** of your files, **synchronize** data on different locations and computers. It is commonly used by unix users to keep a safe backup of their files and is often recommended as the simplest solution for backups and safety copys. 
Rsync minimizes data transfer using delta encoding when appropriate. An important feature of rsync not found in most similar programs/protocols is that the mirroring takes place with only one transmission in each direction. 

---

### Post by anuban on 2008-10-04
I fresh installed Ibex on Hardy with a separate Home.  So all my data is intact.
I am really very impressed with the new dark theme.

But sometimes I am running into an issue where Ibex doesn't let Ubuntu boot.  The slider just gets frozen at around 20% and the only option I have is to Hard Reset. 
I tried restarting, but that doesn't help.  But after several trials it sometime goes through.  But this is not what it should be doing.   I hope this bug has been reported and the devs are aware of it.

Is there any quick solution for this prob...anyone..???:confused:

Thanks
Ubuntu Rocks, Ibex rocks even more...!!!:D

Anurag Bansal
[http://www.knowliz.com](http://www.knowliz.com)

---

### Post by grappler on 2008-10-04
I just tried to do a clean install of 8.10, after using 8.04 on my thinkpad t61p. It was a disaster. Not only  did I have the GigE problem so no ethernet

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555)


but I also had the "Wireless event too big" problem with my ipw4965 card

[https://bugs.launchpad.net/ubuntu/+bug/267063](https://bugs.launchpad.net/ubuntu/+bug/267063).

So no internet connection at all!! I'm just doing a reinstall of 8.04. 

My advice for owners of this laptop is to wait till the RC version appears and the bugs have been fixed

---

### Post by Sef on 2008-10-04
> I just tried to do a clean install of 8.10, after using 8.04 on my thinkpad t61p. It was a disaster. Not only did I have the GigE problem so no ethernet

[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/263555]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555")


but I also had the "Wireless event too big" problem with my ipw4965 card

[https://bugs.launchpad.net/ubuntu/+bug/267063](https://bugs.launchpad.net/ubuntu/+bug/267063).

So no internet connection at all!! I'm just doing a reinstall of 8.04. 

My advice for owners of this laptop is to wait till the RC version appears and the bugs have been fixed     Here's the [GigE sticky]("http://ubuntuforums.org/showthread.php?t=927943") about that problem. Actually it is in the rc version too.   Within  a few days, a newer version (2.6.27-5.8) will be in the repositories and the problem is fixed in it.

Update: The 2.6.27-5.8 kernel is now in the repositories.

---

### Post by sYnOnYx on 2008-10-05
everything is working great for me, its faster than hardy so far. But. I cant get desktop effects enabled. Running a ATI Radeon X1600, any ideas?

---

### Post by carusoswi on 2008-10-06
Stumbled onto the availability of this beta at the end of my weekend.  Call me brave or fool-hearty, but I first downloaded both the live CD file and the Alternate CD file, then, ran the online update routine, and all is working well.  If figured if the upgrade worked, great.  If it didn't, well, there are enough kinks in my XP dual boot that a system rebuild would not be the end of the world.  What I guess I will miss is the sure convergence that I was realizing in solving why 8.04 would randomly lock up on me.  Hopefully, that convergence is moot with the new beta - we'll see.

One thing that threw me off was re-establishing my wireless connection.  The old iwconfig command appears to show valid associations, but, apparently, you cannot use the command line in a terminal to establish a wireless adapter associaton - it would not work for me, and the old Network menu choice is no longer present under System-Administration.

Took me quite a while (5 minutes or less) to discover the icon at the top right of the screen that allows you to graphically browse available connections and to choose one and set it up.

I would criticize the developers for not warning me about this, except that I haven't spent the time reading the documentation in order to ascertain that I didn't miss the warning.

The upgrade process went flawlessly.  I did read some little blurb about a minor performance hit that I suffer from upgrading rather than doing a fresh install.  Would appreciate if someone could clarify that point for me.

Can't say that I've seen much of this new version, yet, but, so far, I see nothing that evokes other than a positive feeling about it.

Caruso

---

### Post by run1206 on 2008-10-06
i just upgraded from hardy to intrepid; all went well. The only problem is the shutdown problem i had before (would freeze after "Will now restart" came on ).

probably a networking issue like before, but that's not a big problem.  Other than that, Intrepid is running pretty good on my Toshiba Satellite :)

i like how you have a Quick Search in Synaptic now, and the theme is pretty awesome too.  Kudos to the developers ;)

---

### Post by zbrox on 2008-10-06
I had some great problems upgrading my girlfriend's laptop to Intrepid Beta. She had some minor problems, so we decided to try the new beta. I'm with Intrepid since early pre-alpha, so I thought everything will be ok.
However the upgrade manager spew some nasty errors while upgrading and in no time libc6 was corrupted.

I tried booting the live CD, but it turns out there are some major problems with the disk drive drivers. It kept spilling buffer I/O errors about sr0 (I guess this is some raid device, probably the cd-rom). This is on a Dell Vostro 1310 laptop. I was able to boot using the alternate cd, chroot, then install the Intrepid libc6 packages by using the LC_ALL=C prefix. The packages I had to download from another computer.

After that a reboot and numerous dpkg -i --force-all installations of separate packages, until dpkg --configure -a ran and then apt-get -f install.

I'm just sharing, in case anybody runs into something similar.

---

### Post by Sef on 2008-10-06
>  I'm just sharing, in case anybody runs into something similar.

Thank you for sharing that.

---

### Post by plun on 2008-10-06
> **zbrox said:**
> spew some nasty errors while upgrading and in no time **libc6 was corrupted**.



There is a bug filed about libc6 and this is important to track down.

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/278804](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/278804)

Thread about this:
[http://ubuntuforums.org/showthread.php?t=939129](http://ubuntuforums.org/showthread.php?t=939129)

---

### Post by zbrox on 2008-10-06
It looks like the same problem but not quite. In my case the dist upgrade failed on numerous packages, including the libc6 one and the errors seem similar to those.
After that however nothing was able to start, giving an error about the command needing GLIBC_2.8. I couldn't even run ls in the command prompt. And when the computer was shut down it wasn't able to start up.
I'll post a link to my entry here, just in case, but maybe the problem is different... I don't know...

---

### Post by plun on 2008-10-06
> **zbrox said:**
> It looks like the same problem but not quite. In my case the dist upgrade failed on numerous packages, including the libc6 one and the errors seem similar to those.
After that however nothing was able to start, giving an error about the command needing GLIBC_2.8. I couldn't even run ls in the command prompt. And when the computer was shut down it wasn't able to start up.
I'll post a link to my entry here, just in case, but maybe the problem is different... I don't know...

Yup.. add your info to the bug report because our devs probably needs
good clues about this.

Also check this bug report if the developer asks for more info, log files etc.

---

### Post by zbrox on 2008-10-06
I'll do that probably tonight, cause right now I'm at work and not on the computer that had the problem.

---

### Post by jlh68 on 2008-10-06
Well with some suggestions from this forum, I finally got my laptop to boot up with 8,10 beta.  I seem to have a slight problem yet, as when I click on the [Places] then any one of the subdirectory choices (such as Home, or Desktop, or any other one) It opens smplayer, instead of the file.  I feel that this is an option that can be changed but I do not know how.

I do notice with the new WiFi driver my signal strength is better.  It appears that 8.10 is using an non-restricted driver now instead of the restricted one in 8.04.

Thanks to all of those that have posted help suggestions.  What worked was a reconfigure of the xserver-Xorg

---

### Post by rouge568 on 2008-10-06
A Warning:
Anyone upgrading should first go into their power preferences and be sure that the computer will not shut down and that the screen will not lock or blank. During my upgrade, the screen went blank and locked (like it was supposed to), but it then crashed, as the mouse and keyboard went unresponsive and the password dialogue box never came up. I was forced to do a hard reset, corrupting the upgrade process. Luckily for me, I knew enough to boot into recovery mode and finish the upgrade manually. Others might not be as fortunate.

So again:
**Before attempting to upgrade to 8.10, make sure that the power preferences will not make the computer shutdown, blank the screen, or lock the screen during the upgrade process.**

---

### Post by The Cokeaholics on 2008-10-07
> I seem to have a slight problem yet, as when I click on the [Places] then any one of the subdirectory choices (such as Home, or Desktop, or any other one) It opens smplayer, instead of the file. I feel that this is an option that can be changed but I do not know how.

Just open Nautilus from a terminal, right-click a folder and change the preferences. (In my case it openened Kaffeine player after I had upgraded to an earlier alpha.)

Robert

---

### Post by Gina on 2008-10-07
> **Sef said:**
> [Rsync Howto]("http://ubuntuforums.org/showthread.php?t=639979") Tutorials and Tips or [Rsync Howto]("https://help.ubuntu.com/community/rsync") Community DocumentsThank you Sef :) I was going to find and post links but been very busy lately.  I also intend adding that and a number of other things to add to my website when I can.

---

### Post by Sef on 2008-10-07
> Thank you Sef :smile: I was going to find and post links but been very busy lately. I also intend adding that and a number of other things to add to my website when I can.

You're welcome.  If you need any help looking, please let me know.

---

### Post by Gina on 2008-10-07
I will - thank you :)

---

### Post by phoogkamer on 2008-10-08
I have been testing an upgrade from a clean Hardy Heron 8.04.1 to Intrepid Beta release. This went flawless. No trouble at all.
I have done this upgrade on a vmware virtual machine.

Peter

---

### Post by crazypenguin2008 on 2008-10-08
i did the hardy to intrepid upgrade on a spare hdd i had and everything went great untill the last update(yesterday 10/7/2008)
i lost wireless and the ability to create a wireless network.

---

### Post by andreselsuave on 2008-10-13
I updated last night and had some errors with some of the packages. I can get to the users selection screen now but when I log into any of them, the Desktop won't load (flat blue screen and mouse). I've been searching the forums this morning and I dont know what to do. Im a bit dissapointed :(

Any help would be appreciated. Thanks

---

### Post by NeoFax on 2008-10-13
Upgraded from Heron to Intrepid went great!  Kudos to all for the hard work!  Intrepid is stable enough, just some niggling problems at the moment.

---

### Post by gibbylinks on 2008-10-13
> **andreselsuave said:**
> I updated last night and had some errors with some of the packages. I can get to the users selection screen now but when I log into any of them, the Desktop won't load (flat blue screen and mouse). I've been searching the forums this morning and I dont know what to do. Im a bit dissapointed :(

Any help would be appreciated. Thanks

same boat here. I have desklets running and can see processes going in, but no icons or menus. 

Help appreciated

---

### Post by thuja.forevergreen on 2008-10-13
I have the same problem as the two users above me.  When I reboot, the user screen comes up, but when I log in, it goes to an orange screen, but x/desktop won't load.  I try to failsafe gnome, but still no go.  I can failsafe the terminal of course and access some programs from there.  Is there a fix for this yet?

---

### Post by Sef on 2008-10-13
> thuja.forevergreen 	 		**Re: Upgrading Ubuntu to Intrepid Ibex from Hardy Heron**
 I have the same problem as the two users above me. When I reboot, the user screen comes up, but when I log in, it goes to an orange screen, but x/desktop won't load. I try to failsafe gnome, but still no go. I can failsafe the terminal of course and access some programs from there. Is there a fix for this yet? 

> gibbylinks 	 		**Re: Upgrading Ubuntu to Intrepid Ibex from Hardy Heron**

	 	 
same boat here. I have desklets running and can see processes going in, but no icons or menus. 

Help appreciated 	

> andreselsuave 	 		**Re: Upgrading Ubuntu to Intrepid Ibex from Hardy Heron**
 I updated last night and had some errors with some of the packages. I can get to the users selection screen now but when I log into any of them, the Desktop won't load (flat blue screen and mouse). I've been searching the forums this morning and I dont know what to do. Im a bit dissapointed :sad:

Any help would be appreciated. Thanks 	


1) What graphics cards are you using?  This is most likely a graphic card problem.

2) What are your system specs?

---

### Post by gibbylinks on 2008-10-14
> **Sef said:**
> 1) What graphics cards are you using?  This is most likely a graphic card problem.

2) What are your system specs?


See below

1) Inno3D 6600GT 128mb (Nvidia chipset)

2) 
Gigabyte GA7N400 Pro
AMD XP3000+
3x 512mb DDR400 PC3200 RAM
80gb Barracuda (SATA 0)
160b Maxtor (SATA 1)
60gb WD600AB(IDE 3)
Sony CRX230ED(IDE 1)

---

### Post by jerrylamos on 2008-10-14
> **thuja.forevergreen said:**
> I have the same problem as the two users above me.  When I reboot, the user screen comes up, but when I log in, it goes to an orange screen, but x/desktop won't load.  I try to failsafe gnome, but still no go.  I can failsafe the terminal of course and access some programs from there.  Is there a fix for this yet?

After weeks! of thrashing around Alpha's (some ran, some didn't) & Beta the "Intrepid orange screen" fix for me on this IBM Thinkpad R31 Celeron 32 bit Intel graphics was:

Boot in recovery mode
Select command line prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core

then the desktop ran.  Original Alpha 5 compiz works on the Thinkpad, which is dual booted, however Alpha 6 & Beta compiz don't.

Sometimes booting goes to command line login prompt, so then I log in and do a 
sudo startx
which works.  Since I'm all about applications,  doing full screen internet, full screen Office, full screen Picasa, ... the "desk top eye candy" that compiz offers is of no use to me.  

I don't have any way of knowing however it seems to me that compiz is all about fancy effects by playing tricks with graphics adapters & drivers, and getting into trouble with the wide variety of hardware and software out here.  

Tell me all over again why compiz has to be installed by default whether I want or use it or not?

Jerry

---

### Post by colonelk on 2008-10-14
Anyone tried an upgrade of Hardy running in WUBI on Vista?

---

### Post by gibbylinks on 2008-10-14
My problem was nothing to do with the x-server.  For some reason scrollkeeper had un-installed which caused a load of packages not to configure correctly.

I couldn't see this at first because every time I ran apt-get the error messages disappeared of the top off the screen. It's only when I did "apt-get |more" that I could read the messages.

Any way I installed scrollkeeper and all the other packages then configured correctly, so I'm now up and running.

:guitar:

---

### Post by BoredOutOfMyMind on 2008-10-14
Is there an Ethernet fix available.  upgrade last night left me with no network and no GDM.

---

### Post by Gael33 on 2008-10-14
I took the leap of faith a couple of days ago, and except for booting problems (I sometimes have to reboot the machine several times to get going), everything else appears to be working fine.
I think I may backup my personal stuff in the next couple of days, and when the 'official' stable version is released I will do a complete clean install.
I must say that I am fairly new to Linux Ubuntu but I'm very impressed with it's workability and ease of use. 
I also have Windows XP Pro on another partition for flexibility as some of my working programs are incompatible with Linux.

gael.

HP Compaq dx 2250 with AMD 64 Athlon 3800+
Platform 86_64
120 gb hdd SATA 0
ATI Graphics Card
Memory 874 MB

---

### Post by thuja.forevergreen on 2008-10-14
okay, scrollkeeper was my problem too.  I can finally get to the desktop now.  

apt-get install scrollkeeper
dpkg --configure -a
apt-get install ubuntu-desktop
apt-get install xserver-xorg-input-all

the last two i did just to make sure, but the culprit was scrollkeeper.  when I installed it, it did some funky stuff.

---

### Post by run1206 on 2008-10-15
> **Gael33 said:**
> I took the leap of faith a couple of days ago, and except for booting problems (I sometimes have to reboot the machine several times to get going), everything else appears to be working fine.
I think I may backup my personal stuff in the next couple of days, and when the 'official' stable version is released I will do a complete clean install.
I must say that I am fairly new to Linux Ubuntu but I'm very impressed with it's workability and ease of use. 
I also have Windows XP Pro on another partition for flexibility as some of my working programs are incompatible with Linux.

gael.

HP Compaq dx 2250 with AMD 64 Athlon 3800+
Platform 86_64
120 gb hdd SATA 0
ATI Graphics Card
Memory 874 MB

if you ever wanna take another leap of faith, you can use your Windows partition while booted and running in Linux.  The program is called Virtualbox; you can "virtually" boot up and run another partition while in Linux. It could help reduce the time of always booting to Windows.
[http://ubuntuforums.org/showthread.php?t=943103](http://ubuntuforums.org/showthread.php?t=943103)

Some programs might work in Linux(the program's called Wine); you could check Wine's program database to see if your programs are compatible.  
[http://www.winehq.org/](http://www.winehq.org/)

Good to see you moved up to Intrepid, hope all works well for you. :)

---

### Post by Gael33 on 2008-10-15
> **run1206 said:**
> if you ever wanna take another leap of faith, you can use your Windows partition while booted and running in Linux.  The program is called Virtualbox; you can "virtually" boot up and run another partition while in Linux. It could help reduce the time of always booting to Windows.
[http://ubuntuforums.org/showthread.php?t=943103](http://ubuntuforums.org/showthread.php?t=943103)

Some programs might work in Linux(the program's called Wine); you could check Wine's program database to see if your programs are compatible.  
[http://www.winehq.org/](http://www.winehq.org/)

Good to see you moved up to Intrepid, hope all works well for you. :)

Thanks for such a helpful reply :KS
I'll check out Virtualbox as soon as I have some spare time ... it sounds very interesting.
I've already got Wine and some of my stuff does work very well through it, there are others that are totally incompatible i.e. MediaFace 4 labeling program ... there is nothing like it within the Linux packages.
Anyway, thanks again, your advice is most appreciated.

gael.

---

### Post by tech0007 on 2008-10-15
Just installed II using the alternate CD on another partition.  I have XP and HH on same PC.  Hardy's my main OS. My initial impression is II seems to be stable enough although I did not really have the time to play around with it yet.  But it looks promising though. I know this is not the right thread to ask but I just want to know if it's better to upgrade to II than stay with HH.  HH is LTS and seems rock-stable for me. Kudos to the developers and keep up the good work!

---

### Post by BoredOutOfMyMind on 2008-10-15
> **BoredOutOfMyMind said:**
> Is there an Ethernet fix available.  upgrade last night left me with no network and no GDM.

Second request 

Any news of a fix for the borked ethernet?

---

### Post by Sef on 2008-10-15
>  HH is LTS and seems rock-stable for me.

If it is rock-stable for you and you want that in your operating system, then stick with Hardy.  There is nothing wrong sticking with an operating system that has support.

---

### Post by Sef on 2008-10-15
>  	Quote:
 	 	 		 			 				 					Originally Posted by **BoredOutOfMyMind** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5965247#post5965247") 				
 				*Is there an Ethernet fix available.  upgrade last night left me with no network and no GDM.*
 			 		 	 	 
Second request 

Any news of a fix for the borked ethernet? 	

What are your system specs?

---

### Post by andrewabc on 2008-10-16
> **BoredOutOfMyMind said:**
> Second request 

Any news of a fix for the borked ethernet?

Do you have the same problem with me when I tried the beta?

[http://ubuntuforums.org/showthread.php?t=937836](http://ubuntuforums.org/showthread.php?t=937836)

There is no network option in menu, and no way to edit or try to fix the network. I'm connected to an ethernet, so it should work fine because it did in last alpha.

I'm waiting until release candidate, unless a fix was released, then I might try daily live cd iso

---

### Post by WallaceS on 2008-10-16
I have just upgraded my (really old) Dell Latitude C610. 

The only problem I have encountered so far is that some windows fail to open, in particular windows related to 'sudo' authorisations e.g. synaptic won't start and 'terminal' just gives an empty box. The Update manager locked the X display completely - had to use ctrl-alt-f1 and kill it from there to recover.

I've managed to fix this, more by luck than judgment, by changing the Visual Effects setting from 'normal' to 'none' in the 'Appearance Preferences' window. I was actually trying to sort out why I had no 'minimise', 'maximise' or 'close' buttons on windows!

Does anyone know if this is a known issue?

---

### Post by Sef on 2008-10-16
> I've managed to fix this, more by luck than judgment, by changing the Visual Effects setting from 'normal' to 'none' in the 'Appearance Preferences' window. I was actually trying to sort out why I had no 'minimise', 'maximise' or 'close' buttons on windows!

Does anyone know if this is a known issue?

I have not seen that one on here before.  If it is an issue then it probably is not a big one.

---

### Post by Gael33 on 2008-10-17
I upgraded the beta version several days ago and it appeared fine at the time with no obvious problems. The program then informed me of downloads and following the instructions 'downloads are like fixes' I duly followed the instructions and continued the downloads ... it downloaded lots of upgrades, and it also removed presumably unwanted packages as well. That was the beginning of the troubles. When I did a recommended reboot the whole process locked up. Now I admit my Linux knowledge base is almost zilch, but with what little know how I have I tried to get it going to no avail. As with most things in life, messing about with a seemingly lost cause is time consuming so I wiped Intrepid clean off my system and returned to reliable Hardy ... I won't reinstall Intrepid until all the bugs are fixed, but I probably will eventually. Ubuntu is a good OS but like all things technical it takes a while to 'get it right'.

gael. :confused:

---

### Post by giruzz on 2008-10-17
> **crazypenguin2008 said:**
> i did the hardy to intrepid upgrade on a spare hdd i had and everything went great untill the last update(yesterday 10/7/2008)
i lost wireless and the ability to create a wireless network.

Similar issue here. WiFi is working, I can see the networks around but when it should connect to mine it says 'wrong password' and it does not connect.

The solution I have found is to connect via Eth0 and then try again a couple of time....only doing this works. I am totally unable to connect to my WiFi if I don't connect to eth0 first.

giruzz

---

### Post by TerpInHotLanta on 2008-10-17
> **WallaceS said:**
> 
I've managed to fix this, more by luck than judgment, by changing the Visual Effects setting from 'normal' to 'none' in the 'Appearance Preferences' window. I was actually trying to sort out why I had no 'minimise', 'maximise' or 'close' buttons on windows!

Does anyone know if this is a known issue?

Try going to the Advanced Desktop Effects Settings and un-check Window Decorations-- you may then need to restart Gnome to see the changes. Do you happen to have Emerald installed?

Hope this helps!
C

---

### Post by caro on 2008-10-22
I'm trying to update from 8.04 to 8.10 using sudo update-manager -d. The update manager started but stopped with the error message that I need to free up space in /boot.

Before I do something I can't recover from, what files in /boot are safe to delete? Here is the output of ls /boot

abi-2.6.20-16-generic initrd.img-2.6.24-18-generic
abi-2.6.22-14-generic initrd.img-2.6.24-18-generic.bak
abi-2.6.24-16-generic initrd.img-2.6.24-19-generic
abi-2.6.24-17-generic initrd.img-2.6.24-19-generic.bak
abi-2.6.24-18-generic initrd.img-2.6.24-21-generic
abi-2.6.24-19-generic initrd.img-2.6.24-21-generic.bak
abi-2.6.24-21-generic lost+found
config-2.6.20-16-generic memtest86+.bin
config-2.6.22-14-generic System.map-2.6.20-16-generic
config-2.6.24-16-generic System.map-2.6.22-14-generic
config-2.6.24-17-generic System.map-2.6.24-16-generic
config-2.6.24-18-generic System.map-2.6.24-17-generic
config-2.6.24-19-generic System.map-2.6.24-18-generic
config-2.6.24-21-generic System.map-2.6.24-19-generic
grub System.map-2.6.24-21-generic
initrd.img-2.6.20-16-generic vmlinuz-2.6.20-16-generic
initrd.img-2.6.20-16-generic.bak vmlinuz-2.6.22-14-generic
initrd.img-2.6.22-14-generic vmlinuz-2.6.24-16-generic
initrd.img-2.6.22-14-generic.bak vmlinuz-2.6.24-17-generic
initrd.img-2.6.24-16-generic vmlinuz-2.6.24-18-generic
initrd.img-2.6.24-16-generic.bak vmlinuz-2.6.24-19-generic
initrd.img-2.6.24-17-generic vmlinuz-2.6.24-21-generic
initrd.img-2.6.24-17-generic.bak


Any help would be appreciated. Looking forward to try Intrepid.

---

### Post by jdong on 2008-10-22
None of the files are safe to manually remove by hand.

Open up Synaptic and perform a search for "linux-image-2.6" through Installed packages, remove all of the "linux-image-2.6.22-*-generic" and "linux-image-2.6.24-*-generic" packages (don't remove linux-image-generic or linux-generic, that is, ones without numbers in the package name) **EXCEPT** for the current kernel version you are running (i.e. the newest one)

---

### Post by Roasted on 2008-10-23
I didn't do an upgrade, but I tried to do a fresh install overtop of Hardy. But I got hit with a kernel panic. Sweet! Love it!

I'm reading that my ASUS mobo didn't come with 64 bit drivers for OS's.

Funny thing is - Hardy 64 bit installed without a problem. :lolflag::lolflag::lolflag::lolflag::lolflag: Shoot me. Please.

---

### Post by jbg7474 on 2008-10-23
I upgraded from hardy last night--no major issues.  However, the nvidia driver did not work after initial reboot.  Had to start in low-graphics mode, then there was some automatic configuration that got me decent screen resolution (but no 3d graphics or compiz).  Tried to run nvidia-settings, and nvidia informed me that the driver was not being used.  Okay, run nvidia-config, restart X, all is well.  Also had to replace a few minor customizations to my xorg.conf.  But again, that's not too hard.

One wishes slightly that an upgrade process would configure xorg.conf to use the new restricted video driver automatically, especially since the new restricted driver was in fact installed as part of the upgrade.

On a positive note, the horizontal scroll on my mouse now works!  No amount of effort could make that work in hardy.  Wireless works without a restricted driver too.

I also noticed that the release notes claimed this was a release candidate, not a beta.  Excellent!

---

### Post by endesign on 2008-10-23
Upgraded last night having enjoyed the three weeks as a noob I spent with Hardy. Went well, its a pretty subtle upgrade with the new features being sensible improvements. There are the odd crashes of some progs now and again but largely only ever at the point I close them for some reason.

Only filed one bug report with launchpad which is that my MS mouse likes to do some jerky dancing now and again but not so bad that I worry.

Best thing so far is that my Huwaei K3520 (aka E169) USB mobile dongle works a dream with Intrepid and even spots the fact that I have 4gb of micro SD storage in it as a separate USB device - even XP on my work laptop sometimes gives me trouble with that. Vodafone's RnD dept Betavine are working on mobile drivers for that device for linux, but it seems that the notebook mobile surfers just need to get Intrepid installed on their eepcs!

So nice one Ubuntu. Now my dual boot in to Vista only ever happens for Flight Sim X... Vista the one game console! BTW, how lame is aero compared with the genuinely useful compiz - that was a major eye opener.

---

### Post by VCSkier on 2008-10-23
I use Google's "Picasa for linux" to manage and organize my pictures which are scattered across a couple drives and operating systems.  It was installed through Google's apt repository ([http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)).  I want to do the upgrade process from 8.04.1 to 8.10 (when it is released), but I'd need to know if Picasa is likely to interfere with the upgrade.

I know that third party software can sometimes cause problems with the upgrade process, but Picasa is the only third party software I have installed, with the exception of some firefox extensions.  I really don't want to uninstall Picasa, that's actually why I don't want to do a clean install.  Has anyone had any experience with this?  Can I perform an upgrade (through upgrade manager) from 8.04.1 to 8.10 (when released) while Picasa is installed, and expect no problems to surface?

Thanks in advance.

---

### Post by propwashz on 2008-10-23
You should be able to upgrade to II from HH with no problems as far as picasa is concerned--I did. After II was installed,I upgraded picasa to the new Picasa3 from Google's linux repositories with no problems too. BUT--you might want to try the Intrepid LiveCD before you do the upgrade just to make sure your computer doesn't have any other issues with Intrepid. If everything does ok with the live cd,boot back into Hardy,and do the upgrade.Good luck.

---

### Post by caro on 2008-10-23
I upgraded from Hardy last night and with just a little time on Intrepid I don't have much to report.  Everything worked fine.  It seems that apps run a little faster but that may just be wishful thinking.

The only thing I have found is that I my touchpad went back to default settings and I can't change them.  When I go to System > Preferences > Touchpad, I get an error message (xorg.conf and HAL so not unexpected).  So, until there is a fix for that, I can't turn off tapping on my touchpad (and I really want to!)

---

### Post by Micronaut on 2008-10-24
During the disk partition stage of 8.10 install, is there a way to remove an existing Ubuntu installation partition and make a new one for a fresh install?  I'm dual booting with xp and the disk manager in the 8.10 installation wont let me delete my existing installation and I can only use the entire disk or resize the disk for a new install.

I would like to format the existing Ubuntu partition and use it for the fresh install.

Thanks for any assistance.

---

### Post by andrewabc on 2008-10-24
> **Micronaut said:**
> During the disk partition stage of 8.10 install, is there a way to remove an existing Ubuntu installation partition and make a new one for a fresh install?  I'm dual booting with xp and the disk manager in the 8.10 installation wont let me delete my existing installation and I can only use the entire disk or resize the disk for a new install.

I would like to format the existing Ubuntu partition and use it for the fresh install.

Thanks for any assistance.

You went into manual partition instead of guided correct?
In manual partition you can format your current partition and then mount it as "/" and it should work.

---

### Post by Micronaut on 2008-10-24
> **andrewabc said:**
> You went into manual partition instead of guided correct?
In manual partition you can format your current partition and then mount it as "/" and it should work.

Apologies.  My laptop was slow and the menu skipped forward twice and I missed the manual setup options. I found the page and successfully formatted and reinstalled Ubuntu.  

Very nice so far :)

Thanks for the reply.

---

### Post by torgo on 2008-10-24
I upgraded to the Intrepid Ibex RC candidate last night. When I rebooted, everything worked EXCEPT I lost all my desktop icons. My gnome menu and launcher works, all the windows have their proper decorations but there are no icons on the desktop.

Also, right-clicking on the desktop no longer activates any sort of menu. Any ideas how to fix that?

---

### Post by torgo on 2008-10-25
> **torgo said:**
> I upgraded to the Intrepid Ibex RC candidate last night. When I rebooted, everything worked EXCEPT I lost all my desktop icons. My gnome menu and launcher works, all the windows have their proper decorations but there are no icons on the desktop.

Also, right-clicking on the desktop no longer activates any sort of menu. Any ideas how to fix that?

It was only a nautilus problem! Someone on another thread in a previous upgrade situation had the problem, and with the right keywords I finally found the solution.

This forum rocks. Thanks!

---

### Post by Borlag on 2008-10-25
The actual installing went very smoothly for me. Couple of settings had reseted during the update, but that's about all there was.

Having tested this for a day now, I've encountered 3 problems so far, 2 of which could very well be related. First one is the eject issue with the tray closing immediately after ejecting, no big deal here, just minor annoyance. The main issue, which is the real killer for me, was that when opening Firefox (7 tabs opening by default), the whole system stalls for 20-50 seconds before resuming properly. Same thing happens when opening new tabs, or switching to tabs that haven't been read in a while and refreshing the page and/or clicking a link from there. Amarok freezes also with Firefox and as such the audio starts skipping or disappearing entirely for the duration of the freeze up.

Apart from that, was wondering why software like Azureus and Pidgin had to be removed with the update, but it's not like adding them back is that hard to begin with. Oh, and the new card style for Freecell and Aisleriot is just ugly (my lady wanted that added).

System used for testing:
AMD 64 3500+ with 2GB RAM running 64bit Ubuntu. Audigy 2 sound card (no issues), GeForce 6600 GT (no issues after installing the 177 drivers)

edit: oh and the webpages for a finnish bank Sampopankki crash the browser immediately if trying to go to the log in page ([http://www.sampopankki.fi](http://www.sampopankki.fi) for the main page, [https://verkkopankki.sampopankki.fi/html/index.html?site=SBNBFI&secsystem=E2](https://verkkopankki.sampopankki.fi/html/index.html?site=SBNBFI&secsystem=E2) for the page that crashes it. I believe this is a java related issue)

---

### Post by Unicast on 2008-10-25
> **Borlag said:**
> edit: oh and the webpages for a finnish bank Sampopankki crash the browser immediately if trying to go to the log in page ([http://www.sampopankki.fi](http://www.sampopankki.fi) for the main page, [https://verkkopankki.sampopankki.fi/html/index.html?site=SBNBFI&secsystem=E2](https://verkkopankki.sampopankki.fi/html/index.html?site=SBNBFI&secsystem=E2) for the page that crashes it. I believe this is a java related issue)

Are you sure that's not your bank crashing and not your browser? ;)

---

### Post by Borlag on 2008-10-25
> **Unicast said:**
> Are you sure that's not your bank crashing and not your browser? ;)

When it comes to that bank, anything's possible. Disabling flash entirely fixed the browser stalling, as well as that page crashing.

---

### Post by isido on 2008-10-25
I upgraded from hardy an hour ago, and had some issues:

1. My "Places" menu doesn't work anymore; if I try to open for instance "Home", I get following error dialog:

"Could not open location 'file:///home/isido'
Failed to execute child process "wxvlc" (No such file or directory)"

Nautilus, however, works when invoked from command line.

2. Sound is gone. Rhythmbox also helpfully offers to find suitable codecs, which should already be installed.

3. Also, the fonts in firefox have changed again (this seems to happen with every upgrade), the fonts seem now somewhat smaller.

Otherwise, things seem to work. Has anyone had similar issues? I haven't looked at launchpad bug reports yet, but I'll do it now.

---

### Post by isido on 2008-10-25
Ok, the solutions to problems were actually quite simple.

1. Places menu not working correctly: vlc somehow hijacked "opening folders" task for itself. I simply changed "Open with" property for folder in nautilus.

2. Sound actually works, but volume level just changed.

All in all, hardy->intrepid seems to be one of the better upgrades.

---

### Post by jaret100 on 2008-10-25
I stayed up to the wee hrs of the morn upgrading.

Previously, when upgrading images, i did the 3-way combination (experimental). that is to say, i had entries for both the 2.6.24-19 and 2.6.24-21 images. I also had to edit the menu.lst file to add 'acpi=off'.

I assume II did not like this modification as i chose to do another 3-way combination merge into the menu.lst. I got error messages after the install saying that that .27 was not installed correctly. However, I believe it did install the image but the entry in the menu.lst was not correct.

To solve this, i booted the .21 image and modified menu.lst. the .27 entry was missing this line.
"initrd		/boot/initrd.img-2.6.27-7-generic"
so i added it and rebooted, selecting new  image and it worked! to make sure i did uname -a  in termainal and it had the .27 image.

Additionally, I still do not have wireless or sound. (but what i do have looks GREAT! yay for Ubuntu). I have a hp pavilion tx 2525. looking through the forums, these models are known for having these two issues. ( i was hoping II would solve them. o well. i guess i can just wait for more updates.)

---

### Post by GordonTGopher on 2008-10-26
After upgrading from Hardy to the RC my machine will not boot, gives an error of 
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/69f3e(long UUID string!)

If I use the GRUB menu to boot the 2.6.24.21 kernel it boots OK

According to this thread [http://ubuntuforums.org/showthread.php?t=956737](http://ubuntuforums.org/showthread.php?t=956737) I'm not alone with having this problem.

I'm a bit of a newb, so I've not done much investigation, I'm happy to do what I can to get the information I need to file a useful bug report. 

Gordon

---

### Post by grappler on 2008-10-26
Three weeks ago I reported on this thread an attempt to install intrepid amd64 beta  on my lenovo t61p. Neither the wireless nor the ethernet drivers  worked at that time - there were known bugs for each -  and I had to reinstall hardy. I've just tried the intrepid amd64 RC live CD and both problems appear to have been fixed. 

In fact the  network manager can now switch automatically between wired and wireless as appropriate - I might consider switching to network manager instead of wicd.   

In any case,  I'll try the upgrade now!

---

### Post by SilverWave on 2008-10-26
I did a clean install of Ibex 8.10 (+kept old home partition).
On Install I chose "Manual" so I could set all mount points myself.

In preparation I took a screen-shot of System Monitor's File System Tab and saved it to my gmail account. Once booted up on the 8.10 LiveCD I logged in to gmail and used this screen-shot to set the Mount point options.

Backed up just in case but no problems with Ibex so far.

I have had an odd problem with my old FF3 profile but I can not be certain of its cause. The Firefox problem is that the alterations that I have made to the toolbars are lost. I have tried various older profiles to no avail.

I have experienced similar problems with a newly created profile but I have a workaround.

The problem:
Changes to the toolbars (extra buttons & moving the searchbox, adding extensions etc.) and rebooting ff results in your changes being lost.

The Workaround:
1. Reboot firefox again (and again) most of the time this restores the toolbars correctly.
2. As you add extensions or change the toolbar layout keep taking copies of your profile.
If 1# does not work go back to your last good copy.
Lather, rinse, repeat :(

Still working out the underlying cause but it will do for now (probably localstore.rdf corruption of some kind).

I have managed to install all of my extensions (and keep the toolbar changes) except NoScript.

---

### Post by fjf on 2008-10-26
Maybe a dumb question, but will this upgrade method (update-manager -d) work to go from ubuntustudio 8.04.01 to 8.10?.

---

### Post by panda726 on 2008-10-26
I'm still working on getting my Intrepid install working (test install on separate partion), but I think the problem is that the copy of grub in my grub partition is old and can't read my Intrepid partition properly.  Should be easy once I update grub from the live disc.

[quote=Isido]1. Places menu not working correctly: vlc somehow hijacked "opening folders" task for itself. I simply changed "Open with" property for folder in nautilus.
[/quote]

It looks like this may be a bug of significance, as I saw another report from someone with a similar problem, except that for him, it was Gparted that had hijacked folders in Nautilus.  This of course caused strange error messages about root permissions being required.  I cannot track down and file a bug report as I use KDE

Tor

---

### Post by NilsE on 2008-10-27
Upgraded from my primary Hardy system to the RC via the "update-manager -d" and it went extremely well.  Had to do a few minor tweaks like associate my wireless router and bluetooth mouse but that is expected. Everything else was carried over even my appearance settings.

I did notice one weird thing which may be related to a carry over setting that I can't find. On a fresh install on another drive it works fine.

When I open Nautilus, graphics are previewed as expected but if I open Nautilus as root (gksudo nautilus) I get no image previews for jpg, png, etc.. I checked and thumbnail preview is set on.

I am still tinkering but was curious if anyone else noticed this.

---

### Post by Knatchwa on 2008-10-29
I was able to complete the upgrade but as I started working with it I started wondering if it was better to Use Ubuntu Server x64 while apparently I am running i686 according to the error message I received from Ubuntu when I was making an attempt to install it within virtual box. 

My question is, how is it that the x64 desktop version I am using now is having no problems and I did not see that message in the initial install while with the server version of 8.10 that error came up. Am I missing something? I tried to research it but could not find the correct keywords. Is there a way to make this work on an AMD64 3200 with 2gig of Ram and Ati Radeon x1300? It's an Athlon to be more specific. So what is the story here? 

I truly appreciate your help in this matter and as a noob to Ubuntu thus far I have been able to work with it relatively well.

---

### Post by jdong on 2008-10-29
Unless you have more than 3GB system RAM (many Intel chipsets) or more than 4GB RAM that you'd like a single application to use (all others), there's arguable advantage to using 64-bit Linux.

This is a hotly debated topic and there's no clear answer, and I'd rather not cloud this thread with a rekindled 32-bit vs 64-bit war :)


Bottom line is I wouldn't spend any time stressing it -- if not all your system RAM is showing up in "free -m", use a 64-bit Ubuntu. Otherwise, don't waste your personal time and effort chasing after 64-bitness :)

---

### Post by meindian523 on 2008-10-30
And why not ```
sudo apt-get dist-upgrade
```May I ask?

---

### Post by jdong on 2008-10-30
> **meindian523 said:**
> And why not ```
sudo apt-get dist-upgrade
```May I ask?


This is entirely unsupported -- Ubuntu's upgrade process requires some quirks to be set to pull back in all the metapackages, install the recommended set of packages (including new packages as a part of Intrepid), marking installation order correctly where it matters, and removing obsolete or problematic packages.

The use of any other upgrade method including "dist-upgrade" is unsupported and is known to result in some issues. If you are an experienced Debian administrator the difficulties that come up should be relatively fixable, but otherwise please don't try this.

---

### Post by Sef on 2008-10-30
> This is entirely unsupported -- Ubuntu's upgrade process requires some quirks to be set to pull back in all the metapackages, install the recommended set of packages (including new packages as a part of Intrepid), marking installation order correctly where it matters, and removing obsolete or problematic packages.

The use of any other upgrade method including "dist-upgrade" is unsupported and is known to result in some issues. If you are an experienced Debian administrator the difficulties that come up should be relatively fixable, but otherwise please don't try this

Thank you for explaining why it should not be used.

---

### Post by meindian523 on 2008-10-30
In short,anything through Synaptic and Update Manager is Ok,while commandline is not and may result in difficullties?Is that one of the reasons people are advised to clean install and not upgrade to a release?And I believe there are issues with the update manager route too?
Or am I mistaken and is upgrading as safe as a clean install?

---

### Post by jdong on 2008-10-30
> **meindian523 said:**
> In short,anything through Synaptic and Update Manager is Ok,while commandline is not and may result in difficullties?

No, there is a command-line interface to the official upgrade method, and this is documented in the Ubuntu release notes on upgrading. This seems to be a common myth that you need a GUI to use the Ubuntu upgrade tools.


> 
Is that one of the reasons people are advised to clean install and not upgrade to a release?And I believe there are issues with the update manager route too?
Or am I mistaken and is upgrading as safe as a clean install?

Actually, **We do NOT advise a clean install** every time you want to upgrade. The upgrade path receives far more testing and attention than the clean install path. The official recommended method for moving to a new version of Ubuntu is to use a supported upgrade procedure!

---

### Post by meindian523 on 2008-10-30
> **jdong said:**
> No, there is a command-line interface to the official upgrade method, and this is documented in the Ubuntu release notes on upgrading. This seems to be a common myth that you need a GUI to use the Ubuntu upgrade tools.
Actually,that's the impression I got from the first post and the replies to my question.I'm not aware of the general impression/myth.

> **jdong said:**
> 
Actually, **We do NOT advise a clean install** every time you want to upgrade. The upgrade path receives far more testing and attention than the clean install path. The official recommended method for moving to a new version of Ubuntu is to use a supported upgrade procedure!
Lol,and here I'm(I'm not sure of anyone else now,last time I asked,the recommended method was a clean install)recommending everyone to clean install because of apparent bugs in dist-upgrade.Thanks for the clarification.

---

### Post by jdong on 2008-10-30
Yeah, a couple core developers yesterday were really irate about users saying "CLEAN INSTALL" unconditionally and wanted to make it clear that upgrading is the recommended way to get to Intrepid.

See [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) for all supported upgrade methods, in case you haven't noticed that page yet :)

---

### Post by sagesparrow on 2008-10-30
Would this advice about upgrading rather than a fresh install apply if upgrading from 7.10?

---

### Post by jdong on 2008-10-30
> **sagesparrow said:**
> Would this advice about upgrading rather than a fresh install apply if upgrading from 7.10?

We'd recommend upgrading from 7.10 to 8.04, then to 8.10. We only support upgrades one release at a time (or LTS -> LTS)

---

### Post by tompickles on 2008-10-30
Good job guys! I upgraded - the first time I've done an incremental upgrade, and Ubuntu is the only distro I'd dare do it on anyway - openSUSE SUCKED at upgradeing :D.

But, wow! Loving the dark theme. Woop woop!

---

### Post by meindian523 on 2008-10-30
> **jdong said:**
> Yeah, a couple core developers yesterday were really irate about users saying "CLEAN INSTALL" unconditionally and wanted to make it clear that upgrading is the recommended way to get to Intrepid.

See [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) for all supported upgrade methods, in case you haven't noticed that page yet :)

So,it's a recent development.So,I can clear my conscience of all self-guilt,I presume.:) I had seen that page,but couldn't find it again.Thanks again for the URL.

---

### Post by tompickles on 2008-10-30
Good job guys! I upgraded - the first time I've done an incremental upgrade, and Ubuntu is the only distro I'd dare do it on anyway - openSUSE SUCKED at upgradeing :D.

But, wow! Loving the dark theme. Woop woop!

Edit: Sorry, this posted twice?!

---

### Post by jdong on 2008-10-30
> **meindian523 said:**
> So,it's a recent development.So,I can clear my conscience of all self-guilt,I presume.:) I had seen that page,but couldn't find it again.Thanks again for the URL.

IIRC the network upgrade was added for Dapper server and beyond. Before then, command-line upgrades were much more difficult.

---

### Post by meindian523 on 2008-10-30
I started with Feisty,so I wouldn't have much idea about that.:)

---

