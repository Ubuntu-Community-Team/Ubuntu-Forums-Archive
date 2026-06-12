---
title: "Ubuntu 16.04 LTS live boot same as install?"
date: 2016-07-19
forum: Installation &amp; Upgrades
---

### Post by pineapplemoonshine on 2016-07-19
I am planning to buy a cheap pc for school, and was thinking about  installing Ubuntu 16.04 LTS on it. I am not sure if it actually works,  so I was planning on testing it with a live boot before installing. My question is: If it works 100% on the live boot, will it still work  when installing it on the HDD without much of an hassle? (removing  windows 10) 
  Without too much hassle I mean not doing a ton of work in the terminal and downloading drivers for hours.
  The PC is a HP 14-ac102no

---

### Post by Bucky Ball on 2016-07-19
Welcome. Have you used Ubuntu before? It never involves downloading drivers for hours. That is a Windows thing. The majority, if not all, of your hardware should work 'out of the box' as the drivers are already in the Ubuntu kernel. Forget 25 digit authentication codes. They don't exist here. About the only thing you might have to work on a bit is wireless and GPU and most issues there can be fixed if required. Just post a new thread here if you can't find an answer elsewhere on the interwebs. 

Yes, if Ubuntu works from the live session, all should be fine with the hard drive install. I'd advise downloading the ISO from the Ubuntu site, creating bootable media (USB or disk), booting from that and selecting 'Try Ubuntu'. That should take you to a desktop. If you get that far, you're on your way.

You might want to throw up the specs of the machine you're looking to buy. Ubuntu might not be the best for your needs. Their are other flavours in the family that are more lightweight and suitable for machines with lower specs. (See Xubuntu, Xubuntu-core, Lubuntu.) Xubuntu fan myself and haven't used Ubuntu for years. 

Any questions/problems, just ask. Good luck. ;)

PS: I don't drink alcohol, but pineapple moonshine does pique my interest ... Tasty?

---

### Post by pineapplemoonshine on 2016-07-19
Hi, and thank you for your amazing answer!
I started using ubuntu when I was 13 years old (school computers, afterwards adapted it to my home) and used it till I became 19 (because of school, got free macs, I don't complain). I'm 23 now, so it's been a while away from it. The last version I used was 10.10

Back then I wasn't an advanced user, and I don't plan on being one, as I didn't use anything more advanced than sudo apt-get install.. and GNOME.. I love GNOME..

I have a pc with windows 10 I use for gaming, but I don't trust the machine I mentioned last post ($180, 32gb storage) to be able to run as smooth with windows 10 as the gaming machine. Which is why Ubuntu (Ubuntu because I prefer that before Xubuntu/Lubuntu etc) is a good alternative.

Back then it was, to me, as easy to install ubuntu on a laptop as pissing on a kitten. The reason why I'm actually created this thread was because after some recent google searches, apparently it's become harder.

But yea, thanks to your post I'm gonna buy that pc and install Ubuntu. Thanks!

(Pineapplemoonshine is really tasty)

---

### Post by yancek on 2016-07-19
If your windows 10 is pre-installed, you will most likely have UEFI and if you want to dual-boot, I would suggest reading the info at the Ubuntu documentation site below.  Even if you do not dual boot, I would suggest reading it as it contains a lot of useful information on UEFI.  It also explains how to set it up to not use UEFI if that is what you want.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Bucky Ball on 2016-07-19
A lot has changed. If you are a Gnome fan, you will not like Ubuntu now! Unless you are up for a considerable mind-shift. It now uses the Unity desktop environment which is nothing like Gnome. :|

If you want a Gnome-like experience, Xubuntu, Lubuntu or [Ubuntu-Gnome]("https://ubuntugnome.org/") (I know nothing about the latter but other do and will hopefully chime in). 

Have a dig about and you should find more info. Or download Ubuntu 16.04 LTS and 'Try Ubuntu' from the install media. You might like Unity. You might not. It received mixed reactions, to put it mildly, when the changeover happened but many people love it now. Some moved to other flavours.

Just to confirm, is the $180, 32gb storage machine the one you're intending running Ubuntu on? If so, how much RAM and which GPU??? This is very important. A full Ubuntu install will want at least 2Gb or more for a good user experience and also will demand something of the graphics that a dinky machine will not provide.

And as yancek mentions, the problems you're talking about are probably to do with UEFI. That is not any fault of Ubuntu's! Microsoft made it harder. That was a hair-puller at the time but you'll find plenty of folk who are across it now and can help. It is actually painless if you do a bit of preparation.

If you are installing Ubuntu by itself, you don't need UEFI, you can install how you always did. If Win10 is installed, you will (and other versions if they are installed using UEFI from Win7 up). But we'll get to that when we do ... 

(FTR, Ubuntu runs fine on Macs. We have an Apple Hardware Users forum here, but welcome back. :))

