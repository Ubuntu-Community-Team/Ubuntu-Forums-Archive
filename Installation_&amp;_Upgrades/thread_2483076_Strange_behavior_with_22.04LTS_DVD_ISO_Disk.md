---
title: "Strange behavior with 22.04LTS DVD ISO Disk ?"
date: 2023-01-19
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2023-01-19
Been using Linux and Ubuntu for over 15 years. Finally decide to DL the ISO file for 22.04LTS. Then burned it to a Verbatim DVD+R 4.7 GB disc using Brasero. Set Brasero burn speed as low as it allowed 6x.  Brasero then did the checksum test after the burn and reported no errors found and reported the burn was a success.

Put that 22.04 DVD into my desktop PC, shown in my signature below, to see what 22.04 looked like and how it ran. Here things got strange. It took forever to load up 22.04. After 10 minutes it first said it failed to load 22.04! Then 10 minutes later 22.04 finally opened. All this 20 some minutes plus, my PC was clicking away, along with hearing the disc spinning up at varying speeds, while trying to open 22.04. Well PC kept clicking away even after 22.04 opened. Was able to play around/use 22.04. At first Firefox was not there, then FF icon did popup allowing FF to be used, getting me on the Internet. All this never happened before all the times trying to give a new version of Ubuntu a test drive!

 When first using 22.04 it was very slow in doing anything. Much slower than any other version used this way. However as time went on things did speed up significantly when using 22.04 on the DVD. By now all that extraneous PC clicking and disc spinning up had ceased. Things now seemed normal.  Liked what I saw in 22.04, while getting used to this new OS. 

This all makes me worry how the 22.04 install will go? Will the install go as all earlier versions went smoothly, or will it be strange also? Thoughts and guidance on this?

---

### Post by guiverc on 2023-01-19
Ubuntu hasn't intended DVD or ***optical***media to be the installation media for some time, very few users used it, so it was opted to not concentrate it from Ubuntu 20.10 and later releases. Ubuntu 22.04 LTS is a few releases beyond 20.10; so why did you opt for *optical* media?

Yes is was proved that 22.04 can boot, and can install from optical media; but that install can take in excess of an hour, and it can take up to three boots/installs to get everything correct, as *timeout* issues on the *optical* drive can be misinterpreted by the running programs, which show unhelpful error messages (*and won't receive due to errors detected on hardware; even though they're just timeouts*).

Ubuntu releases from 20.10 upwards *scan the media for errors*, and whilst this doesn't take long on *flash* media as is expected to be used, you often need to wait the full hour for *optical *media if the drive you're using is a few years old (*ie. spins inconsistently regards revolutions/min*).

I suggest you re-try using a *supported* and *intended *installation media - such as flash drive.

Optical media is not intended to be used (*as installation media*) on any Ubuntu product since Ubuntu 20.04 LTS.

---

### Post by cybrsaylr on 2023-01-20
Thanks guiverc.

I did not know that. The reason I tried a DVD install was a few years ago I had problems doing the flash drive install. For some reason when trying that it just would not work. Used the optical drive to create a DVD for install and it installed 20.04LTS smoothly with no problem. 

So will try using the Startup Disk Creator on 20.04 and hope all past issues have been resolved.
What is the best size Flash drive to use?

Always preferred doing a clean install of all new Ubuntu versions, rather than using the Upgrade option when using Software Updater for updates to all Ubuntu versions.

---

### Post by guiverc on 2023-01-20
FYI: I'd liked to have provided links for more details for my prior reply, but 20.10 was quite a while ago now, and there a numerous bug reports filed over issues relating to ISO changes that started with Ubuntu 20.10 (*the first release where all architectures of Ubuntu was built to boot the same way; ie. an amd64, ppc64el, s390x, arm64 etc. system will boot identically for a given release regardless of machine architecture; this did not apply with 20.04 & before*).  I* could   have gone looking for reference links, but whilst I'm aware one issue was finally resolved with 22.10, some got marked 'won't fix'.*

Best size flash drives depends on the ISO being used; my *Lubuntu 20.04 LTS* was on 2GB, but recent Lubuntu ISOs require 4GB.  Many *flavors* and main Ubuntu can require 8GB thumb-drives.

