---
title: "cannot mount /dev/lop0 (/cdrom/casper/filesystem. squashfs"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by 3gerald on 2010-10-05
help on new install

getting this message no matter what I try off of same cd that just worked on the machine next to it.

"(initramfs) mount mounting /dev/loop0 on filesystem.squashfs failed: Input/Output error
Cannot mount /dev/loop0 (/cdrom/casper/filesystem.squashfs on // filesystem.squashfs"

dell p3 1800mhz 386m ram 120 gb hd  80 gb unformated with win xp on remaining 40 gb dual boot 

love the operating system just learning  it new have it on my laptop and one of the kids machines going for the other kid than mine   thanks

---

### Post by mörgæs on 2010-10-05
There is probably not enough memory for a regular install. You could try the alternate installer for Ubuntu or (even better) go for Lubuntu:

[http://ubuntuforums.org/showpost.php?p=9834517&postcount=261](http://ubuntuforums.org/showpost.php?p=9834517&postcount=261)

---

### Post by esarrat on 2010-10-09
Hello,
I am stumbling across the exact same problem (loop0) while trying to install the 32 bit version of Ubuntu 10.04 on my new Acer Aspire 5551 Laptop (64 bit processor AMD Athlon II P320 Dual Core - 3 GB memory - Windows 7) Any help greatly appreciated !
Eric.

By the way, not sure why, but my computer ignores all the other CD's I've burnt, notably any 64 bit versions of Ubuntu, and even the 32 bit version of the 10.10... Instead of booting on the CD, it starts Windows as if the reader was empty.

---

### Post by nutznboltz on 2010-10-10
> **esarrat said:**
> Instead of booting on the CD, it starts Windows as if the reader was empty.
The firmware "BIOS" needs to be configured to boot from CD.

When you turn on the power to your computer you need to press a key to get into the BIOS setup.  This varies depending on the computer.  There is often a message telling you which one to use.  If no message appears (sometime the message is there for a very short time only) try one of these keys:

F1
F2
F12
Del

---

### Post by nutznboltz on 2010-10-10
I get the "cannot mount /dev/loop0 (/cdrom/casper/filesystem. squashfs" message with an MD5-verified i368 10.10 alternate iso

md5sum ubuntu-10.10-alternate-i386.iso 
419ad8ee1bb76a49490f4a08b5be43f0  ubuntu-10.10-alternate-i386.is

booting as an i686 KVM guest

But when I try the desktop (not alternate) I do not get that error.

---

### Post by esarrat on 2010-10-11
Thank you Nutznboltz. I have done what you describe which is why I am so puzzled. With the CD of Ubuntu 10.04 32 bit, the Notebook boots from the CD, starts the installation of Ubuntu, and then stops with the aforementioned error message. With the 5 other CDs I have burnt with different versions of Ubuntu and the same set up requiring an initial start from the DVD drive, it is as if the hard drive was selected.

I have interrupted the initial installation by clicking on a key while the small keyboard is displayed on the pink scree. I performed the memory check, which passed without failures. Strangely enough, the selection of the option to verify the disc does not result in the execution of any programs. And the option to start ubuntu brings me back to the initial input/output error.

---

### Post by esarrat on 2010-10-12
Hi,
After having repeatedly failed to install from a CD, I used Unetbootin to create a USB stick with the image of Ubuntu 10.04.1 I had downloaded, and... halleluia, it worked :)

---

### Post by 1Dagars1 on 2010-10-12
I am having exactly the same problem. I am installing on 2 seperate systems. One has 750gb hdd and the other 500gb. the 500 gb is a laptop - sony vaio VPCCW21FX i3 with 4 gb RAM. The other is a Dell XPS420 core 2 Duo E8500 3.16Ghz. both run Windows 7 64bit and I had both set up to dual boot with 10.04 LTS and everything worked great. I recently tried the upgrade on my Sony resulting in a failed upgrade. Rendering Linux unbootable. I just wiped the HD, reinstalled windows, and tried to install 10.10.

I am getting the very same error before and after the wipe on the sony as well as on the Dell. I also downloaded and burned .iso off official Ubunto site and i get the same error from both .iso's. I burned both onto a CD as opposed to a DVD.

The exact wording of the error is:
 "BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error Can not mount /dev/loop0 (cdrom/casper/filesystem.squashfs) on //filesystem/squashfs"

I also tried to run from CD .iso without installing on both boxes and get the same error as above.

I tried to re-install 10.04 on the sony vaio which was just wiped and i can install 10.04.

Also, the sony Vaio has a nvidia 320m graphics card and the Dell has an ATI Radeon 3870 x2 with 1gb video.

Oh - i downloaded the .iso's 1 day apart.

Please help. I am not sure if if the .iso i downloaded from Ubuntu were both corrupted, if i am doing something wrong...not sure what is happening.

any help is very appreciated. Thank you.

---

### Post by esarrat on 2010-10-12
Hello,
I have burnt 12 CDs, all good, and to no avail. Not sure what the issue is. Yet, I'd advise you to use Unetbootin. I found it simple and effective and just put all my CDs to the trash :-)

---

### Post by 1Dagars1 on 2010-10-12
So I tried to put this on a bootable USB drive from within Windows and i got the following error:

Data error in 'casper\filesystem.squashfs'. File is broken

I used Universal USB Installer that was recommended on ubuntu.com

---

### Post by mörgæs on 2010-10-12
Though it is recommended on the web page there are quite a few reports in the forum saying that Unetbootin is the way to go.

---

### Post by 1Dagars1 on 2010-10-13
I was going to try Unetbootin next. However I decided to download (from Ubuntu.com) from within 10.04 and burn the CD from there. I also set the burn speed to the lowest speed. This worked for me no problem. Not sure what was corrupting the file...

---

### Post by m4tic on 2010-10-18
This sucks, i get the same problem. word of advice is do not temp would be new users with this release. first impressions count

---

### Post by tarzM on 2010-10-18
I got the same message, with the 1st disk I burned.  After reading a couple of the posts I decided to try a couple of things.

This is what worked for me.
I had downloaded ISO Image Burner 1.1 from isoimageburner.com (not pushing the software it's free)

I selected the ISO image to burn (ubuntu-10.10-desktop-i386.iso), however this software has a checkbox for boot image and it allows you to select a boot image.  I selected the same ISO image as the one I had selected to burn (ubuntu-10.10-desktop-i386.iso).
I selected the slowest speed (someone mentioned this on a previous post)
Clicked burn and it worked great, booted from the CD and installed.

---

### Post by zorrofox on 2010-11-14
I am having exactly the same issue and none of the aforementioned fixes works for me. I'll re-download Ubuntu and just hope that it works, if not then I't's just a waste of time. It takes all night to download a file that big at the internet speeds available in this house. Shame really.

---

### Post by mörgæs on 2010-11-15
Before downloading again you should test the MD5 sum of the ISO. If it is correct, there is no point in a new download.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

A better choice is trying an older release of Ubuntu, preferably an alternate install.

---

### Post by progpen on 2010-11-20
Just adding mine to the list here.  When performing the default install on a Latitude D620 I got the "cannot mount /dev/loop0" error.  I then tried the "try it before installing" option and BusyBox tells me "No init found.  Try passing init= bootarg.

Ubuntu 10.10 is certainly not ready for prime time folks.  I can easily get this installed, but just for S's and G's I'm going to Fedora to see if I run into any issues there.  10.10 is simply not stable enough for me to use daily (that is the impression I have anyway).

---

### Post by mörgæs on 2010-11-20
Problems during installation is not the same as an unstable system once installed.

---

### Post by progpen on 2010-11-20
> **mörgæs said:**
> Problems during installation is not the same as an unstable system once installed.

Basic problems (like this) during installation are most certainly indicative of an OS that is uncooked, unstable, buggy and not ready for daily use.

---

### Post by giorgiomartini on 2010-11-21
****in ubuntu sucks , it supossed to be easy to install yet you have all this problems

---

### Post by progpen on 2010-11-21
I've been running Linux for 12 years (that's 48 in IT years), and running Ubuntu on multiple machines since 4.10.  Ubuntu has come a very, very long way since then and is a great OS.  I have been trying to get Ubuntu onto the home and business desktop for years, but when I see issues like this one, it tells me that we still have a ways to go before Ubuntu can go mainstream.

When non-technical users want to do something as simple and basic as a default install from a CD onto a brand name laptop and come across issues like this, it sets us back significantly.  Those users will run (not walk) to the nearest Windows CD and not look back.  Even more, they will pass their experience on to everyone around them.

Issues like this one truly should have been caught and fixed before this ever left Beta.

---

### Post by serutan on 2010-11-25
Same error. I've been using Ubuntu since Dapper Drake and have had no problems with it, and I'm not going to complain about something that's free and generally excellent. But it surprises me to see all these folks with the same problem and no realistic suggestion of a solution (i.e. yes, the CDROM is first in the boot sequence, yes there's plenty of memory, yes we've tried turning it off and turning it back on...). 

Right now I'm trying to use the LiveCD to solve a completely unrelated problem, and I can't find my original install CD. My question is simple: is there a solution for getting the v10 LiveCD to boot, or should I give up and look for an older version?

---

### Post by mbaribeau on 2010-11-30
I had all the same issues posted and solved it by using the Wubi windows installer [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

---

### Post by tkelito on 2010-12-02
I've run in the same issue on a Celeron 2.0 Ghz box with 2GB DDR3200 RAM.  I am attempting to install the i386 10.10 and I receive that same error.  I really didn't need the GUI anyways so I am burning the server edition to CD right now.  Unfortunately for me this machine is dated so I have no option to boot from USB.

Will post back results, I am not sure of the cause, nor have I been able to find a resolution to fixing it.  

Current Output:

```
(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
```

I started originally with this error, but now have upgrade to the one above:

```
GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
```


Wish I had a fix, I have installed Ubuntu hundreds upon hundreds of times and this is my first issue during bootup.  If I run into the same issue with 10.10 Server I am going to go to 10.4 LTS.

---

### Post by punchcardoperator on 2010-12-13
I got this error too. Since this was my first experience with Ubuntu I was pretty disappointed. I tried all the remedies suggested and they did not work for me. However, I after much flailing about, multiple machines, multiple downloads etc. I noticed that the iso file size was not the stated 693MB. Nor was it consistent across the many downloads I tried.

So, once I managed to get a download with the right files size I did manage to burn a CD and get it a good install. However, when I tried the USB option, I got a weird message about  "not a com32 image" and an abort.

This is supposed to be cured by typing "live" at the boot prompt. That did not work for me but at least I was able to use the CD.

I am guessing there is an intermittent  download issue that is causing this. I don't know if this is the fix or if it is something else but if this works for any one else, please let me know so I can feel like I did something for the community instead of freeloading a great OS.

---

### Post by mörgæs on 2010-12-14
Welcome to the fora.

You shouldn't feel bad about freeloading in the beginning. We all started that way.

If you suspect the download to be a problem, running the MD5SUM-test will tell whether the ISO is all right or not: 

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by chrisblue on 2010-12-21
another one to add to the list. I have been using Mythbuntu and am trying to reload 10.10 and get the same issue...busybox and initrampf etc...

I will have a go a some of the solutions here though I did have a look at my boot sequence and can't see where I can select a USB stick as the boot device.

10.4 loaded though to a desktop on the same machine though it did report some errors.

More info as I keep on working the issue.

---

### Post by drumsareus on 2010-12-22
I was getting this same error and found something that fixed it for me.  I was trying to burn 10.10 onto an old Dell and was getting frustrated.  Turns out when I was burning the .iso using disk utility (on a macbook pro) I was getting a 'medium write error'.  I tried burning onto a different brand of disc and then it started working.  Might not solve the problem for everyone, but for me Memorex CD-R did not work but Phillips did.

---

### Post by mattdan79 on 2011-01-12
Just my 2 cents.
I was trying to install Ubuntu on an older laptop and same thing, sometimes Live CD would load, but most times it would just die with the squashfs message (sometimes I had to hit esc to see it).  Even when it did load the install would always fail with some sort of input output read or write failure.

Long story short the Live CD is NOT going to work (in my opinion) on this system.
Minimal CD option worked for me.  I didn't try the alternative install option, but I'm assuming that would work too.  I 
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

I THINK the problem may be that this system only has 512mb ram.

---

### Post by mörgæs on 2011-01-12
I would think so, too. 512 MB is enough for running Ubuntu when installed, but a live boot sometimes requires more memory than this. 

Anyway, you did the right: Trying various ways of installing is always a good option. If only more people would do this simple test before posting...

---

### Post by snazzed on 2011-02-20
I'm no Linux geek but I think I've nailed this down to certain older (early?) SATA Drives/Controllers.  I am trying to boot with MythBuntu10 (Ubuntu10), 32bit or 64 where appropriate.

**Test scenario:**
PC1 - 2yr old Lenovo Core2Duo (SATA2)
PC2 - 6yr old Lenovo P4 3Ghz SATA

Drive1 - 2yr old Hitachi Deskstar 500GB, SATA2
Drive2 - 6yr old Hitachi Deskstar 40GB SATA (came with PC2)

Error = "(initramfs) mount mounting /dev/loop0 on filesystem.squashfs failed: Input/Output error
Cannot mount /dev/loop0 (/cdrom/casper/filesystem.squashfs on // filesystem.squashfs"


**Results:**
PC1 + Drive1 = works
PC2 + Drive2 = error
PC1 + Drive2 = Error
PC2 + Drive1 = Error

- or - 

SATA2controller + SATA2drive = works
SATA1controller + SATA1drive = error
SATA2controller + SATA1drive = error
SATA1controller + SATA2drive = error



I have 2 other SATA1 drives that have the same problem whether they are in PC1 or PC2.

I don't know if SATA1 *in general* is the problem.  For all I know there are other SATA1 drives/controllers that work with Ubuntu/Mythbuntu.  All I can say is anything with my SATA1 parts don't seem to work for me.  Drive or controller.  

Whatever the problem is, it *is* fixable...  All combinations above work with Mythdora12 (Fedora12) boot disks. 

I'd rather use Ubuntu if possible for reasons I won't bother getting into in this post.

Thanks
snazzed

EDIT:  Could I install on the older PC with an older version of Ubuntu and upgrade it to 12?  Would 2 full version number require a wipe an reInstall?

---

### Post by BigBaka on 2011-03-09
Hi, I just wanted to add my two cents to this thread. I've had all sorts of issues with Ubuntu over the last 2 and a half years I've been using it. For some reason, in spite of the trouble, I've stuck with it, because I believe in the idea. In fact I've slowly been trying to switch our office over to Ubuntu from our Windows system.

That was until today. After a new computer purchase I was all ready to make another Ubuntu installation on but after the live cd developed from remastersys didn't install (crashed at 93%), I downloaded the new 10.10 64 bit iso installation file. But when I got this cannot mount error, it was the final straw. What sort of operating system is it that doesn't even load after downloading directly from the website. I shouldn't have to spend hours and hours trying to get an installation running. I'm not sure why it didn't work, the image file could have been corrupted (was 695 not 693) but frankly I've got better things to do than work it out. 

Although I am still using Ubuntu on my own computer, I'm hereby giving up on installing on any other comps at the office. It was fun for a while, but Ubuntu needs to just work if it is ever going to get anywhere.

Disappointed

BB

---

### Post by mörgæs on 2011-03-09
Sorry to hear that. 

If you want to do one last (and very quick) attempt, you could try burning the alternate 10.04. 
[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

Checking the RAM for errors is also a good test.

---

### Post by BigBaka on 2011-03-09
Hi, I just wanted to add my two cents to this thread. I've had all sorts of issues with Ubuntu over the last 2 and a half years I've been using it. For some reason, in spite of the trouble, I've stuck with it, because I believe in the idea. In fact I've slowly been trying to switch our office over to Ubuntu from our Windows system.

That was until today. After a new computer purchase I was all ready to make another Ubuntu installation on but after the live cd developed from remastersys didn't install (crashed at 93%), I downloaded the new 10.10 64 bit iso installation file. But when I got this cannot mount error, it was the final straw. What sort of operating system is it that doesn't even load after downloading directly from the website. I shouldn't have to spend hours and hours trying to get an installation running. I'm not sure why it didn't work, the image file could have been corrupted (was 695 not 693) but frankly I've got better things to do than work it out. 

Although I am still using Ubuntu on my own computer, I'm hereby giving up on installing on any other comps at the office. It was fun for a while, but Ubuntu needs to just work if it is ever going to get anywhere.

Disappointed

BB

---

### Post by sufifuego on 2011-03-15
> **BigBaka said:**
> Hi, I just wanted to add my two cents to this thread. I've had all sorts of issues with Ubuntu over the last 2 and a half years I've been using it. For some reason, in spite of the trouble, I've stuck with it, because I believe in the idea. In fact I've slowly been trying to switch our office over to Ubuntu from our Windows system.

That was until today. After a new computer purchase I was all ready to make another Ubuntu installation on but after the live cd developed from remastersys didn't install (crashed at 93%), I downloaded the new 10.10 64 bit iso installation file. But when I got this cannot mount error, it was the final straw. What sort of operating system is it that doesn't even load after downloading directly from the website. I shouldn't have to spend hours and hours trying to get an installation running. I'm not sure why it didn't work, the image file could have been corrupted (was 695 not 693) but frankly I've got better things to do than work it out. 

Although I am still using Ubuntu on my own computer, I'm hereby giving up on installing on any other comps at the office. It was fun for a while, but Ubuntu needs to just work if it is ever going to get anywhere.

Disappointed

BB


I do not think that it is file. I actually used Roxio instead of the default windows function to burn the cd image onto the disc and it finally worked. I think that the difference was that I actually verified the copy this time (which Roxio does by default) rather than just copied.  Please try that and see if it works. Good luck!

---

### Post by chrisblue on 2011-03-15
I had the same issues and solved by booting from USB. I agree with the poster above that it sounds like a SATA drive / controller issues as my box has SATA optical drives.

---

### Post by p1ckLe on 2011-03-16
I had this same exact issue and came here for help, made it to page 2 and it seemed people were getting pretty flustered and from what I can tell I figured out the issue, atleast for me.. I had Ubuntu on this system before and formatted and was now reinstalling but with a different CD than I had used previously.. after reading a few pages worth of posts I gathered some info and realized that I didn't use the same program to burn the ISO, I was using Nero this time around so I went back to InfraRecorder or w/e it is that the Ubuntu site recommends and burned it, sure as **** worked out fine. Idk if this will help anybody else, but for some reason Nero would burn it but the disc wouldnt work in the PC. Maybe it was burning too fast as well? Slow your recorder down and if that doesn't work, try the freeware InfraRecorder, works like a charm.

---

### Post by Medievalcyberpunk on 2011-04-08
With the CD i get the cannot mount thing too. Same message.

There is no 'removable disk' in the boot order list so i guess thats why the usb install isnt working(though flashdrives work fine on this comp).

Ive never installed an operating system before, this was a bad first choice.
Anyway ill try again tomorrow i suppose.

---

### Post by mörgæs on 2011-04-08
Hi, welcome to the fora.

Please describe thoroughly your hardware and the steps you have tried. 

Have you used both 10.04.2 and 10.10? 

Older machines can not boot from USB, even though they can read from the USB stick when booted.

---

### Post by llllskywalker on 2011-04-08
I was getting this error after burning the CD. So i tried using the suggested universal USB installer and it gave a very similar error (something about casper and filesystem.squashfs). That made it seem very likely to be a corrupt image.

Turns it, that was indeed the case - the file size was only around 80MB instead of 700+MB like most ubuntu isos. It was obviously corrupted! Which would explain why the windows 7 image burner and Infrarecorder barfed (I had to use ImgBurn) and why it burned so fast :-)

I used Chrome to download it on a windows 7 x64 computer directly from ubuntu's website. Chrome adds a .crdownload to a file while downloading and doesn't remove it until it's complete - and this corrupt image definitely did not have that extension on it.

Other people in this thread have noticed corrupt isos as well. The way I see it, there are three players in the equation:

1) Windows
2) Chrome
3) Ubuntu's website

