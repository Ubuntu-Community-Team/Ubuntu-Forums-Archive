---
title: "Problem Installing, And running From Live-CD"
date: 2006-05-10
forum: Installation &amp; Upgrades
---

### Post by muffinhead on 2006-05-10
I just recieved my ubuntu CD's via Shipit, today in the mail, I was like a kid on christmastime. But when I either go to run the install CD or the Live CD, I get an error right after the hardware check, on the, 

"Load Installer Components from CD". It Says, 

"There was a Problem reading data from the CD-Rom. Please Make Sure it is in the Drive. If retrying Does not work, you should check the Integrity of Your CD-Rom". Failed To Copy file from CD-Rom".

So I check the Integrity of the CD-Rom, and it comes up with an error saying, 

"./pool/main/l/linux-source-2.6.12/md-modules-2.6.12-9-386-di_2.6.12-9.23_i386.udeb,

file has failed the Md5 Checksum Verification. Your Cd-Rom or this file may have been corrupted.

Mind you These are five brand New CD's Professionally Pressed from the factory, and shipped via Shipit, and Every one of them Fails.

I Can't Download it off the internet, because of being on 56k Dial-Up, So I had to order them via Shipit.

I Don't think it's My DVD-RW Drive, as it's nearly brand new and works fine reading/Writing CD/DVD Roms, and Rewritables, in windows and other distros of Linux, I can boot Just fine from a CD/DVD-Rom, Unless my Problem lies in, that I need to have DMA enabled, for my drive, as I saw in another thread, which is not enabled by Default in ubuntu, but am not sure.

If anyone could help me, I'd greatly appreciate your help, Thank You;)
_________________________________________________________________________________
Btw, My system Specs are:

Intel Celeron D 330 @ 2.66 ghz

One, 160 Gigabyte Hard drive, One 120 Gigabyte hard drive, and One 40 Gigabyte hard drive.

1024 Megabytes of DDR Ram.

Geforce Fx 5500 OC Graphics card.

Sound Blaster Live 24-bit Sound Card.

Sony Dual layer DVD-RW Drive,  DRU-810A

---

### Post by matelot on 2006-05-10
Look at this thread a short time ago. Exactly the same problem, but with mine I think it's a compatability issue with the DVD drive. No solutions in sight so far.

