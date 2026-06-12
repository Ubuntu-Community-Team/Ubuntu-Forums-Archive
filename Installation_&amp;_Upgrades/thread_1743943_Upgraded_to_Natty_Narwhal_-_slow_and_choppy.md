---
title: "Upgraded to Natty Narwhal - slow and choppy"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by mankypro on 2011-04-29
This morning I did the upgrade on my year old ASUS NV51n to Natty.

Had to get the new NVIDIA graphics drivers and disable noveau - that was OK.

Unfortunately Unity and booting into the new kernel made the laptop so slow and unusable I decided to try the option to run Ubunty-Classic - basically the same effect.

So I booted into my previous kernel - 2.6.35-22-generic #35-Ubuntu SMP - and the laptop is as snappy as ever.

I'd sure like to give the new OS a spin, but it takes 5 minutes to load Thunderbird!

Any ideas on where to start to figure out what's wrong?

---

### Post by becatlibra on 2011-05-01
I have a very similar issue.  I have an Asus EEE 1000 netbook which was running Meerkat.  I was using a standard Gnome desktop on it and it ran okay.  It's a model with SSD rather than standard HDD and has the MAX ram the unit can handle.

I upgraded to narwhal 2 nights ago and the netbook is now unusable.  Programs take forever (minutes) to load.  I tried to ssh into a server and the session just hung.  I have tried killing off processes like gwibber and the improvement was next to nothing.

Now I am faced with very few options.  Either I can reload the thing with meerkat (or another distro like arch) or I can wait and hope someone can help me.  I would prefer to not have to do the work of reloading at this point and believe a downgrade to be impossible.

Anyone have any ideas what the problem might be?

Thanks

B

---

### Post by dylanthomasfan on 2011-05-01
I have exactly the same problem. I had a great desktop setting, fast and responsive. Now I have an annoyingly slow desktop.

I would not have upgraded if not for the message when I logged on console that said I should upgrade.

Is there a way to downgrade?

These messages should NOT appear for beta software.

---