I have no idea which one is to blame, although the most obvious common denominator for all of us is the ubuntu website. Anyway... for me the problem is solved :-)

---

### Post by Medievalcyberpunk on 2011-04-10
> **mörgæs said:**
> Hi, welcome to the fora.

Please describe thoroughly your hardware and the steps you have tried. 

Have you used both 10.04.2 and 10.10? 

Older machines can not boot from USB, even though they can read from the USB stick when booted.

Cheers! Glad to be here, ive come to the conclusion that the big evil moneybags computer corporation makes big clunky software that is usually too big for the computer they tell you to install it on. I bet they are spying on us too.... and im pretty sure NASA does not use windows.

Anyway Im trying to learn more about computer hardware and operating systems because at the community center where i work we have about 10 pretty nice (quite new) computers networked and internet connected which mostly do NOTHING. Im not quite sure what we should do with them.
People used to use the internet for free here but i think they all have it at home now. 
Weve had a few people in to do computer classes, but not for some time and even then the comps still sat around unused most of the time.

I thought id start with a problem i have with one of my own computers though, an Aspire 3000. 
I use Gimp a lot, it has a nice big screen and i can move it to the couch if i want to draw there.
But its the slowest, clunkiest comp i have. Overheats a bit too (though not as badly as some people on the internets' A3000s have).

Here is what the Squid thing says:
[http://oi52.tinypic.com/xnxhc6.jpg](http://oi52.tinypic.com/xnxhc6.jpg)

Mabey one of the minimum installs? Or even a micro kernel? Ive been reading about those and like the idea, sounds like if you were only going to use a few programs on that comp it would surely be the most efficient. Hmm, though i guess it probably doesnt matter where the drivers are if the whole system is that simple??? Would the minimum installs use more (RAM i guess)than a micro kernel? I think thats the question.[IMG]http://oi44.tinypic.com/2qd6dtw.jpg[/IMG]
If its not plese let me know:D

---

### Post by mörgæs on 2011-04-10
Better to open a new thread (or search the existing ones) rather than posting here, since we are dealing with a new topic.

---

### Post by Medievalcyberpunk on 2011-04-11
Yup, that post just grew and grew.

---

### Post by SaintDanBert on 2011-04-20
Add my ME TOO.

I duplicate posted here: 
[http://ubuntuforums.org/showpost.php?p=10698300&postcount=1](http://ubuntuforums.org/showpost.php?p=10698300&postcount=1)
Since then I installed to a second, identical T42 without error.

As I've read this thread, I don't see a lot of resolution to the troubles.

Thanks in advance,
~~~ 0;-Dan

---

### Post by mörgæs on 2011-04-20
It is not guaranteed to work, but there seems to be good chances if you install from USB.

---

### Post by SaintDanBert on 2011-04-20
> **mörgæs said:**
> It is not guaranteed to work, but there seems to be good chances if you install from USB.

I tried an external USB-connected DVD/CD reader-writer. I would boot
and splash but then fail to mount /dev/loop0 again.  I'm trying to discover what this /dev/loop0 device is about so that I can diagnose further.

I did find this, however.
[https://bugs.launchpad.net/ubuntu/+bug/636711 ](https://bugs.launchpad.net/ubuntu/+bug/636711 )

~~~ 0;-Dan

---

### Post by SaintDanBert on 2011-04-20
When I boot the desktop live-CD, I go directly to splash.

When I boot the alternate live-CD, I get language and other boot options
before I go anywhere else.

Does this shed any light on what is going on?

~~~ 0;-<

---

### Post by mörgæs on 2011-04-20
The alternate CD is not 'live'. It is only for installing. I was about to suggest this.

With 'USB' I meant a USB stick, not a CD attached with a USB cable.

Post 176 in this thread might also help
[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)

and as fas as I know, 10.04.2 is free from the bug.

---

### Post by Marco92 on 2011-04-30
lo sto installando per la prima volta la versione 10.04 e mi durante l installazione mi dà questo errore:

mount: mounting \dev\loop0 on\\filesystem.squashfs failed: no such device
can not mount \dev\loop0 (\cdrom\casper\filesystem.squashfs) on\\filesystem.squashfs

sapete dirmi cosa dovrei fare?

---

### Post by mörgæs on 2011-05-01
There is lots of advice already written in this thread. Have you tried everything mentioned?

- USB and CD
- alternate ISO
- minimal install

---

### Post by Tearo011 on 2011-05-07
**What a terrible ordeal this freaking Ubuntu put you through...](*,)**
[B]
[/B]I cannot even install it and worse than that the freaking meaningless error messages it shows!
[B]"(initramfs) mount mounting /dev/loop0 on filesystem.squashfs failed: Input/Output error Cannot mount /dev/loop0 (/cdrom/casper/filesystem.squashfs on // filesystem.squashfs"
[COLOR=red]What the hell was that?#-o[/COLOR][/B]

They call it free software! This is pull ****, I spent the whole day trying to figure out the problem. Tryied everything and still not working. It cost me more than the price new computer with OS installed.
Don't waste your time on this worthless piece of ****.:shock:

---

### Post by SaintDanBert on 2011-05-08
I get a real sense of frustration from Tearo011. While I'm sympathetic to the frustration, rants like that don't help anyone. I doubt that even Tearo011 got much feel-better relief from the writings.

I've been slinging bits for over 30 years and bad error messages have been a constant source of grief. A pile of techno-babble on the console might have value for the original coder but is rarely useful for an end user. The frustrations voiced by our intrepid poster are a much too common result.

Effective messages might include the following:
[list]
[*]describe what was attempted when the troubles started
[*]describe the troubles in end-user meaningful terms
[*]name any available log file or similar place where the
really technical details might be found
[*]end-user actions that might correct the situation
[*]name where the end-user might learn more from web or doc resources
[/list]

Respectfully,
~~~ 0;-Dan

---

### Post by mörgæs on 2011-05-08
Another option is that Tearo011 reads the thread in which he is posting. This will give him several ideas for solving the problem.

---

### Post by hgn-mu128 on 2011-05-08
Hi everyone, I'm new to the forums, and this is my first post here. No, this is not a new-to-the-forums rant, but I'm just letting the good people here know that I'm having the same problem as the Topic Starter, and many fellow members are having, so that they can help.

Enough of that. The version is 11.04 Natty Narwhal. The above is not the only problem I'm experiencing, I also cannot install using USB drive. After a few pages of the boot messages, it says Writing SCSI cache failed (I don't have the exact wordings). This problem persists for all images on the USB drive, including 11.04 mini, 11.04 alternate and also the CDs of the previous versions of Ubuntu, originally from ShipIt. Alternate install CDs also stall without any error messages just before the Partition Manager loads up (or while it does). Any help appreciated.

PC Specs:
AMD Phenon II&#8482; X4 965
ASUS M4A785TD V-EVO Motherboard
2GB A-Data DDR3 1333GHz
ATI Radeon HD 4200 128MB Integrated GFX

WD 320GB/298GiB HDD
Hitachi LG HL-DT-ST DVDRAM GSA-H42N DVD RAM drive (on IDE Primary Master)

SAMTRON 14" CRT (Pfft.)
USB Mouse, PS/2 Keyboard
AMI BIOS, recently updated.

Similar topic(s) I found:
[http://ubuntuforums.org/showthread.php?t=1556602](http://ubuntuforums.org/showthread.php?t=1556602)

EDIT: I found a web page with the same issue for the Linux Mint. I thought both are encountered in the BusyBox stage, so might help. Note that it did not solved my problem, anyway.
[http://forums.linuxmint.com/viewtopic.php?f=46&t=49868](http://forums.linuxmint.com/viewtopic.php?f=46&t=49868)

---

### Post by mörgæs on 2011-05-09
Have you tried removing **quiet** and **splash** from the boot options? 

This will give you a better chance of seeing what is wrong.

---

### Post by hgn-mu128 on 2011-05-10
I did. The background processing (foreground when the splash is off) shows me a lot of errors, most of them I/O. Then after a few retries, stalls at the error which caused this topic to be born and these users to moan. ;)

About changing drives, as someone pointed out that as a solution. I have 2 Samsung disc drives and a Hitachi-LG. All DVDR/RW. All of them, set on IDE Primary slave (at different times, of course), shows this error regardless of whether I burnt the image on a CD or DVD. Ironically, the LiveCD runs and installs on my old Pentium IV machine with 512M RAM, but produces a GRUB 18 error, after install. :|

---

### Post by mörgæs on 2011-05-10
I guess we have to search further in order to analyse your problem. Have you tried a distro which is not part of the Buntu family?

---

### Post by hgn-mu128 on 2011-05-10
No. Not another linux distribution. But I've successfully installed FreeBSD 8.1 on my old IDE 40G HDD using the same LG DVDRAM.

EDIT: Ubuntu 11.04 installation did boot up now using the alternate ISO on a DVDR. I guess there has been some problems with the burn process, my hard disk now has a bad sector and the second half of it is almost unusable because Ubuntu tried to write ext4 file system onto it, and now every time I create a new partition, the whole extended partition becomes deleted and unallocated. I had to use Parted Magic and Testdisk to repair it. Pretty nice, huh?

---

### Post by jrsutton on 2011-05-19
I had this exact same problem yesterday. I downloaded the 11.04 32 bit desktop version and was trying to install it on a pendrive using the instructed method. I had originally used a web browser to download the .iso. To fix the problem I went to the alternate downloads, NOT the alternate CD, and used the torrent link for the same .iso and pointed it to my original .iso. This showed that it was 87% complete. Which indicated to me that it was corrupted. However, the torrent auto truncated and resumed the file. In less than 5 minutes it finished. I was then able to create the pendrive and successfully boot my netbook and secondary PC from the pendrive with no further issues! Hopefully this helps someone.

---

### Post by jRdbRR on 2011-07-16
Has this issue ever been resolved? I was able to install Ubuntu no problems, but i am currently experiencing this issue w/ BackTrack5 with a live usb (unetbootin and universal usbinstaller), i checked the hash and its all good.  I posted a thread in the Other Distros Forum but got nowhere near the responses seen here.  I also posted on the BackTrack forums but they seem to need to approve posts, and haven't seen mine make the cut as of yet (its been a day.) I have tried it on two different laptops, a Lenovo and a Vaio and both get the same eroror.  The BackTrack splash loads up, but when i get the option of what BackTrack to boot (forensics, etc etc) i get that error...

---

### Post by austinuser on 2011-09-04
> **mörgæs said:**
> Before downloading again you should test the MD5 sum of the ISO. If it is correct, there is no point in a new download.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

A better choice is trying an older release of Ubuntu, preferably an alternate install.

This ended up being the cause of my problem.  I received the 
"can not mount /dev/loop (/cdrom/casper/filesystem.squashfs)" message, searched this forum, say this post, checked the MD5 and it didn't match the hash on 
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

I redownloaded the iso, checked the hash again, burned the CD, and presto it worked.

Seems like there are many causes for this error, and this is just one of them, but an easy one to check.  Hope it helps.

---

### Post by miguel.red on 2011-09-15
My problem is that I am using Windows 7. How do I resolve the issue in Win 7? I want to burn a CD with Ubuntu, done it 3 times in version 11.04 & 10.04 getting the same error in 2 different computers. 
"(initramfs) mount mounting /dev/loop0 on filesystem.squashfs failed: Input/Output error
Cannot mount /dev/loop0 (/cdrom/casper/filesystem.squashfs on // filesystem.squashfs"

---

### Post by mörgæs on 2011-09-15
Hi, welcome to the fora.

If you install Unetbootin in Windows and use it for creating a USB stick, can you then install Ubuntu?

---

### Post by todd422 on 2011-09-19
I am also having trouble with this error, the drive I would like to install Ubuntu on (the only drive connected) is 320Gb.

I recently tried wiping it, though it did fail to finish.
It doesn't show up on 'my computer' anymore.

Please, some advice would be very helpful.

---

### Post by mörgæs on 2011-09-19
I don't think we can add more to your findings. If you suspect hardware errors, best is to download some tools from the harddisk vendor and test it.

---

### Post by todd422 on 2011-09-19
I tried again on 2 other hdds after finding out initial was broken. I've tried the cd/dvd boot, the suggested usb pendrive method and the unetbootin method.  All of which end with this same error. Both 300gb, and 40gb drives are freshly formatted.

---

### Post by mörgæs on 2011-09-20
But do you get this exact error?

"can not mount /dev/loop (/cdrom/casper/filesystem.squashfs) ..."

Else it is best to open a new thread.

---

### Post by Akovia on 2011-10-05
Just chiming in with the same problem and what worked.

MD5 was good but trying to verify MD5 on the burnt CD failed.(Brasero) Not sure if it has something to do with the SATA controller as posted before or not, but using a USB stick worked fine.

If this error is indeed caused by multiple unique scenarios, I would think it would be easier to track down the code and insert a proper "Laymans" error message with maybe some suggestions for a fix. This would considerably cut down on the frustration for a new user and make the whole experience tolerable should something go wrong.

First impressions are everything, and printing out cryptic messages on a console screen would turn off all but the most determined. If Ubuntu has hopes of competing with the big boys, it needs to be on top of an issue like this, if only just a message on how to get further help. I'd be kinda embarrassed if I was trying to convert someone and this happened to them. I really hope this gets the attention it deserves.

Cheers,
Ako

---