---

### Post by pineapplemoonshine on 2016-07-19
I found a way to replace unity with gnome, no problems there

the machine has 2gb of ram with possibilities to upgrade to 8, apparently not so hard on this pc. There's also a Intel HD Graphics inside. Here's the link, you might wanna use google translate if you're not so happy with norwegian. [https://www.netonnet.no/art/ukens-utvalgte/hp-14-ac102no/223481.13355/](https://www.netonnet.no/art/ukens-utvalgte/hp-14-ac102no/223481.13355/)

I also want to completely replace windows 10 with ubuntu, as I don't really like the whole windows thingy, I just use it to play the games I want without having to do a lot of work.. (I just want it simple)

About the mac, gave it to my parents, they had more use for it than I did.. my parents are virus magnets, so at least I have a chance keeping it safe.. (I tried ubuntu as well on them, apparently too advanced, even tho the only programs on the desktop was firefox and openoffice)

---

### Post by grahammechanical on 2016-07-19
There is one important difference between a live session and an installed system. The live session uses an open source video driver. When we install and tick the box "install third party software" we get some free but proprietary audio and video codecs and a proprietary video driver.

Regards.

---

### Post by Bucky Ball on 2016-07-19
[QUOTE=grahammechanical]The live session uses an open source video driver. When we install and tick the box "install third party software" we get some free but proprietary audio and video codecs and a proprietary video driver.[/QUOTE]