[http://ubuntuforums.org/showthread.php?t=173376](http://ubuntuforums.org/showthread.php?t=173376)

---

### Post by muffinhead on 2006-05-11
I found out how to fix that problem, my DVD-RW Drive required that DMA be Enabled via expert installation, and was finally able to install fine.

My new Problem is, when I go to boot Ubuntu up, the Part with the Ubuntu Logo, it freezes, and hang on, "Starting hotplug Subsystem". I looked all over the forums for a fix, and found some, Like pressing "e" on the grub bootloader screen, changing the boot parameter, or whatever it's called to hda6 (My hard drive) rw init=/bin/bash , and edit /etc/hotplug/blacklists with nano to say snd_hda_intel, and snd_hda_codecs, save and reboot but that didn't work:(  

Another method was pressing CTRL + C , Just as the Starting hotplug subsystem is loading, that works somewhat until it finishes loading, and I'm presented with an error, "Failed to Start "X" or Failed  to start "Xorg". 

I saw a driver for ati cards to fix this, but not for nvidia cards, which my Video card is a Nvidia Geforce FX 5500 OC with 256 megs of Vram and Pixel/Vertex Shading 2.0.

Much Thanks to anyone that can help me with this new Problem, Thank You:)

---

### Post by muffinhead on 2006-05-11
Can someone help me with my problem, Thanks

---

### Post by confused57 on 2006-05-11
After you press Ctrl+C & get the error message, try pressing Ctrl+Alt+F1, which hopefully will get you to a text command prompt.

Try entering     sudo dpkg-reconfigure x-server.xorg

It might work to change the driver to "vesa" or "nv", also select the resolutions that your monitor can handle, no higher.  Then type "startx"(without quotes) at the prompt.

Worth a shot, may or may not work.

I can't remember, but is there a "Help" option when the liveCD starts?  I think there is with Knoppix, but I don't remember with Ubuntu.  If there is, it may give you some instructions on what to enter at the intial boot screen.

---

### Post by muffinhead on 2006-05-11
Thanks it worked, I manually edited the packeges including xorg. 

I'm still having a Problem with it freezing at the  "start hotplug subsystem" and Having to try to press CTRL + C , Quick enough to skip it.

Using Ctrl + C to skip the "Start hotplug Subsystem, is a royal pain in the butt, especially since my reflexes are not fast enough to Press Ctrl + C Right before the  "start hotplug subsystem" dialog comes up during boot or loadtime, and it usually end's up in me skipping something needed by ubuntu accidentally as well, although I have managed once to boot into Ubuntu.

Is there any way to permenantly fix this Hotplug Subsystem Problem, with it freezing during load time, so I don't have to press ctrl + c, and Accidentaly skip something needed by ubuntu?

I have an onboard Intel sound card, but am using a sound blaster live 24-bit in it's place, and I have onboard intel extreme graphics 3d, and am using a PCI Nvidia geforce FX 5500 OC, in it's place.

I've already tried everything from, editing /etc/hotplug/blacklists, for the onboard intel sound, with nano, which did absolutely nothing to Unplugging my usb devices, which also did no good.

Is there anyone that has had this Problem, and is experienced in using ubuntu, that can help me solve this problem, as it's a royal pain in the backside.

Much thanks and appreciation to can help me with this problem, as I'll be really glad once I can get this solved, Thank You;) 

If there is any devs, testers, or experienced users, of Ubuntu, Looking at this thread, I'd really appreciate your help, as you may have an idea what I'm talking about. I believe this problem's been posted before, but the fixes don't seem to work for me, Thanks once again:)

---

### Post by confused57 on 2006-05-11
Maybe there's something here that'll help you:

[http://www-uxsup.csx.cam.ac.uk/pub/doc/suse/suse9.3/suselinux-adminguide_en/sec.hotplug.debug.html](http://www-uxsup.csx.cam.ac.uk/pub/doc/suse/suse9.3/suselinux-adminguide_en/sec.hotplug.debug.html)

Hopefully, someone will see this thread who knows a little about your problem.

Do you happen to have any USB modules connected, such as your modem?

---

### Post by muffinhead on 2006-05-12
I figured out what it was causing the hotplug subsystem to freeze during boot.

It is a conflict between my Onboard video chip "Intel Extreme Graphics 3d", and my Nvidia geforce fx 5500 PCI Video card.

I Figured it must be somthing, so in my bios, I switched my onboard Intel Extreme graphics 3d, video on, and my PCI video off, and voila, it didn't freeze or hang during the Loading "Hotplug Subsystem" During Boot.

I really don't know, if it's a driver Problem with My geforce FX 5500, or if it's a conflict between the Onboard Intel Extreme Graphics, and the Geforce FX 5500, that is causing the "Starting Hotplug Subsystem" to hang and freeze during boot.

I want to Use my geforce fx 5500 For Ubuntu, but am currently Unable because of the hotplug, and the conflict/Driver issue between the onboard, and PCI Video card.

I Supplied as much information, as I've figured out, and know, I narrowed it down to a conflict between the onboard, and PCI Graphics cards, and am trying to wait patiently for someone to help me.

If it is the onboard intel extreme graphics 3d causing the conflict with my PCI Geforce fx 5500 Video card, How can I blacklist the Onboard video, in /etc/hotplug/blacklist with nano? what Parameters do I type, to blacklist my Paticular Onboard video?

Much thanks to anyone that can help me;) 

I am anxiously awaiting your help, and solutions to get Ubuntu working correctly, Thank You:)