### Post by jahrome on 2011-05-01
agreed, question now is, whether there will be fixes for these or whther we should choose to reinstall completely. (if so, i wouldn't choose ubuntu again.)

---

### Post by dylanthomasfan on 2011-05-01
There are a bunch of responses out there saying I should match the refresh rate, but I am not sure how to go about doing this in compiz configuration. The options are simply not available!

---

### Post by DestroiTe on 2011-05-01
My desktop also feels somewhat slugish, but not as bad as you guys describe. I'm considering a clean install. You guys should as well...

---

### Post by becatlibra on 2011-05-02
Almost positive that a fresh installation isn't going to help.  Frankly I don't want to waste the time with re-installing Natty.  It performs like a hippo on skates.  Disappointed that no one has chimed in with any questions working towards a solution.

If I am going to reinstall again, I am thinking I'll go with Arch like I run on my workstation at work.  With it's rolling release cycle, upgrades are slightly less painless.

Please though if anyone has any idea why Natty is being so damn slow, let us know.

-B

---

### Post by giuseppe.morana on 2011-05-02
Hi guys,
I've just upgraded to natty and my desktop gone slow.
I read this post:

[http://ubuntuforums.org/showthread.php?t=1742335](http://ubuntuforums.org/showthread.php?t=1742335)

and I think I solved my problem.
It seems there was a refresh rate issue.
I hope this will be helpfull for you too.

---

### Post by becatlibra on 2011-05-03
I seriously doubt this involves the refresh rate.  I could see where refresh rate could be an issue however even an SSH session in terminator was slow/unresponsive.

I'll take a look at it when i get home and let you guys know.

-B

---

### Post by mörgæs on 2011-05-03
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

especially the two posts at the top.

---

### Post by zyrorl on 2011-05-04
I have the exact same laptop and same problem as you. No problems on 10.10 completely unusable on 11.04 this is frustrating. I did a clean install after it didn't work with upgrade. I'm downgrading to maverick for the time being. Not a good experience at all. When I first booted upgraded version, running old kernel really was snappy too, I'm clear the new kernel is to blame... FYI I tried those links posted in the thread nothing helped

---

### Post by TheCuomo on 2011-05-05
Yeah same thing here. I didn't realise this was such a large change. I guess I'm just used to clicking "Update" whenever the screens pop up and trusting that whatever happens will be good!

Anyway I fixed the issue for me, though I doubt my solution will have use for many others. I have an msi U135DX, and an additional monitor. I unplugged the monitor to put in another computer, as I was going to transfer all my data and reinstall 10.10. Then suddenly Natty was working perfectly smoothly, the dock thingy scrolls smoothly, things open at normal speed etc. 

The refresh rate of the additional monitor was already set to 60 Hz as someone mentioned earlier, but for me it was the resolution. Changing the additional monitor to 1024 x 768 (from 1280 x 1024) suddenly fixed everything - my desktop image appeared, so did the files on the desktop.

Maybe that's useful to someone, I dunno.

---

### Post by nariub on 2011-05-05
Upgraded a good 10.10 (64bit) to 11.04 (64bit) online
and the GUI slowed to a crawl, in classic and in the new UI.
I can ssh into the box and it appears as happy as ever.
 
It takes longer to boot than 10.10
after user/pass it take nearly two minutes to put the background up.
it takes another 3 minutes or so to put anything on the desktop (menu or icon)
I have not yet been able to launch anything from the new or classic UI
 
Classic version seems to clip off the power/logout button on the top right, which is how I discovered that ssh was working fine.
 
<CNTRL-F2> gets me to a command prompt to, but it appears to be a bit sluggish for some reason.
 
Mine is a Dell E510/5150, Pentium D Dual Core 2.6G, 4G RAM (dell bios only allows me to see 3.2G), 2x 2T Seagate HDs in RAID1 on the ICH7R, 180G OS / Remainder HOME directory, to get around the GPT boot issue.  Nvidia 7300 LE with 512M video.
 
dont know the current refresh rate or if it has anything to do with it.
would like to know where to check/change this from a commandline as that would be much quicker.
 
I too regret hitting the upgrade button.
I am considering putting 10.04.2 on it so I wont have to deal with it again until 2012.
 
---
side note,
11.04 (64bit) live disc is crappy slow on the machine above too.
  and doesnt complete a boot on a Dell Latitude E6510 (Intel Graphics) while in a docking station.
  pull the Laptop out of the docking station and it works fine and is quite snappy.
  the touchpad even works for tap selection, and up/dn scrolling couldnt seem to work out left/right scrolling.  Nonetheless, I will likely put 10.04.2 on the laptop and pull in some backports to get the touchpad working.

---

### Post by zyrorl on 2011-05-05
anyone find a solution to this yet?

---

### Post by FelipeAragao on 2011-05-06
I'm getting the same anoying response.
Seems like this is gona take long. Such huge problem won't be fixed sonner than 11.10.

Gotta go reinstall 10.10. Who's with me?

---

### Post by WarriorPoetess on 2011-05-06
Well, at least there is one happy person here!):P

Upgraded this morning on HP Pavilion 6700 series. It seems that every system on here loves the new Natty Norwhal. The Wifi, monitor, touchpad, and CD/DVD burner with LightScribe. Not one hitch along the way!! This ole gal loves the new look...however...

I had Maverick working as a private server so that I can test web pages before posting them to the web. This causes the question of: Can a LAMP be installed into this system? If so, would the standard installation be able to be done in the usual apt-get method? (This includes Apache2, PHP5, Perl, Ruby, and PHPMyAdmin.)

If anyone knows it would be greatly appreciated!

Roberta-Jean

---

### Post by BertN45 on 2011-05-06
11.04 uses more memory, if you have e.g. skype and banshee open you already use 0.5 GB. So if you have less then 1Gb of memory things will be slow. On my 3 years old 2GB ex-Vista laptop it works fine, it is a little bit slower then 10.10, especially e.g Firefox when started for the first time. The second time it starts within a second.

With less then 1GB of memory, I would go back to Ubuntu 10.xx or use Xubuntu 11.04, which has a number of great improvements. I can recommend it, since I use it on on my desktop.

---

### Post by zyrorl on 2011-05-06
> **FelipeAragao said:**
> I'm getting the same anoying response.
Seems like this is gona take long. Such huge problem won't be fixed sonner than 11.10.

Gotta go reinstall 10.10. Who's with me?

already did:) im back on 10.10... so much better

