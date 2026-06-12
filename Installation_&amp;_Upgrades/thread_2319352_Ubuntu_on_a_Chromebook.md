---
title: "Ubuntu on a Chromebook"
date: 2016-04-03
forum: Installation &amp; Upgrades
---

### Post by jebediah on 2016-04-03
Hi guys.
Recently i bought a Dell Chromebook that i'm happy with, but i'm missing some functions that i need.
So i googled and found out that Ubuntu works great with Chromebook. But i have some question that i can't find on the wild web.
If i decide to go back to Chromebook OS, how do i make a backup?
Also, is there any known problems with running Ubuntu on a Chromebook?

---

### Post by RobGoss on 2016-04-03
Hello and welcome, From what I know I don't see why you would not be able to revert back to chrome book OS if need. You should make a complete backup of that OS before you try installing Ubuntu. I don't know much about Chrome book despite it's a Google OS / android. I use [Clonezilla ]("http://clonezilla.org/")for all my backup and it works flawlessly, keep in mind there're many other backup methods as well. 

I'm not sure if you know it but you can [try Ubuntu ]("http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install")with out installing it to see how it preforms on your machine if everything goes well you can simply install it.

---

### Post by TheFu on 2016-04-03
ChromeOS has a 'reload chromeOS app' - must be installed from the chrome-store.  [https://support.google.com/chromebook/answer/1080595?hl=en](https://support.google.com/chromebook/answer/1080595?hl=en)

It is possible to "brick" some chromeOS devices.  I have a bricked Acer C720.  To debrick it, I need about $50 in hardware. Since it was already 19 months old when the keyboard stopped working and there were some other issues, I decided to replace it with a newer, faster, more RAM, higher resolution model.  Using it now.  It isn't perfect, and I've been unable to get Ubuntu to load with whole disk encryption. A portable device without whole disk encryption is almost worthless to me.  All versions of Ubuntu from 14.04 and later that I've tried have provided challenges to get the video, networking, touchpad, etc ... working.  Just sayin'.  Tried debian this week - never got any video to work.  Have to try Arch and Fedora next.

**Don't buy a chromebook expecting to get a perfectly working Linux machine. There are challenges.  If you want a Linux machine, much better off going with a normal laptop.** However, some normal laptops aren't easy to get Ubuntu/Linux running on either.  Video, wifi, audio are the normal challenges. If you stick with Intel CPUs that have onboard GPUs, that handles the video stuff almost always.  Intel WiFi is usually well supported too - the 7250 AC chips work.  Audio is a crap-shoot. I don't have any recommendations around that, but I usually purge pulseAudio-* from my systems just like I purge nano and unity-*   That's me. Everyone is different.

There are lots of different chromebooks and many of them have well-worn solutions to get a specific Linux distro working - mostly. Do some searching **before** buying a Chromebook if you plan to run Ubuntu.  The C720 line had reasonable support, for example.  I thought the Toshiba CB35 line had good support too - found people who claimed to have Ubuntu running ... but they had it running without whole disk encryption, I guess. 

There are multiple ways to run a normal Linux distro on chromebook hardware.  
* chroot - crouton
* boot off external USB disks - not ideal and if these are flash memory, it will be slower than you'll like. External SSDs connected to USB3 ports may be a reasonable alternative.
* replace ChromeOS completely - there is a risk of bricking the system.  I did by not reverting to stock ChromeOS before disconnecting the battery.  Many (all?) chromebooks don't have CMOS batteries, so the main battery needs to always have some charge to hold non-default settings.

For most normal end-users, I would steer them away from all of these warranty-breaking solutions.  Even running crouton requires HW changes on most chromebooks (maybe all).   I had to physically remove electrical connections to get crouton working on my newer chromebook to allow developer mode to work.  Without developer mode - you can forget booting and running normal Linux.  The write-protection removal voided the warranty.  The same applied to the Acer C720 and Toshiba chromebooks.

Whatever you do, best to get a non-Atom CPU. Watch out for the N2xxx versions - those CPUs really suck.  The newer Celeron versions are nice.  I wouldn't touch an ARM-based Chromebook - lots of challenges when running a different CPU architecture, but some people like the challenge.

Anyway - hope this provides some realistic expectations.  It definitely is NOT plug-in-play.

---

### Post by jebediah on 2016-04-03
Hi guys and thanks for fast reply :)
Never thought it was that big challenge to run Ubuntu on a Chromebook, but hey, i like challenges.
I'll give the LiveCD a try and see what happens.