Some *architectures *are smaller than others too, so it'll depend on a number of factors you've not provided.  (*Your signature maybe a clue that you want amd64, but many signatures are outdated so I can't assume it's accurate*).

The *smallest* thumb-drives are 8GB when I look for them at the local office supplies stores (*in multipack*), so they'll do, but some ISOs will fit on smaller (eg. 22.10 kinetic LIVE server ISO for *s390x* is only ~1GB in size!).  Currently all ISOs will fit on 8GB I believe.

I'll recommend you verify the ISO as being valid ([https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)) but in my experience that's not the problem, I find about 5-8% of my ISO writes to *flash media* are faulty, and require me to write it again.  Also note that's with Sandisk brand thumb-drives, with my error rates higher with other brands.  Thus I always check the media validation successfully completed prior to starting install.

FYI: *I'm involved with QA or Quality Assurance testing; and have written two ISOs to thumb-drive just today; a jammy daily (what will be released as 22.04.2) & a lunar daily (what will be released as 23.04); both Lubuntu amd64 actually, so whilst 5-8% ISO write to media may not seem a bad failure rate, I find failures far too regularly... Flash media is a CHEAP CONSUMABLE product, made to cost.. It's still good media (I've left flash-drives in my pockets & they've been through the wash & once dried, I could still retrieve data before I threw device out..) but problems with it occur!  It's not high-quality like spinning-rust or solid-state drives that have quality checks built into the device - it's low-end consumer electronics.  I've had best luck with Sandisk brand myself.*

---

### Post by cybrsaylr on 2023-01-22
A little update. Installed 22.04 on my i7 PC with multiple OSs but 22.04 will not boot up.

Since burning that DVD and since checksum test reports no errors, decided to use it to see what 22.04 looked like. Like what it showed. The DVD worked but took ~30 minutes just to fully load 22.04 for a test drive. After 30 minutes my i7 PC calmed down. No more clicking and optical drive spinning up at varying speeds. Then 22.04 ran quite nicely off that DVD. 

Then decided to install 22.04 off my DVD. Used this very helpful YouTube clip for help and advice on how to install: [https://www.youtube.com/watch?v=ESkuXK71Y74](https://www.youtube.com/watch?v=ESkuXK71Y74)
Followed that YT video after figuring what to do. My system has 3 SSDs with multiple OSs, running Windows 10, Ubuntu 20.04, 18.04, 16.04 and 14.04 that all run fine. Decided to install 22.04 on the SSD partition where 16.04 was. Studied this out well beforehand ... I thought. It actually took 15 minutes to fully install 22.04. 

Got the prompt to restart PC after removing 22.04 DVD on restart.  Did that and PC booted up into 20.04 using the 20.04 bootloader which always showed a choice of Ubuntu at the top for 20.04, then listed below were Ubuntu 18, 16 Windows 10 and Ubuntu 14. There was no new 22.04 screens and 22.04 bootloader. 

Tested this out and all OSs still open and run fine except for Ubuntu 16 where I attempted to install 22.04 onto! When trying to open Ubuntu 16, I get an error message saying this device does not exist! 
When I click on, Files > other options, the partition 22.04 exists and is on there fully but will not let me boot up into 22.04. 
Suspect there is a GRUB issue here.

Can anyone help?

---

### Post by JPWhite on 2023-03-25
> **guiverc said:**
> Ubuntu hasn't intended DVD or ***optical***media to be the installation media for some time, very few users used it, so it was opted to not concentrate it from Ubuntu 20.10 and later releases. Ubuntu 22.04 LTS is a few releases beyond 20.10; so why did you opt for *optical* media?



Here is a reason. It is an ideal format for long term storage of a Live CD. I work on all sorts of broken PC's and being able to quickly flip through DVD's to the version of Ubuntu or Knoppix I want is great. I know what I am getting.

With a USB drive its not easy to store, plus the contents may change even I could find a simple way to label the USB drive. Yes USB is much faster but for diagnostics especially at a remote site a swiss army knife of DVD's is much better than a handful of USB drives.

---

### Post by ne29914 on 2023-03-25
Interesting topic, I'll be following this.
I have the opposite problem: I'm unable to live boot or install newer versions from USB thumb drives, but DVD works perfectly.
My old 20.04 thumb drive will also install fine, all newer installs fail.

---