---

### Post by mankypro on 2011-05-06
I've just been booting into my last known good kernel, works fine so far.  I may keep Narwahl on the laptop for a while to see if it gets resolved.

---

### Post by slooksterpsv on 2011-05-06
Quick reply to a comment on the first page, Natty isn't beta it's been released.

---

### Post by zyrorl on 2011-05-06
> **slooksterpsv said:**
> Quick reply to a comment on the first page, Natty isn't beta it's been released.

it's definetly beta quality. lots of ppl i know are having the same issue.

---

### Post by slooksterpsv on 2011-05-06
> **zyrorl said:**
> it's definetly beta quality. lots of ppl i know are having the same issue.
Haha yeah, Beta Quality I agree, Beta not directly labeled as such. I just remind myself think of Vista, that was a big flop, very flaky software, then 7 came out.
So I compare this 11.04 to Vista, and 11.10 may be more like 7 or a Vista SP2.

---

### Post by zyrorl on 2011-05-06
> **slooksterpsv said:**
> Haha yeah, Beta Quality I agree, Beta not directly labeled as such. I just remind myself think of Vista, that was a big flop, very flaky software, then 7 came out.
So I compare this 11.04 to Vista, and 11.10 may be more like 7 or a Vista SP2.

I would personally draw a comparison to Windows ME... rather than vista..

---

### Post by mörgæs on 2011-05-06
Jokes aside: Every operative system, Ubuntu, Windows and what-have-you, is unstable right after the release. 

If you people wanted 11.04 from the very first day (which I will not recommend), why didn't you test it in a live boot before installing?

---

### Post by zyrorl on 2011-05-06
> **mörgæs said:**
> Jokes aside: Every operative system, Ubuntu, Windows and what-have-you, is unstable right after the release. 

If you people wanted 11.04 from the very first day (which I will not recommend), why didn't you test it in a live boot before installing?

I guess i'm just accustomed to ubuntu not being **** every time on release... usually it's relaly good by the time its ready to go live..

---

### Post by slooksterpsv on 2011-05-06
> **zyrorl said:**
> I guess i'm just accustomed to ubuntu not being **** every time on release... usually it's relaly good by the time its ready to go live..

Well they did a BIG change in this one going from Gnome to a Unity/Metacity mix. So Gnome has been really stable, they ventured into an unknown/untested area and took a chance. 10.04 was great, 10.10 was great, 9.10 I had wifi issues with my current laptop, but 8.04-10.10 (with the exception of 8.10 I had issues with 8.10 for some reason) have been really really good on my big desktop.

---

### Post by mörgæs on 2011-05-07
Exactly. That's why I am mentioning the live boot testing.

---

### Post by FelipeAragao on 2011-05-07
> **zyrorl said:**
> it's definetly beta quality. lots of ppl i know are having the same issue.

Agreed. +1

> **mörgæs said:**
> Jokes aside: Every operative system, Ubuntu, Windows and what-have-you, is unstable right after the release. 

If you people wanted 11.04 from the very first day (which I will not recommend), why didn't you test it in a live boot before installing?

I use ubuntu since 9.04. I tested it in live boot, it ****** up with my ubuntu 10.10 (which I had to format and couldn't touch its files) and after some hard work it was finally installed. Even in the live boot it was horrible. My dell has 6GB of memory and 500GB of hard disk. And still, the main button in the upper left hand corner fails as HELL.

I'm really disappointed because this was supposed to by a big success. And yet, they released it as if it was already fine and good to go. Awful way of making unity come out.

---

### Post by lemort on 2011-05-08
Same here. It's a disaster.

AMD Athlon 64 X2 Dual Core Pocessor 4200+ Memory 3 GiB

---

### Post by dylanthomasfan on 2011-05-09
Just wanted to comment in general. I don't like Natty. Not one bit.

10.10 was fast, and this one's slow. On top of this, the sleep/hibernate function is messed up--I have to prertty much reboot after I wake up the machine (didn't have to in 10.10).  I use classic gnome after my initial Unity horrorshow (unusable desktop), and Gnome is just unstable. I have never have had to reboot a linux-based machine so many times (64bit, 2 GB memory, Intel Pentium D/3.00Ghz). I use my Ubuntu box connected to my Panasonic Viera 46 Inch via an AVR thorough a  Radeon HD4550 which I use for HDMI video and audio for my XBMC HTPC).

