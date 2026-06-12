---
title: "Help Please - wubi won't install on Windows 7 64 bit"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by Cueball01 on 2010-01-26
I have a quad core box with Windows 7 64 bit installed on it.  When I try to install wubi I get an error box immediately after clicking on the exe file that says pyrun.exe at the top of the box and the text says no disk in drive insert disk into drive \device\harddisk2\dr2
 
I have to use the task manager to close that window in order to do anything else.  I can't get past this error.  I would love to use wubi to put ubuntu on my system.  Please help me.

---

### Post by Cueball01 on 2010-02-05
Anybody have any ideas at all to help me?   :confused:

---

### Post by Cueball01 on 2010-03-06
Bump... Nobody has any hints or clues to help me???   :confused:

---

### Post by cosmotopper on 2010-03-08
Given that Wubi purports to be a means of introducing Windows users to Ubuntu, I suspect the program may have been written by someone at Microsoft with a slightly different agenda. 

I attempted to install wubi.exe on a Vista machine, then an XP Machine, and got the same error: Windows - No Disk. Moreover, this error could not be dislodged by canceling the window, or attempting to kill the process entirely. In both cases, I had to pull the plug on the PC in order to get it to go away. I was very concerned that I had inadvertently installed malware.

I was eventually able to install Ubuntu 9.10 on the Vista machine, by downloading a file 'wubildr', and then running wubi.exe on the same drive partition (in my case 'F:') where I intended to install the Wubi filesystem files. I also put the Ubuntu 9.10 install disk in the DVD drive, but I don't know if that was necessary or not. Even then, I got an error message when I ran Wubi.exe, but in this case, I hit cancel, and the Wubi install screen finally came up. And BTW, after booting into the WUBI Ubuntu, I found that my system clock had been reset to GMT.

For details on how to do all this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

You can also google (all the words) "wubi windows wubldr" and consider other tutorials and options. I did not install this on a Windows7 machine, so you might want to investigate some of the entries that focus on that specifically. 

