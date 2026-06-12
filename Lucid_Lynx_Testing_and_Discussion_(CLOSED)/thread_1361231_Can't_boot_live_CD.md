---
title: "Can't boot live CD"
date: 2009-12-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Irihapeti on 2009-12-21
I downloaded the alpha 1 live CD image by bittorrent, and updated it to the daily live image of 20 Dec using zsync. I understand that both of these methods include md5sum checking.

Burned the images to CD-RW using brasero (on Hardy), as I've done many times successfully in the past.

Neither CD will boot, nor will either CD allow me to run the CD verification check.

On the 20 Dec CD, if I try to run the verification check, I get the message:
```
Opening pipe: No such file or directory
```
and then everything just stops. I can reboot using ctrl-alt-del (On the alpha 1 CD, it has a blank screen and locks up completely.)

If I try to boot into Lucid from the image of 20 Dec, I get as far as:

```
init: ureadahead-other main process (1050) terminated with status 4
```
followed (sometimes) by a message 
```
udevd (1046) SYSFS{}= will be removed in a future udev version, please use .... 
}= to match the event device, or ATTRS{}= to match a parent device, in /lib .... 
/rules.d/56-hpmud_support.rules:10
```
The .... indicates where some of the message is missing because it extends beyond the edge of the screen.

Then everything locks up completely and I have to power down and up again before I can reboot.

I've attached the output of lshw, in case it's of any use.

Two questions: 1) Does anyone know what I need to do to get this to boot?
2) What package would I file a bug report against? (probably the most important of the two questions)

---

### Post by wilee-nilee on 2009-12-22
I would just download a daily until you get one that works, trying to fix what you have tried already probably isn't going to happen, who knows where the problem is.

---

### Post by Irihapeti on 2010-03-01
Two months later, and I still can't get a Lucid live CD to boot on my desktop computer (no problem on both my laptops). Doing an alternate install only gets me as far as the recovery menu, and then the keyboard locks up.

I've got a bug report open which I update regularly. But I'm starting to get worried. What if this particular bug doesn't get fixed? Do I have to start looking for another distro?

Any ideas for options I can add to the kernel line in Grub? I'm not wanting to give up too easily.

---

### Post by VMC on 2010-03-01
There's problems with the media verification.

 You can check the media this way:

mount the CD/DVD then cd to it and type:

```
md5sum -c md5sum.txt

```

Also have you tried to create a LiveUSB instead?

---

### Post by Irihapeti on 2010-03-01
I just ran the md5sum command on the alternate CD I used to make my latest install attempt. Everything checks out OK.

I've tried a live USB as well, about a week ago, and that didn't do any better.

I've noticed that sometimes - about 50-60% of the time, at a guess - I get problems with my ethernet card. The MAC address gets changed and my router assigns a different IP address. That's a pain because I run a couple of server packages on my LAN. Fortunately, turning the computer off at the wall resets the ethernet card, but obviously there's a problem somewhere.

---

### Post by kansasnoob on 2010-03-02
I would guess that you need to press F6 when the Live CD boots and choose one or more of the following:

acpi=off
noapic
nolapic
edd=on
nodmraid
nomodeset

I'm too tired to go into detail about each but a simple web-search of each should give you an idea. The following link includes some explanation:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by VMC on 2010-03-02
> **Irihapeti said:**
> I just ran the md5sum command on the alternate CD I used to make my latest install attempt. Everything checks out OK.

I've tried a live USB as well, about a week ago, and that didn't do any better.

I've noticed that sometimes - about 50-60% of the time, at a guess - I get problems with my ethernet card. The MAC address gets changed and my router assigns a different IP address. That's a pain because I run a couple of server packages on my LAN. Fortunately, turning the computer off at the wall resets the ethernet card, but obviously there's a problem somewhere.

During install, just after ubiquity finds my time location, I unplug my internet and let it finish installing from cdrom only. Otherwise it takes anther 10 minutes getting updates.

---