In addition, Natty messed up my audio settings (switched my Audio from my ATI HDMI card to on-board audio). Everything is just--a giant flopping mess.

I'll keep this thread updated with any of my tweaks to make this box usable.

Meanwhile, Natty is just a plain unmitigated disaster.

---

### Post by hopwon on 2011-05-10
I was considering upgrading. currently run 10.10 on Core2 1.8GHz 3GB RAM plus I use LVM for volume management. From all the bad things being said on this and other forums I think I will be giving Natty a wide birth until it settles down.

---

### Post by mörgæs on 2011-05-10
@dylanthomasfan: Have you tried a fresh install of Xubuntu 11.04?

---

### Post by EboMike on 2011-05-11
Don't do an upgrade to 11.4. Do a fresh install. It'll do wonders. Here's a brief history of what Ubuntu on my Sony Vaio looked like:

Fresh 10.4 install:
Worked well. Good hardware acceleration. No bluetooth. Microphone doesn't work. Audio output only worked after installing backported ALSA libraries.

Upgrade to 10.10:
Even better. Great hardware acceleration (slight visual artifacts). Bluetooth works. Audio output works. Still no microphone. Bad: Hotkeys stopped working for months. Laptop sometimes won't sleep after shutting lid.

Upgrade to 11.4:
Complete disaster. Apparently no hardware acceleration. Moving a window ran at 4fps, even without eye candy. Computer was extremely unresponsive. Typing fast often ended up with missing letters. Audio output completely distorted. Things stopped working right, had to reset often.

Fresh 11.4 install:
Bliss. Hardware acceleration back in full force. Computer very responsive, better than  before. Hotkeys work. Microphone works! Happy.

---

### Post by dylanthomasfan on 2011-05-11
[mörgæs]("http://ubuntuforums.org/member.php?u=939075"):

Thank you for your suggestion. I can try a fresh install, but I won't be able to get to this for a couple of weeks.

Meanwhile, I am running Gnome safe mode and the machine is far more usable now. Except, I cannot figure out how to get the correct refresh rate setting for my Panasonic Viera TH-46PZ85U @ 1080P. Is it 30Hz or 60Hz? Or something else? I checked with the ATI board's  config and that did not help as well. (I connect the HDMI on [FONT=verdana,arial,helvetica][SIZE=-1]Sapphire Radeon HD4550 512 MB DDR3 VGA/DVI/HDMI PCI-Express Video Card 100252HDMI via an AVR with HDMI input.)

I am partial to Ubuntu and I want this to be a super distro: I apologize for my rather dire sounding rants from the earlier posts.
[/SIZE][/FONT]

---

### Post by mörgæs on 2011-05-11
> **EboMike said:**
> Don't do an upgrade to 11.4. Do a fresh install. It'll do wonders. Here's a brief history of what Ubuntu on my Sony Vaio looked like:

Fresh 10.4 install:
Worked well. Good hardware acceleration. No bluetooth. Microphone doesn't work. Audio output only worked after installing backported ALSA libraries.

Upgrade to 10.10:
Even better. Great hardware acceleration (slight visual artifacts). Bluetooth works. Audio output works. Still no microphone. Bad: Hotkeys stopped working for months. Laptop sometimes won't sleep after shutting lid.

Upgrade to 11.4:
Complete disaster. Apparently no hardware acceleration. Moving a window ran at 4fps, even without eye candy. Computer was extremely unresponsive. Typing fast often ended up with missing letters. Audio output completely distorted. Things stopped working right, had to reset often.

Fresh 11.4 install:
Bliss. Hardware acceleration back in full force. Computer very responsive, better than  before. Hotkeys work. Microphone works! Happy.

+1. If people would do this, the forum would be half the size.

---

### Post by mörgæs on 2011-05-11
> **dylanthomasfan said:**
> [mörgæs]("http://ubuntuforums.org/member.php?u=939075"):

