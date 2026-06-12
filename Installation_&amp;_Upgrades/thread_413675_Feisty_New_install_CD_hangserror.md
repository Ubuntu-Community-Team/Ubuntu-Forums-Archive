---
title: "Feisty New install CD hangs/error"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by cogadh on 2007-04-19
I have tried two different burns of the Feisty  install CD and tried booting with the "acpi=off" option that I have seen suggested on the boards, but I still get this same message:

```
Busy Box v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh: can't access tty: Job control turned off
(initramfs)
[    67.38093] ata2.00: revalidation failed (errno=-5)
[   88.954882] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   88.954938] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 data 36 in
[  118.516337] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  118.516393] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 data 36 in
[  146.958352] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  146.958407] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 data 36 in
```

The system will only respond to CTRL-ALT-DEL and does the same exact thing on reboot. Anyone have any ideas?

System specs:
Intel P4 2.0 GHz
1 GB PC 2100 RAM (2 x 512)
120 GB PATA primary drive
100 GB PATA secondary drive
GeForce FX 5200 256MB video
SB Audigy LS sound
Intel D865PERC mobo w/ latest BIOS
Samsung Lightscribe CD/DVD writer
Plain 32x CD-ROM drive

---

### Post by chakkaradeep on 2007-04-19
What was the speed that you burnt the Images ?

---

### Post by cogadh on 2007-04-19
I honestly don't know. I burned the images in Windows using ImgBurn and allowed the application to determine the burn speed. I have used this method successfully dozens of times now to burn Ubuntu and other Linux ISOs, so I don't see how that could be a problem, but I am open to any suggestions.

On a side note, I tried running the install again and I'm not sure this is relevant, but a very strange thing happened. The same errors occurred, except after a few minutes, my CD/DVD burner drive (the one I was booting from) began to spin at an insanely high speed. I tried again booting from the plain 32x CD drive and it started to do the same thing (though its top speed is significantly lower than the CD/DVD drive). It didn't make any sense, since the install had already failed, there was no reason for the drives to spin up like that.

---

### Post by lakersforce on 2007-04-19
This happens to me too. It also happened when I had the Beta installed and I reported it. Im sorry to see that they have not fixed it.

---

### Post by cogadh on 2007-04-19
You were never able to get past it in the beta?

---

### Post by Falconix on 2007-04-19
I have the same problem,
 
my specs is Dell dimmension 8200 
processor: Intel Pentium 4 2.2 Ghz
RAM: 512 MB
HDD: 40 GB

when i boot from the Ubuntu CD it's seems like it trying to read the floppy.

---

### Post by chakkaradeep on 2007-04-19
> **cogadh said:**
> I honestly don't know. I burned the images in Windows using ImgBurn and allowed the application to determine the burn speed. I have used this method successfully dozens of times now to burn Ubuntu and other Linux ISOs, so I don't see how that could be a problem, but I am open to any suggestions.

On a side note, I tried running the install again and I'm not sure this is relevant, but a very strange thing happened. The same errors occurred, except after a few minutes, my CD/DVD burner drive (the one I was booting from) began to spin at an insanely high speed. I tried again booting from the plain 32x CD drive and it started to do the same thing (though its top speed is significantly lower than the CD/DVD drive). It didn't make any sense, since the install had already failed, there was no reason for the drives to spin up like that.

I doubt its becoz of the Images burnt at high speed. 

Please check for Options or Burn Speed in the Software you use. If you find the burn speed option, choose 10x or 12x and burn the CD. This should normally work.

---

### Post by lakersforce on 2007-04-19
nope. I searched the forums for a solution and when I could not come up with one I re-installed 6.10

EDIT: It happened after on of the usual updates. And it was rather late in the Beta stage.

---

