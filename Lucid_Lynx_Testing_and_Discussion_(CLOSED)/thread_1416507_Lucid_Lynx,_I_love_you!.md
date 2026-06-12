---
title: "Lucid Lynx, I love you!"
date: 2010-02-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Robin Nixon on 2010-02-26
I just installed Alpha 3, and right at the end of the installation my NVidia card was recognized, and the display went to full widescreen. After reboot it's still there and crystal clear. Something I haven't seen since 9.10, and only then by deliberately installing new drivers.

Also, I sometimes charge my iPhone on Ubuntu when I don't want iTunes to come up bothering me on my Mac. So I had my iPhone plugged in and when Alpha 3 installed, guess  what? I can now access all my tunes, playlists, apps and everything from my iPhone 3G using Nautilus. And what else? RhythmBox interfaces with it, working like iTunes! Blimey, I didn't even know this was on the list of planned additions. I'm looking forward to seeing if I find anything else.

So, well done everyone, it looks like 10.04 will be an excellent release, maybe even ground breaking.

---

### Post by lancest on 2010-02-26
> **Robin Nixon said:**
> I just installed Alpha 3, and right at the end of the installation my NVidia card was recognized, and the display went to full widescreen. After reboot it's still there and crystal clear. Something I haven't seen since 9.10, and only then by deliberately installing new drivers.

This may be the Nouveau driver that was backported to .32. It seems to work quite well. 
Amazing about your I-Phone! Ubuntu 10.04 is about greatness.

---

### Post by JCoster on 2010-02-26
> **Robin Nixon said:**
> I can now access all my tunes, playlists, apps and everything from my iPhone 3G using Nautilus. And what else? RhythmBox interfaces with it, working like iTunes! Blimey, I didn't even know this was on the list of planned additions. I'm looking forward to seeing if I find anything else.

Is your iPhone jailbroken to be able to do this?

---

### Post by aviedw on 2010-02-26
Thats great news. You have a lot of guts installing the alpha. Im with 9.10 and its rock solid for me. Im truly happy with my distro in every way. The only gripe that i have with 9.10 is that they made it so hard to change the log on screen or the splash screen or the boot up muisc. But its not really that big of a deal.

---

### Post by Robin Nixon on 2010-02-26
> Is your iPhone jailbroken to be able to do this?Nope - this is a fully unbroken iPhone 3GS 32Gb with the latest 3.1.3 firmware :)

---

### Post by taranfx on 2010-02-26
That's a great news guys!
Even I had installed Lucid recently, but didnt attach iPhone. Damn, now I see it.
Anyways, if you are on Ubuntu 9.1, it's still easy to do it, I wrote aguide a while back : [Sync iPhone in Ubuntu]("http://www.taranfx.com/sync-iphone-linux")
cheers. 
Waiting for Official announcement :p

---

### Post by djwazza on 2010-02-26
Agree Lucid looks great, but what's with the lack of wifi support for Realtek 8192? I have a Samsung N150 and I was waiting for the Alpha 3 in order to get wifi access back without messing around too much.  I'm a Linux noob so Win 7 has still got me in thrall until the wifi issue is addressed.  Is it on the horizon and when will wubi work properly so LL can start capturing Windows users?

---

### Post by djwazza on 2010-02-26
PS Just read the disclaimer at the top of the thread. I'll post in launchpad...doh!

---

### Post by jaminthorns on 2010-02-26
If this information be true, I'm sure that Ubuntu could gain a whole new audience of people that are reluctant to install ubuntu simply because of lack of iPod Touch/iPhone support. Just another sign of how fast Ubuntu is progressing. This is awesome! :D

---

### Post by Mr. Picklesworth on 2010-02-26
> **Robin Nixon said:**
> I just installed Alpha 3, and right at the end of the installation my NVidia card was recognized, and the display went to full widescreen. After reboot it's still there and crystal clear. Something I haven't seen since 9.10, and only then by deliberately installing new drivers.

That actually just rocked my world. I didn't know this operating system *could* do something like that. Is it possible that it just magically detected your monitor right but was still running with the previous driver, or did your copy of Ubuntu indeed perform magic?