Thank you for your suggestion. I can try a fresh install, but I won't be able to get to this for a couple of weeks.

Meanwhile, I am running Gnome safe mode and the machine is far more usable now. Except, I cannot figure out how to get the correct refresh rate setting for my Panasonic Viera TH-46PZ85U @ 1080P. Is it 30Hz or 60Hz? Or something else? I checked with the ATI board's  config and that did not help as well. (I connect the HDMI on [FONT=verdana,arial,helvetica][SIZE=-1]Sapphire Radeon HD4550 512 MB DDR3 VGA/DVI/HDMI PCI-Express Video Card 100252HDMI via an AVR with HDMI input.)

I am partial to Ubuntu and I want this to be a super distro: I apologize for my rather dire sounding rants from the earlier posts.
[/SIZE][/FONT]

I can not help with this, but try the thread here:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by blauendonau on 2011-05-11
I did a clean install of Xubuntu 11.04 yesterday over Maverick and regretted it. It took longer to boot up than the supposedly heavier GNOME in Maverick, even on a perfectly clean install. (And my machine is by no means slow.) I tried installing kubuntu-desktop but KDE is so slow to load up it's almost unusable. YMMV but I've heard a lot of complaints about Natty feeling "bloated" even on fast computers.

I'd suggest sticking to the older version you have if you're considering moving to Natty. There's no big rush, Maverick will be supported for another year and Lucid for two, you can wait until 11.04 has a chance to mature or the hopefully improved 11.10 comes out.

---

### Post by zyrorl on 2011-05-11
> **EboMike said:**
> Don't do an upgrade to 11.4. Do a fresh install. It'll do wonders. Here's a brief history of what Ubuntu on my Sony Vaio looked like:

Fresh 10.4 install:
Worked well. Good hardware acceleration. No bluetooth. Microphone doesn't work. Audio output only worked after installing backported ALSA libraries.

Upgrade to 10.10:
Even better. Great hardware acceleration (slight visual artifacts). Bluetooth works. Audio output works. Still no microphone. Bad: Hotkeys stopped working for months. Laptop sometimes won't sleep after shutting lid.

Upgrade to 11.4:
Complete disaster. Apparently no hardware acceleration. Moving a window ran at 4fps, even without eye candy. Computer was extremely unresponsive. Typing fast often ended up with missing letters. Audio output completely distorted. Things stopped working right, had to reset often.

Fresh 11.4 install:
Bliss. Hardware acceleration back in full force. Computer very responsive, better than  before. Hotkeys work. Microphone works! Happy.

I did a fresh 11.4 install, full format, re-partition.

It was complete failure. 4fps? good luck, more like 1fpm.

I'm running a dual core 2.8ghz laptop. Not exactly the top of the line Core i7 but no slouch either. 4GB of ddr3 Ram, Nvidia GT240M 1GB of Video ram.. It should be able to eat it alive.

Natty Narwhal = Nutty Narfail.

---

### Post by EboMike on 2011-05-12
> **zyrorl said:**
> I did a fresh 11.4 install, full format, re-partition.

It was complete failure. 4fps? good luck, more like 1fpm.

I'm running a dual core 2.8ghz laptop. Not exactly the top of the line Core i7 but no slouch either. 4GB of ddr3 Ram, Nvidia GT240M 1GB of Video ram.. It should be able to eat it alive.

Natty Narwhal = Nutty Narfail.

That's unfortunate. I heard there were problems with Nvidia GPUs, particularly with the proprietary drivers. I remember seeing some juju advice about deliberately disabling the drivers, or postponing their installation, or whatever, but chances are that some Nvidia GPUs simply don't work right with the Narfail. Which would be sad, given how widespread Nvidia is. I'm not quite sure how that could pass QA.

I have a quite underpowered VAIO with an Intel chipset, and even the wobbly windows effect is flying at full framerate. It must be an Nvidia driver issue.

---

### Post by Gunner2677 on 2011-05-12
It seems alot of people are getting mixed results. I'm running Natty on my Gateway ID59c laptop and it runs pretty good. Only thing I had to tweak was my settings for the function keys to adjust brightness and sound levels. Other than that, the only thing I've seen is the Menu bar at the top go blank sometimes when using different programs. Doesn't happen all the time but is still a pain. You can actually roll over the area with your mouse and still get the drop down menus (in order to reboot, etc.)

