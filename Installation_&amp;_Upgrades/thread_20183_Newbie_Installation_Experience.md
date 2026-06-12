---
title: "Newbie Installation Experience"
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by Forrest on 2005-03-15
I just wanted to write a little bit about my experience with Ubuntu over the last few days.

I have an older Toshiba AMD 366Mhz laptop that I wanted to return it to some sort of basic functionality.  I felt that Win98 was not an option due to internet security issues and what not.  I did a little searching and was recommended Ubuntu.

I downloaded the Warty ISO and burned the ISO to a disk.  My plan was to follow the mini-installation guide in the "how-to" section of this site.  I installed the software using the custom feature.  After that I loaded the proper modules and rebooted the system.  Things at this point were quite broken.  The IceWM module only appeared to half load.  I tried reinstalling the system several times after this all with the same result.  I even tried the full installation but that would always fail before it finished (I lost another few hours to this thinking I had a bad ISO).  On a whim I decided to plug the laptop into a network connection and low and behold it actually worked this time.  I find it quite odd that an ISO install disk can not complete a functional installation without being connected to the internet.  And even more frustrating is that it wasn't mentioned anywhere in the how-to guide.

After finally getting into a working GUI with minimal applications loaded I begin to find other issues.  First off I have no access to my internal clock via the BIOS so I have no way of adjusting the clock.  I also can't access any network setup features as the minimal installation apparently feels changing network settings isn't needed and, yet again, nothing is mentioned in the how-to guide.  Nothing explains the file structures and basic commands for navigating your system either.  By luck a few old DOS type commands seem to work but nothing on this website even mentions it.

My conclusion is that this installation isn't usable.  Installing Firefox went well but I stopped there.  With no way to browse files, move files, delete or create files, I see no point in even trying to install OpenOffice.  By the way, the how-to instructions to install these items also don't work.  I browsed the security.ubuntu.org files on a working PC to try to find working applications to install, and those 9/10 times didn't work either.  Why was this stuff stated as being included on the ISO?

So here I am, after 10-12 hours of install after install, poking a stick at it. I consider myself a fairly capable PC user and I'm in awe that you guys can get this stuff working and actually enjoy it.  I don't think I've ever had such a bad experience learning new software.  I feel like I shouldn't have followed that how-to guide but it was all that was available, not to mention that the full install failed all the time anyway.  I also spent a good amount of time with the search feature of this forum. ](*,)

If anyone has any resources to better instructions please post them.  Nothing on this site even remotely covers even the most basic of installations, it all sort of assumes that it works from the beginning and that you know to setup a network connection before installation?!?!  I'd love to get this working still and any help you can point me to would be greatly appreciated.

---

### Post by BaffledMollusc on 2005-03-15
I don't know if I'm qualified to respond to this post since I've only just installed Ubuntu myself and everything worked perfectly for me (except WEP encryption which I'm still wrestling with). But I thought I'd respond to a few of your points by way of encouragement (we're trying to convince people to stick with Linux, right guys?).

[QUOTE=Forrest]I just wanted to write a little bit about my experience with Ubuntu over the last few days.

I have an older Toshiba AMD 366Mhz laptop that I wanted to return it to some sort of basic functionality.  I felt that Win98 was not an option due to internet security issues and what not.  I did a little searching and was recommended Ubuntu.
[/QUOTE]

*Can* you have Ubuntu (or more accurately, Gnome) on a laptop like this? Wouldn't you need more memory? (Again, not sure how much you have, but given it's a 366MHz I'm guessing it's not much...)

[QUOTE=Forrest]I downloaded the Warty ISO and burned the ISO to a disk.
[/QUOTE]

You might want to try the Hoary 5.04 preview release instead of Warty. I haven't tried Warty, but newer is better, hopefully...

[QUOTE=Forrest]
My plan was to follow the mini-installation guide in the "how-to" section of this site.  I installed the software using the custom feature.  After that I loaded the proper modules and rebooted the system.  Things at this point were quite broken.  The IceWM module only appeared to half load.  I tried reinstalling the system several times after this all with the same result.  I even tried the full installation but that would always fail before it finished (I lost another few hours to this thinking I had a bad ISO).  On a whim I decided to plug the laptop into a network connection and low and behold it actually worked this time.  I find it quite odd that an ISO install disk can not complete a functional installation without being connected to the internet.  And even more frustrating is that it wasn't mentioned anywhere in the how-to guide.
[/QUOTE]