Great to know libgpod supports the iPod touch now!
Just [checked the web site]("http://gtkpod.wikispaces.com/"), and that seems to be confirmed.

---

### Post by Owen.C93 on 2010-02-26
It can read my ipod nano 5g, but can't play anything.

---

### Post by J_Stanton on 2010-02-27
> **Robin Nixon said:**
> I'm looking forward to seeing if I find anything else.  i found Simple Scan in the graphics menu and it is pure genius. What a beautiful easy to use scanning app. the best i've ever used. i think lucid is going to raise the bar for most distros.

---

### Post by J_Stanton on 2010-02-27
> **aviedw said:**
> You have a lot of guts installing the alpha. it doesnt require guts just an extra hard drive or partition. ;)

---

### Post by libihero on 2010-02-27
my laptop can suspend for the very first time :D
only problems i have is my wifi is "disabled" and i cant vertical scroll over the volume icon to change the volume

---

### Post by Robin Nixon on 2010-02-27
> **Owen.C93 said:**
> It can read my ipod nano 5g, but can't play anything.

Try opening Rhythmbox then select your iPod and double click one of the audio files. You will then be prompted to download the correct plug-in. If you only have AAC files then it will recommend *gstreamer0.10-plugins-bad* (strange name but it seems to work), this usually comprises over 20 different files.

Otherwise, if you have mp3 files on the player, you'll probably have a choice of three mp3 plug-ins to download. They are much quicker. You should then be able to click files from your iPod within Rhythmbox.

After that you should be able to open the ipod from your desktop where you can select the iTunes_Control folder followed by Music, and then click on files within the music folders there. They are stored by number so it will be pretty random what you get. That's because they are all referenced by index files for the player to make sense of them.

But... you can copy all the files off your iPod into an Ubuntu folder and can then drag and drop them into Rhythmbox (or use Import File) and then you have a backup of your iPod's music. As you may know, you can't do this with iTunes as there are limits to syncing devices with computers.

Then, if you drag and drop a file from your Music collection onto your iPhone, it gets downloaded.

Like I said, I love it! :) My only fear is that an Apple firmware upgrade could change this...

---

### Post by kyleabaker on 2010-02-27
I was also surprised about iPhone/iPod Touch support. I upgraded from 9.10 where I had to [manually install](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/) and configure my iPod Touch to get it working with Rhythmbox. Its always nice to see plug-n-play support!

I'm also looking forward to the music store with the combination of sync'ing everything to the clouds!

---

### Post by praveenmarkandu on 2010-02-27
it's great that lucid will have iphone support. i tried plugging in my dad's iphone in karmic and it wouldnt transfer files. im a big fan of ubuntu and i do look forward to new features.

however i think we should be real about the situation. lucid is a LTS and everyone knows there are an insane amount of open bugs on launchpad affecting karmic. im currently watching 9 bugs that severely change the way i deal with my pc for the worse.

they are trying to fix these with the 100 papercuts initiative, but in a lot of cases, a plaster isn't a good enough when surgery is required.

in my opinion, canonical has dropped the ball on lucid. instead of putting serious effort into fixing bugs, they are introducing a music store into an LTS release. its not a completely terrible idea, but it would be better if it was in lucid+1. also, naming it Ubuntu One Music Store while already having Ubuntu One cloud backup is silly.

---

### Post by kyleabaker on 2010-02-27
> **praveenmarkandu said:**
> also, naming it Ubuntu One Music Store while already having Ubuntu One cloud backup is silly.

+1 Not sure what they were thinking if they thought that sounded cool. However, there are still ~2 months left to work out plenty of bugs so your watched bugs stand a good chance of being thoroughly fixed.

---

### Post by nanog on 2010-02-27
>  im currently watching 9 bugs that severely change the way i deal with my pc for the worse.

**Please** post about the bugs. Its therapeutic and you might find people have already solved the problem or found work arounds. At the very least it will attract attention to the bugs and might even occasionally attract a developer or ubuntu member's eye. For example, I have non-working hardware that I fixed by blacklisting broken kernel drivers. I never reported the bug in ubuntu since its a rare upstream kernel bug and is being worked on there. Another example: virtualbox usb is currently broken but there is a simple workaround posted here but not in launchpad.