**:EDIT:** I found Someone with a similar Problem related to the intel extreme graphics, and Geforce FX in this [Thread]("http://www.ubuntuforums.org/showthread.php?t=28840&highlight=Intel+extreme+graphics+hotplug")

Almost the same exact problem as me, related to the hotplug, and the conflict between the two display adapters, his username is "IAmNotPhillip", and is the third post up from the bottom of the first page, where he mentions it.

---

### Post by muffinhead on 2006-05-12
I'm bumping this up, before it get's bumped way down to the bottom, where no one can see it.

Read above Post, So you can better help me. I believe it's  conflict between my onboard video, and my Geforce fx 5500 PCI Video card, Thank You:) 

Btw I don't know if we are allowed to bump threads or not, I don't want to make it seem like I'm a noob, although I am a newbie to linux. Please don't be harsh on me, if I may have broke a rule, because I didn't know;)

---

### Post by muffinhead on 2006-05-13
Can someone Please help me:confused: , and let me know what I have to do, to make it stop freezing at "Hotplug subsystem" Aparently My Nvidia card is causing it to Freeze at "Starting Hotplug subsystem" , as I'm able to use My Intel Extreme Graphics 3d Onboard video just fine, without Problems. But I really want to use my Geforce fx 5500, instead of onboard video.

As I mentioned two posts above this one, it seems to be a conflict/driver Problem with the geforce FX 5500, or between the onboard video, and my PCI Geforce FX, that is causing it to freeze during boot on "Starting Hotplug subsystem"

Can someone tell me what I need to do, or edit/blacklist, to be able to use my geforce FX 5500, without it freezing during boot on the hotplug subsystem?

I'm really Desperate to get everything working correctly, and would appreciate someones help, that has had a similar problem before, and has solved it, or helped someone solve it.

Thanks, if you can help me, I don't know how many times this post is going to be bumped  down to the bottom, or next page, and bumped back up again, before someone could help me solve my problem:( .

I would really appreciate help, or a solution As Soon As Possible, Thank You.:)

---

### Post by confused57 on 2006-05-13
I may have found a link(s) that could help:

[http://www.ubuntuforums.org/showthread.php?t=33142&highlight=PCI+Graphics](http://www.ubuntuforums.org/showthread.php?t=33142&highlight=PCI+Graphics)

[http://www.ubuntuforums.org/showthread.php?t=156014&highlight=PCI+Graphics](http://www.ubuntuforums.org/showthread.php?t=156014&highlight=PCI+Graphics)

---

### Post by muffinhead on 2006-05-13
Thank You confused, I really appreciate it, It worked Perfectly. Now I can load ubuntu on my Nvidia GeForce FX Card, without it freezing at "hotplug". 

I have the Nvidia Drivers installed, and are working perfectly, Now my screen savers run at normal speed compared to my Onboard Video, which was really slow. Thank you very much:) 

Btw, If an Admin or Moderator is viewing this thread, sorry I kept bumping this thread back up, and double posting. I don't know your posting rules, but will gladly view them as soon as I find them. Sorry for any inconveniences, I may have caused;)

---

### Post by confused57 on 2006-05-13
Good job, glad you got everything working,  I probably would have given up.
In my opinion, you provided additional information each time you bumped the thread and you were following logical troubleshooting steps to correct the problem(s).  What's irritating is when people bump a thread when they haven't gotten a response in an hour. 
What piqued my interest is that I have a Nvidia GeForce XFX5500; but it is AGP,  and works flawlessly, without having to install any additional drivers(I don't do any graphics designing or 3D gaming).  I felt it had to be that yours was PCIe, so I did a quick title search with "PCI graphics" & came up with the links that sounded just like your problem.
Check back when you're ready to install, the liveCD is great for a test run.

---

### Post by ehyb on 2006-06-07
i have the very same problem... same integrated video, same nvidia 5500 card! can anybody please help us?:-|

---