Yes, I find this a bit odd too. I didn't run into this because the install recognized my wireless network and happily went with that. But surely the installer should not fail if there is no network connection, or at the very least display some sort of informative message. Anyone have any comments on this?

[QUOTE=Forrest]
After finally getting into a working GUI with minimal applications loaded I begin to find other issues.  First off I have no access to my internal clock via the BIOS so I have no way of adjusting the clock.
[/QUOTE]

Don't understand this. Weren't you asked during the install if you wanted to use the hardware clock? Do you mean you can't adjust the clock from within the OS (I'm writing this on a Mandrake linux OS, so I can't check how the clock on the Ubuntu desktop behaves).


[QUOTE=Forrest]
I also can't access any network setup features as the minimal installation apparently feels changing network settings isn't needed and, yet again, nothing is mentioned in the how-to guide.  Nothing explains the file structures and basic commands for navigating your system either.  By luck a few old DOS type commands seem to work but nothing on this website even mentions it.
[/QUOTE]

The file browser is your friend. Under the "Applications" menu on the GUI isn't there something like "File Manager" or "File Browser" or something which works like Windows file explorer?

Something occurs to me - you said you made a minimal GUI install, presumably because of memory issues. If that's the case I guess your Gnome desktop is something I'm not used to so I can't really make suggestions.

[QUOTE=Forrest]
My conclusion is that this installation isn't usable.  Installing Firefox went well but I stopped there.  With no way to browse files, move files, delete or create files, I see no point in even trying to install OpenOffice.  By the way, the how-to instructions to install these items also don't work.  I browsed the security.ubuntu.org files on a working PC to try to find working applications to install, and those 9/10 times didn't work either.  Why was this stuff stated as being included on the ISO?

So here I am, after 10-12 hours of install after install, poking a stick at it. I consider myself a fairly capable PC user and I'm in awe that you guys can get this stuff working and actually enjoy it.  I don't think I've ever had such a bad experience learning new software.  I feel like I shouldn't have followed that how-to guide but it was all that was available, not to mention that the full install failed all the time anyway.  I also spent a good amount of time with the search feature of this forum. ](*,)

If anyone has any resources to better instructions please post them.  Nothing on this site even remotely covers even the most basic of installations, it all sort of assumes that it works from the beginning and that you know to setup a network connection before installation?!?!  I'd love to get this working still and any help you can point me to would be greatly appreciated.[/QUOTE]

Sorry I can't be more help. As I said, I did a full Hoary 5.04 install rather than a custom cut-down Warty install, so we're in totally different boats. This post is mainly just to encourage you not to give up, and hope someone with some actual experience in installing on older laptops posts something  :-)

---

### Post by Forrest on 2005-03-16
Thanks for the encourgement BaffledMollusc.  I'm going to wait a few days and give it another go.  I think I may have some odd laptop hardware that's creating an issue.  I had a sharing issue with IRQ 3 when I tried it the first time, IRQ 3 is now disabled so maybe I can try a new install.

The weird thing is that it clearly can't install properly yet it gives little to no information as to why.  I've tried to look at log files, as direct by this forum, and those locations and files simply don't exist.

I don't have a file manager, and that's a big part of my problem.  I tried apt-get install mc and it can't find it.  So it'll be a bit more guessing to track down a small file manager on security.ubuntu.org.

I don't think I'm using GNOME, I installed IceWM for the GUI.  The laptop has 64 Mb of RAM so I think it'll chock on some of the fatter GUIs.

If worse comes to worse I have an old copy of Windows 2000 that will at least install.  At this point just getting something to install without a ton of errors would be good.  I've so far had a great experience using Open Source software as some really talented people have made some absolutely great applications.  I'm not sure what happened with Linux though, maybe OS complexity coupled with all the different types of hardware in the world just don't mix well.

---

### Post by mips on 2005-03-16
I would advice using the preview hoary, rather go with array 6 release.

cheers
mips

---