---

### Post by zekopeko on 2010-02-27
> **praveenmarkandu said:**
> in my opinion, canonical has dropped the ball on lucid. instead of putting serious effort into fixing bugs, they are introducing a music store into an LTS release. its not a completely terrible idea, but it would be better if it was in lucid+1. also, naming it Ubuntu One Music Store while already having Ubuntu One cloud backup is silly.

Actually it makes a lot of sense since the purchased music is going to be synced to Ubuntu One.

---

### Post by aV Echelon on 2010-02-28
Though I'm very glad about this, I wouldn't use it unless they're making improvements to it. So far (in karmic) it's incredibly buggy and risky.

---

### Post by stmiller on 2010-03-01
Seems that this only works with fat formatted iPods/iPhones. HFS+ formatted are out of luck, even with the hfs packages installed.

Still researching...

---

### Post by listerthrawn on 2010-03-01
Can you upload ringtones to the device with all this new functionality?

I use my iphone with karmic currently and it's about the only thing I can't do.

Last time booted up itunes in a vm to upload a ringtone and it helpfully erased my entire music library from the phone. grr.

Chris

---

### Post by martini1179 on 2010-03-01
Can someone confirm if you can actually transfer music to an iPhone/iTouch via Rhythmbox in Lucid?

---

### Post by Digikid on 2010-03-01
Sounds promising.....

---

### Post by simmeson on 2010-03-01
> **martini1179 said:**
> Can someone confirm if you can actually transfer music to an iPhone/iTouch via Rhythmbox in Lucid?
I can confirm that it's possible to transfer music to an iPod Nano 5th Gen 16GB, including album-art. :) Not sure about the iPhone though.

---

### Post by xir_ on 2010-03-01
this is great new i remember having to transfer all my music via a ssh tunnel over wifi when it first came out.

id love know know how the devs got round the encryption hash used to keep people on itunes.

---

### Post by sudoer541 on 2010-03-01
> **martini1179 said:**
> Can someone confirm if you can actually transfer music to an iPhone/iTouch via Rhythmbox in Lucid?


I have the same question.
also, A youtube video tutorial/ tour would be great!!!

---

### Post by exavoid on 2010-03-01
Excellent news :D

---

### Post by Rob2687 on 2010-03-01
It seems like iPhone/iPod Touch support isn't 100% complete. At least with Rhythmbox.

I can playback files perfectly fine but write support seems kind of spotty. A few times i have been able to drag and drop files and it synced right away. Most other times nothing happens then magically it will start to sync. i haven't been able to create or modify playlists. there doesn't seem to be support for editing tags either. I don't know if it's because there is no support for stuff in the low level libraries or if it's just rhythmbox.

There's no sync button so it's just do it and hope it works kind of situation over here.

---

### Post by PRGUY85 on 2010-03-01
I am loving Alpha 3 so far.  Very impressed with boot time and how polished everything is.  Yet, I have some problems:

1) Empathy...I gave it a try in Karmic and had to go back to Pidgin. Was hoping Lucid would be better, but I am having a hard time with MSN support.  My buddies tell me I appear offline.  Really want to use Empathy since its better implemented on the OS.

2) MeMenu, I love it yet is there a way to choose where to broadcast? I would just like to use the field to update Twitter, not everything else.  

3) After my first boot, now every time I boot the mouse pointer appears on a black screen with a command line prompt on the left upper corner.  I have to hit Enter for the Login window to appear. Any ideas?

4) My Wireless Network is not connecting by default.

Either way, good stuff so far.

---

### Post by goog64 on 2010-03-01
I can't transfer songs to my iPhone using 10.04 Rhythmbox. If anyone finds a solution, please post here?
Thank you.
JF

---

### Post by rahilm on 2010-03-01
hey..you people forgot the lightning fast usb-transfer speeds that would embarrass even windows 7.

---

### Post by goog64 on 2010-03-01
Some more info:
In Rhythmbox, when I drag and drop a song into my iPhone icon, I get a "transferring" message. I can then play the song in Rhythmbox via the iPhone icon. However, when I disconnect the iPhone, the song does not exist on the phone.
Ubuntu 10.04
Jailbroken iPhone 2g running 3.1.2 firmware.

