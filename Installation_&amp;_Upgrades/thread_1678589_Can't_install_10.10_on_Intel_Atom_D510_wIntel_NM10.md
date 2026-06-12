---
title: "Can't install 10.10 on Intel Atom D510 w/Intel NM10 Chipset"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by JohnnyPuffs on 2011-01-30
Hi All,

First post to the forum. Having major problems installing 10.10 Desktop x64..

Started using Ubuntu about a month ago and am loving it. My office consists mostly of Macs with a couple Windows boxes and a CentOS box running Asterisk.

I've managed to install 10.10 Desktop on an AMD Athlon II x 2 without any issues at all.

 I also installed on an Asus netbook (Atom N260 w Intel integrated GMA 950). Again no issues whatsoever.

Both these boxes were running Windows 7 previously.

I'm now trying to install 10.10 on our last remaining Windows machine with no luck.

It's an MSI Wind Box I built. It's got the Intel Atom D510 proc. w Integrated Intel GMA 3150 graphics core. 4GB RAM. Have tried to install from both External CD Drive as well as USB Stick. No luck with either.

Originally  got the blank/black screen.

Have searched and read the threads I've found and tried some of the different solutions:

F6 then change the line to add to the boot line:

nomodeset

Then nomodeset + each of the following

acpi_osi=
acpi_osi=\"Linux"\
acpi_osi="Linux"

Those all got me past the blank screen, but hung fairly quickly into the install.