Having just adopted Ubuntu recently, I have been amazed at the quality and finish of this remarkable achievement, particularly the 9.10 release. This release of Ubunutu actually provides mainstream Windows users with a highly compatible workalike Linux system that makes a very persuasive case for migrating out of the Windows desktop entirely. It is very sad to see a companion project undermine all of that by failing to handle a few very obvious loose ends in the install, which should be (particularly given it's purpose) 100% bulletproof. 

I did get it to work, but I plan to uninstall it, and focus entirely on providing a trial copy of Ubuntu using VirtualBox, a much easier and more versatile approach, given that it enables the Windows user to run both Windows & Ubunutu simultaneously, rather than "either or". One other reason for installing Wubi is to get a look at it's Vista/Win7 dual-boot configuration, just as an example of dealing with the new Windows boot schema.

---

### Post by sanderj on 2010-03-08
Have you seen this bug report (+ workaround): [https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881) ?

---

### Post by cosmotopper on 2010-03-08
> **sanderj said:**
> Have you seen this bug report (+ workaround): [https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881) ?

Thanks for that link. I have now read it. I have the utmost respect and appreciation for those who contribute their time and effort to create useful open-source software. Having spent 32 years coping with Microsoft's predatory marketing and product development strategies, I am also a big supporter of Linux, FreeBSD, Open Solaris, Mozilla, etc. 

That said, the bug report I read is representative of a mindset which explains (IMHO) why it has taken so long to dislodge Microsoft's illicit hegemony over mainstream desktop computing. Without dwelling too much on the particulars, I believe that if a piece of software is worth building, it's worth building it right. If the problem here is with Python, use Perl, or C++, or assembler. To answer a bug report by saying (in effect) "Just keep hitting enter and eventually you will get to the install dialog..." (44 keystrokes later) misses the entire point.

Mainstream Windows users, typically those who use Windows at work, do not have the time or the tolerance to be put through a process just to get to square-1. Even after I managed to get through this inexplicable gauntlet, I was still left wondering if I had somehow downloaded a tainted copy of Wubi.exe, and the error dialog was being put up by some sort of virus, malware, whatever. Even more disturbing, I don't remember the last time I encountered a program that could actually force me to power-cycle the PC in order to regain control. This made me even more concerned that I had stumbled on a Trojan of some kind. 

I can honestly say, in my view, it would be better to pull the 9.x version of Wubi than leave it out there in this condition. Ubuntu has set an extraordinarily high standard in terms of ease-of-installation, and compatibility with Microsoft's latest attempts to derail competing uses of the PC hardware (ie: the BCD boot device database, SYSTEM partition, RECOVERY partition, etc. etc.). The whole point of Wubi appears to be to offer the Windows user a "very safe" means of trying a Linux-style OS, and this implementation actually produces the exact opposite result. Frankly, I suspect it would make more sense to implement Wubi on a rescuecd or usb stick, rather than risk putting a new user through this unfortunate series of problems. And, as I mentioned in my original posting, Ubuntu 9.10 running under VirtualBox is a better, easier solution on any reasonably late-model PC.

I don't mean to disparage anyone involved with Wubi. I'm merely trying to emphasize the importance of not reinforcing the historically bad reputation *NIX desktops have had amongst Windows users, namely that they are only for "Techy-Types", people who enjoy fixing bugs and finding work-arounds to problems which Windows users simply don't want to deal with.

---

### Post by Mark Phelps on 2010-03-09
Another point worth considering is that, at least according to the Wubi Guide I just looked at 5 minutes ago, Windows 7 is NOT listed under the Operating Systems supported.

While this might mean that the Guide isn't current, I would think that, given that Win7 has been out for MONTHS now, the Wubi project folks would have SOME interest in keeping their Guide current.

If it were not for the large numbers of posts we get here about Wubi NOT working on preinstalled Win7 systems, I would think that the Guide just needs updating to include Win7.  

But maybe, there are more basic problems with getting Wubi to work under Win7.  And if THAT is true, the Wubi project folks need to update their Guide to inform folks of the problems.  New Ubuntu users are not going to search around for bug-reporting links to find out why they can't boot into Ubuntu!

---

### Post by lisati on 2010-03-09
As a contributor to the previously mentioned bug report, my advice is: eject ("safely remove") any extraneous devices such as card readers. You should then be able to run Wubi without the annoying error messages. Simple.

---

### Post by cosmotopper on 2010-03-10
> **lisati said:**
> As a contributor to the previously mentioned bug report, my advice is: eject ("safely remove") any extraneous devices such as card readers. You should then be able to run Wubi without the annoying error messages. Simple.

I tried installing Wubi on two machines, one with Vista, the other XP/SP3. Both machines have built in card readers. As I understood the bug report, the error dialog occurs regardless of whether there is media in any of the slots. 

It's not clear to me why the error dialog is necessary at all, unless Wubi is unable to locate a primary partitionable device. Maybe the error dialog is coming from pyrun.exe? If not, I would recommend deferring the error dialog entirely, unless wubi is unable to find the wubildr file in the root of an existing partition. 

I believe the partition & boot management on Win7 is the same as Vista, hence while I have not tried it, I would expect to be able to get it to work on Win7, since I got it to work on Vista. A very good resource for information concerning Microsoft's new boot loader may be found at: [www.multibooters.co.uk](www.multibooters.co.uk) If there are differences in Win7, there may be documentation there.

---

### Post by Mark Phelps on 2010-03-10
> **cosmotopper said:**
> I believe the partition & boot management on Win7 is the same as Vista, hence while I have not tried it, I would expect to be able to get it to work on Win7, since I got it to work on Vista. 

While the filesystems used by Vista and Win7 are the same (i.e., Transactional NTFS), the boot schemes are not.

On unformatted drives, Vista installed one partition; on unformatted drives, Win7 installs two partitions.  While both OSs then boot from the first partition they installed, the presence of this extra partition appears to be presenting problems in some cases for Wubi.

---

### Post by cosmotopper on 2010-03-11
> **Mark Phelps said:**
> While the filesystems used by Vista and Win7 are the same (i.e., Transactional NTFS), the boot schemes are not.

On unformatted drives, Vista installed one partition; on unformatted drives, Win7 installs two partitions.  While both OSs then boot from the first partition they installed, the presence of this extra partition appears to be presenting problems in some cases for Wubi.

Thanks for that correction. Come to think of it, given what Wubi is trying to do (although I'm not sure exactly how Wubi works), it very easily could get fouled up given Win7's gratuitously complex configuration. It does appear to be working fine as a dual-boot option on this E-Machine.

Having only worked with one original Win7 system so far (HP-Laptop), I'll assume all Win7's are setup this way, but I would recommend anyone contemplating doing this visit [www.multibooters.co.uk](www.multibooters.co.uk), and read it thoroughly.

FBO those who haven't worked with Win7 yet, there's a very small 'SYSTEM' partition created as the primary bootable NTFS partition, followed by a second primary NTFS partition containing the remainder of the OS but which in my case had no label. In the case of the HP Laptop I setup, I didn't check to see what the original partition schema looked like, but it appeared to me that when I built the recovery disks, Win7 shrunk the second NTFS partition, and inserted another one at the end of the disk (about 12GB as I recall), and copied the contents of the recovery disks into that area. That partition showed up in the MBR with the label 'RECOVERY'.

(Note: On all the Vista systems I've seen, the 'RECOVERY' partition has been pre-loaded as the first primary non-bootable partition, followed by one bootable primary partition containing Vista. This creates it's own set of problems if you want a dual-boot system.)

So (back to Win7...), at that point, you have a set of 3 DVD recovery disks, and this additional partition which is presumably there for backup purposes.(?) Coincidentally, by doing it this way, Microsoft uses up 3 of the 4 MBR slots. Furthermore, there is an issue regards the size designation of the 3rd (unnecessary) partition, relating to parted or sfdisk, or some combination of the two, wherein for example, if you use sfdisk as follows:

sfdisk -d /dev/sda > sda.dump.bin

And then try to recreate the MBR with sfdisk:

sfdisk /dev/sda < sda.dump.bin 

You get an error from sfdisk indicating that the 3rd partition is not the right size. I know there's a solution to this problem, I just haven't gotten around to tracking it down. (For now, I'm just discarding the 3rd partition entirely.)

My procedure to re-configure the Win7 PC for dual-boot operation was as follows:

1. Make image copies of all the MS partitions on an external USB drive.
2. Delete the third partition entirely (it isn't needed, and Win7 will boot without it, and with no complaining).
3. Use ntfsresize to shrink the 2nd NTFS partition down to something in the 40G-60G range, then make another image copy of the shrunk NTFS partition. 
4. Add an Extended partition, with one or two NTFS partitions at the beginning for use as common storage, the first being 16G-24G, so in case you do want to restore the 'RECOVERY' partition you threw away, you can do so. The second one is just a judgment call based on how you plan to use the machine. 
5. Add your Linux slices.
6. Possibly fill out the disk with another primary NTFS partition as a placeholder, in case you need to use the 4th primary slot for some other purpose. 

In my case, Win7 (or was it HP?) told me I was only allowed to make one set of recovery disks. Of course this prompted me to burn a second set of my own, and I used that set to successfully restore the system. (So, I guess I cheated Microsoft out of another opportunity to charge me extra for something they should have provided for free in the first place.)

I believe Ubuntu will do it's own slices if you want it to (caveat, I've been using FreeBSD & Solaris for about 15 years, only now getting into Linux, so all I can say is this approach has worked for me on two machines, one a laptop, the other a quad-core Gateway desktop).

I did install Ubuntu 9.10 on a couple of Vista systems, and it setup the dual-boot flawlessly. I have not installed Ubuntu on a Win7 platform, so I don't know if that works. I used SystemRescueCD for all of the above (a superb suite of tools).

---

### Post by Cueball01 on 2010-03-23
I will try some of the workaround info and report back on my progress.
 
Thanks for the insight.

---

### Post by Mark Phelps on 2010-03-23
Looks like this thread is getting confusing ...

To try and clear it up, dual-boot with Wubi and dual-boot with Ubuntu in its own Ext4-formatted partition -- are entirely DIFFERENT implementations of dual-booting.

So, it's not surprising that Wubi installations fail to reboot properly but external partition installations work OK.

In my case, I ONLY use the second approach, and have NEVER had a problem dual-booting versions of MS Windows (XP through Win7) with versions of Ubuntu (7.04 through 9.10).

---

### Post by Deozaan on 2010-04-29
Just thought I'd pop in and say I'm having this problem right now on 10.04 LTS in Windows 7, 64-bit.

I'll try the "workaround" listed here: [https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881)

Thanks for the information.

---

### Post by 321System123 on 2011-06-04
> **Deozaan said:**
> Just thought I'd pop in and say I'm having this problem right now on 10.04 LTS in Windows 7, 64-bit.

I'll try the "workaround" listed here: [https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881)

Thanks for the information.


Okay, To help everyone with this problem. The errors are on verisons 9.10 and higher. Please get a 8. verison and do a upgrade in ubuntu as that's the best way to fix this issue. [Click here]("http://old-releases.ubuntu.com/releases/8.10/") for the link to the 8.10 version. I would imagine that this problem will be fixed in the next update but that's just my opinion NOT FACT. I have tested this solution myself and it works. Just do a inside upgrade.

Everyone is making it complex to understand but really its just a simple fix.

---