---

### Post by martini1179 on 2010-03-01
> **PRGUY85 said:**
> 

3) After my first boot, now every time I boot the mouse pointer appears on a black screen with a command line prompt on the left upper corner.  I have to hit Enter for the Login window to appear. Any ideas?

4) My Wireless Network is not connecting by default.

#3 sounds like the texbook definition of a bug. 

#4 is very similar a bug that I encountered in the Karmic betas. The wired network I was on defaulted to being disconnected upon most boots. It was fixed shortly before release, if memory serves.

---

### Post by Neezer on 2010-03-01
I hooked my ipod touch up to 10.04 and it recognized it. Much of the music that I had synched to it from the itunes store will not play on it, even after loading the plugins for it. Some of my music that wasn't bought from the store plays.

I tried to drag and drop a file onto my ipod touch, and now when I browse the ipod, it gives me a screen saying "No Music you can download music from iTunes." 

I can browse my ipod through rhythmbox and see all of my music though. I deleted the song that I dragged on it, and it is still giving me the message.

---

### Post by Keyper7 on 2010-03-02
> **PRGUY85 said:**
> 2) MeMenu, I love it yet is there a way to choose where to broadcast? I would just like to use the field to update Twitter, not everything else.

From my quick tests, it seems that the MeMenu broadcasts to wherever Gwibber is configured to broadcast. So if you don't want, for example, to update your Facebook status with the MeMenu, open Gwibber and disable Facebook updating by clicking on its logo below the input box.

---

### Post by PRGUY85 on 2010-03-02
> **Keyper7 said:**
> From my quick tests, it seems that the MeMenu broadcasts to wherever Gwibber is configured to broadcast. So if you don't want, for example, to update your Facebook status with the MeMenu, open Gwibber and disable Facebook updating by clicking on its logo below the input box.

I'll give that a try.

---

### Post by cariboo on 2010-03-02
> **goog64 said:**
> I can't transfer songs to my iPhone using 10.04 Rhythmbox. If anyone finds a solution, please post here?
Thank you.
JF

Instead of embedding your post in a Lucid love fest thread, you would probably be better off starting a new thread

---

### Post by Robin Nixon on 2010-03-04
Well, I suppose it was too much to hope for from an Alpha. Now the Nvidia support has vanished with today's update. I'm back to a non widescreen maximum resolution of 1280 x 1024 by default, with big black unused areas down either side. Well, at least this time I was able to download and install the recommended driver and it actually worked.

I hope it returns to working by default without loading a driver though.

---

### Post by uBeer on 2010-03-04
> **rahilm said:**
> hey..you people forgot the lightning fast usb-transfer speeds that would embarrass even windows 7.

Is it really faster than in Karmic? Can you elaborate a bit?

---

### Post by Jeztastic on 2010-03-04
Hi - will the ipod integration work as well in other media players- amarok and exaile for example?

---

### Post by brucemartin on 2010-03-04
wow this is amazing. but why no official word from canonical on this? i'd love to hear something related to it, like there is work in progress, because from what i read it doesn't work very well for everybody for now

---

### Post by Wiebelhaus on 2010-03-05
I love it!

---

### Post by Roosje on 2010-03-06
> **PRGUY85 said:**
> 
3) After my first boot, now every time I boot the mouse pointer appears on a black screen with a command line prompt on the left upper corner.  I have to hit Enter for the Login window to appear. Any ideas?

 Same problem here, any idea what is causing it?

Wilco

---

### Post by magneze on 2010-03-06
I must say I'm overall impressed by Lucid. It seems to be in a much better state that Karmic was at this point in it's cycle. As far as I can tell everything works and it looks great. Boot time and splash is great too. Shaping up nicely - can't wait for the final release so I can upgrade everywhere.

---

### Post by rawmill on 2010-03-09
Another user who cannot delete or add music to the iPhone 3G (not jailbroken).  I can play from it, but not write anything to the device.

---

### Post by mlkovacs on 2010-03-13
Lucid Lynx Rocks on Intel Macbook

Daily Build Live CD from March 12 2010 booted without a hitch. Everything worked. Wireless was enabled after installing the BCM driver through Jockey.