### Post by Irihapeti on 2010-03-02
The ethernet problems don't arise when I'm doing an install off the alternate CD, although, as you say, it can sometimes be a bit too enthusiastic about getting updates. It happens when trying out the live CD and also when trying to get a command-line install to boot.

Last evening I tried various kernel options, including one I hadn't tried before - nodmraid. No luck. I followed the link kansasnoob suggested, and some of the links given in that page, and tried some extra options that looked as if they might have been relevant. Still no luck.

---

### Post by crjackson on 2010-03-02
I was having a similar problem.  I downloaded the ISO from Ubuntu's server and burned on different media and slower speed.

Tried it again and it installed without a glitch.  It's running very well here now.

---

### Post by Ibidem on 2010-03-02
@Irihapeti-Try deleting the option "quiet"-- that way, you can see where it freezes.
Then post the last lines it spits out before it dies.
Note that this will give you miles of boot messages.

Ibidem

---

### Post by Irihapeti on 2010-03-02
@Ibidem
Here we are:

```

sd 8:0:0:0: [sdd] Attached SCSI removable disk
aufs 2-standalone.tree-20091207
squashfs: version 4.0 (2009/01/31) Phillip Lougher
init: ureadahead-other main process (1682) terminated with status 4
init: ureadahead-other main process (1683) terminated with status 4
Adding 1044184k swap on /dev/sdc5. Priority:-1 extents:1 across 1044184k

```
To answer some of the other questions, I have checked the md5sum of the liveCD image that I have against the figure posted on cdimage.ubuntu.com, and it matches. I've also tested the live media in one of my laptops, and it boots without any problem.

---

### Post by robert shearer on 2010-03-02
How many drives in that machine ??

