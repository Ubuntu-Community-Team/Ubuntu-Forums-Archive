---
title: "Intrepid Alpha 1 released"
date: 2008-06-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Raptor45 on 2008-06-28
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-June/000440.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-June/000440.html)
[QUOTE=Steve Langasek]
  "Once the baby is strong enough to follow its mother, the pair joins other
   mothers and babies. The youngsters become independent quickly. An ibex
   kid can jump on its first day of life, and it joins kid groups by the
   fourth week. Even at an early age, lambs and kids are agile and alert.
   Although they are weaned by four to six months of age, they remain with
   their mothers for at least a year."

   [http://www.sandiegozoo.org/animalbytes/t-goat_sheep.html](http://www.sandiegozoo.org/animalbytes/t-goat_sheep.html)


Welcome to Intrepid Ibex Alpha-1, which will in time become Ubuntu 8.10.

Pre-releases of Intrepid are *not* encouraged for anyone needing a stable
system or anyone who is not comfortable running into occasional, even
frequent breakage.  They are, however, recommended for Ubuntu developers and
those who want to help in testing, reporting, and fixing bugs.

Alpha 1 is the first in a series of milestone CD images that will be
released throughout the Intrepid development cycle. The Alpha images are
known to be reasonably free of showstopper CD build or installer bugs, while
representing a very recent snapshot of Intrepid. You can download it here:

  [http://cdimage.ubuntu.com/releases/intrepid/alpha-1/](http://cdimage.ubuntu.com/releases/intrepid/alpha-1/) (Ubuntu)
  [http://cdimage.ubuntu.com/kubuntu/releases/intrepid/alpha-1/](http://cdimage.ubuntu.com/kubuntu/releases/intrepid/alpha-1/) (Kubuntu)
  [http://cdimage.ubuntu.com/xubuntu/releases/intrepid/alpha-1/](http://cdimage.ubuntu.com/xubuntu/releases/intrepid/alpha-1/) (Xubuntu)

See [http://wiki.ubuntu.com/Mirrors](http://wiki.ubuntu.com/Mirrors) for a list of mirrors.

The primary changes from Hardy have been the re-merging of changes from
Debian and the upgrade of the Linux kernel to a pre-release version of
2.6.26.

Please refer to [http://www.ubuntu.com/testing/intrepid/alpha1](http://www.ubuntu.com/testing/intrepid/alpha1) for information
on changes in Ubuntu.

This is quite an early set of images, so you should expect some bugs.  For a
list of known bugs (that you don't need to report if you encounter), please
see: [http://www.ubuntu.com/testing/intrepid/alpha1](http://www.ubuntu.com/testing/intrepid/alpha1)

If you're interested in following the changes as we further develop
Intrepid, have a look at the intrepid-changes mailing list:

  [http://lists.ubuntu.com/mailman/listinfo/intrepid-changes](http://lists.ubuntu.com/mailman/listinfo/intrepid-changes)

We also suggest that you subscribe to the ubuntu-devel-announce list
if you're interested in following Ubuntu development. This is a
low-traffic list (a few posts a week) carrying announcements of
approved specifications, policy changes, alpha releases, and other
interesting events.

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)

Bug reports should go to the Ubuntu bug tracker:

  [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Enjoy,
-- 
Steve Langasek
On behalf of the Ubuntu release team[/QUOTE]

---

### Post by |{urse on 2008-06-28
sweet ^^ been waiting for this to go alpha.

---

### Post by Nullack on 2008-06-28
Yep, Im on the download to start testing

---

### Post by Raptor45 on 2008-06-28
Been having trouble with the alpha install; haven't tracked down exactly whats wrong.

On boot it complained it couldn't find the iwl4965 firmware, and sure enough nothing in /lib/firmware exists.

EDIT: Turns out linux-ubuntu-modules for the new kernel doesn't seem to be in the repositories.

---

### Post by scokar on 2008-06-28
I had two issues w/kubuntu intrepid 64 bit alternative install

a) (user error) i did not want grub installed, was unable to 'cancel' so i gave it no device to install to.   system booted from grub to busybox --> reinstall

b) Xorg did not start. nvidia card,  generic driver. had to copy hardy xorg.conf file over.  difference was presence of:

Option          "UseFBDev"              "true"


removing that resolved issue (by copying Hardy xorg)

so far, i'm in  kde 4.x, able to run konqueror and post my feedback here. no other testing performed.

Thanks.

---

### Post by Nullack on 2008-06-28
Dammit :mad: Badf burn, formatted, no more iso, now the d/l is timing out and no mirrors have replicated yet

---

### Post by Raptor45 on 2008-06-28
Not timing out for me, but regardless: torrents are attached if you'd like to try them.

---

### Post by mattisking on 2008-06-28
Anyone know at what point Live CD's will be included?

---

### Post by Raptor45 on 2008-06-28
LiveCD is planned to be included in Alpha 2.

[http://www.ubuntu.com/testing/intrepid/alpha1](http://www.ubuntu.com/testing/intrepid/alpha1) :
> Alpha 1 does not include LiveCD images, only images with the Ubuntu alternate installer. Intrepid LiveCDs will be made available with Alpha 2.


---

### Post by Gina on 2008-06-28
Downloading it now (64bit)  :)  Started it when I got up - taking 2hrs plus - slow download only 80-90 KB/s.  Server must be busy! Everyone downloding.

---

### Post by Yes_It's_Me on 2008-06-28
Yep, I'm upgrading my desktop now!

I was going to wait and all, but...screw that!

---

### Post by kripkenstein on 2008-06-28
There is a funny situation with the torrents...

Currently 32 people are trying to download the basic one (i386-alternate, there is no live), but only 1 seed, me, and my upload speed is a paltry 12K :(

I set my bittorrent to superseeding, which should make the most of it, but at this rate those 32 people are not going to get satisfaction any time soon ;)

---

### Post by Nullack on 2008-06-28
Ill have time for bug reports on launchpad later but for now:

1. [Hardware clock fails to be set by any known method during boot]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/243798")
2. [Wrong boot drive is generated by grub and results in no boot unless user edits the menu.lst for the correct drive]("https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/243803")
3. [PcSpeaker enabled by default in pulse audio]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/243804")
4. [Compressed archives (mine was a zip) arent being extracted in file roller I had to command line the extraction]("https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/243807")
5. [AppArmor isnt working]("https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/243810")
6. IMHO the usability of the new theme is poor and Im sorry to say I dont think I couldnt live with it
7. [In sources, release upgrade is incorrectly set to only LTS]("https://bugs.launchpad.net/ubuntu/+bug/243813")
8. [Given up for now on the .09 NVIDIA driver for my 8600 GT. Too many GPU errors and sometimes it would not log me in from the GDM, taking me back to the GDM during user logon unexpectedly,.]("https://bugs.launchpad.net/ubuntu/+bug/243817")

---

### Post by Gina on 2008-06-28
I still can't get past the partitioning stage on my AMD64 - still unable to create or modify partition for the system.

---

### Post by shuttleworthwannabe on 2008-06-28
screenshots...please...

---

### Post by Nullack on 2008-06-28
> **Gina said:**
> I still can't get past the partitioning stage on my AMD64 - still unable to create or modify partition for the system.

I always do a manual partition setup anyway so I cant comment on that use case. Manual works fine.

---

### Post by kripkenstein on 2008-06-28
> **shuttleworthwannabe said:**
> screenshots...please...

Here you go...

---

### Post by shuttleworthwannabe on 2008-06-28
nice..what fonts are you using? Why the hardy wallpaper and "black" panels? Is the theme in ibex going to follow the mobile Ubuntu route? That will look great! Glassy icons and all.
S

---

### Post by Gina on 2008-06-28
> **Nullack said:**
> I always do a manual partition setup anyway so I cant comment on that use case. Manual works fine.I was using Manual - I too always use Manual (except if I particularly want to check another option).

Photo of error attached :-

---

### Post by kripkenstein on 2008-06-28
> **shuttleworthwannabe said:**
> nice..what fonts are you using? Why the hardy wallpaper and "black" panels? Is the theme in ibex going to follow the mobile Ubuntu route? That will look great! Glassy icons and all.
S
Um, I don't know the answer to any of those questions, this is a fresh install from 5 seconds ago ;)

That's what it looks like out-of-the-box (and without Compiz).

---

### Post by Nullack on 2008-06-28
I had many problems getting the .09 nvidia driver working. Patched it using the Devs patch, but the xorg.conf was very fussy. Below is what is working for me now:

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

In particular it doesnt seem to like having dynamictwinview turned to false

EDIT: Ive given up for now on the nvidia patched driver. I would get GPU errors and it would recover, but then sometimes it would not let me log on from GDM where it would bounce back to the GDM during user logon.

---

### Post by spamzilla on 2008-06-28
Install via VirtualBox 1.62 worked fine and intend to upgrade my laptop for alpha to or 3 whenn they are released.

---

### Post by obscur156 on 2008-06-28
Thanks guys,i am running it right now and every thing is ok.So far so good.Just hoping that it will be better than hardy for video driver cause i can only get low res with nvidia driver with hardy.So my main OS is Gutsy but probably its just me.Nice work to all the DEVS working on it.

---

### Post by Mazza558 on 2008-06-28
There should be a theme chooser during installation.

---

### Post by MadsRH on 2008-06-28
> **kripkenstein said:**
> Here you go...
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=75580&stc=1&thumb=1&d=1214647899[/IMG]


OH MY GOD!!! This is hideous and certainly a step down after the beautiful Hardy release :(

I hope this will change dramatically before the final release

---

### Post by ronacc on 2008-06-28
mater of taste . I actualy like the dark window background better .

---

### Post by go7Ul1ai on 2008-06-28
Is there any way I would be able to download this theme without upgrading to Alpha 1? There should be a way to package it or something?

Cheers to anyone who can do this for me,

Lee

---

### Post by Gina on 2008-06-28
> **MadsRH said:**
> OH MY GOD!!! This is hideous and certainly a step down after the beautiful Hardy release :(

I hope this will change dramatically before the final releaseMy sentiments exactly.

---

### Post by Manosdoc on 2008-06-28
[ATTACH]75594[/ATTACH] Another screenshot

Nasty bug in iwl3945 "Microcode not found" in 2.6.26-2 kernel
My wireless 3945 messed up.

Also Pulseaudio messed up with Intel HDA

---

### Post by Manosdoc on 2008-06-28
> **lee.jarratt said:**
> Is there any way I would be able to download this theme without upgrading to Alpha 1? There should be a way to package it or something?

Cheers to anyone who can do this for me,

Lee

It must be on Intrepid incoming Artwork wiki
Check it. You should find other nice Themes there..

---

### Post by soccerboy on 2008-06-28
I just finished d/ling the hardy image.   Let's get back to downloading now.

---

### Post by go7Ul1ai on 2008-06-28
> **Manosdoc said:**
> It must be on Intrepid incoming Artwork wiki
Check it. You should find other nice Themes there..

Thanks man, made my day :)

---

### Post by PRGUY85 on 2008-06-28
Although I am one of the many that are clamoring for a new theme, this dark theme isn't cutting it for me.  Maybe it is just filler before the actual thing.

---

### Post by Mazza558 on 2008-06-28
> **Manosdoc said:**
> [ATTACH]75594[/ATTACH] Another screenshot

Nasty bug in iwl3945 "Microcode not found" in 2.6.26-2 kernel
My wireless 3945 messed up.

Also Pulseaudio messed up with Intel HDA

Wow, wait, is this using the new RGBA Murrine engine? I see transparency!

---

### Post by Gina on 2008-06-28
**Update on Alpha 64 bit install problem.** 
Tried Hardy and got same error - ran the TestDisk on SystemRescueCD and it found no problem with the HD or partition table etc.  However, trying to set up and format a new partition with GParted also failed - so I think I may have a hardware problem.  Now trying a partition, known to be good, that I used for one of my Hardy installs.  Alpha install has passed the partitioning stage successfully (it seems) and went on to other stages.  It is now sitting at 43% **Configuring apt** and **Scanning the mirror...** it's been at that point for over half an hour now which is NOT the usual behaviour.  I don't think anything more will happen however long I wait! :(  Going to try installing Hardy (or maybe the 32bit version)

---

### Post by psyke83 on 2008-06-28
> **lee.jarratt said:**
> Is there any way I would be able to download this theme without upgrading to Alpha 1? There should be a way to package it or something?

Cheers to anyone who can do this for me,

Lee

Here you go: [http://ubuntuforums.org/showpost.php?p=5266732&postcount=26](http://ubuntuforums.org/showpost.php?p=5266732&postcount=26)

---

### Post by psyke83 on 2008-06-28
> **Mazza558 said:**
> Wow, wait, is this using the new RGBA Murrine engine? I see transparency!

Yes, although the RGBA effects may be disabled in the theme before the final release.

---

### Post by Manosdoc on 2008-06-28
> **Mazza558 said:**
> Wow, wait, is this using the new RGBA Murrine engine? I see transparency!

yes! I did it on purpose to check this in my screenshot!
It looks cool

---

### Post by Manosdoc on 2008-06-28
> **lee.jarratt said:**
> Thanks man, made my day :)

No prob!
Check here, the Comic gel theme
[https://wiki.ubuntu.com/Artwork/Incoming/Intrepid](https://wiki.ubuntu.com/Artwork/Incoming/Intrepid)

---

### Post by ajmal_82 on 2008-06-28
hey,guys chill.i am there isnt anything worth watching in alpha.so dont write cd's and waste them.wait for next alpha if something significant comes then upgrade.upgrade using synaptic or use images inside xp/win like wubi dont waste cd's.i heard cd material is not recycle-able.

---

### Post by Nullack on 2008-06-28
> **ajmal_82 said:**
> hey,guys chill.i am there isnt anything worth watching in alpha.so dont write cd's and waste them.wait for next alpha if something significant comes then upgrade.upgrade using synaptic or use images inside xp/win like wubi dont waste cd's.i heard cd material is not recycle-able.

Sorry, but thats nonsense. There is important bugs to identify, report and get resolved. I for one want the gold release of Intrepid to be the best ever......

---

### Post by psyke83 on 2008-06-28
> **ajmal_82 said:**
> hey,guys chill.i am there isnt anything worth watching in alpha.so dont write cd's and waste them.wait for next alpha if something significant comes then upgrade.upgrade using synaptic or use images inside xp/win like wubi dont waste cd's.i heard cd material is not recycle-able.

Well then, perhaps we should take the initiative to save the environment, and create a new kind of CD that can be reused. Ladies and gentlemen, I will call this new format a "re-usable CD"...

Seriously, there's plenty to test in alpha 1 and there's no need for negativity. We need more people to test, file bug reports and contribute to Ubuntu in a positive way.

---

### Post by plun on 2008-06-28
> **Manosdoc said:**
> yes! I did it on purpose to check this in my screenshot!
It looks cool

Complete list of RGBA supported apps

[http://www.cimitan.com/murrine/rgba-support/list](http://www.cimitan.com/murrine/rgba-support/list)

Some work to apply patches for non official apps   :)


Just great anyway...

---

### Post by ronacc on 2008-06-28
> **ajmal_82 said:**
> hey,guys chill.i am there isnt anything worth watching in alpha.so dont write cd's and waste them.wait for next alpha if something significant comes then upgrade.upgrade using synaptic or use images inside xp/win like wubi dont waste cd's.i heard cd material is not recycle-able. 
 5 USES FOR OLD CD's

1 coasters for big drinks
2 furnature levelers
3 frisbies
4 opart projects
5 wheels for real smal soapbox racers

---

### Post by Exsecrabilus on 2008-06-28
The theme sucks ***.

---

### Post by Manosdoc on 2008-06-28
> **Exsecrabilus said:**
> The theme sucks ***.

It Actually rocks.
One thing I would rip off and change is the Icoset.
Too much fisher-prise.
For a proffesional look new-up to date modern icons needed.
There are tons...

---

### Post by mitchellcipriano on 2008-06-28
Has anyone had success getting a good install in VirtualBox? I get an unknown boot option quickly followed by a crash.

---

### Post by soccerboy on 2008-06-28
i installed in virtual box but installed using hardy live image.  The new kernel keeps crashing in virtualbox.  I didn't like the theme in the screenshots but now that I am in it I love it.  I second the opinion of a better iconset.  We have compiz already, let's get 3d icons (I know I can install it myself but for the inexperienced user).

---

### Post by KrazyPenguin on 2008-06-28
> **ronacc said:**
> 5 USES FOR OLD CD's

1 coasters for big drinks
2 furnature levelers
3 frisbies
4 opart projects
5 wheels for real smal soapbox racers

Hopefully you folks use CD-R's for testing.
:shock:


They last years!!!

;-)

---

### Post by mivo on 2008-06-28
> **ronacc said:**
> mater of taste . I actualy like the dark window background better .

I don't. That's just very hard on the eyes. Looks good if you glance at it for a few minutes, but it isn't ergonomic if you look at it for hours. I'd get a headache from the dark window backgrounds within a couple hours.

I do agree that the installer should offer three or four different themes to choose from (and I don't mean the stock Gnome ones), since people have different preferences and needs.

---

### Post by msrinath80 on 2008-06-28
> **Nullack said:**
> Sorry, but thats nonsense. There is important bugs to identify, report and get resolved. I for one want the gold release of Intrepid to be the best ever......

Actually, the original poster's comment does have some merit. The major change that Intrepid Ibex will feature when compared to Hardy Heron is the new GNOME, which is yet to be released. Other than that everything else is a minor upgrade, maybe even the kernel.

---

### Post by ronacc on 2008-06-28
> **msrinath80 said:**
> Actually, the original poster's comment does have some merit. The major change that Intrepid Ibex will feature when compared to Hardy Heron is the new GNOME, which is yet to be released. Other than that everything else is a minor upgrade, maybe even the kernel.

which even if true does not in anyway diminish the need to find, report and fix bugs

---

### Post by kevpan815 on 2008-06-28
I Used The (Sudo Update-Manager -D) Command 2 Upgrade From 8.04 And It Works Just Fine, Just As Long As I Don't Try It In A Wubi.Exe Install.

---

### Post by Exsecrabilus on 2008-06-29
Can somebody post a screenshot with Firefox and Nautilus open?

---

### Post by douham on 2008-06-29
Here you go. I changed to Human-Murrine the, the default theme on the iso is a bit ordinary.

---

### Post by spamzilla on 2008-06-29
Alpha 1 seems to work very well. Compiz / AWN works fine, intel 4965 wireless chip works out of the box, finally the blacklight issue on my laptop seems to be fixed and things just feel snappier. However, sound is borked atm but it was on Hardy too.

---

### Post by philinux on 2008-06-29
Yeah I've got the login and logoff sounds but when I go to prefs>sound and try test I get zip.

---

### Post by VChief on 2008-06-29
I just installed Alpha 1 in VirtualBox. If everything works ok on that, I have a partition that's just itching to be used as a help to the Ubuntu community. That way, I can give some real feedback on any issues it may have on this kind of laptop (Thinkpad T61). Looking forward to helping out.

---

### Post by Seventh Reign on 2008-06-29
I love the new theme.  Dark, easier on the eyes and easy to read.

Has anyone created an actual Ibex wallpaper yet?

---

### Post by Seventh Reign on 2008-06-29
Nevermind lol I found them

---

### Post by Exsecrabilus on 2008-06-29
> **douham said:**
> Here you go. I changed to Human-Murrine the, the default theme on the iso is a bit ordinary.
I kinda wanted to see how the folder icons were and it displayed text on the default dark theme..... ^_^;;

---

### Post by JACooks on 2008-06-29
> **Exsecrabilus said:**
> I kinda wanted to see how the folder icons were and it displayed text on the default dark theme..... ^_^;;

Here you go!

---

### Post by mivo on 2008-06-29
Horrible. Matter of preference, I know, but this looks just very unergonomic and amateurish.

---

### Post by caish5 on 2008-06-30
Maybe this theme is deliberately awful so we'll all accept the current theme for another 10 releases!

---

### Post by vishzilla on 2008-06-30
Yuck! :P the theme is disgusting....I feel the Chocolate theme is a better choice to work on if they are going with the brown

---

### Post by Nullack on 2008-06-30
Why are yall so hung up on the GUI theme in gnome :) Theres alot more substantial issues IMHO. I dont use Linux because of a gnome theme. To me its about security, robustness, having good packages available etcetc.

I encourage people testing the Alpha to get into the system more deeply.

---

### Post by Gina on 2008-06-30
Not bothered personally.  Anyway, since I use a separate /home partition, installing the Alpha didn't change the Theme - I'm on Human-Murrine from Hardy - I like that :)

---

### Post by Seventh Reign on 2008-06-30
seriously .. there are an infinite number of color combinations and ways to make your system look.  You can make your Ubuntu Pink, Neon Green, and Lavender if you prefer.  So they chose a theme that not a lot like as the default.  How many people stay with the Default theme on ANY Distro?

---

### Post by Lorenz on 2008-06-30
Wow, I sure hope the look will be upgraded. Doesn't look too good at all, in my opinion. But I'm sure they are trying a lot :)

---

### Post by Gina on 2008-06-30
They've changed themes several times in the development phase of previous versions, I see no reason for this one to be any different.  Don't worry about it. :)

---

### Post by ronacc on 2008-06-30
Ah the traditional theme,iconset,color,background discussion starts again . next come the polls.

---

### Post by kripkenstein on 2008-06-30
> **ronacc said:**
> Ah the traditional theme,iconset,color,background discussion starts again . next come the polls.
lol, so true :) It's like a ritual in these parts.

---

### Post by Kevbert on 2008-06-30
Kubuntu Alpha release install went well on my AMD64.  Keyboard recognized correctly as GB (Logitech wireless keyboard).  Deleted old partition, space reused by auto-setup.  Recognized WinXP, Ubuntu 7.10 and Kubuntu 8.04 and added to new grub menu.
Unfortunately when rebooted asked for username and password in text mode.  As soon as I entered this received an error -
b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4)
b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed
This message was continually repeated and had to reboot (Ctrl-Alt-Del) to get out of it.
Went to lib/firmware directory and no files are shown.
Have bcm4306 wireless card and had ethernet card connected to router during install.
Will post back once installed software.

---

### Post by Nullack on 2008-06-30
> **kripkenstein said:**
> lol, so true :) It's like a ritual in these parts.

An unfortunate one too because it distracts attention from the real things that matter most.

---

### Post by scradock on 2008-06-30
> **Kevbert said:**
> Kubuntu Alpha release install went well on my AMD64.  Keyboard recognized correctly as GB (Logitech wireless keyboard).  Deleted old partition, space reused by auto-setup.  Recognized WinXP, Ubuntu 7.10 and Kubuntu 8.04 and added to new grub menu.
Unfortunately when rebooted asked for username and password in text mode.  As soon as I entered this received an error -
b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4)
b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed
This message was continually repeated and had to reboot (Ctrl-Alt-Del) to get out of it.
Went to lib/firmware directory and no files are shown.
Have bcm4306 wireless card and had ethernet card connected to router during install.
Will post back once installed software.

That's normal - any new install will be lacking the proprietary drivers. You will need to install them using fwcutter. What I do is to keep a copy of the whole firmware directory hidden away and copy it into the /lib/firmware dir as soon as I can. Then even if the wired connection doesn't work the wireless connection will.

I saw the same warning the other day - it also says that "support for [version 3] drivers will end on July 1st 2008". It may be that the move to version 4 drivers will become obligatory. Does anyone have any information about this?

---

### Post by psyke83 on 2008-06-30
> **Nullack said:**
> An unfortunate one too because it distracts attention from the real things that matter most.

I would argue you're wrong. Part of the reason why people choose Ubuntu over Debian is due to the extra effort taken to make the system more user-friendly and appealing in many areas, and artwork is one of these areas.

I would say that moaning is not helpful, but offering constructive criticism and suggestions can help immensely.

---

### Post by Lorenz on 2008-06-30
> **Nullack said:**
> An unfortunate one too because it distracts attention from the real things that matter most.

Quite on the contrary - I would think that looks matter a lot.

By the way, I think that black/dark themes are overrated. I got the feeling that many real Ubuntu geeks love them, combined with Conky and I-don't-know-what-else, but overall I think light themes are more easy on the eye and less geeky.

---

### Post by ronacc on 2008-06-30
since things like artwork ,themes etc are so very subjective and also very eaisly changed (customised) theese endless discussions of them resolve nothing and serve only to give those of us who are hanging around the dev forum something to chew on while wating for breakage .

---

### Post by Kevbert on 2008-06-30
> **scradock said:**
> That's normal - any new install will be lacking the proprietary drivers. You will need to install them using fwcutter. What I do is to keep a copy of the whole firmware directory hidden away and copy it into the /lib/firmware dir as soon as I can. Then even if the wired connection doesn't work the wireless connection will.

I saw the same warning the other day - it also says that "support for [version 3] drivers will end on July 1st 2008". It may be that the move to version 4 drivers will become obligatory. Does anyone have any information about this?

Thanks Scradock.  Where's the best location to save these files ?  I've copied the firmware to my Intrepid Home directory.  Now I just need to extract and install them.  I may try the Broadcom one on Gutsy as I can't get my wireless to turn on (in Gutsy) since the error occurred. Could I used the small firmware file generated in /lib/firmware (Gutsy) directly in Intrepid ?

---

### Post by Nullack on 2008-06-30
The look is subjective, and its easily changed.

There is far more important issues than the look. The architecture of the system - the security of the system - the performance of the system - the functionality of the system. Thats where real contributions can be made instead of incessant opinions about the look.

Every release far too much focus is put on the look instead of people being observant and astitute.

How many bugs have you all raised?

What functionality have you tested?

Like another poster also pointed out, there's too much focus on the trivial and not enough on the detail.

---

### Post by psyke83 on 2008-06-30
> **Nullack said:**
> The look is subjective, and its easily changed.

Ah I see. Let's give up then, and set the default theme to Clearlooks and use the GNOME icon theme.

> **Nullack said:**
> There is far more important issues than the look. The architecture of the system - the security of the system - the performance of the system - the functionality of the system. Thats where real contributions can be made instead of incessant opinions about the look.

Before I talk about artwork, let me acknowledge your point that other aspects of development are important - very important.

> **Nullack said:**
> Every release far too much focus is put on the look instead of people being observant and astitute.

How many bugs have you all raised?

What functionality have you tested?

Like another poster also pointed out, there's too much focus on the trivial and not enough on the detail.

There are technical issues that need attention, in fact. Many GTK applications are buggy and require patching to become compliant to dark themes. For example: Firefox's Preferences (icon's text), VLC's Settings, Gnome Control Center - all of these have issues with dark themes, where the text colour is chosen incorrectly.

The reason why the input background of NewHuman isn't white is that it will cause these applications to display white text on a white background, so having a light brown allows us to at least see the text. We need issues like these identified and fixed.

There's no need to whine about artwork, because there is a lot of constructive work to do in this area, just like every other part of Ubuntu.

---

### Post by Nullack on 2008-06-30
Im glad you recognise that it doesnt end with artwork. People will be drawn to the aspects of the system that appeals to them - great. Though when it becomes a matter of the majority seeming to download the releases to look at artwork then the quality of Ubuntu suffers.

To give an example so you can see where Im coming from, one bloke came on here and said that nothing was really new and it wasnt worth "testing" or indeed burning a CD for because thats bad for the environment.

In the interests of achieving a top quality outcome I think we should be encouraging people to get deep into the system - to explore functionality - to observe - to report bugs.

I personally applaud your efforts to do so with getting into the details of the look and I hope that other people will put their best in too.

---

### Post by mivo on 2008-06-30
> **ronacc said:**
> since things like artwork ,themes etc are so very subjective and also very eaisly changed (customised) theese endless discussions of them resolve nothing

First impressions are important. Yes, people can change the appearance easily, however, most casual users, to whom Ubuntu wants to appeal to, will not want to do that. It is hard enough to get people to even try out Ubuntu (or any Linux), and if what they first see is not attractive, then that's it. Chance blown. I personally like the current default theme, but I stopped using Ubuntu as introduction to Linux. I use a Mint or DreamLinux Live CD for that purpose now.

These discussions could achieve something: The decision makers realising that it would be a clever move to include several themes and let the user choose one during installation (or offer them through the settings). 

If they have to go with only one, it should be a theme that meets ergonomic standards and is suited for use in an office.

---

### Post by soccerboy on 2008-06-30
I just tried to copy files from my laptop running ubuntu to my iMac.  When i copied files to my thumb drive it took less than a second.  When I copied them to my iMac from my thumb drive it took over 15 seconds.  I say kudos to the developers for making memory access so fast in linux.  I tried the reverse too, copying files from my iMac to ubuntu, same result.  Faster in ubuntu.
I am happy gvfs is now able to give the speeds it promised. (bug solved)

---

### Post by Kevbert on 2008-06-30
Using AMD64 Kubuntu version, multibooted with XP, Ubuntu 7.10, Kubuntu 8.04.
Finally wireless is working (however KNetworkManager shows unknown device and  vendor).  Card is a Broadcom BCM4306.  Seems to work fine.
Had problem getting Xserver running by modifying xorg.conf.  Just couldn't get graphical interface up (I'm using a Nvidia Geoforce 7600GS). Tried using
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` 
This failed to resolve my problem. Even tried using Kubuntu 8.04 xorg.conf but that didn't want to know.  Got around problem by booting into recovery mode and using the menu option to reconfigure xorg (and it worked first time). 
Next problem is updates.  The only way I can install updates is via terminal as any other way asks for root passwords.  It's the same for installing other programs.
The new Kickoff menus look flash, though the Classic ones are fine.

---

### Post by Gina on 2008-06-30
For getting nVidia graphics working with Intrepid and the latest kernel see [THIS THREAD]("http://ubuntuforums.org/showthread.php?t=810661")

Edit... I should add that this is a bit complicated.  You might be able to get the correct screen resolution by editing **xorg.conf** and using the **nv** driver (though it didn't work for me).  

OOPS must be half asleep :lolflag: you got it working :)

---

### Post by Seventh Reign on 2008-06-30
I suppose its probably because I dont run alot of the "heavy/extensive" programs that alot of you guys/gals use.  I basically install the system, add Amarok, k3b, vlc, and the NORMAL version of xchat (hate the gnome version), and I'm done.  I dont mess around with AWN, Conky, Compiz(much), Cairo-Dock etc.  I also dont have wireless (yet), bluetooth, or a printer.  So I'm guessing thats why my install of 8.04 was so flawless.  Now I've upgraded my "Playaround-Backup" system to II, and I'm genuinely impressed.  If I didnt know that this was just an Alpha, I wouldnt believe it.  I've only been running it for about 9 hours, but so far with all the stuff I use installed its been perfect.  

Shoot, at this point I'll be afraid to run anymore updates for the chance it screws up an ALREADY stable system :-(

---

### Post by caryb on 2008-06-30
On the topic of Ubuntu artwork there has been a niche industry spring up because of the perceived failure of Ubuntu to do a decent theme/artwork. I have been looking at mint Linux from my very quick look all I can see is it is Ubuntu with a decent theme:confused: I personally use Kubuntu because I don't like the Ubuntu colours. (colors for our US friends)

Please don't interpret this as a flame or a rant! I just want to point out that others are thinking the same & the consequence is fragmenting Ubuntu into other distros to remedy what I see as a failing.


Cary

---

### Post by mbarvian on 2008-06-30
> **JACooks said:**
> Here you go!

ha, you even got his post in that screenshot :D

---

### Post by philinux on 2008-06-30
sudo dpkg-reconfigure -phigh xserver-xorg

This command does not configure graphics.

xorg.conf is a stub file now.

Without the -phigh it will only configure mouse and keyboard.

System Prefs Screen Resolution or xrandr is the "new" way and friendly recovery mode which has in its menu xfix.

---

### Post by lockerhaxor on 2008-06-30
I'll probably start testing this, as I want to help out, and frankly, my Ubuntu Machine isn't my primary. So no need to be stable lol.

EDIT: Page snipe.

---

### Post by Gina on 2008-07-01
You don't use Ubuntu as your primary OS???? :shock:  :eek:  :wink:

---

### Post by Exsecrabilus on 2008-07-01
> **mbarvian said:**
> ha, you even got his post in that screenshot :D
What can I say? I'm to awesome to miss in any photo shot/shoot.

---

### Post by zekopeko on 2008-07-01
well i'm pretty excited with this release because we are getting a lot of eye-candy. and /me loves eye-candy.
check out some of macslow's mockups and blueprints

[https://blueprints.edge.launchpad.net/~macslow](https://blueprints.edge.launchpad.net/~macslow)

[https://wiki.ubuntu.com/DesktopTeam/Specs/SpitAndPolish](https://wiki.ubuntu.com/DesktopTeam/Specs/SpitAndPolish)

if we could get rounded corners and transparency it would rock. and i hope that the memaker and gdm-face-browser with openGL will make it in this release.

i believe if ubuntu/gnome/linux could get the same level of "spit and polish" (consistency) as OSX it would surely attract people to it. imagine 1000's of windows/osx converted developers contributing code to linux/xDE ecoystem... now THAT would be a force to be recond with.

---

### Post by Nullack on 2008-07-01
I dont see those blueprints on the Intrepid schedule?

---

### Post by zekopeko on 2008-07-02
woops! my bad. it's a future goal of macslow i would say. but it could creep in intrepid (crosses fingers and hopes macslow is a coding robot powered with a fusion reactor)

---

### Post by quique1hn on 2008-07-03
Kubuntu alpha 1 didn't work. right now I using Ubuntu alpha 1... so for so good:lolflag:

---

### Post by tech0007 on 2008-07-05
I've successfully upgraded one of my machines to alpha1 using 'update-manager -d' and is working fine so far.  I want to upgrade the VM on my hardy laptop which has slower connection.  So i burn the iso. Can I just run 'gksu "sh /cdrom/cdromupgrade"'?

I like the new theme in II. It's cool.

---

### Post by TFrog on 2008-07-08
> **mitchellcipriano said:**
> Has anyone had success getting a good install in VirtualBox? I get an unknown boot option quickly followed by a crash.

I was able to install Kubuntu 8.10 Intrepid on Virtualbox 1.6.2 from Sun.  Works like a champ.  Still looking for someone who knows how to get the Broadcom drivers working in Intrepid.  I have a spare hard drive for this laptop I'd like to use for testing while I keep my working hard disk with Hardy only.

The key to getting 8.10 Intrepid to install in Virtualbox is to shut down the ACPI driver and also turn off the ACPI switch during install of Intrepid.  I believe this was an issue when Hardy first went Alpha as well.  Try turning ACPI off both in the virtual machine and during install of Intrepid.  Should work fine.  After install you can then turn on ACPI in your virtual machine.

One last coment to all, QUIT TALKING EYE CANDY AND LOOKS.  THEY ARE UNIMPORTANT AT THIS STAGE OF DEVELOPMENT.  REPORT BUGS, FIXES, AND WORKAROUNDS.  I'm so sick of people talking about looks and eye candy in an Alpha release.

---

### Post by caryb on 2008-07-08
TFrog, I setup a lot of IBM servers with Broadcomm nics, I found that Ubuntu finds the card with lspci but the problem is in the /etc/network/interfaces file if you edit it to look like this & restart networking it should work.

```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```

I use a static address on my servers but from memory the dhcp did work.

Cary

---

### Post by monsterikan on 2008-07-08
i'm redirecting my question to this thread:

if i upgrade my hardy heron to intrepid ibex (alpha), can i roll back the version to hardy? because i really need intrepid ibex for a glance review.

btw, what is the difference between alternate and server?
so this alpha version has no desktop installation?

---

### Post by Archmage on 2008-07-08
> **monsterikan said:**
> if i upgrade my hardy heron to intrepid ibex (alpha), can i roll back the version to hardy? because i really need intrepid ibex for a glance review.

Nope, you can't and at the moment Ipex isn't looking that good as it will look at the end.

---

### Post by monsterikan on 2008-07-08
thx for the info. 
maybe instead of "upgrading" my linux, i should install it in a new partition

---

### Post by autocrosser on 2008-07-08
I have Hardy for a stable backup & two testing Ibex--one I fresh-install at alpha/beta points & one I just upgrade steady from the last stable release. I recommend that you DO NOT share /home(s)--Partition so you can reinstall the OS in case of a "blow-up" & keep your home intact afterwards.

Take a look at the HowTo by Raptor45--- [http://ubuntuforums.org/showthread.php?t=852857](http://ubuntuforums.org/showthread.php?t=852857)  Good info in that thread.

---