Guess i'll be back with more questions later :D

---

### Post by RobGoss on 2016-04-03
That's the only way to enjoy such a great distribution and the best thing of all we learn from our mistakes....Good luck

---

### Post by TheFu on 2016-04-03
> **jebediah said:**
> Hi guys and thanks for fast reply :)
Never thought it was that big challenge to run Ubuntu on a Chromebook, but hey, i like challenges.
I'll give the LiveCD a try and see what happens.

Guess i'll be back with more questions later :D

You'll need to do some pre-boot work first. Chromebooks don't just boot of any flash/USB devices.  The normal USB flash drive for Linux is the easy part. You'll have to open the case, void the warranty, break a specific-for-the-model-chromebook electrical connection to even get that to happen.  Sorry if that wasn't clear before.

Every chromebook is a little different, so instructions that you seek aren't generic. They are SPECIFIC for the exact model of chromebook you have.   For example, I have a "Toshiba Chromebook 2", but they've made 6 different models with that same name over the years. The instructions are different for each of them.  Online, the screw to remove is different between the models too.  I had to guess, fortunately, I got it correct according to photos found 4 weeks later.

Didn't mention this, but many Chromebooks don't allow "disk" storage to be upgraded. They use eMMC storage, chich is soldered onto the MB.  What I wanted was m2.SSD - which both the C720 and Toshiba C3350 have.  The C3350 is a cheap ultrabook without the $700 price, IMHO.  RAM connect be upgraded on any chromebook I've seen. 2G is fine for lite use, but 4G really makes these machine puuuurrrrrr.

Just to clarify - I have a Toshiba CB35-C3350 (Core i3 5015U) model. The CB35-C3300 with a Celeron has a nice, fast, CPU for $100 less too.
Why did I want the Toshiba?  Sub 3lbs, 8hrs battery, 1080p and 4G of RAM.  Everything else is available on cheaper models from everyone else.  The Dell is heavier and more costly, but Dell keyboards ARE MY FAVORITE.

---

### Post by jebediah on 2016-04-03
Followed [this guide]("https://www.youtube.com/watch?v=UWXO61_v_xo") and it worked untill 2:05
When i hit CTRL+L i only hear some beeps and nothing more.

Have to find some more guides :)

---

### Post by xmbwd on 2016-04-03
I highly recommend heading over to [John Lewis' site]("https://johnlewis.ie/custom-chromebook-firmware/rom-download/") and installing SeaBios.  It lets you use a Grub bootloader.  You should then head over to the [coreboot on Chromebooks]("https://plus.google.com/communities/112479827373921524726") community page, where you can find helpful install instructions and guides.  Like the Ubuntu community, those folks are very helpful.

---

### Post by jebediah on 2016-04-04
After some trial and errors i finaly got Ubuntu to work, and only with two "problems" :)
First one is that i have to start Ubuntu using sudo startunity from ChromeOS, not a big deal.
But the second one is a litle harder to fix. My Wy-Fi wont work.

Did some more reading and noticed that many recomended GalliumOS, so i will give it a try later.