However, on my office PC, I'm having a hell of a time trying to get my wireless USB to work. I've been playing with it for about a week and I've only found one workaround that allows me to see network broadcasts however I cannot connect. Guess I'll just have to wait until it is patched. :(

---

### Post by zyrorl on 2011-05-12
> **EboMike said:**
> That's unfortunate. I heard there were problems with Nvidia GPUs, particularly with the proprietary drivers. I remember seeing some juju advice about deliberately disabling the drivers, or postponing their installation, or whatever, but chances are that some Nvidia GPUs simply don't work right with the Narfail. Which would be sad, given how widespread Nvidia is. I'm not quite sure how that could pass QA.

I have a quite underpowered VAIO with an Intel chipset, and even the wobbly windows effect is flying at full framerate. It must be an Nvidia driver issue.

I would believe that except that even with NVIDIA drivers turned off it runs like a hog.

---

### Post by nariub on 2011-05-13
> **nariub said:**
> Upgraded a good 10.10 (64bit) to 11.04 (64bit) online
and the GUI slowed to a crawl, in classic and in the new UI.
I can ssh into the box and it appears as happy as ever.
 
It takes longer to boot than 10.10
after user/pass it take nearly two minutes to put the background up.
it takes another 3 minutes or so to put anything on the desktop (menu or icon)
I have not yet been able to launch anything from the new or classic UI
 
Classic version seems to clip off the power/logout button on the top right, which is how I discovered that ssh was working fine.
 
<CNTRL-F2> gets me to a command prompt to, but it appears to be a bit sluggish for some reason.
 
Mine is a Dell E510/5150, Pentium D Dual Core 2.6G, 4G RAM (dell bios only allows me to see 3.2G), 2x 2T Seagate HDs in RAID1 on the ICH7R, 180G OS / Remainder HOME directory, to get around the GPT boot issue.  Nvidia 7300 LE with 512M video.
 
dont know the current refresh rate or if it has anything to do with it.
would like to know where to check/change this from a commandline as that would be much quicker.
 
I too regret hitting the upgrade button.
I am considering putting 10.04.2 on it so I wont have to deal with it again until 2012.
 
---
side note,
11.04 (64bit) live disc is crappy slow on the machine above too.
  and doesnt complete a boot on a Dell Latitude E6510 (Intel Graphics) while in a docking station.
  pull the Laptop out of the docking station and it works fine and is quite snappy.
  the touchpad even works for tap selection, and up/dn scrolling couldnt seem to work out left/right scrolling.  Nonetheless, I will likely put 10.04.2 on the laptop and pull in some backports to get the touchpad working.

Update:
 Safe Mode graphics worked for me on my Dell E5150 with Nvidia 7300 LE card

Methinks my answer lies here

[https://bugs.launchpad.net/ubuntu/+source/nux/+bug/728745](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/728745)

used jockey-text to determine my available drivers

sudo jockey-text -l
  (that is a lower case L like in Lima)

and then told it to use the old driver rather than current
sudo jockey-text -e xorg:nvidia_173


Word is, nvidia-current and natty have issues.

Nariub

---

### Post by zyrorl on 2011-05-16
That doesn't work for me unfortunately... i don't have a card that old.. I have a GT240M... which is a much newer chipset and that driver is too old for it. I'd lose support for HDMI Audio among many other things.

---

### Post by aselvan on 2011-05-22
Similar issues on my Dell Latitude D630... over all, a sluggish performance compared to the performance prior to upgrading. I had trouble initially running the nvidia-173 and had to rebuild manually since the upgrade did not install the correct linux-headers. Hope the slowness gets addressed soon.

---

### Post by zyrorl on 2011-06-01
Does anyone know if this slowass ubuntu has been fixed yet? im afraid to upgrade again given it'll probably assplode on me.

---

### Post by slooksterpsv on 2011-06-03
> **zyrorl said:**
> Does anyone know if this slowass ubuntu has been fixed yet? im afraid to upgrade again given it'll probably assplode on me.

Just gotta follow the first link here: [http://ubuntuforums.org/showthread.php?t=1749312](http://ubuntuforums.org/showthread.php?t=1749312)

It has tips, fixes, etc. for Unity even things that make it "seem" slow.

---

### Post by zyrorl on 2011-06-03
> **slooksterpsv said:**
> Just gotta follow the first link here: [http://ubuntuforums.org/showthread.php?t=1749312](http://ubuntuforums.org/showthread.php?t=1749312)

It has tips, fixes, etc. for Unity even things that make it "seem" slow.

It appears like you're trying to insult my intelligence by saying "seems". No it is slow.
Even gnome classic is slow. It's got nothing to do with unity.
Moving mouse cursor is slow. Logging in is slow. As soon as x boots CPU goes to 100% CPU. Nothing in that thread suggests fixes to it.

Even live cd is so slow, maverick Live cd is at least 100 times faster. I'm staying with 10.10 until this huge issue is solved.

---

### Post by dylanthomasfan on 2011-07-30
I finally downgraded back to Maverick, and my desktop feels so .... much .... better. BTW, I had to go through the install process again for Maverick, as there is no way to downgrade from 11.04 to 10.10 that I am aware of. Unity blows. Now, I want to be sure I never upgrade to 11.04.

---

### Post by mörgæs on 2011-07-30
Again, 11.04 only has major problems, if you try Ubuntu. Just go for Xubuntu and you will (probably) be all fine.

---

### Post by Raygreen on 2011-07-31
It's kind of funny I just kind of came back to using Ubuntu in the last week. I installed it back on both my old Dell C810 Latitude and on a newer Compaq desktop which it shares with Windows 7. On the laptop I had Ubuntu 8.10 and Windows XP. I am now installing Ubuntu 10.10.  I had installed 11.04 but it was just too sluggish, even though it seemed ok running off the CD running Live. I had put 9.04 but seemed to have issues with constantly disconnecting from the WiFi. 

I have 11.04 running pretty smoothly on my Compaq Desktop. But had issues when I tried to install it the first 2 times. I then ran a windows command from the windows install disk to fix the bootsect of MBR. Then installed 9.04 and upgraded through 11.04. That messed up. I was left with a background and no taskbars or launch tools. I then did a clean install of 11.04 and that is working pretty smoothly now. I had to run som commands to get the weather to show back up on the top right taskbar and trying to get used to the launcher on the left side of the screen. I did  also change the close, minimize buttons to the right side. 

I am generally impressed with Ubuntu. I first tried it back in 2008. I still think that Windows 7 is a more polished and have had issues in the past with upgrades going horribly wrong leaving a unusable OS and having to reinstall completely.  There are still are enough programs that can't run on Linux and not even using Wine. Right now there are iTunes, Netflix that come to mind. But for most other oprations Ubuntu works great.

[COLOR="DarkOrchid"]One funny note: I was trying to put Ubuntu on my older laptop and could not figure why the Ubuntu 10.10 disk was not being read by it. I tried it on my other computer and then tried other disks with Ubuntu 9.10 and 11.04 and all would read fine. Finally I figured out the problem. I had burnt it to a DVD and the older computer could only read CDs. Boy, did I feel stupid![/COLOR]

---

### Post by nariub on 2011-08-13
> **nariub said:**
> Update:
 Safe Mode graphics worked for me on my Dell E5150 with Nvidia 7300 LE card

Methinks my answer lies here

[https://bugs.launchpad.net/ubuntu/+source/nux/+bug/728745](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/728745)

used jockey-text to determine my available drivers

sudo jockey-text -l
  (that is a lower case L like in Lima)

and then told it to use the old driver rather than current
sudo jockey-text -e xorg:nvidia_173


Word is, nvidia-current and natty have issues.

Nariub

Finally got around to actually rolling back to nvidia_173
discovered it was blacklisted in /etc/modprobe.d/nvidia-graphics-drivers.conf

Commented out the blacklist
activated the 173 driver from ubuntu classic no effects
and for good measure
/etc/environment UNITY_FORCE_START=1

Months later, I finally have Ubuntu Unity 3d and Ubuntu Classic and safe mode and Unity2d all working again.

Glad this ain't my day job.

---

