---
title: "Karmic frustrations: failed installation"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by michael37 on 2009-10-16
Today I tried to install Ubuntu Karmic LPIA onto my netbook.  My frustrations are highlighted with a tag **[COLOR="Red"](UGLY)[/COLOR]**

Tools used: A desktop running Windows XP and Ubuntu Karmic Beta Desktop edition.

Here is how it went.
[LIST=1]
[*]Searched for Karmic Beta version of karmic-alternate-lpia.iso.  
[*]**[COLOR="Red"](UGLY)[/COLOR]**Realized that [http://cdimages.ubuntu.com/ports/releases/karmic/](http://cdimages.ubuntu.com/ports/releases/karmic/) is actually empty.
[*]Downloaded a daily version from [http://cdimages.ubuntu.com/ports/daily/20091015/](http://cdimages.ubuntu.com/ports/daily/20091015/)
[*]Renamed .iso to .img (see [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)), as I would do with a netbook remix.  Downloaded Image Writer for Windows (see same link) and successfully wrote it to the USB stick.
[*]**[COLOR="Red"](UGLY)[/COLOR]**Disk won't boot, says no operating system. 
[*]**[COLOR="Red"](UGLY)[/COLOR]**renamed file back into iso.  So, is it not really a USB image?  Given that lpia is designed for netbooks, how many will actually have a CD-ROM?  Btw, my netbook doesn't boot from an external USB CD-ROM.  Boots just fine from USB sticks.
[*]Booted desktop into Ubuntu Karmic Beta Desktop. Installed usb-creator-gtk package using Synaptic.
[*]**[COLOR="Red"](UGLY)[/COLOR]**ran usb-creator-gtk, version 0.2.11 from karmic post-beta.  It finds USB stick, but is unable to format it or use it. 
[*]**[COLOR="Red"](UGLY)[/COLOR]**sudo umount /dev/sdb
ran fdisk and created a partition 1 to span all disk
formatted file system
sudo mkfs.ext3 /dev/sdb1
removed USB disk, reinserted it.  
usb-creator-gtk exited with "unable to install bootloader"
[*]reformatted it again
sudo mkfs.vfat /dev/sdb1
removed usb stick, reinserted it
usb-creator-gtk works this time, wrote .iso onto USB stick: /dev/sdb1
This is mostly described in bug 415103, the bus is NOT assigned so may not be fixed by Karmic release.  Did I mentioned ugly?
[*] Booted netbook from USB, selected option to install
[*] **[COLOR="Red"](UGLY)[/COLOR]**Result: Kernel Panic - not syncing: VFS: unable to mount root fs on unknown-block (104,1)
[*] .
.
And here is how the first installation failed. And there was evening, and there was morning, the second day. [Source: Genesis]
.
.
[*] On a hunch, I used a different 1GB USB memory stick.  The only perceptible difference by me, a user, was that the first stick was detected as "Removable Device - USB Storage" by BIOS, and the second stick was detected as "USB Storage Device".  Created partition, formatted it, and used usb-creator to build USB image from .iso
[*] Netbook booted from the USB flash stick. Grub worked.  
[*] Installation started successfully:  Language, keyboard, repository on flash disk, preconfiguration, installer, create users.
[*] **[COLOR="Red"](UGLY)[/COLOR]** Network configuration failed.  Tried to acquire DHCP.  Ubuntu needs restricted drivers for my wireless device, and my wireless network is password encrypted, so I am not even sure what installer was trying to do.  **Confusing for new users.**  Skipped this step.
[*] Partitioning worked flawlessly, considering a complex multi-boot scheme (I try to test a lot of versions, like netbook-remix on this netbook too).
[*] Install the base system worked. Configure apt worked.
[*] **[COLOR="Red"](REALLY REALLY REALLY UGLY)[/COLOR]**Apt detected 888 packages on the USB stick. Tried to install some packages, and aborted at about 50%. Error message: **"An installation step failed.  You can try to run the failing item again from the menu, or skip it and choose something else.  The failing step is: Select and install software"**
Skipped this step since I had no other options.  **[COLOR="Red"](UGLY)[/COLOR]** This is how the story would end for most users.
[*] Grub2 install worked. 
[*] Computer rebooted from hard drive into **[COLOR="Red"](UGLY)[/COLOR]** base system. That means text only, no graphics, no network.  
[*] Logged in as yourself in order to complete the installation by hand.  Manually mounted USB flash disk with repository on it.
sudo mount /dev/sdc1 /mnt
[*] **[COLOR="Red"](UGLY)[/COLOR]** Apt is still searching for CDROM which I don't have.  Changed /etc/apt/sources.list to look for 
deb file:/mnt karmic main restricted
[*] Thank you, maintainers, for creating a single umbrella package.
sudo apt-get install ubuntu-desktop
**[COLOR="Red"](UGLY)[/COLOR]** Aborted with Hash Sum mismatch errors for ttf-unfonts-core and ubuntu-wallpapers packages.
[*] Per apt-get suggestion, ran 
sudo apt-get install ubuntu-desktop --fix-missing
After an hour of work, an almost functional OS was installed.
[*] After that, tried to brute install two packages with hash sum problems.
sudo dpkg -i /mnt/pool/main/u/ubuntu-wallpapers/ubuntu-wallpapers_0.29_all.deb
**[COLOR="Red"](UGLY)[/COLOR]** Aborted with "corrupted filesystem tarfile - corrupted package archive".  
[*] Rebooted netbook, now with a familiar Karmic gdm login screen.  Logged into functional gnome session.
[*] Went into System -> Administration -> Hardware Drivers.  **[COLOR="Red"](UGLY)[/COLOR]** Tried to enabled restricted b43 wireless driver; failed to enable since needed packages are not installed
[*] Inserted USB stick with installation.  It was detected as a digital audio player.  Ubuntu offered to open it in Rhythmbox.  Hmm.
[*] Since the stick is mounted as /media/WIN98, changed /etc/apt/sources.list to 
deb file:/media/WIN98 karmic main restricted
Ran
sudo apt-get update
[*] **[COLOR="Red"](UGLY)[/COLOR]** Still failed to activate proprietary Broadcom driver.  No error message is given.
[*] Ran
sudo apt-get install --reinstall b43-fwcutter
It tries to download something from downloads.openwrt.org and **[COLOR="Red"](UGLY)[/COLOR]** fails since no network is available.
Come on, guys, I am trying to install the network driver here!
[/LIST]


I'd say Karmic is not ready for prime time.  Still 15 days to go...

---

### Post by Eclipse. on 2009-10-16
Well for a start mostly all your problems are not problems with karmic, just general things screwing up.

I understand what you are saying though about there being no .img install for LPIA.Download unetbootin from the archives and use that to get the .iso onto your usb drive.

---

### Post by nanog on 2009-10-16
.

---

### Post by coolbrook on 2009-10-16
> **nanog said:**
> With all due respect your problems have more to do with your inability to:

a) To find the appropriate place to download iso (hint: beta link on front page of [www.ubuntu.com](www.ubuntu.com))

[http://www.ubuntu.com/testing/karmic/beta](http://www.ubuntu.com/testing/karmic/beta)
[http://releases.ubuntu.com/releases/9.10/](http://releases.ubuntu.com/releases/9.10/)

b) Your failure to read the detailed instructions on how to make a bootable usb drive for install:

[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

And btw ubuntu daily images are not milestone *releases*. They are meant for testing purposes only and are often buggy and too big to fit on a cd.

[https://wiki.ubuntu.com/Testing/ISO](https://wiki.ubuntu.com/Testing/ISO)

Note red warning messages:
[http://cdimage.ubuntu.com/ports/daily-live/current/](http://cdimage.ubuntu.com/ports/daily-live/current/)


_ _ _ _ _

(rtfm)

Rude much?

---

### Post by michael37 on 2009-10-16
was: response to comment#3. deleted since comment was removed.

---

### Post by michael37 on 2009-10-16
> **Eclipse. said:**
> Well for a start mostly all your problems are not problems with karmic, just general things screwing up.

> **Eclipse. said:**
> 
I understand what you are saying though about there being no .img install for LPIA.Download unetbootin from the archives and use that to get the .iso onto your usb drive.
Agreed.  My intent is to identify the problems before release goes out in this messy state.

As you see, I used usb-creator.  A few lessons from this:
[LIST=1]
[*]No way to build functional USB image on Windows.
[*]usb-creator is an application from main.  Why use alternative from universe when one from main should do the job?
[*]usb-creator has a bunch of problems which are still not addressed
[/LIST]

---

### Post by null_pointer_us on 2009-10-16
> **michael37 said:**
> As you see, I used usb-creator.  A few lessons from this:
[LIST=1]
[*]No way to build functional USB image on Windows.
[/LIST]
Can you use [unetbootin for Windows]("http://unetbootin.sourceforge.net/") to write the USB image from .iso?

It's always worked fine for me though I'm not sure what the LPIA thing is.

EDIT: Nope, LPIA Karmic would still [fail when run from USB image]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1565354.html").

---

### Post by nanog on 2009-10-17
Ouch...apologize for my rudeness.

---

### Post by michael37 on 2009-10-17
Big update to the OP with juicy details.

---

### Post by radimvice on 2009-10-18
Question: Did you verify the MD5 checksum of the .ISO file after you downloaded it? If the checksum doesn't match, this would probably account for your problems starting with #20.

I just finished a similar install of Karmic LPIA on my Dell mini9 netbook and I ran into the same "Select and install software" failure during my install. Thanks to your suggestions, I manually set my USB key as the repository and finished up from the command-line.

My guess is that the integrity of the ISO file is the main issue that needs to be fixed here - after my failure I checked my ISO file and the checksum was invalid. I've since re-downloaded the daily 'karmic-alternate-lpia.iso' twice, and both times the checksum turned up invalid (with different signatures each time).

Turns out that in my case, it was the file 'libgs8_8.70.dfsg.1-0ubuntu3_lpia.deb' that had an invalid checksum, so I re-downloaded the file manually and replaced it on my USB key. After that, apt-get update and apt-get install ubuntu-desktop, and everything was fine after that.

Since .torrent files aren't available for the LPIA alternate install image (BitTorrent does a checksum of each small chunk as it downloads), I wonder if there's some other way users can download this ISO with all the bits intact, or possibly repair individual invalid components after the download? (Is this eventually what those .jigdo files could be used for?)

---

### Post by michael37 on 2009-10-18
> **radimvice said:**
> Question: Did you verify the MD5 checksum of the .ISO file after you downloaded it? If the checksum doesn't match, this would probably account for your problems starting with #20.

I just finished a similar install of Karmic LPIA on my Dell mini9 netbook and I ran into the same "Select and install software" failure during my install. Thanks to your suggestions, I manually set my USB key as the repository and finished up from the command-line.

My guess is that the integrity of the ISO file is the main issue that needs to be fixed here - after my failure I checked my ISO file and the checksum was invalid. I've since re-downloaded the daily 'karmic-alternate-lpia.iso' twice, and both times the checksum turned up invalid (with different signatures each time).

Turns out that in my case, it was the file 'libgs8_8.70.dfsg.1-0ubuntu3_lpia.deb' that had an invalid checksum, so I re-downloaded the file manually and replaced it on my USB key. After that, apt-get update and apt-get install ubuntu-desktop, and everything was fine after that.

Since .torrent files aren't available for the LPIA alternate install image (BitTorrent does a checksum of each small chunk as it downloads), I wonder if there's some other way users can download this ISO with all the bits intact, or possibly repair individual invalid components after the download? (Is this eventually what those .jigdo files could be used for?)

Interesting observation.  I ran into the same problem with corrupted install while trying Karmic alpha, but I ignored the problem assuming it was due to alpha.  I will definitely check the md5sum next time I download the iso.  See the right values in file MD5SUMS, same folder (e.g. [http://cdimage.ubuntu.com/ports/daily/20091019/](http://cdimage.ubuntu.com/ports/daily/20091019/))

---

### Post by eckertd on 2009-10-23
I've tried both Desktop and Alternate CD images (both pass MD5SUM check) and end up with a corrupt file during base install which causes it to abort

perl-modules_5.10.0-24ubuntu4_all.deb

---

### Post by snowpine on 2009-10-23
Curious why you are interested in lpia instead of "standard" ubuntu or netbook remix? It seems that lpia is not supported by Canonical any more, now that the Atom is well-supported by the linux kernel. Your troubles installing it support my hunch that lpia is not a priority for Canonical.

The i686 kernel (2.6.31) is running great on my Dell Mini 9. What would the benefit be of switching to lpia? Why do Debian, Arch, Fedora, etc. not come in lpia flavors? Curious to know more about the project since I've never really understood it. :)

---

### Post by michael37 on 2009-10-23
> **snowpine said:**
> Curious why you are interested in lpia instead of "standard" ubuntu or netbook remix? It seems that lpia is not supported by Canonical any more, now that the Atom is well-supported by the linux kernel. Your troubles installing it support my hunch that lpia is not a priority for Canonical.

The i686 kernel (2.6.31) is running great on my Dell Mini 9. What would the benefit be of switching to lpia? Why do Debian, Arch, Fedora, etc. not come in lpia flavors? Curious to know more about the project since I've never really understood it. :)

Why get a netbook in the first place?  To get a lightweight long-lasting computer which performs all daily functions.  LPIA consumes less power than i686 -> battery lasts longer -> I am happy.  The reverse is just as true.

---

### Post by snowpine on 2009-10-23
> **michael37 said:**
> Why get a netbook in the first place?  To get a lightweight long-lasting computer which performs all daily functions.  LPIA consumes less power than i686 -> battery lasts longer -> I am happy.  The reverse is just as true.

Interesting. What is your source please on the longer battery life? When I tested it for 9.04, the difference was negligible. I wonder if 9.10 has made some big new improvement?

---

### Post by michael37 on 2009-10-23
> **snowpine said:**
> Interesting. What is your source please on the longer battery life? When I tested it for 9.04, the difference was negligible. I wonder if 9.10 has made some big new improvement?

[Source.]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_power_usage&num=1")

What was your test procedure?  Unless you document it, it's not a particular valuable testimony...

---

### Post by snowpine on 2009-10-24
> **michael37 said:**
> [Source.]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_power_usage&num=1")

What was your test procedure?  Unless you document it, it's not a particular valuable testimony...

Re-read that article from back in March... we had several threads when it came out.

The article is NOT comparing Ubuntu i386 vs. Ubuntu lpia... it is comparing Ubuntu i386 vs. the "MID" edition. MID edition is a completely separate project; it does not use the Gnome desktop for one thing and is very stripped down (looks like a cell phone interface). Is the 11% power savings due to the lpia kernel or because MID is a "lightweight" distro that uses lower system resources?

My methodology was very unscientific, I confess. I installed Ubuntu 9.04 i386 and used it every day for a week. Then I installed Ubuntu 9.04 lpia and used it every day for a week. I got an average of 4 hours battery with i386 and 4 hours 5 minutes with lpia. 

I also used "Dellbuntu" lpia 8.04 (the factory pre-installed Ubuntu on my Dell Mini) briefly. It was terrible. :(

My contention is that, if the lpia kernel was the superior choice for the Atom processor, then surely Arch, Debian, Fedora, Slackware, or heck, even Moblin, the distro *invented by Intel* would offer it as a choice. How's it working out for you so far? ;)

---

### Post by michael37 on 2009-10-24
> **snowpine said:**
> My methodology was very unscientific, I confess. I installed Ubuntu 9.04 i386 and used it every day for a week. Then I installed Ubuntu 9.04 lpia and used it every day for a week. I got an average of 4 hours battery with i386 and 4 hours 5 minutes with lpia. 
It would help to have a solid assessment.  

Let me illustrate on an example: based on his own unscientific assessments, I have a friend who swears that 89 gasoline gives his car 10% better mileage than 87 gasoline.  He says he tested and he is totally certain.  Good testimony? ... except it is not scientifically possible.  More [here]("http://www.ftc.gov/bcp/edu/pubs/consumer/autos/aut12.shtm").  Anyway, that's off topic.

> **snowpine said:**
> My contention is that, if the lpia kernel was the superior choice for the Atom processor, then surely Arch, Debian, Fedora, Slackware, or heck, even Moblin, the distro *invented by Intel* would offer it as a choice. How's it working out for you so far? ;)
Actually, I am not convinced whether moblin kernel is i686 or lpia.  Lpia is not a true separate kernel, it's just a flavor of i686 kernel with slightly different compile flags.  For that reason, any i386 application runs just fine on lpia installation.  Here is my uname -a output as a proof.
Linux mycomputer 2.6.31-14-lpia #48-Ubuntu SMP Fri Oct 16 14:03:04 UTC 2009 i686 GNU/Linux

Overall, I am running Karmic 9.10 lpia and [thread="1294173"]it is working quite well[/thread]. Just painful to install.

---

### Post by snowpine on 2009-10-25
Cool, I just read your other thread... what are you getting for battery life, if you don't mind my asking?

Also, you might know the answer to this question: My new computer has an Atom 330, which is the dual core version. Do you recommend I go with lpia or 64-bit?

---

### Post by michael37 on 2009-10-26
> **snowpine said:**
> Cool, I just read your other thread... what are you getting for battery life, if you don't mind my asking?

Also, you might know the answer to this question: My new computer has an Atom 330, which is the dual core version. Do you recommend I go with lpia or 64-bit?

This is the first laptop which I can use in a cellphone mode.  Use during the day, charge at night.  My old laptops had to be hibernated and then took a while to wake up.  This one sleeps (and apparently consumes very little power while sleeping), and then wakes up in less than 30 seconds.  That's how I like it.  I use it to browse web, to check emails, facebook, IM, etc, and I turn it on and off all the time.  So I can't really answer your question how long it lasts.

[s]I definitely recommend lpia.  Atoms do not support 64-bit (so really 32-bit is your only other option)[/s] -- see next post.

---

### Post by michael37 on 2009-10-26
> **snowpine said:**
> 
Also, you might know the answer to this question: My new computer has an Atom 330, which is the dual core version. Do you recommend I go with lpia or 64-bit?
and I stand corrected, Atom 230 and 330 does support 64-bit.

Source: [http://www.intel.com/products/processor/atom/specifications.htm](http://www.intel.com/products/processor/atom/specifications.htm)

I have no idea how 64-bit would perform on Atom since I have Z series.  Try and tell us :) ?

---

### Post by snowpine on 2009-10-28
I've spent a few days testing different versions of Ubuntu on the Atom 330. 9.04 64-bit works fine; 9.10 64-bit was very crashy and freezy. Yesterday I tried 9.04 lpia and was very impressed with the speed of XP inside Virtualbox (a major concern of mine). Something about the lpia kernel is good for virtualization. I plan to test 9.10 lpia today. (edit: 9.10 crashed and burned... this Foxconn box seems to have trouble with compiz in Karmic (see [this bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/400934")). I've re-installed 9.04 lpia.)

It's confusing because this box seems capable of running all 3 architectures (i386, amd64, lpia)... which one to choose?

---

### Post by VMC on 2009-10-28
> **michael37 said:**
> and I stand corrected, Atom 230 and 330 does support 64-bit.

Source: [http://www.intel.com/products/processor/atom/specifications.htm](http://www.intel.com/products/processor/atom/specifications.htm)

I have no idea how 64-bit would perform on Atom since I have Z series.  Try and tell us :) ?

Wow, I didn't realize that any Atom chip had 64-bit instruction set, let alone dual-core.

---

### Post by snowpine on 2009-10-28
> **VMC said:**
> Wow, I didn't realize that any Atom chip had 64-bit instruction set, let alone dual-core.

The Atom 330 is basically two single-core Atoms side by side (from what I understand). Since it uses hyperthreading, it shows up as 4 cores in system monitor. :)

---