> **xmbwd said:**
> I highly recommend heading over to [John Lewis' site]("https://johnlewis.ie/custom-chromebook-firmware/rom-download/") and installing SeaBios.  It lets you use a Grub bootloader.  You should then head over to the [coreboot on Chromebooks]("https://plus.google.com/communities/112479827373921524726") community page, where you can find helpful install instructions and guides.  Like the Ubuntu community, those folks are very helpful.

Thanks xmbwd. I'll give it a read and see how much i understand :D

---

### Post by TheFu on 2016-04-04
If you are still running ChromeOS, then you are probably NOT booting Ubuntu. You are booting chromeOS and running inside a chroot.  Please confirm.  Any help is VERY different depending on the way you are running.

For example, did you open and remove the BIOS write protect screw and break that electrical connection?

Sorry - can't watch youtube.

---

### Post by jebediah on 2016-04-04
> **TheFu said:**
> If you are still running ChromeOS, then you are probably NOT booting Ubuntu. You are booting chromeOS and running inside a chroot.  Please confirm.  Any help is VERY different depending on the way you are running.

For example, did you open and remove the BIOS write protect screw and break that electrical connection?

Sorry - can't watch youtube.

Thats correct. ChromeOS is booting up and i have to use some commands to launch Ubuntu.
I have not made any changes to the hardware what so ever.

---

### Post by TheFu on 2016-04-04
I'm surprised it is working at all.  On my chromebooks, flashing the BIOS was required and to do that, removing the BIOS protection screw was mandatory.

So you are using crouton?  If so, there are 3 commands to know - you'll probably need to run these weekly, since google can push an update that breaks the OS running inside the chroot.  Last week, that happened to me TWICE. Thanks google.

```
# Backup - not using the default location - specify EXACTLY the backup file
sudo edit-chroot  -f ./crouton-2016-mm-dd.tgz -b trusty

# Update / patch the "trust" crouton chroot OS. Run only when it isn't booted.
sudo bash ./crouton -u -n trusty

# Restore - from the exact backup file you specify
sudo edit-chroot -r trusty  -f ./crouton-2016-mm-dd.tgz  
```

You may need to reinstall/refresh the crouton script after a google update is forced down.  I only run ChromeOS as guest - never login with gmail account - so all the data is wiped every logout/reboot of ChromeOS.  I'm a control freak, so I always want to specify which files are used for the backup/recovery.  Plus, since the default backups are put under the HOME, that doesn't work for my "guest" chrome user.  I backup to a 500G USB external drive. That partition is mounted to /var/host/media/removable/xyz

Wifi/networking ... Ubuntu or any OS running in the chroot (under crouton) don't get to control the networking.  That all happens inside chromeOS.  Use the chromeOS settings to manage that.  It also handles all sound and microphones.  These things tend to break every time google pushes an required/mandatory chromeOS update.

I think that running sudo apt-get update/upgrade from inside the chroot is still required, but I'm not positive.  The "crouton -u" command above is definitely required, however.

Hope this helps and doesn't make more confusion.

---

### Post by jebediah on 2016-04-04
> **TheFu said:**
> I'm surprised it is working at all.  On my chromebooks, flashing the BIOS was required and to do that, removing the BIOS protection screw was mandatory.

So you are using crouton?  If so, there are 3 commands to know - you'll probably need to run these weekly, since google can push an update that breaks the OS running inside the chroot.  Last week, that happened to me TWICE. Thanks google.

```
# Backup - not using the default location - specify EXACTLY the backup file
sudo edit-chroot  -f ./crouton-2016-mm-dd.tgz -b trusty

# Update / patch the "trust" crouton chroot OS. Run only when it isn't booted.
sudo bash ./crouton -u -n trusty

# Restore - from the exact backup file you specify
sudo edit-chroot -r trusty  -f ./crouton-2016-mm-dd.tgz  
```

You may need to reinstall/refresh the crouton script after a google update is forced down.  I only run ChromeOS as guest - never login with gmail account - so all the data is wiped every logout/reboot of ChromeOS.  I'm a control freak, so I always want to specify which files are used for the backup/recovery.  Plus, since the default backups are put under the HOME, that doesn't work for my "guest" chrome user.  I backup to a 500G USB external drive. That partition is mounted to /var/host/media/removable/xyz

Wifi/networking ... Ubuntu or any OS running in the chroot (under crouton) don't get to control the networking.  That all happens inside chromeOS.  Use the chromeOS settings to manage that.  It also handles all sound and microphones.  These things tend to break every time google pushes an required/mandatory chromeOS update.

I think that running sudo apt-get update/upgrade from inside the chroot is still required, but I'm not positive.  The "crouton -u" command above is definitely required, however.

Hope this helps and doesn't make more confusion.


Thanks! Gonna bookmark this thread so i know where i can find those commands when needed :) Thanks again.