### Post by kamstrup on 2005-03-16
To be honest I would not install any (recent) GNOME desktop on a machine with your specs. I'd go for Slackware with XFCE as my desktop environment. You'd just need the Slackware 10.1 CD1 to do this.

Don't get me wrong I really dig Ubuntu but GNOME/GTK is not really good friends with old computers with...

---

### Post by de_doughboy on 2005-11-07
I can sympathize with you my freind. After several hours I was able to get Hoary Rel 5.4 to work on my old AT Pent-1 using an 80-MHz CPU. It's not an easy task since most of the X-windows scripts fall over when using the ISO install disk on an older AT. However, I did follow a freind's advice and first down loaded the _* go Live-CD ISO-CD *_version to CD, before I tried to create a hard disk partion. Using the Live-CD will  help you determine if your PC has any hardware issues before you spend hours trying to install it onto your hard disk. Let's face it. We don't live in a perfect world, and neither is my suggestions below. If you want to use the latest Ubuntu then you have to realize that this is a developers community and not a production environment.

 Amazing enough that when I booted from _*go Live-CD ISO*_ on my old AT Pentium-1  it launches after 1/2-hr with only 512-Meg RAM (using 128-SIMMS x 2).  The slower the PC the more patience you need to have. The system is very stable once it gets up, and yes there is an issue with accessing the system clock, but that seems minor worry to other headachs.  It took me a few hours to bone up on the workings of X-windows, and openOffice. These are easy enough to master if you have any experience with Unix or Red Hat. Yes even the Word Processor worked direct off the the go LiveCD, and you can save files to the desk top. 

Here is what I did,

1) Read everything you can find on the forum about creating a barebones system. (Including the footnotes/fine print!) One article didn't tell me that a barebone system you have to set up your own user path and user profile so be careful. Some things in Linux user guides are just understood. Like where is the root path.  

2) To install onto your HD. First boot from iso-CD set up disk as boot: server (not custom) then let it walk though until it falls over. If you don't touch it you might even get all the way through the first time. 

3) The base system install  might halt when it gets to the boot manager. I found BUM and GRUB to be totally user unfreindly, so I backed up to the install menu and _used LILO _to create the initial partion in the Linux Master boot Record (MBR). I then used a commercial windows boot manager called (osl2000) windows version 1 to manage the CPU's boot sequence. Since I am more comfortable with windows I used this manager to keep track of my my HD disk partions so I would not accidently overwrite windows by mistake.

You might have to re-install windows 9x/Win-2K on front end of the disk for this boot manager to work otherwise Linux won't see it. Once osl2000 is installed and you reboot then you can see the Linux partions and swap space easy enough. You can get osl2000 from the zdnet website at [http://www.zdnet.com](http://www.zdnet.com) 

4) I used the minimal install instructions on [http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html) most useful.  The first page tells you to start off as a super user enter: "sudo su -"  what they don't tell you is that you have to have the path setup correctly beforehand and that "sudo" and "apt-get" commands are found in /usr/bin or /etc/initid bins. Don't worry if you don't understand paths all that  much just set the default path to include /usr/bin as follows: PATH=$PATH:/usr/bin
I set my entire path to be equal to ISO LIVE-CD by booting up first and then checking the path names and lenghts under the root console. See Apps->Systemtools->RootTerminal to get to the root console window under X-layers.


5) You should try to become familar first with the look and feel of Ubuntu by  booting off the ISO _*go Live-CD*_ first. Sorry I have to empathize this again because most Linux newbies panic when they can't get back to an workable OS. This is one way of learning the internals before you try your first install.

You can even play around with mounting services for HDs floppies and CDs using go LIve CD, but only if you remembered to write down the names of your partions during the bootmanager setup stage. 

After the Linux-OS was up and running I used this

 #mount -n -L LINUX /dev/hdb1 

to boot off my secondary harddrive without too much difficultly. 

So far the system is stable and I have only had to reboot once because of the boot manager install and that was a windows 9X install issue not a Linux one. Now I can see why some users have reported that their Linux have been up for a year or more without a single reboot. That is pretty amazing considering how many times a day I have to reboot my winPro OS. 

if your still struggling then write back to me here.

---