### Post by cogadh on 2007-04-19
Well, one extremely sloooowww burn later and... no joy. :(

The same errors occur and the same weird drive acceleration occurred. Any other suggestions?

---

### Post by viciouslime on 2007-04-19
> **cogadh said:**
> Well, one extremely sloooowww burn later and... no joy. :(

The same errors occur and the same weird drive acceleration occurred. Any other suggestions?

Have you checked the md5sum of your iso? It could've been corrupted during download...

---

### Post by cogadh on 2007-04-19
I thought of that and since I got the download through Bitorrent, I figured that was pretty likely, but... no joy. :(

The MD5s check out fine. However, just for giggles, I'm still downloading a second copy to try out.

---

### Post by cogadh on 2007-04-19
Well, after another long download, slow burn and a reboot, the same error happens. That's 4 CDs burned from two different images (both of which pass the MD5 check), downloaded from two different sources (one http the other Bitorrent), and none of them work.

I think its safe to say this isn't a problem with the CDs themselves, but is more likely a compatibility problem with either my CD drives or the IDE controller. The IDE controller seems more likely, since both CD drives behave the same way despite the fact that one is a shiny new Lightscribe drive and the other is a generic old 32X drive.

If anyone has any brilliant insight into this problem, I would appreciate the help greatly.

EDIT - Just to be certain of the CDs, I have tried them on another computer and they do work fine on that one.

---

### Post by crouton on 2007-04-19
If you're the adventurous type, try setting your BIOS to its defaults (including PnP OS settings) and try the install again.  If that fails, change the PnP OS setting.

I had a similar issue with 6.10 that resolved itself when I changed the PnP OS setting.

---

### Post by cogadh on 2007-04-19
Great minds think alike! I already tried that, unfortunately... still no joy. :(

Just out of curiousity, what PnP setting worked for you? It might be a good starting point for me to further troubleshoot this.

I'm trying to download the alternate install CD now, to see if that is more successfull.

---

### Post by eyelessfade on 2007-04-19
> What was the speed that you burnt the Images ?

It has nothing to do with with the cd. This is a known problem with the last kernels. I have the same problem from hd, and I have used feisty since flight 3. Now I only get problem with boot every 10th boot or so.. Improvement but stil...

And yes its sad that its not been fixed.

---

### Post by cogadh on 2007-04-19
Well that's not good news.

I also found some references to changes in the way the new kernel handles SATA/PATA drives, which would seem to be directly related to my problem. I also realized that my mobo has both SATA and IDE controllers, but only IDE drives, so I tried disabling the SATA controller in BIOS (I don't need it anyway), but that made no difference.

I can't imagine that my system is so unique that this only affects me and a small portion of other Ubuntu users. Looks like I'll be waiting for the next version to come out. Hopefully they will fix this by then.

---

### Post by eyelessfade on 2007-04-19
the kernel.org people have been working on this for a while. I thought it was fixed. The problem is that its a small portion of people testing the ubuntu beta releases so not all bugs get fixed. I hope a lot of "missed" bugs will be fixed in the nearest future.

---

### Post by danielph on 2007-04-19
Just wanted to add that I just ran into this trying to install on a standard Dell 8500 laptop. I checked the md5 and did a verify on the burn and tried a slower burn rate just in case, but it still fails. This was Feisty final (downloaded on a torrent) [SIZE=-1]ubuntu-7.04-desktop-i386.iso[/SIZE]

---

### Post by cogadh on 2007-04-19
How's this for a kick in the pants:

The alternate install CD? Useless, has the same problem as the regular install CD. So I switch to my P3 500 MHz, 192MB RAM, 8GB HDD, 8MB S3 Savage PRO, generic sound system and try installing Xubuntu Feisty...

IT WORKED! My crappy, *really old*, made out of spare parts machine can install Feisty with no problems, but my much better, only about four years old primary machine can't even load the kernel! It's not like my primary system is even near top of the line, bleeding edge technology. If it was, I would understand problems with the IDE controller, but *come on*, I have the Intel 865 chipset for cryin' out loud! It don't get much more basic than that.

---

### Post by lopzided on 2007-04-19
having the same problem on my HP Pavillion 9900.

it's not a problem with the cd (or in this case, dvd).

it installed PERFECTLY from the same CD on my HP workstation xw4000.  both are p4 2gigs, both have 512mb ram.

just incase though, i burned another cd....checked the md5 sum, as well as burning it at 4x.  no dice.

this happens to me when trying to boot the livecd...thank god i didn't do an upgrade!

---

### Post by cogadh on 2007-04-19
> **lopzided said:**
> thank god i didn't do an upgrade!

Amen brother!=D>

---

### Post by lopzided on 2007-04-19
a few side notes:

1. the whole time the loading bar is showing (right before it crashes to BusyBox), my floppy drive is crunching away like it's trying to read a disk.  there is not a disk in the drive.

2. i spoke to someone in IRC that said he had a similar problem, and fixed it by messing around with GRUB settings...but he couldn't remember exactly what it was.  i personally have no experience messing around in grub....he thinks it had something to do with the locations of your hard drives?  can someone help out on this one?

if anyone has any ideas, i'm surely willing to try them...i've been counting down the days till i could use feisty (i always wait for final release), and now i can't use it!  :(

---

### Post by Kleist on 2007-04-19
This is my experience so far:

I've been running ubuntu 6.10 for a while, very happy with it. Then, when the beta release of ubuntu 7.04 came out I was very anger to try it. So I downloaded and booted the live cd. Then, the problems started. 

I got this message that other have described:

****/bin/sh can't access tty; job control turned off**** etc...

and took an eternity to do anything so a booted again the cd in safe graphics mode, and even through I got a lot of errors I could got the live desktop. 

I tried to make a clean  install from there, and apparently everything worked fine. Even the installation imported my windows settings to ubuntu. Since, I didn't like the default screen resolution I tried to 1024x768 pixels and...everything frozen. I booted the computer and alas! I got this error that the grub was corrupted!

I'm not an computer expert, so I just booted a knoppix cd and backup my data and...installed everything again just as before.

Now, with the final release I got the same error when I tried to boot the live cd...and of course I didn't even tried to install Feisy Fawn. 

So, I guess I'll wait a while to see what's going on. My experience with ubuntu has been so far very satisfactory, and I hope you guys will solve this soon.

:)

---

### Post by goatflyer on 2007-04-19
Well, I just downloaded the Feisty x86 desktop cd and I get the same problem on both of my computers!

(live cd drops into busybox and spits out:)
/bin/sh can't access tty; job control turned off
then after about 30 seconds:
ata 2.00 failed to set xfermode (err_mode=0x4)


Both machines can boot Breezy and Dapper live cds no problem,  One machine IS my main Ubuntu Dapper box, the other is a garden-variety e-Machines CeleronD with 1GB ram running windows xp.  I tried all the boot options suggested on the Feisty CD, nothing seems to help.

What are the odds of there being a feisty 7.04.01 coming out soon?

.

---

### Post by Rhawi Dantas on 2007-04-20
Yeah, I had the same problem with a Dell Inspiron 9400 in Ubuntu Feisty.

Previously I had, ALMOST, the same problem with 6.10, the only thing I did was disabling Wi-Fi in my BIOS.
So I could have a laptop with ubuntu but without internet... how great is that ?!? \\:D/

But anyway, I tried, this time with feisty, desktop-i386...

Also heard the same thing about sata-pata problem from a friend from work... but he was complaining about debian

Did you guys remember the good ol' days of 5.10 ? Ething was smoother :P

Anyway, remember to post here people if u get any results...

See ya and good luck for us

---

### Post by revelation.now on 2007-04-20
I've been experiencing exactly the same problems listed above. I am getting the ata error upon first boot and during the installation everything seems to lock up after the update manager core. It eventually resumes but doesn't seem to install gnome so when it finally boots I get bash. Ejecting the CD drive seems to help boot along.

Is installing a fresh copy of 6.10 and upgrading likely to replicate this problem? Sorry, I didn't see this explicitly mentioned above. If it just means a delay on boot because my CD/floppy drive are connected thats not a problem, but if everything else runs unaffected including the update I'm not that concerned

---

### Post by sundowndk on 2007-04-20
I got the same error when trying the LiveCD. I then decided to upgrade my 6.10 by using the update manager. 

The upgrade went smooth, and besides Grub detecting my harddrives wrong (hd1,0 should be hd0,0), everything works perfectly. I havent experienced the tty error at all, yet :)

---

### Post by Alacrity on 2007-04-20
ME2!

Tried all the Feisty Betas, Feisty final, Feisty alternate, and finally Xbuntu.  Checked all M5sums.  Burned a lot of CDs for Pete's sake.

Same TTY error everytime on my Sony PCG-FX340 laptop. Just when I was really getting to like Ubuntu from the 6.10 version.  And, I was anxiously awaiting the new 2.6.20 wireless Linux native drivers (zd1211 and others).

So, is it the 2.6.20 kernel?

I would love to hear from the Ubuntu staff on this one.

Please.

---

### Post by Falconix on 2007-04-20
I don't have any clue of why this error appear.
The live CD don't work on my Dell Dimension 8200, i get the tty error.
On my Dell Inspirion 9200 it's working well no problems at all.

So i installed Ubuntu Edgy Eft (6.10) on the Dimension machine, and then upgraded to Feisty Fawn with out any problems, Feisty Fawn booting up just fine.

---

### Post by ajifans on 2007-04-20
> **viciouslime said:**
> Have you checked the md5sum of your iso? It could've been corrupted during download...

Same problems with me.  I'd checked the md5sum of the iso, and burnt at a slow speed.  Looks like an Ubuntu bug that hasn't been fixed since beta. :mad:

---

### Post by CheeseEatingBulldog on 2007-04-20
I just installed feisty and this is happening to me too, if I just wait it will eventually time out on the third try and boot, but is there anyway of telling the system to stop looking for sata drives, cause I have none.

---

### Post by cogadh on 2007-04-20
You are getting the same error message and it was still able to boot and install? When I get the error message, the system just gives up and never boots.

---

### Post by cogadh on 2007-04-20
Just to keep all of my troubleshooting steps in one thread, I have continued to try the following, all with no success:

1. Physically disconnect floppy and second CD drive to prevent detection, still produces same error (as well as few more)
2. Run install with a read-only disk in the floppy drive, new errors at first, but the same one in the end.
3. Completely remove previous installation of Edgy and restore MBR to get rid of GRUB, same error
4. Disable floppy and extra CD drive in BIOS, same error (but no extra ones like the physical disconnect)

I'm always willing to try anything else, if anyone has any more ideas.

---

### Post by cogadh on 2007-04-20
Another interesting tidbit:

I re-ran the install, this time without the quiet splash enabled and found that the tty error seems to be due a timeout that occurs while the kernel wastes a ton of time trying to talk to SATA drives that are not present. This is despite the fact that I have disabled SATA in my BIOS. Even after the tty error occurs, the system continues to try and communicate with my drives until it finally realizes they are not SATA and finally mounts them as SCSI (which they also are not, but I understand this is how the new kernel does IDE). It then immediately detects my CD drives and loads a generic CD driver, but it is too late, the install has already timed out.

Now, technically, the system is a functional terminal at this point. You can run terminal commands and such and there is a file system present, but I don't know what script/command to run to get the install running again. Anyone have any ideas on that?

---

### Post by akniss on 2007-04-20
Another thread with some users having the same problem:
[http://ubuntuforums.org/showthread.php?t=415041](http://ubuntuforums.org/showthread.php?t=415041)

---

### Post by lopzided on 2007-04-20
well, installing the alternative cd worked for me...

now i get to start a new thread : bootup is PAINFULLY slow....and if i switch to tty1 while its at the loading bar (which is where it stays for FOREVER), i get multiple instances of messages like this :

ata2.00: failed to set xfermode (err_mask=0x4)

it does, however, after three or four minutes, return to the normal boot, where everything seems to work fine.

EDIT::  if you&#341;e having the same problem AFTER an install, and you can somehow successfully get to a command prompt, check this out, it might help : (copied/pasted from another thread)

edit the networking boot file
Code:

sudo kedit /etc/rcS.d/S40networking

(if you got no kedit use gedit or something)

now, put "##" in your code as follow:
(or simply overwrite your code with those lines respectively)
Code:

case "$1" in
start)
	log_action_begin_msg "Configuring network interfaces"
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 120" || true
##	if [ "$VERBOSE" != no ]; then
##	    if ifup -a; then
##		log_action_end_msg $?
##	    else
##		log_action_end_msg $?
##	    fi
##	else
##	    if ifup -a >/dev/null 2>&1; then
		log_action_end_msg $?
##	    else
##		log_action_end_msg $?
##	    fi
##	fi
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 15" || true
	;;

stop)

the result: no pausing or stucking during bootup, and the network device still works as usual..

---

### Post by strikeback03 on 2007-04-20
I appear to be having the same error, when trying to run the LiveCD I get this:

[IMG]http://img.photobucket.com/albums/v315/strikeback03/installerror.jpg[/IMG]


I have a more or less functional Edgy installation, would I be better off trying to upgrade through the System Updater?

This is on a P965 motherboard with a C2D E6600 and 2GB RAM.  and I have all SATA drives, no IDE or floppy.

---

### Post by words1 on 2007-04-21
Looks just like what I get with two SATA drives.  This is a major problem.

---

### Post by MacD on 2007-04-21
Same problem on Dell Dimension 4600 which currently runs Edgy upgrade from Dapper Just Fine.
I did swap out the OEM DVD player with a DVD burner since that last Ununtu install.?

Media boots fine on another machine (acer aspire 3620).

Alternate install CD did not work either on the Dell.

I was hoping for a clean install to reclaim windows disk space and clean up some broken packages.

---

### Post by anjulraval on 2007-04-21
in my case, MD5 is correct, CD burning speed is 8X.. - though not able to install ... 

system hangs during installation have to reboot to exit;
few operations are shown failed during installation (i suppose its because of CD error);

im installing ubuntu 7.04 on acer tm4000, vista already installed, 512 RAM , 1.6 GHZ.


any suggestion ???

---

### Post by chakkaradeep on 2007-04-21
After going thru several complaints, I see that the problem is with the ATA drivers and SATA disk whereas the compaints with using the ATA drivers with IDE is less.

Have anybody in this thread filed this with launchpad ?? If not , please do ASAP

---

### Post by adam0509 on 2007-04-21
same here :

[http://ubuntuforums.org/showthread.php?p=2498385](http://ubuntuforums.org/showthread.php?p=2498385)


For me, it comes from my CD Drive

---

### Post by ilobmirt on 2007-04-21
I am also one of those people who can't get a clue of why the the latest version of Ubuntu is inoperable through the live-cd. I've been upgrading my computer through a clean install via live-cds since breezy without a problem. Here is how my experience went...

1. Download an iso off the web via, web browser.
2. burn the iso to a cd-rw using k3b
3. reboot computer.
4. choose the first option and....
5. see the computer stop at "loading" :P

for #4 I've also tried the safe option and the check cd for defects option. (both end up at #5)

Things I've done to make sure I wansn't "seeing things":

[LIST=1]
[*]Had k3b check the cd for defects. (it returned an error for every cd I threw at it)
[*]Created a new virtual machine via, vmware. Using the real cd reproduced steps 3-5. Running the iso ran PERFECTLY!!! 
[*]checked the md5 sum of the iso. (results were successful. md5 did match its suggested value)
[*]Used the default cd burner application that came with ubuntu. no dice :(
[/LIST]

It does seem suggestive that it may be somewhere in the process of writing the iso to the cd-rw. However, I do doubt it since I threw all 25 of my new cd-rws at it. They were new for Christ sake!

I probably would like to understand more about the iso files I've downloaded from one of the available mirrors. I'd then use those settings with my burning app and see if I go anywhere with this.

---

### Post by CheeseEatingBulldog on 2007-04-21
> **lopzided said:**
> well, installing the alternative cd worked for me...

now i get to start a new thread : bootup is PAINFULLY slow....and if i switch to tty1 while its at the loading bar (which is where it stays for FOREVER), i get multiple instances of messages like this :

ata2.00: failed to set xfermode (err_mask=0x4)

it does, however, after three or four minutes, return to the normal boot, where everything seems to work fine.

EDIT::  if you&#341;e having the same problem AFTER an install, and you can somehow successfully get to a command prompt, check this out, it might help : (copied/pasted from another thread)

edit the networking boot file
Code:

sudo kedit /etc/rcS.d/S40networking

(if you got no kedit use gedit or something)

now, put "##" in your code as follow:
(or simply overwrite your code with those lines respectively)
Code:

case "$1" in
start)
	log_action_begin_msg "Configuring network interfaces"
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 120" || true
##	if [ "$VERBOSE" != no ]; then
##	    if ifup -a; then
##		log_action_end_msg $?
##	    else
##		log_action_end_msg $?
##	    fi
##	else
##	    if ifup -a >/dev/null 2>&1; then
		log_action_end_msg $?
##	    else
##		log_action_end_msg $?
##	    fi
##	fi
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 15" || true
	;;

stop)

the result: no pausing or stucking during bootup, and the network device still works as usual..

That did absolutely nothing for me, still times out 5 times before continuing boot.

---

### Post by revoltism on 2007-04-21
I got it working when i swapped to my dvd-rw drive. 

I changed bios cd-rom priority from my dvd to my dvd-rw and booted the feisty cd in my dvd-rw and it worked.


it seams like some dvd-rom's aren't working right. I'll guess they make a fix pretty soon.

---

### Post by crouton on 2007-04-21
Just as an update, I'm doing this on a P3-733 with *no* SATA/SCSI at all.  It's still 'detecting' sda and sdb devices which makes no sense to me at all.

2nd update: Just found out that the 2.6.20 kernel that 7.04 comes with assumes all ide/scsi/sata is under its scsi subsystem, which would explain the use of sda/sdb/etc for standard IDE devices.

3rd update: Replacing the old standard CDROM with a CD-RW appears to have solved the error loop problem for me.

---

### Post by cogadh on 2007-04-21
> **chakkaradeep said:**
> After going thru several complaints, I see that the problem is with the ATA drivers and SATA disk whereas the compaints with using the ATA drivers with IDE is less.

Have anybody in this thread filed this with launchpad ?? If not , please do ASAP

Apparently, this problem was filed with Launchpad during the beta, but it was not fixed prior to release. From what I have read here and elsewhere, this is a known problem with the current kernel, which means there is really not much that the Ubuntu people can do about it until it is fixed in the official kernel release.

Oh, and the problem is not restricted to SATA disks. My system is completely IDE, though it is SATA capable. I have disabled SATA in the BIOS, yet the problem still occurs while detecting the drives. Even if I re-enable SATA in the BIOS, it is a problem.

---

### Post by cogadh on 2007-04-21
SUCCESS!!

Well, sort of. I was looking through the multitude of posts with this particular problem and realized that the vast majority of people experiencing this issue are having when trying to do a clean install. So I thought "Why not try installing Edgy and do an upgrade to Feisty?" So I did just that. Several hours later, I rebooted the new Feisty system and...

ARRRRGH! That same damned tty error!

However, this time I happened to have my computer case open when it happened (I had been experimenting with disabling extra drives). I noticed that the drive that spun up to full speed this time was not my shiny new Lightscribe drive as I previously thought, but was in fact my old standard CD-ROM drive. I only use that drive for testing so I tried disabling it. Up till now I had been using that drive to run my installs and had been disabling the Lightscribe drive. I figured the CD-ROM drive is old and more likely to be supported fully by Ubuntu. However, after disabling it and rebooting...

Lo and Behold, there was Ubuntu! And there was much rejoicing! \\:D/ 

However, the fact that I couldn't do a clean install was still bugging me so I tried running the Feisty install disk from the Lightscribe drive with the old CD-ROM drive disabled. 

HA! It works!

So my conclusion is that while the problem is still related to the known kernel issues with IDE, it is more likely a combination of those issues with particular hardware. The CD-ROM drive I have is so generic it doesn't even have a brand name on it, but Windows detects it as "LG CD-ROM CRD-8320B" If you have one of these drives, I recommend looking at that as the cause of the problem first.

---

### Post by revoltism on 2007-04-21
I was looking in to it and notised the IDE-Configuration tab in bios after i changed from AHCI to Standard IDE everything work fine. No slow boot and no problem with dvd-rom.

---

### Post by lopzided on 2007-04-21
> **CheeseEatingBulldog said:**
> That did absolutely nothing for me, still times out 5 times before continuing boot.

same here....i posted it after i saw it worked for someone else...but it didn´t work for me either :(

so rebooting is hella slow...but at least the install works (using alternative cd)

---

### Post by Kleist on 2007-04-21
This worked for me:

I downloaded the alternate Cd and upgrade within ubuntu 6.10. It took a long time to do the upgrade, almost 70 minutes, but I didn't have any problem. 

Now, I have ubuntu 7.04 running and I don't see any problem, except that the boot time has increased notably. It takes almost two minutes, but besides that I notice the programs running faster and of course, the desktop looks great. 

I will wait a while before trying a clean install. I don't want to mess around with the hardware and cables inside the computer. 

But of course it bothers that a clean install brings all these problems.

---

### Post by strikeback03 on 2007-04-21
I have a Lite-On SATA DVD burner, not an LG.

---

### Post by lopzided on 2007-04-22
> **revoltism said:**
> I was looking in to it and notised the IDE-Configuration tab in bios after i changed from AHCI to Standard IDE everything work fine. No slow boot and no problem with dvd-rom.

i searched my BIOS for something like this setting and couldn't find anything like it...

however, i DID notice that the configuration for my default video card was set to PCI, and mine's AGP.  i changed it to AGP, and no more slow boot.

---

### Post by BetterLateThanNever on 2007-04-24
Hmm..I had this problem too (dropping out to BusyBox shell etc etc)

Try adding all_generic_ide to the boot command line after starting the install cd i.e. boot the cd, at the install menu press F6 and add <code>all_generic_ide</code> (before the double hyphens). 

Works for me.

---

### Post by BetterLateThanNever on 2007-04-24
Don't forget to add it to your grub boot also (which I did first time!) :D

---

### Post by owerio on 2007-04-24
Samsung  SATA HD080HJ and NEC 3540 DVDRW user. Same problem. Can install neither Dapper nor Fesity. Edgy installs with no problem. Even upgrading with alternate cd on Edgy didnt help. Upgrade process work but after next boot it freezes with the new kernel. I can just log into system with the default Edgy kernel in safe graphic mode. In short, bye to Ubuntu till 7.10 ...

---

### Post by Arjan Kon on 2007-04-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107417](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107417) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Adding all_generic_ide to the boot options let me boot the live cd, but now i don't have a /dev/hda or /dev/sda (and thus unable to install...)

---

### Post by harmlessdrudge on 2007-04-25
I am also experiencing a completely hung computer when attempting to install Ubuntu 7.04. 

The PC is a Compaq Presario 700 laptop which previously ran Edgy, but without the wireless card being recognized: a Belkin 54g. I thought I'd wait for Feisty; it's a spare machine. Now I can't even install.
 
Mint Linux 2.2, a derivative of Ubuntu, installs without a problem. However, the wireless card is also not recognized, nor is a USB mouse.

I am still new to Linux and I find that many of the references to solutions here depend on existing knowledge (just update GRUB is not helpful if you don't what GRUB is). I would like to see a step by step solution if there is one. A YouTube video wouldn't hurt either if this is a common problem.

I tried the alternate distribution. That didn't solve the problem. If there is a fix I'm not clear on how long it will be before Ubuntu is updated. Do I have to wait for the next release?

Unfortunately, I have little time or inclination for much fooling around with Linux internals and tweaking and tuning. I just want it to "work out of the box."

---

### Post by CheeseEatingBulldog on 2007-04-25
I got rid of the timeouts on boot up by adding 'irqpoll' to my grub line and now it boots without pause.

---

### Post by wrikent3500 on 2007-06-12
it works on an acer aspire 3620...not mine hangs got as close as the password screen and that`s it.

---

### Post by kineem on 2007-07-26
Has there been any patch for this problem?

---

### Post by www.rzr.online.fr on 2007-08-09
maybe this is the SATA/PATA issue :
  [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)
--
[http://rzr.online.fr/q/ATA](http://rzr.online.fr/q/ATA)

---