So do not tick that box to install third-party drivers or updates. You can update and install whatever drivers you need once installed and that will avoid the glitch of wrong graphics or other drivers. Ticking that box best avoided during install anyway unless specifically required for some reason (and it's 99% of the time not). Much safer to see what you need once installed, which, with Intel graphics which are very well supported on older machines, is probably/possibly nothing ... :)

The majority of codecs, and other things, can be installed later with ubuntu-restricted-extras and VLC (a sound and vid player which I think may be there by default in Ubuntu-Gnome, but don't quote me there).

As you only intend to install Ubuntu and not a dual-boot, you can install exactly as you always did, no UEFI required (and that machine may not use UEFI anyhow, depending on age). If it's set up for UEFI now, though, we can give you a hand switching all that off and set up to install in legacy, old-school style. ;)

Major difference from user perspective is that with UEFI you can, theoretically, have as many partitions as you like of any kind, primary or extended, on one physical disk. With legacy, you are limited to four partitions, either primary or extended. The way around this, as you may know, is that an extended partition is like a container which holds logical partitions, theoretically as many as you like.

Last note: Ubuntu can be installed on either a logical partition inside an extended partition or a primary located anywhere on the drive. Windows needs a primary partition, preferably first drive, first partition if you want to avoid complaints!

Hope that gives a few more clues.

---

### Post by pineapplemoonshine on 2016-07-24
I am back from a small vacation now, so haven't gotten the chance to read, sorry.

I am not a techie. What I understood was to not tick the box to install third-party drivers or updates. Will Ubuntu still install wifi-drivers if they somehow disappear?

Anyhow, I'm gonna order that pc, I'll get back to you guys if there's any problems with the install and drivers and such :)

Edit: Apparently a problem already.. was going to prepare by burning the ubuntu .iso to a disk, but apparently it won't do. Checked it out, and it's an .iso archive (I don't know) . Any simple solutions? Using Windows 10, and the file is opened in 7zip. Downloaded it from [http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/)

---

### Post by Bucky Ball on 2016-07-24
You don't open the ISO. You use it to burn a disk image to a DVD (or USB). That is all. Don't know what app does this in Win. Nero? Don't know if that still exists even.

[LIST]
[*]Download Ubuntu ISO from the Canonical site
[*]Burn install DVD or USB
[*]Boot the computer and change boot device in BIOS to DVD or USB (on some machines you can hit F12 to select a boot device)
[*]When you get to the options screen, 'Try Ubuntu' and see how it goes before installing
[*]If all good, click the 'Install Ubuntu' icon on the desktop
[/LIST]

[This might help]("https://help.ubuntu.com/community/BurningIsoHowto"), but if not, try a search for 'install ubuntu' and you will find tens of links that might.

---

### Post by pineapplemoonshine on 2016-07-24
Yea, I understood, but the .iso file acted like a standard zip-folder, and when trying to burn it to a dvd it simply wouldn't. I installed some other software tho (which wanted me to install norton antivirus as well, blow me) , and this time it appears to work. Gonna test it on my main pc (not installing) then I'm gonna try it on the new pc when it arrives. Thanks :) 
(... waitwhat, the burner software installed crapware as well.. ****..)
Edit: It was a virus.. I tell you, ubuntu will be a blessing.. takes way too much time to remove stuff from windows..

---

### Post by Bucky Ball on 2016-07-24
You create a disk image on the media, DVD or USB. How are you trying to burn the disk? You shouldn't need anything special to do this. I would have thought Win would have a capable tool. 

You don't copy the ISO to the disk. It won't boot. Not a data disk. It is a bootable disk image you're after. Sorry if you already know this, but better to confirm. :)

---

### Post by pineapplemoonshine on 2016-07-24
I tried to burn it to the disk using ImgBurn (apparently one of the top choices, never again, full of malware), and simply burned the .iso to the disk. Didn't even come up at all when rebooting, the option to boot from disk wasn't there.
Moved all dvd related boot options to the top in the bios, still not. Should try another burner program..

Edit: Oh, lol.. Entered the settings for the file, and changed the "Open In.." - settings from 7zip to the windows default.. now it actually looks like a .iso file and not a .rar file :)
Time to test again! (Also got the option to burn to disk)

---

### Post by Bucky Ball on 2016-07-24
It looks like a .rar file??? What are you doing with a Ubuntu download that is a .rar file???

Are you [downloading from here]("http://www.ubuntu.com/download/desktop")? If not, please do so. You should be starting with a an .iso file and not needing to convert .rar files, wherever they came from. 

Once you have the ISO from the official download site, burn a bootable disk image to a disk using, hopefully, a bug free burner. You can also create a USB if you'd rather.

---

### Post by pineapplemoonshine on 2016-07-29
I was totally wrong with all the .iso stuffs and installing.
I bought me a usb stick, and downloaded the exact .iso file you linked to, and now the amazing Ubuntu is installing nicely!

I tried using Win10 for a little while (got the pc in the mail yesterday) , but I discovered it was sluggish as f. Used the Live Boot to test first, and worked as a charm, so now it's installing. I'll be sure to get back to this amazing forum if I need more help!
Thank you!

---

### Post by Bucky Ball on 2016-07-29
Great news. If you're happy, please mark the thread as solved to help others. Thanks. (Thread Tools at top right or see link in my signature.)

Don't hesitate to post a new thread if you hit a brickwall or have further questions. This will improve you chances of support rather than posting on this one which has been resolved and may have a misleading thread title for your next issue. Good luck. :)

---

### Post by pineapplemoonshine on 2016-07-30
Thank you! I'll be sure to use this forum whenever I need help :)
Edit: Oh, Unity works perfect, no need to do anything here :)

---