I just found [COLOR=#252525][FONT=sans-serif]MattDevo's RW_LEGACY bios which seems kinda cool, with working dual-boot. Have to give it a try with GalliumOS.[/FONT][/COLOR]

---

### Post by jebediah on 2016-04-08
So back again with some new questions.
Currently i'm running both ChromeOS and GalliumOS with dual-boot thanks to Crouton.

1. How do i remove the current Linux dist? I've done a Powerwash several times but still i'm able to boot into Gallium. I've even turned of developer mode, but looking at the storage i can't see any different, so i guess the Linux dist is still on the drive?
2. I've tried GalliumOS, Lubuntu and Ubuntu and all of them has the same problem. The sound doesn't work. So i tried to find a solution and stubled over this [LINK]("https://plus.google.com/+JamesFuBEEFCAKE/posts/Tf4Pc5Z8reH"). But no one explain how to copy that file from ChromeOS. How do i do that?

---

### Post by TheFu on 2016-04-10
How to remove depends on how/what you installed.  Crouton has a built-in option to remove stuff - check the help for instructions.  I've never used "powerwash" - find it easier to wipe the SSD (I replaced the 16G original with a 64G and a 128G (other box).  Sound is funky, but works once you understand it is a passthru from ChromeOS via crouton.  There's a "cras" sound driver on mine.  Sometimes the hardware in the chromeos settings expect headphones, so verify that isn't it.  Sometimes I have to insert and remove a headphone jack to get it reset.  With a true dual-boot, sound was just like any other PC - needed the correct drivers to work.  Standbye stuff needed special driver resets ... highly model dependent.  Again - FIND A HOW-TO FOR YOUR SPECIFIC MODEL OF CHROMEBOOK for more help.

How to copy files? Open a terminal and use the cp command. This isn't point-n-click time.
```
cp /path/to/some/source-file  /path/somewhere/else/target-file
```
Lots of short-cuts. You can learn those on day 1 of any basic linux training.  Absolute paths vs relative paths and save much typing. I only use full-paths when absolutely required.  May need to copy to ~/Downloads/ or /tmp/ first. Using temporary areas is a common theme with Unix. I think both of those areas are shared by crouton between both OSes.

If the permissions are fine, that should work. If not, use sudo and fix the target-file permissions.  Be careful NOT to overwrite existing files - manually check.  With tab-completion, this stuff doesn't need much typing. If tab-completion isn't understood - watch a youtube video ASAP. It is easy to use and understand, but a video is 1000x easier to understand than reading about it.  I'm amazed at the number of youtube Linux training videos that don't use tab-completion.  Not sure I'd stay in a class being taught by any instructor NOT using it. </rant>

---

### Post by jebediah on 2016-04-12
> **TheFu said:**
> How to copy files? Open a terminal and use the cp command. This isn't point-n-click time.
```
cp /path/to/some/source-file  /path/somewhere/else/target-file
```
Lots of short-cuts. You can learn those on day 1 of any basic linux training.  Absolute paths vs relative paths and save much typing. I only use full-paths when absolutely required.  May need to copy to ~/Downloads/ or /tmp/ first. Using temporary areas is a common theme with Unix. I think both of those areas are shared by crouton between both OSes.

If the permissions are fine, that should work. If not, use sudo and fix the target-file permissions.  Be careful NOT to overwrite existing files - manually check.  With tab-completion, this stuff doesn't need much typing. If tab-completion isn't understood - watch a youtube video ASAP. It is easy to use and understand, but a video is 1000x easier to understand than reading about it.  I'm amazed at the number of youtube Linux training videos that don't use tab-completion.  Not sure I'd stay in a class being taught by any instructor NOT using it. </rant>

If i try that command i only got -No such file or directory
Which is wierd since asound.state should be placed at /var/lib/alsa/

---

### Post by mail-2o on 2016-04-12
Thanks for this thread. I was considering a Chromebook and don't mind a challenge, but a multiday challenge I can do without, so am grateful that you have stopped me going down this route and also that you are prepared to persevere.

---

### Post by jebediah on 2016-04-13
> **mail-2o said:**
> Thanks for this thread. I was considering a Chromebook and don't mind a challenge, but a multiday challenge I can do without, so am grateful that you have stopped me going down this route and also that you are prepared to persevere.

I guess it would be 100 time easier if you are familar with linux. For me it's been at least 15 years since i played around with a linux dist, so starting with flashing a chromebook is a big challange

---

### Post by jebediah on 2016-04-14
So after a day of trail and error and found out that Ubuntu 14 "Trusty" with XFCE or LXDE desktop environment work best om my Dell.
I skipped the dual-boot firmware and launch Ubuntu from the terminal instead. It's cool to be able to switch back to ChromeOS in a sec when it's needed.

The only "problem" i can't solve is the system language and keyboard layout. The only desktop environment i stumble upon that has some kind of menu where i can choose language is Enlightenment "E17"
I guess there's some command or script to run for downloading new language, but that's out of both my and googles knowledge.

---

### Post by TheFu on 2016-04-14
Seems you are way passed the original question. Time to open a thread for any other question separately.

However, running in a chroot under chromeOS, which is what you are doing, has security and privacy implications.  Maybe it doesn't matter to you.

For language support, there are different ways to enable/add it.  Plus, I suspect that running in a chroot has important impacts to the results. Be certain to mention that, if you ask for help.  Don't think there is a GUI way.

---