> Adding 1044184k swap on /dev/**sdc5**
sd 8:0:0:0: **[sdd]** Attached SCSI removable disk


Presumably you have two Hard drives at sda and sdb ?

Strange that the live disc is trying for swap on sdc then.

---

### Post by Irihapeti on 2010-03-02
> **robert shearer said:**
> How many drives in that machine ??



Presumably you have two Hard drives at sda and sdb ?

Strange that the live disc is trying for swap on sdc then.

Yes, I have three drives in that machine. One SATA drive (the original one with Hardy and the swap partition on it) and two IDE drives that I was given.

The funny thing is that Hardy (mostly) calls the SATA drive /dev/sda. Karmic and Lucid think that it is /dev/sdc. I don't know why this is, but it certainly had me tearing my hair for a while.

Occasionally, Hardy will get confused and decide that the SATA drive is /dev/sdc. I've fixed that by putting UUIDs in Grub menu.lst.

---

### Post by robert shearer on 2010-03-02
I seem to recall a problem booting live cd with mixed ide and sata.

Will go away and cogitate.

Meanwhile, a possible workaround can you unplug the two ide drives leaving only the sata and see if the cd will boot.


Edit:  [http://ubuntuforums.org/showthread.php?t=1297988](http://ubuntuforums.org/showthread.php?t=1297988)
       [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/32357](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/32357)

---

### Post by Irihapeti on 2010-03-03
Well, I tried disconnecting the two IDE drives, and it made no difference. Unless you count the huge fright I got when I discovered that the SATA drive wasn't being recognised by the BIOS after I'd reconnected the other drives. :) Anyway, that's sorted out now (I suppose wriggling the power and SATA connections helped?). 

I also tried booting a 9.10 live CD that I have lying around, and that behaved fine, so I think it's something Lucid-specific.

---

### Post by Ibidem on 2010-03-03
Is one of the IDE drives a CD drive...?
IDE has always been solid, but SATA sometimes won't work.

---

### Post by robert shearer on 2010-03-03
About now I would be disconnecting all drives and moving the cd to master on the first buss then seeing if it will boot.

That would reduce the possible number of component/cable combinations to the minimum.

Given the odd behavior of the bios in recognising drives have you checked the cabling and jumpers ?.
Does seem like a Bios/drives sort of problem and I believe Lucid handles devices differently to previous releases.
Someone with more knowledge here feel free to correct me please :D

I have had problems with drives that are configured as master/slave, only to find they perform fine when set without jumpers in their 'cable select' mode. Just a long shot.

with no drives (other than cd) connected you shouldn't get the o/s looking for swap and certainly not on sdc (that sometimes is sda!!)

---

### Post by Irihapeti on 2010-03-03
Here's the current setup:

1st master: CDROM
2nd master: IDE HDD
2nd slave: IDE HDD

Lucid is the only live CD among my collection that won't boot. I've also got a command-line install of Lucid on /dev/sda6, and it's behaving pretty much the same.

Maybe that's my way of saying that I don't really want to do any more fiddling around inside the box if I can possibly help it. :)

If it would help any, I can post the syslog from the command-line install. It might give a bit more detail.

---

### Post by Irihapeti on 2010-03-05
If anyone's interested, I have posted a syslog from the command-line install of the 5 March alternate CD image here: [http://launchpadlibrarian.net/40250979/syslog.lucid.txt](http://launchpadlibrarian.net/40250979/syslog.lucid.txt)

Whatever it might be calling the drives and partitions, it's finding and mounting the right ones. I would be thinking about blacklisting drivers, if only I had some idea of which ones to try. Any ideas?

---

### Post by VMC on 2010-03-05
> **Irihapeti said:**
> Here's the current setup:

1st master: CDROM
2nd master: IDE HDD
2nd slave: IDE HDD

...
Maybe that's my way of saying that **I don't really want to do any more fiddling around inside the box** if I can possibly help it. :)

If it would help any, I can post the syslog from the command-line install. It might give a bit more detail.
Ok then. but what I would do is unplug both HD's and have just the CDROM drive attached to prove that either Lucid boots or doesn't.

Also you did check the shorting pins that CDROM is either cable-select or master. Don't depend on BIOS info only.

---

### Post by Irihapeti on 2010-03-05
OK, what I disconnected both IDE hard drives and leave just the SATA drive and the CD drive connected. That's how the box was when I first got it.

Lucid live CD doesn't boot. Nor does an alternate install boot properly - the keyboard is frozen. All other live CDs boot, including Karmic, which also calls the SATA drive /dev/sdc.

---

### Post by robert shearer on 2010-03-05
What happens if you disconnect **all** hard drives and only have the cd connected.

Will it boot Lucid cd then ?.

(I suspect also that it would boot with cd and ide drives -no sata, but try the cd by itself first)

---

### Post by Irihapeti on 2010-03-05
> **robert shearer said:**
> What happens if you disconnect **all** hard drives and only have the cd connected.

Will it boot Lucid cd then ?.


No.

It makes absolutely no difference.

---

### Post by robert shearer on 2010-03-05
Strange !.

Have you another cd drive to try.

Seems to be the only other common denominator (apart from Bios, Mobo etc etc etc )

Has to be a hardware glitch as there does not seem to be any other posters with the same problems ???

---

### Post by VMC on 2010-03-05
> **robert shearer said:**
> Strange !.

Have you another cd drive to try.

Seems to be the only other common denominator (apart from Bios, Mobo etc etc etc )

Has to be a hardware glitch as there does not seem to be any other posters with the same problems ???

I was thinking the same thing. The OP first reported this using a December CD.

---

### Post by Irihapeti on 2010-03-05
Sorry, no other CD drives to try.

If previous distros are working with my hardware, then it would seem that something's been done differently in Lucid that isn't working.

If I could find a workaround - maybe it's this Plymouth thing that's the problem, and plenty of people are having boot problems because of that - then maybe I could make some progress. Some have uninstalled Plymouth altogether, but I don't know how you uninstall something when the system won't boot.

---

### Post by ankspo71 on 2010-03-06
Hi,

You are not the only person having trouble with booting into a Lucid aplha3 cd. Do you use an nvidia graphics card? If so the problem might be with the new open source Nouveau drivers that replaced the older open source (nv) ones. I was having trouble booting into a live desktop, but after trying 2 more build versions, the problem went away. 

Here is my bug report, which also seems to effect other people, including someone with an Intel graphics card:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/529563](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/529563)
Here is the thread I posted here about it:
[http://ubuntuforums.org/showthread.php?t=1418101](http://ubuntuforums.org/showthread.php?t=1418101)

Maybe someone will say something in those threads that will help. I don't think it's possible to uninstall something (such as plymouth) from a cd that doesn't at least have a base system running either. My only advice is to keep checking the daily builds iso's to see if the problem gets fixed. I would keep reporting the problem with each daily build so they know if they fix it for you or not too. Good luck.

---

### Post by Irihapeti on 2010-03-06
No, I don't use nVidia. It's an onboard graphics chip (see the "lshw.txt" attachment to an earlier reply). I noticed that someone with very similar hardware had reported a bug with the screen being all distorted - the image, that is, not the actual LCD screen.

I don't use each daily build because I have limited bandwidth. I do report every so often. The bug is 499399, if you want to have a look.

---

### Post by VMC on 2010-03-06
> **Irihapeti said:**
> Sorry, no other CD drives to try.

... I meant to try a newer daily-live and not another cdrom drive. I know you have limited bandwidth but the newest one that I tried has a completely reworked Ubiquity it might be worth upgrading. Try using zsync its faster than a completed download. That's what I use.

---

### Post by ankspo71 on 2010-03-06
In addition to the zsync advice, you can also check the manifests for version changes before downloading to make sure you download something that might make a difference.

Daily Build 06-Mar-2010 includes:
plymouth 0.8.0~-12
plymouth-x11 0.8.0~-12
-
ubiquity 2.1.32
ubiquity-casper 1.224
ubiquity-frontend-gtk 2.1.32

The manifests are found right next to the iso's we download.

---

### Post by Irihapeti on 2010-03-06
@VMC & ankspo71
Thanks for the input. I've actually been using zsync for quite a while and it does save on bandwidth. I think the problem has been because I've been trying the alternate as well as the live CD = double the downloads.

The latest changes look like they might do something useful. I might just take a look.

I like what I see of Lucid on my two laptops (EeePC 900 and ancient Toshiba Satellite A10). It's just the desktop that won't play.

---

### Post by Irihapeti on 2010-03-06
No luck with the image of 6 March. It does the same thing.

---

### Post by robert shearer on 2010-03-06
From your lshw.txt

>  *-display **UNCLAIMED**
                description: VGA compatible controller
                product: CN896/VN896/P4M900 [Chrome 9 HC]
                vendor:** VIA Technologies**, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: latency=32 mingnt=2
                resources: memory:d8000000-dbffffff(prefetchable) memory:dd000000-ddffffff memory:de000000-de00ffff(prefetchable)

I believe that linux has problems with Via graphics.Support is poor and perhaps someone can comment if this works with Lucid for them.

---

### Post by Irihapeti on 2010-03-07
If by "poor support" you mean that the onboard VIA chip doesn't support 3D, compiz and so on, then I'd agree. I have to use the Vesa driver, but as I'm not into compiz and games, that doesn't bother me.

But in terms of totally refusing to function at all, this is the first time that's happened in over 2 1/2 years of playing with Linux, and I've tried a few distros in that time.

---

### Post by Ibidem on 2010-03-07
I recall that someone else in this forum had trouble with Via graphics (Lucid "killed" the board).

---

### Post by KrazyPenguin on 2010-03-07
Is this a regression?? Does karmic work??

Maybe install karmic and do a dist-upgrade??

(edit: sorry your interested in the livecd only-- ok can't help there)

---

### Post by Irihapeti on 2010-03-07
> **KrazyPenguin said:**
> Is this a regression?? Does karmic work??

Maybe install karmic and do a dist-upgrade??

(edit: sorry your interested in the livecd only-- ok can't help there)

Yes, Karmic does work. The graphics are fine, within the limitations I noted in my last reply. 

My main concern is getting a working Lucid install on this PC. I'm quite happy to use the alternate installer. In fact, I've done so. The trouble is that it doesn't work any better. The boot process freezes at the same point. I could try a dist-upgrade, but I think I'd be up against the same thing.

---

### Post by KrazyPenguin on 2010-03-07
> **Irihapeti said:**
> Yes, Karmic does work. The graphics are fine, within the limitations I noted in my last reply. 

My main concern is getting a working Lucid install on this PC. I'm quite happy to use the alternate installer. In fact, I've done so. The trouble is that it doesn't work any better. The boot process freezes at the same point. I could try a dist-upgrade, but I think I'd be up against the same thing.

Not sure but if your settings work from karmic and you keep the same settings, then it might work.

Then it could be a regression in the kernel as well.

Isn't using Karmic an option, or are you just curious to try lucid??
Anyway, hopefully this bug is worked out before the final.
gl
;-)

---

### Post by daetsy on 2010-03-07
I had the same problem, black screen then nada. The dist upgrade from Karmic worked for me, so maybe you should give it a try. The only problem for you is that it downloads about 700Mb of files.

---

### Post by Irihapeti on 2010-03-07
@KrazyPenguin
The thing about Lucid is that it's the LTS release. My idea was to go from LTS to LTS. I currently use Hardy as my main system, but I test all sorts of other stuff. (Hence the extra drives and partitions :) )

@daetsy
You can also dist-upgrade from an alternate CD, and as I already have a recent one lying around, I can save myself some bandwidth. I just might try it...

---

### Post by Irihapeti on 2010-03-07
Well, I've learned something from doing the dist-upgrade.

It still doesn't work. It still gets to the same old place and locks up.

BUT, just on the off-chance, I thought I'd try booting into the Karmic kernel which was still there....

AND IT BOOTS!! I'm posting from it right now.

Whoever suggested it might be a regression in the kernel was onto something, it seems.

Many thanks.

---

### Post by Irihapeti on 2010-03-16
I still can't get the live CD to boot, or a hard disk install with the Lucid kernels to boot either. Only Lucid install with Karmic kernel will boot, which isn't quite what's supposed to happen.

---

### Post by Nyoro on 2010-03-17
I had trouble booting the live CD too. I tried booting without the quiet and splash kernel parameters and noticed a lot of messages about being able to access fd0 in the kernel messages. So I disabled the floppy drive in my bios, and this solved the problem for me.

Unfortunately, after installing the system, I now consistently get a black screen after the boot splash screen, and I am unable to access the terminals on ctrl-alt-f1/2/3/4. This is probably an unrelated problem though.

So, you might try disabling your floppy drive in your bios and see if that helps.

---

### Post by Irihapeti on 2010-03-17
Thanks for the suggestion. However, floppy drive is already disabled in the BIOS.

---

### Post by qwerty2009 on 2010-03-17
im having the exact same problem, i want to start testing i know its not my .iso or cd as ive downloaded and burned plenty of times now. 

the live cd starts shows the ubuntu logo then asks what language, then i click try... shows the blinking " - " for bout 2 seconds and screen goes black but disc continues to load. 

why isnt this bug fixed yet its been months now since its been confirmed and im not using nvidia

---

### Post by qwerty2009 on 2010-03-17
filled a bug report [https://bugs.launchpad.net/ubuntu/+bug/540100](https://bugs.launchpad.net/ubuntu/+bug/540100)

couldnt file it in the lucid section so doubt it'll even get seen tho.

@ Irihapeti : if you test out beta 1 could you please come back to this thread to say whether or not the live cd works?

---

### Post by Irihapeti on 2010-03-19
I have tested the beta 1 release and

I still can't boot the live CD.

I have an install on the hard drive. I can boot it if I use the Karmic kernel, but it freezes at the same place if I try to use the Lucid kernel.

Is that what they call a regression?

---

### Post by Irihapeti on 2010-04-08
Beta2 liveCD doesn't work. There are a couple of error messages I haven't seen before (noted in the bug report) but the end result is the same.

---

### Post by robert shearer on 2010-04-12
> **Irihapeti said:**
> Beta2 liveCD doesn't work. There are a couple of error messages I haven't seen before (noted in the bug report) but the end result is the same.

Yes, I too had boot problems with the beta2 cd.
"soft lock-up cpu1 after 61 seconds" repeating.

Eventually under other options I checked 'no modeset' **and** 'no dmraid' and it booted fine from there-on.

Once booted I was able to install and the errors are not present booting from hard disk.

---

### Post by Irihapeti on 2010-04-12
> **robert shearer said:**
> Yes, I too had boot problems with the beta2 cd.
"soft lock-up cpu1 after 61 seconds" repeating.

Eventually under other options I checked 'no modeset' **and** 'no dmraid' and it booted fine from there-on.

Once booted I was able to install and the errors are not present booting from hard disk.

I tried those options and unfortunately they didn't make any difference.

The good news is that someone else had the same problem during ISO testing and reported it as a bug. One of the devs is now involved in that, so here's hoping.

---

### Post by Irihapeti on 2010-04-13
I've found a workaround for the hard-drive install, though not for the live CD.

I added "blacklist viafb" to /etc/modprobe.d/blacklist.conf

It *finally* boots with the Lucid kernel.

---

### Post by Irihapeti on 2010-04-14
For the live CD, adding "viafb.modeset=0" to the boot command works. I also remove "quiet splash" - not sure how necessary that is, though.

---

### Post by tea for one on 2010-04-14
> **Irihapeti said:**
> I've found a workaround for the hard-drive install, though not for the live CD.

I added "blacklist viafb" to /etc/modprobe.d/blacklist.conf

It *finally* boots with the Lucid kernel.

Good morning

I am very grateful to you for finding this solution. I have a 4 year old laptop with a VIA graphic component and your solution helped immensely. Previously I was struggling with the black screen.

I did notice that there is also a file "blacklistfb.conf" within modprobe.d; should the "viafb" be added to that file?

I suspect that your solution will help many users with 3/4 year old laptops contaning VIA graphics. 

Once again, many thanks

---

### Post by Irihapeti on 2010-04-14
> **tea for one said:**
> Good morning

I am very grateful to you for finding this solution. I have a 4 year old laptop with a VIA graphic component and your solution helped immensely. Previously I was struggling with the black screen.

I did notice that there is also a file "blacklistfb.conf" within modprobe.d; should the "viafb" be added to that file?

I suspect that your solution will help many users with 3/4 year old laptops contaning VIA graphics. 

Once again, many thanks

Nothing needs to be done to "blacklistfb.conf"

It looks like a fix has been released. If you have the latest module-init-tools, then it should work without the entry in "blacklist.conf"

I'll be testing the live CD in a day or so.

It wasn't actually my solution. Someone else found it. I have been looking at all the bugs I can find with P4M900 or similar chip with Chrome graphics, which is how I happened across it.

Anyway, I'm pleased I don't have to switch distros.

---

### Post by Irihapeti on 2010-04-14
Live CD of 14 April boots to desktop. No command-line editing needed.

I think we can mark this as *really* solved. :) :) :)

---

### Post by digitalbrain on 2010-04-14
> **Irihapeti said:**
> Live CD of 14 April boots to desktop. No command-line editing needed.

I think we can mark this as *really* solved. :) :) :)

Could you please give the download link?

---

### Post by Irihapeti on 2010-04-14
> **digitalbrain said:**
> Could you please give the download link?

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Then choose i386 or amd64 version. I've been using i386.

---

### Post by tea for one on 2010-04-14
> **Irihapeti said:**
> Live CD of 14 April boots to desktop. No command-line editing needed.

I think we can mark this as *really* solved. :) :) :)

Good evening

I have also tested the Ubuntu Daily build of 14 April via a USB device without persistence.

The Live OS booted (without adding further instruction to the boot command) into the Gnome desktop and both sound and wired broadband were fine.

I installed Ubuntu onto a spare drive and I can report that sound and wired internet are OK.

My 3 year old HP Deskjet F380 was detected automatically (via System > Administration > Printing).

I am now going to add Ubuntu Restricted Extras and some other applications to continue with the tests.

Marking this thread as solved for users with VIA graphic components seems
a good idea.

Best wishes

---

