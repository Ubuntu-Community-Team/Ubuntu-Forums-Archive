---
title: "Lucid Lynx Alpha 3 Released"
date: 2010-02-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-02-25
Alpha 3, the third milestone of the Lucid Lynx development cycle leading to Ubuntu 10.04, has been released. Refer to the links below for more information:

[list] [*] [Release announcement]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2010-February/000682.html") on the [ubuntu-devel-announce mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce")
[*] [Technical Overview]("http://www.ubuntu.com/testing/lucid/alpha3")[/list]

**Downloads**

(Please prefer torrents, and [using rsync / zsync]("https://help.ubuntu.com/community/RsyncCdImage"))

[list][*][http://cdimage.ubuntu.com/releases/lucid/alpha-3/](http://cdimage.ubuntu.com/releases/lucid/alpha-3/) (Ubuntu)
  [*][http://uec-images.ubuntu.com/releases/lucid/alpha-3/](http://uec-images.ubuntu.com/releases/lucid/alpha-3/) (Ubuntu Server for UEC and EC2)
  [*][http://cdimage.ubuntu.com/kubuntu/releases/lucid/alpha-3/](http://cdimage.ubuntu.com/kubuntu/releases/lucid/alpha-3/) (Kubuntu)
  [*][http://cdimage.ubuntu.com/xubuntu/releases/lucid/alpha-3/](http://cdimage.ubuntu.com/xubuntu/releases/lucid/alpha-3/) (Xubuntu)
  [*][http://cdimage.ubuntu.com/edubuntu/releases/lucid/alpha-3/](http://cdimage.ubuntu.com/edubuntu/releases/lucid/alpha-3/) (Edubuntu)
  [*][http://cdimage.ubuntu.com/mythbuntu/releases/lucid/alpha-3/](http://cdimage.ubuntu.com/mythbuntu/releases/lucid/alpha-3/) (Mythbuntu)
  [*][http://cdimage.ubuntu.com/ubuntustudio/releases/lucid/alpha-3/](http://cdimage.ubuntu.com/ubuntustudio/releases/lucid/alpha-3/) (Ubuntu Studio)[/list]

See [http://wiki.ubuntu.com/Mirrors](http://wiki.ubuntu.com/Mirrors) for a list of mirrors.

---

### Post by kansasnoob on 2010-02-25
Looking really good too :D

After installed the only issue I've encountered is the known plymouth bug. Maybe they should have gone with a Desoto or a Dodge :p

During install the only nuisance I see is having to login as Ubuntu w/no password which is awfully minor.

IMHO at this point this definitely looks like the best Ubuntu ever.

---

### Post by k3lt01 on 2010-02-25
Well, I'm glad someone thinks its good cause mine is now so slow I can see an ice age developing before it will do anything I want it to. I'll take a good look at it later tonight to see what has happened.

---

### Post by Neezer on 2010-02-25
I have a partition that I'm not using, and I am interested in trying 10.04...I know it isn't a release yet, and I could encounter some problems. Is there anywhere I can go to report bugs that I find while using it? I don't know that much about this...Do I have to partition for swap? I have 4 GB of ram, so that should be enough. I don't know that I have ever even used my swap space before.

---

### Post by VMC on 2010-02-25
> **Neezer said:**
> I have a partition that I'm not using, and I am interested in trying 10.04...I know it isn't a release yet, and I could encounter some problems. Is there anywhere I can go to report bugs that I find while using it? I don't know that much about this...Do I have to partition for swap? I have 4 GB of ram, so that should be enough. I don't know that I have ever even used my swap space before.

If you install Lucid on the spare partition it will find your swap partition. Also look at [Launchpad]("https://launchpad.net/ubuntu"). For error reporting, select the "Bug" tab. You have to join to add or comment on any bug reports.

---

### Post by Harlekin33 on 2010-02-25
CAT 6 all the way!

Yeay!

---

### Post by andrewabc on 2010-02-25
> **Neezer said:**
> I have a partition that I'm not using, and I am interested in trying 10.04...I know it isn't a release yet, and I could encounter some problems. Is there anywhere I can go to report bugs that I find while using it? I don't know that much about this...Do I have to partition for swap? I have 4 GB of ram, so that should be enough. I don't know that I have ever even used my swap space before.

Only need 1 partition for swap (will be used for both OS I'm pretty sure. Worked for me).

When you encounter a bug/problem check forum to see if any other threads like it. Possibly create a thread to see if anyone else has same problem, and create bug report at [launchpad](https://bugs.launchpad.net/).

Biggest problem depending on what other OS you use is that GRUB would be main thing to affect loading of other OS. But grub should work fine.

I'd try livecd or liveusb first before installing to make sure basic stuff works.

---

### Post by ndefontenay on 2010-02-25
I've downloaded an image using rsync and used the image in a virtual box. I get the prompt for language and then select try without installing.

From there nothing. The size of the image was 685 MB.

Is there a problem with this way of acquiring an image?

I tried getting that image again to no avail with the same method, it can't install.

---

### Post by Uncle Spellbinder on 2010-02-25
Just got home from work. Glad to see Alpha 3 released. Downloading now.

---

### Post by ranch hand on 2010-02-26
> **ndefontenay said:**
> I've downloaded an image using rsync and used the image in a virtual box. I get the prompt for language and then select try without installing.

From there nothing. The size of the image was 685 MB.

Is there a problem with this way of acquiring an image?

I tried getting that image again to no avail with the same method, it can't install.
Did you run the md5sum check on the bugger?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

This will tell you if the image you downloaded is good.

If that checked out I would boot to the CD again and click on the option to check the CD.  There have been bugs in that option with 10.04 I hope it works.

You give no info on your box at all.  If we had that we might see where a problem may be.  From the info you provided this is all the advice that can really be given.

---

### Post by ndefontenay on 2010-02-26
Well it's a simple virtual box with just 1GB RAM allocated an 8GB disk.

I will do the md5 check sum and see again.
I completed downloading again I didn't have time to do a checksum before work.
I was just looking for a quick feedback to see if I was the only one experiencing this.
It sounds like it x)
So tonight check sum and CD check from the menu.

thanks dude

---

### Post by Luffield on 2010-02-26
I get a blank screen too, with an md5-checked iso file on an Ubuntu 9.10 host. I'll try again when I boot into Windows XP later today.

Edit: it might just work, according to comment #28 in the relevant bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/510571](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/510571)

---

### Post by ranch hand on 2010-02-26
> **ndefontenay said:**
> Well it's a simple virtual box with just 1GB RAM allocated an 8GB disk.

I will do the md5 check sum and see again.
I completed downloading again I didn't have time to do a checksum before work.
I was just looking for a quick feedback to see if I was the only one experiencing this.
It sounds like it x)
So tonight check sum and CD check from the menu.

thanks dude
We really need information on your computer.  What is the hardware that this is running on.

Look at the bottom of this post and you will see what I mean.  That is my box and there are problems that I will have that folks that have intel video will not.  My SB sound card will not have the same problems that some others will.

These little details realy do make a difference.

---

### Post by Neezer on 2010-02-26
I am trying to make an external USB drive (160BG) my bootable usb drive. Can I do this? I have done it with a flash drive before, but not an external hard drive. When I get to the startup usb maker, It won't let me create it. It keeps telling me I need to format the disk. I have tried ext3, and ext4. Am I missing something? I would normally use a cd, but I don't have any available at the moment.

---

### Post by VMC on 2010-02-26
> **Neezer said:**
> I am trying to make an external USB drive (160BG) my bootable usb drive. Can I do this? I have done it with a flash drive before, but not an external hard drive. When I get to the startup usb maker, It won't let me create it. It keeps telling me I need to format the disk. I have tried ext3, and ext4. Am I missing something? I would normally use a cd, but I don't have any available at the moment.

I think you confusing two operations. The Startup Disk Creator creates an image of the ISO to usb. 

If I understand you, I think you want to install Lucid onto a usb hard drive. Is that right?

---

### Post by Luffield on 2010-02-26
Alpha 3 works well on Virtualbox 3.1.4 on Windows. ndefontenay, I think the problem you have is caused by a bug in Virtualbox and not in Alpha 3.

---

### Post by andrek on 2010-02-26
I just installed it and I've got to say - it's blazing fast. It just flies on my dell studio 1555.
But here's the thing : as we all know proprietary ati drivers don't work with the new Xserver and so Ubuntu uses opensource -ati instead. They seem nice, KMS works wonderfully but there's one glitch - it's quite unusable on any laptop since the power management of the graphic card doesn't exist at all. The fan goes non-stop. Is there any way to lower the gpu clocks / voltages so that it'd be cooler AND more quiet?

Also, Catalyst Control Center ( or however it is called ) allowed me to manage my contrast settings. Is there any tool for that for the opensource -ati drivers? ( and no, I'm not looking for xgamma app )

---

### Post by ranch hand on 2010-02-26
> **Neezer said:**
> I am trying to make an external USB drive (160BG) my bootable usb drive. Can I do this? I have done it with a flash drive before, but not an external hard drive. When I get to the startup usb maker, It won't let me create it. It keeps telling me I need to format the disk. I have tried ext3, and ext4. Am I missing something? I would normally use a cd, but I don't have any available at the moment.
I am running, right now, on my test platform which is a dual HDD external enclosure with two 320Gb WD HDDs.  I have another external that is a single 320Gb.

I would recommend turning off your internal drive(s) in bios while you are installing on the external.  You also need to set the bios to boot in this order;
1>CD
2>USB Device
3>Internal HDD

With the internal(s) off there is no chance of screwing them up on install and it will leave the mbr alone so that you can check the external, by itself, to make sure it works right.

When you are happy with it you can then turn on the internal and boot to the external and run;
```

sudo update-grub

```
Then run;
```

sudo grub-mkconfig

```
Take a look at the output carefully to make sure that it is correct for the internals.

If it is do;
```

sudo grub-install /dev/sda

```
editing the "sda" to fit your box (could be that is not the right designation for your mbr if you are not running SATA).

---

### Post by Neezer on 2010-02-26
> **VMC said:**
> I think you confusing two operations. The Startup Disk Creator creates an image of the ISO to usb. 

If I understand you, I think you want to install Lucid onto a usb hard drive. Is that right?


nope, I only have an external usb hard drive handy. I don't have a flash drive with me, or blank cds. I have a 15GB partition on my laptop that I want to put 10.04 on. I already have a /swap on the laptop as well, and I think that will work with both linux installs....I'm also running 9.10 on the laptop. 

So in recap, I want to put 10.04 on my laptop hdd. I don't have a flash stick, or a blank cd to make an iso disk. I do have an external hard drive though. I have tried to make a usb startup disk on my usb hard drive, but it isn't working.

---

### Post by vange on 2010-02-26
The fix you suggested works - thanks. Running VirtualBox 3.0.8_OSE r53138 on host OS Ubuntu 9.10.

---

### Post by k3lt01 on 2010-02-26
> **Neezer said:**
> I am trying to make an external USB drive (160BG) my bootable usb drive. Can I do this? I have done it with a flash drive before, but not an external hard drive. When I get to the startup usb maker, It won't let me create it. It keeps telling me I need to format the disk. I have tried ext3, and ext4. Am I missing something? I would normally use a cd, but I don't have any available at the moment.@ Neezer, I did the whole make a usb startup disk to and it wouldn't work. So I went searching and found [this thread]("http://ubuntuforums.org/showthread.php?t=1288604"). It should give you an idea how to do it. It worked for me on a usb flash drive setup for mini installs and my 500gb Seagate setup for full installs with repositories and all.

---

### Post by WatTwo on 2010-02-26
I just got alpha 2 yesterday.. (didn't know alpha 3 would be out today XD)

So is there a way to just update from 2 to 3?

---

### Post by ratcheer on 2010-02-26
Yes, just do a safe-upgrade.

Tim

---

### Post by Uncle Spellbinder on 2010-02-26
> **ratcheer said:**
> Yes, just do a safe-upgrade.

Tim

```
unclespellbinder@lucid:~$ sudo apt-get safe-upgrade
E: Invalid operation safe-upgrade
unclespellbinder@lucid:~$ 
```

---

### Post by ratcheer on 2010-02-26
> **Uncle Spellbinder said:**
> ```
unclespellbinder@lucid:~$ sudo apt-get safe-upgrade
E: Invalid operation safe-upgrade
unclespellbinder@lucid:~$ 
```

Huh? It worked for me, this morning (I used aptitude). Did you update, first?

Tim

---

### Post by Uncle Spellbinder on 2010-02-26
> **ratcheer said:**
> Did you update, first?
Yes

I ended up downloading Alpha 3 and did a clean install.

EDIT:
The command does not work in Alpha 3. Just tried it (unless a 'new' version needs to be available).

---

### Post by ratcheer on 2010-02-26
Note to others doing an upgrade from alpha2 to alpha3: there is a warning on the alpha3 page that libmysqlclient16 must be reinstalled after the upgrade.

[http://www.ubuntu.com/testing/lucid/alpha3#Issue%20when%20upgrading%20from%20Lucid%20Alpha%202](http://www.ubuntu.com/testing/lucid/alpha3#Issue%20when%20upgrading%20from%20Lucid%20Alpha%202)

Tim

---

### Post by grubdude on 2010-02-26
Not to change the subject, but can I assume that the lack of the Ubuntu splash screen after logging in with Alpha 3 is normal?

Thanks

---

### Post by godhika on 2010-02-26
> **Uncle Spellbinder said:**
> ```
unclespellbinder@lucid:~$ sudo apt-get safe-upgrade
E: Invalid operation safe-upgrade
unclespellbinder@lucid:~$ 
```

The command for safe upgrade is > sudo aptitude safe-upgrade

---

### Post by ranch hand on 2010-02-26
Just do;
```

sudo apt-get upgrade

```
in apt.

I think it is safer than aptitude.  Opinions differ on this.  You should pick one and stick with it though or some things get a little jumbled in both.

The aptitude safe upgrade is about like synaptics safe setting.  It will let more through than apt will.  I like this.

I do the apt stuff and then go to synaptic and go through the stuff held back one at a time and see what I think is safe to install.

What is safe to install, you may ask.  That is up to you.

I upgrade things that may be removing files if it looks like they are replacing them with something that will work.  I also do things that are going to install extra files (usually).

Apt is kind of conservative but that is nice, particularly if you only have one install.

---

### Post by tad1073 on 2010-02-27
> **Uncle Spellbinder said:**
> Yes

I ended up downloading Alpha 3 and did a clean install.

EDIT:
The command does not work in Alpha 3. Just tried it (unless a 'new' version needs to be available).

I downloaded A3 but when I select install and try it from the menu my monitor shuts off.

---

### Post by Uncle Spellbinder on 2010-02-27
> **tad1073 said:**
> I downloaded A3 but when I select install and try it from the menu my monitor shuts off.

Mine shut off for about 2-3 minutes. Came back on and all was fine. Don't know if it's a bug or not, but it seemed part of the install process.

---

### Post by tad1073 on 2010-02-27
> **Uncle Spellbinder said:**
> Mine shut off for about 2-3 minutes. Came back on and all was fine. Don't know if it's a bug or not, but it seemed part of the install process.

I figured it out. I removed quiet splash and enabled nomodeset.

---

### Post by teh603 on 2010-02-27
Rock solid on my Inspiron 1564, compared to Alpha 2 which froze the instant I tried to use a menu (compiz and bad vido drivers?). Video actually works, as opposed to Karmic. Gotta love the fact that the Arrandale chipset is really too new for good support, lol.

Minor issues, which I'm probably going to file using Ubuntu-bug tomorrow: Using the BMC wifi restricted driver, Network Manager incorrectly reports loss of connection. System fails to wake from suspend (minor, because the boot time without plymouth is so bloody fast). ACPI has no idea how long the battery lasts, but gives me a rough percentage of how much charge it has in it.

---

### Post by ejket on 2010-02-27
I got impatient and thought I'd try the 64-bit Alpha3.  It's working very well so far.  Yes, I had my screen power down on me at the start of the install, but fortunately I was busy doing something else, and when I looked again, it was all good.

For an alpha release, this is pretty nice.  My only notable problem so far is I don't have audio in VLC, just a crackly sound.  All other sound is fine after nuking pulseaudio:

```
sudo mv /usr/bin/pulseaudio /usr/bin/pulsesucks
```

(This is the only reliable solution I've found to get the hda_intel sound driver working in Debian/Ubuntu.)

I wanted OO 3.2 and it works fine.  Everything else is fast and smooth.  This is going to be a great LTS release, I think.

---

### Post by mechanic on 2010-02-28
It might be my imagination but the KDE version (kubuntu) looks cleaner than the previous Karmic. KDE 4.4 may have cleaned up the graphics a bit. And the annoying power management bug - no profiles found - has been cleared.


The ony problem with these alpha releases is that packages flow in at a high rate, every day there is 50 or so to update.

---

### Post by louieb on 2010-02-28
> **andrek said:**
> ... but there's one glitch - it's quite unusable on any laptop since the power management of the graphic card doesn't exist at all. The fan goes non-stop....

Not my experience. Power management work fine on my 6 year old IBM T30. ATI mobile radon graphics. Fan seems to go on and off about the same as prior versions. 

Still am getting hit with the random logout. 

Boot time is the shortest yet. Wonder if using the ext4 file-system has anything to do with it.

---

### Post by ranch hand on 2010-02-28
I do not think that ext4 has anything to do with boot time.  I have a couple 8.04>10.04 upgrades which use ext3 and they boot the same as my ext4 installs.

I do see some lack of performance and a very little more instability in the ext3 installs.  This could, of course, be different on different hardware.

---

### Post by andrek on 2010-02-28
> **louieb said:**
> Not my experience. Power management work fine on my 6 year old IBM T30. ATI mobile radon graphics. Fan seems to go on and off about the same as prior versions. 

Still am getting hit with the random logout. 

Boot time is the shortest yet. Wonder if using the ext4 file-system has anything to do with it.

Are you sure you're using the open-source driver, not the proprietary Catalyst one? If I remember right, the power management options for the -ati driver are going to be added to 2.6.34 kernel. Correct me if I'm wrong.

---

### Post by k3lt01 on 2010-02-28
> **louieb said:**
> Still am getting hit with the random logout.Mine logs out everytime I do a fresh boot. After a while on the 2nd boot it settles down then it can range from completely unusable to slow as a wet week.

I downloaded a daily last night so I think I will do a clean install just incase there is anything lagging behind tat shouldn't be there.

---

### Post by jerrylamos on 2010-02-28
New A3 install on i845 Intel Video Graphics.

Very sick and intermittent from the .iso, hangs, my background is my wife in a bathing suit which turned into psychedelic colors,  suddenly boot to a never ending logon screen, etc.  Fix broken  packages no help.

Then I tried the usual "nomodeset" and xorg.conf Driver "vesa" a little help, still crashed after a few minutes, can't do Ctrl-Alt-F1, can't ssh in from another pc, dead as a doorknob.

So in a Thinkpad T40 with ati graphics, the A3 release bugs:
[http://www.ubuntu.com/testing/lucid/alpha3](http://www.ubuntu.com/testing/lucid/alpha3)
mentioned that a package version mixup so run:
sudo apt-get install libmysqlclient16/lucid

So it's been running for a whole 2 hours since!  
Of course, "nomodeset" and Driver "vesa" as well as the libmysqlclient16.....whatever that is.

Jerry

---

### Post by Trapper on 2010-02-28
>                      Originally Posted by **Uncle Spellbinder**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8890973#post8890973")                 
                 *Mine shut off for about 2-3 minutes. Came back on and all was fine. Don't know if it's a bug or not, but it seemed part of the install process.*
> **tad1073 said:**
> I figured it out. I removed quiet splash and enabled nomodeset.

My monitor went to sleep and never responded, even after a lengthy time. I tried the routine of removing the quiet slash and enabled nomodeset. When I booted I had a several minute lag but then the installed "tried" to start the gui. I ended up with an "out of frequency" message from my monitor.

I noted something else real strange though. I had a ton of sr0 read failures. I had no way of actually doing a check of the cd I burned. I did have a good md5sum on my download though. I redownloaded the amd64 desktop iso torrent again, had a good md5sum check, burned and tried to install from the cd but encountered the same sr0 error problems and the monitor went out of sync when the installer tried to start the gui.

Then I burned the same iso image to a blank "DVD". The installer booted up with no problem, I got the gui and the install went well. Go figure.

---

### Post by teh603 on 2010-02-28
> **Trapper said:**
> Then I burned the same iso image to a blank "DVD". The installer booted up with no problem, I got the gui and the install went well. Go figure.
I did my install off a DVD as well. I've heard of other issues regarding burning Lucid to a CD, but most of those are related to Kubuntu and the size of the iso.

---

### Post by louieb on 2010-02-28
> **andrek said:**
> Are you sure you're using the open-source driver,.
I'm using the defaut driver - lshw shows the driver to be radon. Hardware drivers does not give me the option for anther driver for this card. 

Do not think it put out much heat - just has 16MB memory  Just not that high powered. Could be why I'm not having a heating problem. 
 
> **k3lt01 said:**
> Mine logs out everytime I do a fresh boot.

When I 1st login after a reboot - It puts my session in tty1 (finger command) instead of the expected tty7. If I logout and log back in then the new session is on tty7 and I have not gotten the random logout. Until that get fixed guess I just have to put up with logging in twice.

---

### Post by Aname on 2010-03-01
Hi all. I've installed Alpha 3, everything seemed fine, then when I rebooted I just got a black screen. I think all I did was enable extra visual effects. I'm on a Radeon card, using the default driver. Any ideas how to get it working again? Thanks.

---

### Post by ElSlunko on 2010-03-01
> **Aname said:**
> Hi all. I've installed Alpha 3, everything seemed fine, then when I rebooted I just got a black screen. I think all I did was enable extra visual effects. I'm on a Radeon card, using the default driver. Any ideas how to get it working again? Thanks.

I get a blank boot screen too. Even the monitor goes into power save as if it lost the signal but everything boots normally -- just had to wait. Does it fail to boot ?

---

### Post by Brinstar on 2010-03-01
wubi on Alpha 3 64-bit is trying to download the iso for Karmic 64-bit, is this what is supposed to happen?

i want to try lucid out but only as a wubi install, not as a proper system just yet. maybe when its finally released i will do that.

---

### Post by cpmman on 2010-03-01
I installed from the iso disc to my Medion MD96640 which is notorious for hot running after using the iso for a test boot.  Lucid has been running for several hours now and the sensors give me approx 67% of critical temps.  Thanks for the partial upgrade tip - being a biker I tend to 'go for it' when there is any doubt but your very sensible explanation of why I should not has convinced me to follow your advice.  As a computer user from the days of dos and cpm through ms-dos, gem, solaris, various mainframe proprietary systems and the terrible Windoze escapes, it is a pleasure to be able to find such excellent advice and help from the Ubuntu community.  Many thanks from a very satisfied user.

---

### Post by crjackson on 2010-03-01
Well, I can't get A3 to install.  It runs fine in the LiveCD but the install always stops at 48% and tells me that there is an I/O error. It says it has one of these problems.

1) CD/DVD is defective or dirty
2) CD/DVD drive is defective or has a dirty lens
3) HD is defective.

I've download multiple times.  I know the drives (DVD/HD) are solid.

I downloaded the Daily Build and it won't even boot to a live desktop.

How can I get this installed (without installing Karmic and upgrading)?

---

### Post by exavoid on 2010-03-01
I installed the Alpha 3 with no updates, because when I tried to upgrade the installer before installing the full system it didn't work for me, it didn't pass the 93%. 
For now I'm just testing it :)

Regards

---

### Post by crjackson on 2010-03-01
Well, I finally got it installed.  I downloaded the daily build again and burned again.  I used a different brand CD and it went.  So far so good...

---

### Post by andrewabc on 2010-03-01
> **crjackson said:**
> Well, I finally got it installed.  I downloaded the daily build again and burned again.  I used a different brand CD and it went.  So far so good...

Next time you could also try alternate cd. Wouldn't solve the problem of livecd not working, but sometimes alternate cd will install when livecd doesn't.

---

### Post by teh603 on 2010-03-01
> **exavoid said:**
> I installed the Alpha 3 with no updates, because when I tried to upgrade the installer before installing the full system it didn't work for me, it didn't pass the 93%. 
For now I'm just testing it :)

RegardsI had that happen once with an un-updated installer. It froze somewhere when the GRUB installer was "searching for other operating systems."

---

### Post by crjackson on 2010-03-01
> **andrewabc said:**
> Next time you could also try alternate cd. Wouldn't solve the problem of livecd not working, but sometimes alternate cd will install when livecd doesn't.

I did download the alternate installed and that was going to be next but it wasn't needed.

---

### Post by andyvr4 on 2010-03-01
> **teh603 said:**
> Rock solid on my Inspiron 1564, compared to Alpha 2 which froze the instant I tried to use a menu (compiz and bad vido drivers?). Video actually works, as opposed to Karmic. Gotta love the fact that the Arrandale chipset is really too new for good support, lol.

Minor issues, which I'm probably going to file using Ubuntu-bug tomorrow: Using the BMC wifi restricted driver, Network Manager incorrectly reports loss of connection. System fails to wake from suspend (minor, because the boot time without plymouth is so bloody fast). ACPI has no idea how long the battery lasts, but gives me a rough percentage of how much charge it has in it.

Is this with compiz enabled and all the fancy graphics stuff running?

I'm looking at getting a new laptop very shortly with the i3 and would really like to get the integrated graphics for the power savings because I've got my desktop for gaming. All that I use my laptop for is browsing the internet and open office!

I've just been worried about how well these new intel integrated graphics are going to work with linux, I've always stuck with nvidia because I know they're supported really well, I just don't like the idea of the power hungry nivida graphics in a laptop that has no need for a performance graphics card!

Thanks

---

### Post by teh603 on 2010-03-02
> **andyvr4 said:**
> Is this with compiz enabled and all the fancy graphics stuff running?

I'm looking at getting a new laptop very shortly with the i3 and would really like to get the integrated graphics for the power savings because I've got my desktop for gaming. All that I use my laptop for is browsing the internet and open office!

I've just been worried about how well these new intel integrated graphics are going to work with linux, I've always stuck with nvidia because I know they're supported really well, I just don't like the idea of the power hungry nivida graphics in a laptop that has no need for a performance graphics card!

ThanksActually, I disabled Compiz because of some percieved stability issues- I've had the odd freeze with it on, although I'm not sure if it was Compiz' fault. The AntSpotlight screensaver runs really fast, though. I probably need to download Alien Arena and try that as well.

I know there's some "official" diagnostics for 3D performance, but I don't know how to run them.

---

### Post by Neezer on 2010-03-02
Is this a new feature in 10.04?

When I was installing I had several partitions on sda. I was having problems installing, but then I realized i needed to specify which partition I wanted as /. I have a different 9.10 partition on there as well, along with a /home for 9.10.

If I were to tell the installer to use the /home partition from my 9.10 install for the /home for my lucid install, would it have reformatted it? or would it use it as is?

---

### Post by andyvr4 on 2010-03-02
> **teh603 said:**
> Actually, I disabled Compiz because of some percieved stability issues- I've had the odd freeze with it on, although I'm not sure if it was Compiz' fault. The AntSpotlight screensaver runs really fast, though. I probably need to download Alien Arena and try that as well.

I know there's some "official" diagnostics for 3D performance, but I don't know how to run them.

Thanks, I wonder if they're going to eventually get the intel driver to where it'll fully support compiz.  That's really one of my biggest concerns with getting an i3 or i5 laptop with the integrated graphics.  I've regretted getting the ati graphics ever since I got my previous laptop and swore that I'd never get anything, but nvidia graphics from now on and now I'm looking at intel, haha!

---

### Post by VMC on 2010-03-02
> **Neezer said:**
> ...
If I were to tell the installer to use the /home partition from my 9.10 install for the /home for my lucid install, would it have reformatted it? or would it use it as is?Only if you tell it to reformat.

---

### Post by nutznboltz on 2010-03-03
This is still not in Lucid:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/482419](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/482419)

---

### Post by teh603 on 2010-03-03
> **andyvr4 said:**
> Thanks, I wonder if they're going to eventually get the intel driver to where it'll fully support compiz.  That's really one of my biggest concerns with getting an i3 or i5 laptop with the integrated graphics.  I've regretted getting the ati graphics ever since I got my previous laptop and swore that I'd never get anything, but nvidia graphics from now on and now I'm looking at intel, haha!To be honest, I've always found myself disabling compiz for various reasons. One of the biggies is accidentally switching desktops while trying to drag something. I've gotten better results from the Intel chips in my Acer Aspire One than the nVidia chips in dad's Acer AspireRevo, so I'm starting to stick to Intel.

---

### Post by teh603 on 2010-03-03
Just updated today, and there seems to be better acpi support. The battery icon in the menu bar actually reports estimated battery life and charge time now.

Alien Arena crashes very hard, though.

---

### Post by taavikko on 2010-03-04
Just did a clean install from alpha3.amd64 image and somehow .bashrc failed to get copied from /etc/skel/ and thus making use of terminal less functional...

Anyone else?

---

### Post by VMC on 2010-03-04
> **taavikko said:**
> Just did a clean install from alpha3.amd64 image and somehow .bashrc failed to get copied from /etc/skel/ and thus making use of terminal less functional...

Anyone else?

I didn't do a direct alpha3 install, but I did do a fresh install on daily-live feb28th, which was after a3. I don't have any problems using the terminal.

What specifically is less functional?

---

### Post by taavikko on 2010-03-04
> **VMC said:**
> 

What specifically is less functional?

Loss of auto-completion :)
Problem was solved by just copying the /etc/skel/.bashrc to $HOME

Was just wondering if somebody else stumbled on the same issue...

---

### Post by VMC on 2010-03-04
> **taavikko said:**
> Loss of auto-completion :)
Problem was solved by just copying the /etc/skel/.bashrc to $HOME

Was just wondering if somebody else stumbled on the same issue...

That's funny, 'cause I don't use that feature. I had to look it up. I forgot how :)

BTW- I know you use **_Aptitude_**. Are you getting the core dumps that many of us are getting, using aptitude? I can't even trust aptitude anymore. I created a bug report and "me to" another.

---

### Post by louieb on 2010-03-04
> **VMC said:**
> ...you use **_Aptitude_**. ...core dumps ... 

No core dumps here. Put Lucid on sometime in Dec - about every other day do:

```
sudo aptitude update
sudo aptitude safe-upgrade
```

Just wondering though - have not been annoyed but the update-manger yet - has automatic update notification  been enabled.
> Loss of auto-completion :smile:

Would not have noticed - one of the 1st thing I did was install zsh and make it my default shell.

---

### Post by ndefontenay on 2010-03-04
Hi everyone.

Installed alpha 3 last night. I couldn't take advantage of gwibber as I was having a SIGDEV error with it. it's a know bug and so far nothing to be done about it.

Empathy also tends to crash from time to time.

Otherwise:
I tried installing skype for ubuntu 8.10 or higher and it was saying my package is corrupted... I'm downloading it again but just want to know. Did anyone installed skype successfully?

Iphone: After the buzz yesterday about iphone supported under linux, I open rythmbox and saw the ipod. I clicked on it and I saw the musics. I could play them no problem.

I then wanted to move a file from my music library which I did by a drag/drop on the iphone icon. I could see the song in the play list on rythmbox but it never synchronized the iphone.

So question: anyone tried synchronize musics on iphone yet with rythmbox? Are supposed to just listen and use gtkpod for sync?

---

### Post by teh603 on 2010-03-04
To be honest, I've been removing Gwibber and Empathy. I don't do social networking.

Did anyone catch what the update to libplymouth did this morning? I removed Plymouth so I didn't catch quite what it was supposed to do. Then again, Plymouth gives me ureadahead errors, almost a minute tacked onto my boot time, and a black screen of frustration.

---

### Post by ndefontenay on 2010-03-04
Oh yeah booting and general resource usage: Lightning fast!
The boot is indeed around 10 secs for me so promises are hold here.

Before I get the Ubuntu splash screen however I get a load of messages showing too quick for me too read but it makes it looks unpolished or like there's a problem at boot time. Is there a way I could get those boot messages?

When shutting down I also get a tiny cursor showing up on the right hand side of the screen, at the edge in the middle for no apparent reasons.

---

### Post by dinamic1 on 2010-03-05
> **ndefontenay said:**
> Oh yeah booting and general resource usage: Lightning fast!
The boot is indeed around 10 secs for me so promises are hold here.

Before I get the Ubuntu splash screen however I get a load of messages showing too quick for me too read but it makes it looks unpolished or like there's a problem at boot time. Is there a way I could get those boot messages?

When shutting down I also get a tiny cursor showing up on the right hand side of the screen, at the edge in the middle for no apparent reasons.

pause/brake button?

---

### Post by hibit on 2010-03-06
Hi All,

Am currently running the latest Lucid updates on the laptop here and am getting regular periods of 100% disk i/o which are causing significant slow down. Looking at top and atop it seems trackerd might be the cause. Anyone else seeing this? Am happy to provide more info if it would help fix the issue.

Jim

---

### Post by VMC on 2010-03-06
> **hibit said:**
> Hi All,

Am currently running the latest Lucid updates on the laptop here and am getting regular periods of 100% disk i/o which are causing significant slow down. Looking at top and atop it seems trackerd might be the cause. Anyone else seeing this? Am happy to provide more info if it would help fix the issue.

Jim

**trackerd** was reported years ago and is still valid today. Its file indexing. You can read about it [**here**]("http://ubuntuforums.org/showthread.php?t=591867").

---

### Post by andrewabc on 2010-03-06
I didn't think file indexing was installed and running by default?

---

### Post by VMC on 2010-03-06
> **andrewabc said:**
> I didn't think file indexing was installed and running by default?

Here's another view on the topic of **_[trackerd]("http://www.howtogeek.com/howto/linux/what-is-trackerd-and-why-is-it-running/")_**

---

### Post by Orographic on 2010-03-07
> **teh603 said:**
> To be honest, I've always found myself disabling compiz for various reasons. One of the biggies is accidentally switching desktops while trying to drag something. I've gotten better results from the Intel chips in my Acer Aspire One than the nVidia chips in dad's Acer AspireRevo, so I'm starting to stick to Intel.

Thanks for that, interesting stuff and thanks andyvr4 too. I'm looking at getting a new desktop with an i3 in it as I don't game and want a low power chip, might even get the i5 6xx series. Australian computer magazines are rating these chips very well if you are not into gaming and you can even add a GPU if needed although there is some memory latency in that regard.

My current system is about 32 months old and still running well but will buy a new system some time this year. 

Will keep an eye on how Lynx develops.

---

### Post by Orographic on 2010-03-07
BTW, can you disable compiz the usual way via the appearances tab in Lynx? I do this for Karmic anyway as I have an integrated graphics board (945GZM-S2).

---

### Post by ndefontenay on 2010-03-07
Anybody else experience a black screen with just a cursor on the top left and a working mouse?

When I press any button, including the shutdown button, the cursor will then write some weird characters.

I'm not sure either how to get more information about this and how to pose this bug on launchpad.net. Some help would be welcome.

Thanks

Nico

---

### Post by woodbj on 2010-03-07
> **ndefontenay said:**
> Anybody else experience a black screen with just a cursor on the top left and a working mouse?

When I press any button, including the shutdown button, the cursor will then write some weird characters.

I'm not sure either how to get more information about this and how to pose this bug on launchpad.net. Some help would be welcome.

Thanks

Nico

I get this but I just hold down enter and the login pops up

---

### Post by ndefontenay on 2010-03-07
Thanks a lot woodbj :)
say I was wondering. It didn't happen the first reboot but then I started toying around with compiz and at the next reboot bam, problems again.

Can you tell me if you got it right away or if you use compiz? I will try the press enter trick and if it works like that I'll disable compiz and try again.

Thanks a bunch.

---

### Post by woodbj on 2010-03-08
> **ndefontenay said:**
> Thanks a lot woodbj :)
say I was wondering. It didn't happen the first reboot but then I started toying around with compiz and at the next reboot bam, problems again.

Can you tell me if you got it right away or if you use compiz? I will try the press enter trick and if it works like that I'll disable compiz and try again.

Thanks a bunch.
I have my visual effects set on extra and haven't changed the setting all through any of the development, it started happening to me about 2 weeks ago

---

### Post by scouser73 on 2010-03-08
I noticed that when setting up dual monitors on 10.04 the **Xorg.conf** worked straight away.

---

### Post by Stason on 2010-03-08
Did aptitude safe upgrade. Mldonkey gave some errors at the end, presumably due to that libmysqlclient16 bug. Reinstalled that and mldonkey from synaptic. Had to reboot two times, first had that weird relogin stuff trying to launch firefox, second reboot - black screen. Third reboot - all seems fine.

Visually have a few new icons, volume control is now missing from taskbar, bloody window buttons are now on the left! (who's idea was that???) , got much more flickering on boot, some color lines and weird progress bar, which disappears after 2 seconds or so. My graphic card (7300GT) now gets recognized by X-screen. Seem to get some less tearing during video playback. OpenGL screensavers are now working. Terminal got purple background.

Ice1712 config is still broken, the card output is not picked up by default. Cured using same stuff as for A2: [http://ubuntuforums.org/showpost.php?p=8794658&postcount=31](http://ubuntuforums.org/showpost.php?p=8794658&postcount=31)

---

### Post by ukblacknight on 2010-03-08
> **ndefontenay said:**
> I've downloaded an image using rsync and used the image in a virtual box. I get the prompt for language and then select try without installing.

From there nothing. The size of the image was 685 MB.

Is there a problem with this way of acquiring an image?

I tried getting that image again to no avail with the same method, it can't install.

I'm getting this when trying to install Kubuntu 10.04 alpha 3 in VirtualBox.

After selecting the language, the screen just goes black - nothing.

I'm able to run the image as a LiveCD in the virtual machine, but the Installer just crashes after it loads.

VirtualBox 3.1.4
Ubuntu 9.10 Host

Edit: I downloaded the image normally from their site, did it twice.  I'm unable to check the disk for errors either!

---

### Post by VMC on 2010-03-08
> **ukblacknight said:**
> 
Edit: I downloaded the image normally from their site, did it twice.  I'm unable to **check the disk for errors** either!

To check the disk, use the md5sum check. Put your cd in the cdrom and then as an example do the following. Your mounts and ISO naming may differ. md5sum.txt should be the same:

```
$ mount
...
/dev/sr0 on **/media/Ubuntu 10.04 i386** type iso9660 (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
===
$ **cd /media/'Ubuntu 10.04 i386'**
===
/media/Ubuntu 10.04 i386$ **md5sum -c md5sum.txt**
./casper/initrd.lz: OK
....
./README.diskdefines: OK
```

---

### Post by ukblacknight on 2010-03-08
I don't have any CD's to burn to! :(

I've managed to get the installer going now, I think I made the mistake earlier by trying to update the installer.

Fingers crossed :)

---

### Post by ranch hand on 2010-03-08
Goodness, where did this "-c" come from?  How come no one ever told me (whine whine).  That is neat.

Thanks, a new command (to me), oh boy.

---

### Post by ndefontenay on 2010-03-08
> **woodbj said:**
> I get this but I just hold down enter and the login pops up

That totally works although my initial setting was to log in automatically. When I press enter I get the log in screen.

---

### Post by ndefontenay on 2010-03-08
Another cool addition was the auto fill of the configuration settings in Evolution.

I've configured my gmail account and as soon as I got it completed, it offered imap.gmail.com. Same for smtp.

If it fails to connect, it will display an error telling so and provide a link to google help. That is a very nice addition except.... The link is broken :(
I did find out quickly by searching gmail smtp though.
I suppose anybody redirected to google help could come up with that easily enough.

---

### Post by ratcheer on 2010-03-09
Why are there no new Lucid daily images for today (March 9)? They have pushed out a new kernel revision (2.6.32.16) since the March 8 images were published. So, I would think there should be new dailies.

Tim

---

### Post by Uncle Spellbinder on 2010-03-09
Just received some 105 updates. Among them 2.6.32.16. Seems there is an issue. I now get the indicator applet crashing constantly and the panel is borked. Clicking on panel icons seems to hide the panel for a second, then re-appear.  Some panel icons are not responsive. Same for the menu items in the panel. No idea if it's related to the kernel update or not, though.

---

### Post by VMC on 2010-03-09
> **ratcheer said:**
> Why are there no new Lucid daily images for today (March 9)? They have pushed out a new kernel revision (2.6.32.16) since the March 8 images were published. So, I would think there should be new dailies.

Tim

I wondered why there were so many updates after zsyncing today's daily-live. I foolishly thought I was upgrading from Mar08.

---

### Post by DoeRayMe on 2010-03-09
> **Uncle Spellbinder said:**
> Just received some 105 updates. Among them 2.6.32.16. Seems there is an issue. I now get the indicator applet crashing constantly and the panel is borked. Clicking on panel icons seems to hide the panel for a second, then re-appear.  Some panel icons are not responsive. Same for the menu items in the panel. No idea if it's related to the kernel update or not, though.

2.6.32.16 is totally messed up on my system, so i still use the -15 one at the moment.

Hopefully this problem is fixed soon

---

### Post by Uncle Spellbinder on 2010-03-09
> **DoeRayMe said:**
> 2.6.32.16 is totally messed up on my system, so i still use the -15 one at the moment.

Hopefully this problem is fixed soon
Wierd thing is,  2.6.32.15 is not present. The previous version was always left to choose if desired. It's not listed in grub. Just 2.6.32.16.

---

### Post by DoeRayMe on 2010-03-09
> **Uncle Spellbinder said:**
> Wierd thing is,  2.6.32.15 is not present. The previous version was always left to choose if desired. It's not listed in grub. Just 2.6.32.16.

-15 is still listed in grub for me, i have to boot into that to have a usable system :(

---

### Post by ratcheer on 2010-03-09
Ok. I had already cleaned the March 8 version from my system in preparation for today's. Looks like I will have to wait until tomorrow and see what it brings.

Tim

---

### Post by K. Hendrik on 2010-03-09
The new Dark theme isn't bad but the Dark-Menus are too much for me, I'd love it with light menus like the lighter theme and Aubergine highlighting for selected entries.

---

### Post by teh603 on 2010-03-09
> **K. Hendrik said:**
> The new Dark theme isn't bad but the Dark-Menus are too much for me, I'd love it with light menus like the lighter theme and Aubergine highlighting for selected entries.

The old appearance theme is still installed. Its just not the default anymore. Try System -> Preferences -> Appearance .

---

### Post by K. Hendrik on 2010-03-10
> **teh603 said:**
> The old appearance theme is still installed. Its just not the default anymore. Try System -> Preferences -> Appearance .

No, I don't mean the old theme I like the new better but I think It should be a little different.

---

### Post by imobomi on 2010-03-11
> **ndefontenay said:**
> That totally works although my initial setting was to log in automatically. When I press enter I get the log in screen.
I was having this issue too.  Removed plymouth, and now it goes straight to login.

---

### Post by ndefontenay on 2010-03-14
> **K. Hendrik said:**
> No, I don't mean the old theme I like the new better but I think It should be a little different.

The alternative also exists. It's theme name is Radiance. It's the white version of the same theme. I like it much better.

---

### Post by K. Hendrik on 2010-03-15
> **ndefontenay said:**
> The alternative also exists. It's theme name is Radiance. It's the white version of the same theme. I like it much better.

I know I'd like a theme with the Ambiance Windowboarders and Taskbar but the light menues of Radiance (and some more Aubergine for Highlightings)

---

### Post by Jazmac on 2010-03-15
Can anyone help?  I had Alpha 3 installed and looking sweet.  Set up Firefox and all was well until I decided to run synaptic to update whatever latest I may have missed.  Now when I boot up, I come to a black screen with a log in.  I log in and it's like I'm in a terminal.  No icons, no graphics nothing.  I'm running a dual boot on a Gateway MT6459  AMD 64 Turion.

How do I get to my desktop??

-Jazmac

---

### Post by IanW on 2010-03-15
Jazmac - Looks like you've caught [bug 538214]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214"). Try pressing Alt+F7.

---

### Post by nanonils on 2010-03-15
O sweet self inflicted software pain: test drove todays built Lucid alpha 3 for 64bit and found it worked flawlessly. 

I then upgraded. Result: unable to boot no matter what kernel I choose. 

Never mind this is a production machine (giggle). The live CD is working fine which I'm using to write this.

Can anyone advise what to do other than interrupt boot and go to the command line to install updates every now and then? Of course counting the days until the beta release on March 18 helps, too.

Attached is the screen shot at which the machine gets hung (not sure how I would report this to Launchpad).

Thaaanks!

---

### Post by Jazmac on 2010-03-15
> **IanW said:**
> Jazmac - Looks like you've caught [bug 538214]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214"). Try pressing Alt+F7.

I'll try that.  Thanks

-JazMac

---