Sometimes hanging after last line or two (don't remember exactly) saying 

"agpgart-intel 0000:00:00.0: detected 16380K stolen memory"

then hanging at:

"hpet:0 3 comparators, 64-bit 14.318.180 MHz counter"

From the posts I've read a lot stems from Nvidia drivers.. Which is strange because the AMD machine does have Nvdia drivers, while the Atom D510 does not..

Also it installed no issues on the Atom N260 w Intel GMA 950. But the D510 w Intel GMA 3150 is giving me problems. I would have thought the other way around if anything.

Any suggestions? It would be most appreciated!

I'm downloading the "alternate" .ISOs right now.. and I guess will give them a shot.

Thanks in advance for any help!

Best,
JP

---

### Post by stompy11 on 2011-01-30
Thats what i did and the alternate worked for me, its not the prettiest installer but got the job done. good luck and keep us posted.

---

### Post by davidmohammed on 2011-01-30
try

nomodeset and one of the 'common boot options' from [here]("https://help.ubuntu.com/community/BootOptions").

---

### Post by JohnnyPuffs on 2011-01-30
UPDATE:

Tried installing WUBI..

Seemed to install, but when booting into Ubuntu is hanging (which I expected)

Tried Safe Graphics mode and got:

[   7.069184] agpgart-intel 0000:00:00.0: detected 16380K stolen memory

Then tried ACPI workarounds and got:

[   7.691453] agpgart-intel 0000:00:00.0: detected 16380K stolen memory

FInally tried to install the alternative .ISO.. Seemed to get way further through the process, but at one point  it seems like it just stopped recognizing my monitor, as the power light was blinking as though no PC was plugged in.. I let it hang that way for awhile in case it was still installing. Shut down and reboot got me back to the WUBI boot screen, so apparently the install was unsuccessful.

Now I'm really lost! :confused:

Thanks again,
JP

---

### Post by stompy11 on 2011-01-30
during the alternet install how far did you get?


in my experience wubi failed when the live cd failed, but the alternet worked great. also check disk for errors or try usb.

---

### Post by JohnnyPuffs on 2011-01-30
> **davidmohammed said:**
> try

nomodeset and one of the 'common boot options' from [here]("https://help.ubuntu.com/community/BootOptions").

Will try some of these.. thanks..

---

### Post by JohnnyPuffs on 2011-01-31
OK, So I'm about to give up hope here..

I read and tried just about every combo of everything from suggestions from you guys, from [this thread]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/") and [this thread]("http://ubuntuforums.org/showthread.php?t=1613132").

NOTHING has worked..

At this point I've gone so far as to format the drive to start from a blank state. I've tried both 64bit and 32bit booting from both CD Drive as well as USB stick. Also tried the "alternate" install.

The furthest I have seemed to get was with the alternate install, it went though "loading additional components", got to "Detecting Network Hardware" which just sticks at 0% "Detecting Hardware, please wait..."

I gotta say I'm really bummed about this. Apparently it's an issue for a lot of people and was so well before 10 came along.. You'd think there would be a good universal fix by now..

Any last suggestions before I give up and install another flavor??

Thanks again,
JP

---

### Post by davidmohammed on 2011-01-31
ok - I found some threads on your chipset - it is possible that both lucid and maverick kernels do not support the intel chipset that your motherboard has.  However it is likely that Natty does.

Give the [natty daily build]("http://cdimage.ubuntu.com/daily-live/current/") a spin - if it works then you know its a kernel issue - its unlikely other distros will work unless they have a newer kernel than maverick.

---

### Post by JohnnyPuffs on 2011-01-31
Thanks davidmohammed..

Downloading as we speak and will update shortly..

I've got a bit of brain drain at the moment, but I swear there were some threads I cam across with people successfully running 10.4 and 10.10 with my chipset..

Be back shortly.

---

### Post by JohnnyPuffs on 2011-02-01
OK, so here is the latest...

I ran the natty daily x64.. first time it seemed to be running fine, then hung when downloading/installing language pack (don't remember exactly what it said) and threw this error:


"An error occurred when installing packages
E-sub process /usr/bin/dpkg returned an derror code (1)

The following packages are in a broken state:

console-setup

This may be due to using an ld installer packages or it may be due to a bugging sowme of the packages listed above. The installer will try to continue anyway&#8230;.."


Then after I clicked "OK" to continue anyway it immediately gave me a new message box:

"Installer Crashed.. We're sorry.. reports this bug, etc,..."

Could not close that message box. Had to force power off.

I had downloaded the torrent the first time because of the painfully slow http download.. so I went back and did the http download from the link you gave above.

Ran the installer again with the same results. Except this time it did let me close the "Installer Crashed..." box and went into desktop mode.. Some things are working but it seems like some are not. Hard to tell as the layout is different from 10.10. So I clicked "Update Manager" and it gave me a message about a partial update due to issue before. It is currently downloading 886 files.. We'll see what happens.

FYI - Both time I clicked "Install Ubuntu" not "Try from Ubuntu without an change to your computer". I also clicked the checkbox to download and apply updates during install.

I did notice on the link you sent me the file says "Last modified 31-Jan-2011" yet when I do a "get info" on my Mac it says created/last modified December 1, 2010.

So updates finished and everything was screwy. I went ahead, re-downladed another ISO and tried again. This time it installed, with some weird issues..

Currently it is showing I have dual monitors, one beinge LAPTOP, the other being my correct monitor.. Only in mirrored mode does it work and I can only set the res to 1024 x 768, using a wide screen 24 inch LCD. If I turn off LAPTOP I can set my monitor to 1920 x 1080, but it only shows the top right corner of the desktop down in the bottom left corner of the monitor. Pretty sure with my other installs I originally could not get past 1024 x 768 and I needed to download a driver.. But, no strange mirroring problem. 

So the system seems to be working just OK.. I get thrown errors here and there so not stable at all, but it's a beta..

**Is there a way for me to do an install of 10.4 or 10.10 with a newer kernel? Or maybe /downgrade or install 10.4 or 10.10 on top of this.. or as a separate system. Then use the modules I need to get it working. I know you can update to new kernels, but I can't complete an install so that's not an option. It would have to be from the initial install..**

Thanks again for the help. Very much appreciated!

Best,
JP

---

### Post by davidmohammed on 2011-02-01
actually what you have described is in a weird way good news - it shows that either/both a newer kernel with the newer X-stack is compatible with your motherboard/chipset.

Natty is in alpha - so still very early in its development - will be released sometime in April.

I'm not sure about trying to install maverick/lucid with a newer kernel and/or X stack.

Maybe a combination of the [mainline kernels]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds") and the [X-edgers]("https://launchpad.net/~xorg-edgers") ppa will help.

_Maybe someone here can chip in a help at this point._

The only other suggestion I have is maybe the latest fedora release - a little more cutting edge than maverick - but I cant comment on the stability.

---

### Post by davidmohammed on 2011-02-01
ok - having googled, it seems the following is one good possibility to install a newer kernel/x-stack.

remove the D510 computer hard-drive and install it into one of your other computers you know that can install maverick.

Install maverick.  

Download the 3 kernel deb files from that mainline kernel web-page corresponding to the latest maverick (2.6.370rc2) and install.  Reboot and make sure it looks like its running ok.

Then add the edgers ppa and update.  

You should now be working with a "bleeding" edge version of maverick.  Remove the hard-drive and put it back into the D510.  power up.  Hopefully that will fix stuff.

---

### Post by JohnnyPuffs on 2011-02-01
Hey David,

Thanks again for the help! It is truly appreciated!!

I thought about popping the drive in another PC but wasn't sure if it would be a waste of time.. I'm going to try that out this afternoon when I get some time. Fedora is an option, but I've gotten to like Ubuntu and if I am actually going to be using a few PCs with Linux Desktops they all have to be the same. Some of my employees are already hesitant to use something other than Mac/PC, so throwing 2 distros at them would not make me popular.. ;)

I'll post my outcome once I get to it.. I'm having high hopes!!

Thanks again.. have a great day.

---

### Post by JohnnyPuffs on 2011-02-03
Hey David,

Finally got around to switching drives out and trying this.. It worked!! Thanks for the help.. Very much appreciated!

Ran into some difficulties along the way and still having a few minor issues, but it is installed and running well for the most part.

I have been wanting to try out KDE so I ended up installing Kubuntu 10.10.. Initial install went fine. Downloaded and installed the three 2.6.370rc2 mainline kernel file. Rebooted and all was still looking fine. 

Adding the edgers ppa and updating gave me a problem.. After updating I rebooted and when the desktop cam up it was a completely garbled mess. You could tell the desktop was behind it but there was no way to see anything. Booted the live CD and took a look around the files on the hard drive. Then re-read the documentation for edgers ppa.. Seems the Nvidia proprietary driver needs to be removed before installing..

Reinstalled the whole she-bang all over again, deleted the Nvidia driver, added edgers ppa and updated. Rebooted and same problem. Screen just a mess. Spent a bunch of time  messing around with it and looking for solutions, then thought about it and realized the D510 doesn't use Nvidia so it might be fine as is.. Plopped the drive back in the D510 and everything was fine!

The two problems I'm having now are that it sets the display to 1024x768 automatically. I can go in and re-set the display to 1920x1080 and everything looks solid. I save that as default, but every reboot puts it back to 1024x768.. Not the worst thing in the world as I won't reboot all the time.. but fairly annoying. I'll do some digging about  the issue.

I'll also be connecting to the machine mostly remotely from another computer in the office. I installed Desktop sharing and the first time I connected it was fine. Got a solid 1920x1080, which is perfect as the screen on the connecting computer is 1920x1200.. But now every time I have re-connected I get a 1024x768 remote desktop.. That one is a hassle as I really wanted to run the machine headless..

I don't get the whole 2 display setup in both KDE and Gnome.. I have one monitor hooked up, yet it insists on showing me I have two connected. In Gnome I mirrored them to solve the problem and in KDE I disable the LDVS1 display.. I just don't get the concept of it saying there are two monitors connected..

Time to do some digging in the forums..

Thanks again for the help. I was pretty much ready to give up on that machine with Ubuntu. Wouldn't have gone any further it it were not for your help.. Cheers!!

JP

---

### Post by davidmohammed on 2011-02-03
excellent news - hopefully this thread will help someone else in the future with similar issues.

Not sure about the resolution issues - perhaps another thread needs to be created.

Also - I'm wondering - was it the combination of the new kernel + edgers that fixed it, or did you just need the new kernel?

One way to find out is to install ppa_purge

you can ppa_purge the edgers to restore the original maverick X stuff.

If the desktop comes backup - you know you dont really need the 'bleeding edge' graphics (not very stable given the name!).  Maybe this will fix your resolution issues....

Recommend you backup what you've got first though just incase stuff screws up again (recommend clonezilla).

Good luck

---

### Post by JohnnyPuffs on 2011-02-03
Hey David,

Can't say for sure yet.. but my hunch is that it was the new kernel that did the trick. I'll purge the edgers ppa later on and post the results. Hopefully some of my resolution issues are fixed.. Though I've seen a few posts with this  bug with Kubuntu. Apparently it's been there for a few versions and people are a bit miffed it has not been fixed yet.. 

While I REALLY like the KDE interface so far it does seem to be a bit more buggy and more of a hassle to work with that Ubuntu/Gnome.. Maybe getting rid of edgers ppa will help it out a bit. If not it's back to straight Ubuntu.. Could be myself as well.. I've got a 2 year old, a 3 month old and have been working 14-16 hours days the past two months or so.. The sleep deprivation is making me a bit looney.. :)

Thanks!

---

### Post by JohnnyPuffs on 2011-02-04
OK,

FInal comments and thoughts on the whole install..

So David.. it seems to be just the Kernel that did the trick. I did a ppa-purge on edgers and not only is everything still working, the system actually appears quicker and more stable.

I'm really liking both Ubuntu and Kubuntu as Desktop systems.. I think I'm drawn a bit more to the KDE interface because I really like graphic design. More as a hobby, than anything else.. so the KDE interface is a bit more appealing to me. At least for the moment, as it's brand new to me. Like any other OS, I'm sure once the "new-ness" wears off, it will not be as big a factor.

I finally got my desktop resolution to save correctly on reboot, which was no small task. It apparently has been an issue for a lot of people for a least a few releases. It was supposed to be fixed with 4.6, but apparently is not. I literally spent at least 3 hours digging through forums and solutions. I ended up having to write a shell script using xrandr to set the resolution at startup each time and have it Autostart.

With Ubuntu, I set my resolution at 1920x1080 at the start and it was never a problem.

Considering Kubuntu's mission statement is:


> The Kubuntu Team mission is to lead in the development and advancement of free software as well as **to produce the greatest desktop operating system** that is:

Open
**Reliable**
**Stable**
**Usable**
Accessible
Attractive
**Consistent**
Discoverable

 I have to say the display settings being so difficult to work through is a major FAIL. One of the major apparent goals behind *ubuntu is to make a Linux Desktop a REAL and legitimate alternative to Windows/Mac, which means newbs. Something like getting your monitor resolution set should be a 1 minute operation and a no brainer.

I've been working with Linux since 1994 since I went into the web "biz", but essentially am a LAMP guy. I've only worked with command line mostly, a couple web guis to simplify management. Mostly working with headless servers. This was my first delve at all to even look at a Linux Desktop. I've dealt with thousands of clients daily for the past 17 years, who are all Windows/Mac users, and they can barely get a grasp of that. There is no way in a million years they would ever be a candidate for a Linux desktop when things that should be automated during setup become hour(s) long procedures and involve command line/scripting knowledge.

IMHO the 2 things holding back Linux as a serious alternative for a desktop environment.

1. The setup for any Desktop environment needs to be brainless. Pop a disk in, answer a few simple questions, have a cup of coffee and when you come back it's done.

2. Adding hardware needs to be as simple a procedure as it is on Doze/Mac.. I realize a lot of hardware manufacturers are not proving Linux drivers, but that is a major hurdle. I got a rocking deal on three 2TB external USB 3.0 drives. Grabbed a couple USB3 PCIe cards and plopped them in both a Mac and Windows machine and was up and running in minutes.. Took me hours of trying to get it setup on Ubuntu, digging through more forums, docs, etc until finding the answer. This after reading article after article about Linux being the first to support USB3, etc.. Articles from 09 and forward I believe. Yet in 2011 it's still a PIA to do.

Once you get these OS setup, they work beautifully. Very intuitive for the most part. But without a resolution for the two issues above, going "mainstream" with Linux Desktops is not happening.

Alright, sorry for the rant and tangent.. but it just seems a little silly that *ubuntu main pitches are  how easy everything is I would expect things to be a bit easier. Without prior Linux experience the bulk of people will have a hard time and most likely give up..

David, a big thanks once again for all your help. Very happy I finally have this setup and running smooth. I owe you a beer mate!

If anyone has any specific questions about getting this to work, feel free to post here or PM me and I would be happy to try and pass along the kindness I was given and help you out if I can..

Take it easy,
JP

---

### Post by rrinker on 2011-02-25
Interesting. I just built a box with a D510, using an Intel D510MO motherboard. All with the intention from the start of using 10.10. I downlaoded 10.10 and burned a CD. Booted it up and ran the trial mode, worked just fine, so I hit the install button and let it chug. Absolutely no problems, liek every other time I've installed various versions of Ubuntu - and why it is the only Linux flavor I even care to try - it just WORKS.

System Specs: Intel D510MO Atom motherboard, 1 stick (2GB) Geil DDR2 800 RAM, LG DVD burner, WD 750GB Green HDD (I had a spare), Apex MI-008 mini-ITX case w/ 250W PSU, and a Rosewill RNX-N250PC PCI WiFi adapter.

I had to download and compile drivers for the wifi card but everything else just plain worked.
     
               --Randy

---

### Post by pldaniels on 2011-02-26
I'm using the D510 as a low-power 1U www/email server in a colo facility (bonus discounts for being low power).

Anyhow, I've found that the hyper-threading may be a culprit in an infrequent lock/boot situation so I'm trying to disable it.  I've added 'noht' into the grub.lst file but I still see 4 CPUs in top when I reboot.

Anyone had success using noht to disable the hyperthreading?  Next step is for me to get someone to go and disable HT in the BIOS at the colo facility (3000km away).

Other than, that, Ubuntu 10.10 Server loads blindingly fast even on 2.5" 5400rpm 160GB drives - so fast that the tech there asked "Are you running SSDs?".

Paul.

---