I did not install Lucid to disk, I only booted the Live CD as this Macbook doesn't belong to me.

---

### Post by darco on 2010-03-13
I'm loving the new theme!..Purple rocks!......Plymouth and Nouveau looking good too! Other than a few quirks (login, hit enter to complete boot, memory issue;possibly ureadahead related, usb transfer still slow from hdd to usb thumb drive) this is going to be a great release!

---

### Post by vishalrao on 2010-03-13
@mlkovacs: does lucid boot *directly* off macbook without any apple's evil stuff like bootcamp or efi workarounds???

---

### Post by praveenmarkandu on 2010-03-13
sorry to rain on everyones parade again but im just going to wait for the final release. karmic looked promising until the final release.i have quite a few problems with my karmic such as the eject button for the DVD drive doesnt work (kernel problem it seems [bug #397734]("https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/397734")), brasero doesnt support multisessions ([bug #498406]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/498406")) , suspend when laptop lid close doesnt work ( [bug #44058]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/44058") ), vnc doesnt refresh with compiz ( [bug #353126]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126?comments=all"))

its all well and good ubuntu is trying to look like a modern operating system with all the bells and whistles. but at what cost? stability is there like with all linux distros but usability bugs arent getting fixed fast enough. also with all the modifications the canonical team are making with the UI, how is that going to fit into gnome3 in the grand scheme of things. a lot of the work they are doing with the anataya project will be wasted. unless the plan to stick to gnome 2 forever. adding a music store and a cloud service should be all secondary projects in my opinion and are just there to draw in windows and mac users. im no developer or anything but i think canonical is not doing enough to contribute to upstream eventhough they hold the most popular linux distro.

im a big fan of open source advocacy, but i hope people would take a step back and look at things realistically instead of being all fanboy like. when i recommend ubuntu to my friends, i want it to work for them.

---

### Post by vishalrao on 2010-03-14
> **praveenmarkandu said:**
> sorry to rain on everyones parade again but im just going to wait for the final release.

go ahead. when you choose to "wait for the final release" you're not "raining" on anyone's "parade" i assure you :lolflag:

---

### Post by Coder543 on 2010-03-14
I can confirm. Rhythmbox is able to read and write music to my iPod Touch... however it frustrates me that playlist creation doesn't seem to work. (seeing as Apple was pretty dumb not to allow the iPod Touch to modify any playlist it wants to from the iPod. Its not like it would take much to enable that...)

Maybe this will get fixed sometime soon.

---

### Post by mlkovacs on 2010-03-14
> **vishalrao said:**
> @mlkovacs: does lucid boot *directly* off macbook without any apple's evil stuff like bootcamp or efi workarounds???
The Macbook boots directly of off the Live CD. Just press and hold the "Option" key when booting up to get the boot device menu. Select the cd icon. Let UBuntu boot normally. After it boots go to System >> Administration >> Hardware Drivers and install the wireless drivers. Have fun.

---

### Post by Coder543 on 2010-03-14
> **mlkovacs said:**
> The Macbook boots directly of off the Live CD. Just press and hold the "Option" key when booting up to get the boot device menu. Select the cd icon. Let UBuntu boot normally. After it boots go to System >> Administration >> Hardware Drivers and install the wireless drivers. Have fun.

This is hardly new... the MacBooks themselves *emulate* an MBR environment for the benefit of operating systems that don't deal well with efi (such as Ubuntu). So, I installed good old Hardy Heron (8.04) on my MacBook years ago without any "efi hacks" or bootcamp. The wireless was a pain, but other than that, "it just works."

---

### Post by vishalrao on 2010-03-14
thanks for the info coder543 and mlkovacs, i dont own/use mac(book)s so was just curious in case i buy one of them :)

---

### Post by ndefontenay on 2010-03-14
Hi.

Did you try adding new songs to your iphone? I tried to no avail.
I would be happy to hear others experience for that respect.

Nico

---

### Post by Coder543 on 2010-03-14
Yes, and it worked

---

### Post by aV Echelon on 2010-03-16
I have a Ipod Touch 1G with Firmware 3.1 and it doesn't work for me. I have to wait about 30-40 minutes until it actually finishes, and even then, sometimes the songs don't show up. 

Though I am trying it in Karmic..not sure if the one in Lucid is much different.

---

### Post by jtholb on 2010-03-23
I've got an iphone 3g firmware 3.0.1 which is jailbroken and I can't transfer songs to the phone in Rhythmbox in Lucid either (in fact the phone doesn't show up in Nautilus as well)...just to add my two bits.  It's early days yet so hopefully this will get addressed.

---

### Post by _h_ on 2010-03-23
I agree with OP choice of topic name.

Lucid is sexy, and I love it. :D

---

### Post by shindou01 on 2010-03-23
> **Robin Nixon said:**
> I just installed Alpha 3, and right at the end of the installation my NVidia card was recognized, and the display went to full widescreen. After reboot it's still there and crystal clear. Something I haven't seen since 9.10, and only then by deliberately installing new drivers.

Also, I sometimes charge my iPhone on Ubuntu when I don't want iTunes to come up bothering me on my Mac. So I had my iPhone plugged in and when Alpha 3 installed, guess  what? I can now access all my tunes, playlists, apps and everything from my iPhone 3G using Nautilus. And what else? RhythmBox interfaces with it, working like iTunes! Blimey, I didn't even know this was on the list of planned additions. I'm looking forward to seeing if I find anything else.

So, well done everyone, it looks like 10.04 will be an excellent release, maybe even ground breaking.

I'm using Lucid Lynx Beta 1 on a Compaq CQ40-401AU with ATI Radeon 3200HD and AMD Turion X2 and a 2GB RAM and almost the same thing happened to me. I installed it and my display went on with great resolution as well. Although the drivers for my graphic adapters which was for Karmic isn't working anymore.

> **lancest said:**
> This may be the Nouveau driver that was backported to .32. It seems to work quite well. 
Amazing about your I-Phone! Ubuntu 10.04 is about greatness.

maybe this was also the case with my graphic adapter...I tried using new drivers i downloaded but it made a mess so i restored my backup for it...And another thing, using Karmic I can't use my wireless adapter but on Lynx I only had to use Jockey to download the drivers and it's good to go...I'm loving it even more now.

> **aviedw said:**
> Thats great news. You have a lot of guts installing the alpha. Im with 9.10 and its rock solid for me. Im truly happy with my distro in every way. The only gripe that i have with 9.10 is that they made it so hard to change the log on screen or the splash screen or the boot up muisc. But its not really that big of a deal.

you gotta try lynx out man...I've only used Karmic Koala for 1 week before upgrading to the Lucid Lynx Beta1 and it's a lot better (IMHO)...And I'm only running the 32bit version...Now I really want to try the 64 bit version...

---

### Post by chuebner on 2010-03-28
Rhythmbox iPhone support doesnt work for me in Lucid Beta 1.

The first time after boot the iPhone is recognized but only if rhythmbox is started after the iPhone is plugged in. When it is recognized, selecting it does nothing whatsoever.

rhythmbox --debug gives an error message "unhandled media"

Hopefully this will get fixed before final.

---

### Post by cough on 2010-04-04
I've just installed Beta 1 and plugged in my iPhone 32G 3GS (not jailbroken). RhythmBox detected my iPhone almost immediately, I was album to browse and play music (with album art) from my iPhone and even add a playlist, but cannot transfer music to or from my iPhone.  Hopefully transfer is just around the corner.

---

### Post by UnknownFear on 2010-04-05
This is great news for Ubuntu users! If the newest release of Ubuntu can in fact support iPhone, iPhone 3GS & iPod Touches in their out-of-box state (ie; not jailbroken), than I can definitely see an increase in the number of users using Ubuntu. I for one will be VERY happy to finally see Ubuntu support iPhone / iPod Touch :)

---

### Post by Roxas-X2 on 2010-04-27
I've been gagging for this since I bought my iPod touch 2g. I thought I'd be trapped with vista forever. It was horrible re-migrating from Karmic :(

Just upgraded my acer aspire one with the latest lucid release and my ipod syncs, transfers songs both to and from in rhythmbox and I can browse in nautilus. 

It is jailbroken but I don't think that really matters

---

