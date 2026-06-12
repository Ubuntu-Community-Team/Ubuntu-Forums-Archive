---
title: "Compaq F730US - Tips?"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by Greg T. on 2007-12-17
I'm curious as to whether anyone has any tips regarding the Compaq Presario F730US (aside from, "Don't get it!") Many people have been snagging the F700 line of laptops recently because they've been marked down so low as of late. ($450 or less.) I picked one up yesterday and spent a couple hours doing a Vista backup (onto two DVDs) and resizing the Windows partition so I could dual boot (using a tool within Vista, ironically). I then dropped my Feisty installation CD into it. It's been a mixed bag so far.

What works:

- Installation worked, but only after adding "noapic" as a boot parameter. Credit goes here: [http://ubuntuforums.org/showthread.php?t=614326&highlight=f730us+noapic](http://ubuntuforums.org/showthread.php?t=614326&highlight=f730us+noapic)

- Speaker sound works, but only after adding "options snd-hda-intel model=laptop" to /etc/modprobe.d/alsa-base. [http://ubuntuforums.org/showpost.php?p=3501600&postcount=90](http://ubuntuforums.org/showpost.php?p=3501600&postcount=90). I haven't tried my headphones, though. There are various threads indicating that sound may disappear if you dual-boot into Vista and then back to Ubuntu. One workaround is to unplug the power and reboot... twice. Your mileage may vary. [EDIT: Pulling the plug and battery seems to be sufficient. The config file change doesn't seem to be needed.]

- Wireless works, but I had to configure it using ndiswrapper. One problem particular to the F730US is that HP Compaq doesn't list the drivers. See this thread for more, including a link to the Broadcomm drivers that worked for me: [http://forums12.itrc.hp.com/service/forums/bizsupport/questionanswer.do?admit=109447627+1197918076455+28353475&threadId=1170475](http://forums12.itrc.hp.com/service/forums/bizsupport/questionanswer.do?admit=109447627+1197918076455+28353475&threadId=1170475). However, if you're trying gutsy, there are new restricted drivers that may eliminate the need for ndiswrapper.

What doesn't:

- Ubuntu will occasionally tell me that CD has been mounted when none is in the drive.  

- I'm struggling with suspend / hibernate at the moment. On suspend, the screen will blank but it will not recover on resume. I've followed the nvidia instructions here, to no avail: [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend).

Aside from (or in addition to) the "noapic" parameter, I've seen a dizzying and sometimes contradictory variety of boot parameters suggested for this and similar Compaq and HP laptops. Each parameter seems to have its own set of drawbacks, ranging from excessive CPU utilization to wireless and USB incompatibilities. If something worked for you, you could save me and others a lot of trial-and-error time by posting.

This laptop will be a Christmas gift to my parents. The suspend issue is a deal-breaker for me. If I can't wrestle this laptop to the ground using Ubuntu, I'll have to fall back to the default Vista installation. However, if I can get it working, I'll likely switch over their desktop to Ubuntu as well. I suspect I'm not the only one in this situation. Tips/suggestions/advice welcomed.

AMD Mobile Athlon 64 X2 TK-55(1.80GHz)
15.4" Wide XGA 
1GB RAM
120GB 5400 RPM Hard Drive
NVIDIA GeForce Go 6100

---

### Post by ZanexGt on 2007-12-18
Hey Greg, I (like many others I presume) am in the same boat as you. 

I just recenty purchased a Compaq F730US for less than $400 and am trying hard to get it working properly in Ubuntu. So far I have been less than successful.

Stats:
AMD Mobile Athlon 64 X2 TK-55(1.80GHz)
15.4" Wide XGA 
1GB RAM
120GB 5400 RPM Hard Drive
NVIDIA GeForce Go 6100 
Ubuntu 7.10 Gutsy

So, like you, I shrank the Vista partition and opened up 43GB or so for my linux install. Using the noapic and acpi=off boot flags is the only way I can get the laptop to boot. However, using the acpi=off boot flag must be generating all sorts of wonky IRQ requests because I have noticed a severe performance penalty. Something is definitely amiss. Additionally my touchpad is not working in 7.10. I've had to resort to a USB mouse for GUI inputs

I haven't had the time to try out the Wireless or Suspend/Hibernate features. I'll be sure to post again once I have attempted both. However, first on my agenda is to get my CPU utilization down so that the laptop is usable in Ubuntu.

I have heard of folks installing Feisty, setup up the boot parameters and then upgrading to Gutsy. I'm not sure if that would alleviate any heartache or if it would just be a waste of time. If anyone reading this is stuck and looking for another soution to install Ubuntu on one of these laptops, I guess its worth a try.

---

### Post by wespad on 2007-12-18
I also had problems with the Live CD, on my new Compaq C713NR. If you're sure you want to install, and not just try it out, then burn a copy of the Alternate CD, and install in textmode. That's what I did, and my install went smoothly.

---

### Post by emitchlpd on 2007-12-18
I also have an f730us. I used the noapic and irqpoll options to do the install, but discovered that after installing I needed to remove these options from /boot/grub/menu.lst in order to have sound work correctly again. I found that after removing those options from the kernel options the random CD insert stopped happening.

I also need to pass the "laptop-hp" option to the snd-hda-intel driver.

At this point I'm very happy with the machine. The touchpad "on/off" button is handy for when I'm typing, but I've found that when I turn the touchpad back on, the Help app launches, for some reason. That is, the Ubuntu Help Center. That's not the same as hitting F1, which launches help for the current application.

I'm curious if anyone else is seeing this behavior, and hopefully if anyone has a workaround.

---

### Post by ZanexGt on 2007-12-19
> **emitchlpd said:**
> IThat is, the Ubuntu Help Center. That's not the same as hitting F1, which launches help for the current application.

I'm curious if anyone else is seeing this behavior, and hopefully if anyone has a workaround.

I am experiencing the same exact behavior. I would like to fix this but still have other things that are more pressing before I run this down.

---

### Post by Greg T. on 2007-12-19
I'm in the same boat on the trackpad triggering help as well. XanexGt, if you can't get the trackpad working at all, check to make sure you have the settings listed in this post: [http://ubuntuforums.org/showthread.php?p=2570111&highlight=trackpad#post2570111](http://ubuntuforums.org/showthread.php?p=2570111&highlight=trackpad#post2570111)

---

### Post by ZanexGt on 2007-12-20
Update:

Ultimately, my installation needed only the noapic boot parameter to work properly. I have read contradictory opinions on whether or not to continue using the . boot parameter after installing Ubuntu. However, it seems to be running fine with the parameter in place. 

I got the wireless installed. First, I tried the Gutsy built in restricted driver manager and it did not work well at all! I only got as far as the router seeing the laptop, assigning an IP address and then nothing. Ultimately i ended up using the ndiswrapper and after that my wireless started working.

After wrestling with the nm-applet, i ended up ditching it for wicd. The nm-applet uses the keyring manager and wanted a password upon every boot so that the keyring manager could assign my WPA password to nm-applet. What it boiled down to was a big pain! After installing wicd, all is great. I get no popups asking for passwords and my wireless networking is working breezily!

As for the touchpad, following my reboot after my initial post in this thread, it started working properly and I have had no troubles whatsoever.

As for the sound, it didn't work directly after install but it started working today before i even attempted to get it to work. Seems to be working just fine!

Lastly, my suspend seems to be working properly! I was surprised, especially after Greg T. said he was having problems with it.

So, basically, everything is working great now for me on F730US! Thanks all.

---

### Post by Greg T. on 2007-12-20
A few tidbits to pass along.

- After playing around with multiple boot parameters, I was able to successfully sleep and resume using the obscure parameter "acpi_sci=level". After so many failed attempts, I about fell out of my chair when it worked. I found this fix on the gentoo forums: [http://forums.gentoo.org/viewtopic-t-598307-start-0-postdays-0-postorder-asc-highlight-acpisci+level.html](http://forums.gentoo.org/viewtopic-t-598307-start-0-postdays-0-postorder-asc-highlight-acpisci+level.html). I'm actually using the following for my boot parameters, based on a number of threads: irqpoll no_timer_check noirqdebug pci=routeirq acpi_sci=level. With these parameters (as well as acpi_sci=level all by itself), not only do suspend and resume work, but everything else continues to work as well, including the USB ports. However, if I suspend/resume and then later attempt to restart the laptop, it will hang right before restarting. I suspect this has to do with nvidia; my desktop acts the same way. It's a small bug, regardless.

- Since adding the new boot parameters, I'm no longer having problems with the DVD drive.

- After dual booting into Vista, I encountered the "no sound" bug that I mentioned in my initial post. I actually had to unplug the power and pop out the battery to get sound to work again.

- My big concern is wifi. Using version 1.50 of ndiswrapper and the Windows XP driver mentioned in my initial post, I had inconsistent results in connecting to my wrt54g at home. (Vista also sometimes failed to connect to it, though overall it did a much better job.) Probably half the time I was unable to connect and it seemed like successes and failures ran in bunches. There are many wireless routers in range of my condo and my wireless router uses customized and potentially outdated (Sveasoft) firmware, so perhaps the problem has little to with the laptop. Tonight I'm at my parent's home, and using their wrt54g router--which was flashed tonight with the latest standard Linksys firmware--on a basically empty set of wireless networks has resulted in much better results. I'm establishing connections within five seconds in every instance. So it's possible that the connectivity problems I was having were not at all due to the laptop. I'm still worried that the worm could turn (against me) again on this, though, so I'm not declaring victory quite yet.

Because of the last point, the jury is still out on whether I'll keep Ubuntu on this laptop. How well has your wireless connectivity been working?

---

### Post by ZanexGt on 2007-12-20
> **Greg T. said:**
> A few tidbits to pass along.

- Since adding the new boot parameters, I'm no longer having problems with the DVD drive.
.

Because of the last point, the jury is still out on whether I'll keep Ubuntu on this laptop. How well has your wireless connectivity been working?


Greg, interesting comments. I have not had any issues with the CD/DVD drive mounting or trying to mount discs when there were no discs in the drive. However, that could be due to the fact that I am running Gutsy and IIRC you are running Feisty. IT could also be due to something else. 

As for the boot parameters, thanks for posting what you found on the Gentoo forums. I am currently using only the 'noapic' parameter and everything seems to be working fine. I still have to do a complete testing on the hibernate/suspend features as I have only tried to hibernate once, and it worked perfectly. With all the trouble you have had, I may just be lucky. If I have any trouble, I'll be trying out your parameters.

Also w/ the wifi, under the Gutsy restricted driver manager, I had NOTHING but trouble. It never did actually work. Once i switched to the ndiswrapper method using th xp driver, I have had no problems. since I use wicd instead of nm-applet to handle my network connections and since wicd runs with init.d on boot, I have wireless connectivity as soon as I can use my laptop. I assume it takes 3-5 seconds to connect but it seems instant to me since it's ready to go upon access to the GUI. 

I think the problems you are experiencing are more likely due to network traffic or your router. I am using a cheap-o trendnet router and a real nice Bufalo (flashed w/ DD-WRT) without any troubles. Always connects and always runs real quick. 

I do have one question though, at startup I notice a message which flashes by so quickly I haven't been able to write it down. However its something along the lines of "PCIBIOS BUG FOUND X9087091238". Are you experiencing anything similar?

---

### Post by Greg T. on 2007-12-20
Yes, I'm getting the BIOS Bug message as well. It's been present regardless of whatever boot parameters I've tried, and I've tried several. I wish I knew how to make it go away, but it's running OK, so no harm, no foul. 

Thanks for the posting about your wireless. Ndiswrapper seems to be the way to go; it's been running flawlessly for the last day or so. I'm using nm-applet, but cobbled together a script that passes the password to my keyring on startup, so that I don't have to enter the keyring password each time I logon. 

Your experience in getting suspend to work with the noapic parameter may be unique. Then again, I'm running feisty, not gutsy, which may contribute to the problems I had as well. It's good to know there might be more than one way to get it working.

One other bug I've noticed: Despite the above, I've been unable to come out of suspend on a couple occasions. Both times, it's been when I've been on battery power.

---

### Post by asmodaous on 2007-12-23
How do I go into the /boot/grub/menu.lst to take off the noacpi line. When I try it states I do not have premission....PLEASE HELP.

---

### Post by asmodaous on 2007-12-23
I can't get the sound to work. I have added the options snd-hda-intel model=laptop the alsa-base but nothing. I can watch dvd's but with no sound. PLEASE HELP

---

### Post by Rick K on 2007-12-23
I was given a Compaq F730 as a birthday present and this thread has been immensely helpful on installing Ubuntu Gutsy.

My only problem appears to be the wi-fi.  I installed ndiswrapper, but not sure how to get it to work from there.  Any help would be greatly appreciated.

Thanks for all the previous help.

Rick

---

### Post by ZanexGt on 2007-12-23
> **asmodaous said:**
> I can't get the sound to work. I have added the options snd-hda-intel model=laptop the alsa-base but nothing. I can watch dvd's but with no sound. PLEASE HELP

This is a weird issue where if you boot into Microsoft Windows Vista, and then try to reboot into Ubuntu, the sound will stop working. I haven't figured out how to fix this 'bug' however, here is a good workaround to get your sound working. 

To enable sound, turn off your laptop completely. Then remove the power cord. Next, remove the battery from your laptop. Now, reinsert your battery and power cord and reboot your laptop. Once Ubuntu loads back up, you should have sound enabled. *Note,  whenever you boot into Vista, you will need to go through this process to re enable sound (another reason not to use Vista)

---

### Post by asmodaous on 2007-12-23
I can't figure it out how that works but it worked. Thank you ZanexGt. I do not have Vista on my laptop at all, thank god.

---

### Post by ZanexGt on 2007-12-23
> **asmodaous said:**
> How do I go into the /boot/grub/menu.lst to take off the noacpi line. When I try it states I do not have premission....PLEASE HELP.

What you need to do is (in gnome) go to /boot/grub and copy menu.lst to your Desktop.  Before you remove the 'noapic' line, you'll see something like this:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e33dd5b3-fc83-46c4-9361-0be9543afac7 ro quiet splash noapic

Once the menu.lst file is on your desktop, open it up and remove the 'noapic' line from the appropriate line, you should be able to find it easily.

Next, open up a terminal window. type in:

1. cd Desktop
 
2. sudo cp menu.lst /boot/grub
(enter your password when asked)

3. voila, your done! 

enjoy!

---

### Post by ZanexGt on 2007-12-23
> **asmodaous said:**
> I can't figure it out how that works but it worked. Thank you ZanexGt. I do not have Vista on my laptop at all, thank god.

asmodaous, have you seen the following thread?

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

I used this thread and it worked perfectly. Let us know if this thread helps you.

---

### Post by Greg T. on 2007-12-24
If you're having trouble with ndiswrapper, I learned a few things the hard way.

There is a change to /etc/iftab that is needed before installation of ndiswrapper can succeed. The line that begins with an "eth1" (no quotes) needs to be commented out. I discovered this here: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)). (Do a search on iftab.) 

In addition, make sure that /etc/modprobe.d/ndiswrapper contains only one line, that reads: "alias wlan0 ndiswrapper" (no quotes). Without it, the wireless hardware won't configure properly.

Finally, I needed to add "ndiswrapper" (no quotes) to the end of /etc/modules. Without it, every boot resulted in a hang. 

The simplest instructions (no manual compiling of ndiswrapper) can be found here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) [EDIT: This works, but I had trouble losing wireless on suspend/resume until I upgraded to the most recent version of ndiswrapper (from the sourceforge site, not the repos) + the driver linked to in the first post of this thread.]

---

### Post by Greg T. on 2007-12-24
Getting suspend to truly work required turning off the "sync to vblank" option in compiz (many threads on this) and also required adding a couple scripts to get networking to work on suspend/resume. [https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28manager%29%7C%28network%29](https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28manager%29%7C%28network%29)

Getting this laptop to run Ubuntu can be done, but it's not easy.

---

### Post by Rick K on 2007-12-24
Greg,  Thanks for the info, but now I have an even bigger problem.  I can't make a wired connection work with the laptop.    I know that the connection works since I'm using the same set up on a different machine (desktop running Gutsy).  Any suggestions?

Thanks

---

### Post by Rick K on 2007-12-24
> **Rick K said:**
> Greg,  Thanks for the info, but now I have an even bigger problem.  I can't make a wired connection work with the laptop.    I know that the connection works since I'm using the same set up on a different machine (desktop running Gutsy).  Any suggestions?

Thanks

Also, I checked the everything on the machine when it came out of the box with Vista pre-loaded.  It all worked then.

Thanks.

---

### Post by ZanexGt on 2007-12-24
> **Greg T. said:**
> If you're having trouble with ndiswrapper, I learned a few things the hard way.

There is a change to /etc/iftab that is needed before installation of ndiswrapper can succeed. The line that begins with an "eth1" (no quotes) needs to be commented out. I discovered this here: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)). (Do a search on iftab.) 

In addition, make sure that /etc/modprobe.d/ndiswrapper contains only one line, that reads: "alias wlan0 ndiswrapper" (no quotes). Without it, the wireless hardware won't configure properly.

Finally, I needed to add "ndiswrapper" (no quotes) to the end of /etc/modules. Without it, every boot resulted in a hang. 

The simplest instructions (no manual compiling of ndiswrapper) can be found here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

This is really interesting Greg. I hadn't heard of any of the tips you listed here and my installation of the ndiswrapper worked fine. Additionally, I seem to have no trouble connecting to my wireless with WPA/WPA2 enabled. However, I do get an occasional conncection dropout which seems to correlate with the laptop going on power savings mode.

---

### Post by Rick K on 2007-12-24
Zane,

How did you get your wifi to work then?

Any help would be appreciated.

Thanks.

Rick

---

### Post by DonDodge on 2007-12-24
Thanks for this thread. I got my wife a F730US for Christmas and plan to install gutsy on it. All this info will be very helpful.

Has anyone been successful at getting the internal fax/modem to function?

---

### Post by Greg T. on 2007-12-24
I haven't tried the modem. 

My big problem remains suspend/resume, which tends to hang on a blank screen about 1/3 of the time. I'm running feisty, however.

---

### Post by ZanexGt on 2007-12-24
> **Rick K said:**
> Zane,

How did you get your wifi to work then?

Any help would be appreciated.

Thanks.

Rick


I used [these](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) directions to install the ndiswrapper in Gutsy to get the WIFI working. Although these instructions are written for Feisty, they work fine for gutsy. 

Let us know if this works for you as well.

---

### Post by ZanexGt on 2007-12-24
> **DonDodge said:**
> Thanks for this thread. I got my wife a F730US for Christmas and plan to install gutsy on it. All this info will be very helpful.

Has anyone been successful at getting the internal fax/modem to function?

No problem. I haven't tried out the fax/modem yet.

---

### Post by Rick K on 2007-12-24
Zane,

Your instructions link did the trick!

Thanks again!

---

### Post by Greg T. on 2007-12-24
I finally seemed to have gotten all hardware to work with feisty. I had a couple lingering suspend / resume issues. Occasionally, the laptop would hang when trying to come out of suspend. This was due to compiz, so I had to turn it off entirely. (I.e., disable desktop effects.) This is in addition to the "sync to vblank" issue I mentioned earlier. (Compiz has more than one issue with suspend.)

Also, even after getting the laptop to resume consistently, I was having troubles with wireless failing to work. This was very sporadic; it might work the first three or four "suspends," but then wireless give out and fail consistently after that. Nothing short of rebooting could get the wireless to restart. The fix here was to include ndiswrapper in the whitelist section of acpi-support and to use the most recent version of ndiswrapper from the sourceforge site (1.51) and the driver noted in the first post of this thread.

---

### Post by ZanexGt on 2007-12-25
> **Rick K said:**
> Zane,

Your instructions link did the trick!

Thanks again!

No problem, glad you got it to work!

---

### Post by Rick K on 2007-12-25
Since y'all have been so helpful, I still have one really odd problem to ask about.  

The F730 wireless will connect and see several weak wifi connections except for the one in my house (Austin has a lot of free floating wifi).  It will see my own network by name but **won't connect **to it, although the Windows XP machine in the same house connects no problem.  I'm using a Linksys WRT54GL router with Firmware v4.30.0.  I  reset the router and the shared key.  The XP machine continues to connect no problem, but the Ubuntu still won't connect.

Interestingly, the one free floating network that F730 will connect to is a very weak free Linksys.

Anyone else have a similar problem and/or a possible solution?  Any help would be greatly appreciated.

Happy holidays!

Rick

---

### Post by Greg T. on 2007-12-26
You might try changing the wireless channel. I had problems connecting in my condo, where there were 8 or so wireless access points in range, but no problems connecting at my parent's, where there usually was only one WAP in range.

---

### Post by Rick K on 2007-12-27
Well, I tried all of the possible channels, but still no connection.  Any other suggestions?

Rick

---

### Post by sdahlin on 2008-01-19
Has anyone come up with a solution yet to the need for the "noapic" kernel parameter on startup for the compaq F730US (and many of the Compaq/HP laptops it seems).  Everything now works but I feel there is a sluggishness that I should not be experiencing.  Stuff just takes longer than it should and I suspect it is the use of the "noapic" parameter.

Steve

---

### Post by Greg T. on 2008-01-30
I'm using:

```
irqpoll no_timer_check noirqdebug pci=routeirq acpi_sci=level
```

for my boot parameters. See post #8 earlier in this thread.

---

### Post by wantless on 2008-02-01
> **emitchlpd said:**
> The touchpad "on/off" button is handy for when I'm typing, but I've found that when I turn the touchpad back on, the Help app launches, for some reason. That is, the Ubuntu Help Center. That's not the same as hitting F1, which launches help for the current application.

I'm curious if anyone else is seeing this behavior, and hopefully if anyone has a workaround.

If you go to System -> Preferences -> Keyboard Shortcuts
and disable Launch help browser under Desktop, that fixed the problem for me

---

### Post by vendetta red on 2008-03-21
Adding my two cents in:

I also own a Compaq F730US and thanks to a combination of this thread and the updates in 8.04, I have been able to leave windows behind completely on this computer.

The laptop boots fine without any additional boot parameters, but I did find that I needed to use "acpi_sci=level" as mentioned by Greg to get Suspend to work. Wireless wasn't too difficult, and I didn't need to use ndiswrapper. I got the firmware I needed from linuxwireless.org and (after enabling the restricted driver Heron found for my wifi adapter) following the instructions on linuxwireless.org was able to get my adapter working flawlessly!

Also, sound worked out of the box with 8.04, so I am now a happy camper :)

---

### Post by ZanexGt on 2008-04-27
> **vendetta red said:**
> I got the firmware I needed from linuxwireless.org and (after enabling the restricted driver Heron found for my wifi adapter) following the instructions on linuxwireless.org was able to get my adapter working flawlessly!

Also, sound worked out of the box with 8.04, so I am now a happy camper :)

Glad to hear everything worked out for you. I have yet to upgrade to Hardy as I am a little concerned about the Broadcom 43xx bug and the associated fix. I figured that waiting a month or two is not a bad idea as folks iron out the issues between the broadcom wireless drivers and Hardy. 

However, seems like you got everything to work properly.

---

### Post by Greg T. on 2008-05-01
I did a fresh install Hardy on a spare partition and fought through a few issues, but it seems to be working now. I used the "noapic" kernel option to install, which might not have been needed, but has been in the past, so I stuck with it here.

- Startup: I still get the BIOS bug message at boot, but it doesn't seem to stop anything.

- Video: After installation, the hardware driver manager ("System" -> "Administation" -> "Hardware Drivers") said that nvidia card was enabled, but not in use. Baffled, I reinstalled nvidia-glx-new, which worked but resulted in corruption when switching to a virtual console or the restart/shutdown splash screen. I uninstalled nvidia-glx-new and went with nvidia-glx instead. This gives me the same hardware driver manager status as before, but I now ignore it, because everything works, including Compiz.

- Audio: Sound didn't work out of the box, but popping the battery out and unplugging the power cord solved the problem, as before. Easy fix.

- Wireless: Wireless works and does so seemingly much better than before, but that's a meaty topic I'll tackle in a separate post.

- Battery: Screen brightness seems to trend generally downward over time. I installed an LCD brightness applet to manually reset the brightness when the screen gets too dark, but haven't found a fix for the underlying bug.

- Suspend: Suspend generally works and without any special scripts or kernel options, after applying the the tweaks noted here: [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend). It very occasionally would refuse to come out of suspend, which may have to do with Compiz, but it seems to work even more consistently when I use the kernel options I used with my Feisty setup: "irqpoll no_timer_check noirqdebug pci=routeirq acpi_sci=level". 

- Shutdown/Restart: Shutdown and restart were very slow until I applied the fix listed here: [http://ubuntuforums.org/showthread.php?p=4858236#post4858236](http://ubuntuforums.org/showthread.php?p=4858236#post4858236). Until I did this, on shutdown and restart it was dropping into the virtual console and hanging for up to 45 seconds before finally getting to the exit splash screen.

---

### Post by Greg T. on 2008-05-01
I had success with my Broadcomm BCM4311MCG (rev 02) wireless using ndiswrapper on a fresh install of Hardy. I used ndiswrapper instead of the b43 native driver after reading some iffy reports on the b43. Installation was simpler than it was on previous attempts in Feisty and allowed me to connect well when multiple networks were present, something I had trouble doing until now (and noted by another poster earlier in this thread). Instructions follow.

Using synaptic or the command line, install the following packages:

- cabextract
- ndiswrapper-common
- ndiswrapper-utils-1.9

Download the most recent version of the XP Broadcomm driver (for the HP Pavilion dv6105us, because HP doesn't provide a wireless driver online for the f730US): [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-53245-1&lc=en&cc=sg&lang=en&os=228&dlc=en&product=3245619](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-53245-1&lc=en&cc=sg&lang=en&os=228&dlc=en&product=3245619)

The driver is in a "softpaq" .exe file, which requires that the driver be extracted from it. In terminal, change to the directory that contains the softpaq file and use cabextract to extract the driver:

```
cabextract sp36684.exe
```

Then enter the following into terminal:

```
sudo su
echo "blacklist b43" >> /etc/modprobe.d/blacklist
```

Change to the directory that contains the extracted driver and enter the following into terminal:

```
ndiswrapper -i bcmwl5.inf
```

Finally, due to an obscure bug there is a need to edit rc.local:

```
sudo gedit /etc/rc.local
```

Add the following to lines to the end of the rc.local script, just before the "exit 0":

```
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44
```

Then reboot. That should do it. The downloaded and extracted files can be safely deleted at this point, if all's working.

---

### Post by Greg T. on 2008-05-01
I should mention one other fix to a wireless problem that apparently existed in Gutsy. I use nm-applet to manage my wireless connections, but gnome-keyring requires that I enter a password before I can connect to wireless access points that use encryption. I used the same password I use to login. Unfortunately, although I login automatically, I nonetheless get prompted for the gnome-keyring password every time at boot, before connecting to my WAP. To eliminate the irritation of entering this password each time at boot, I changed this password to a blank password. Note that this does not change my user password. The password change can be done by navigating the following:

"System" -> "Preferences" -> "Encryption and Keyrings" -> "Password Keyrings" tab -> select "login Automatically unlocked when user logs in" -> press "Change Unlock Password"

---

### Post by Greg T. on 2008-05-03
I may have found a workaround the screen dimming problem. I disabled "Dim display when idle" in gnome-power-manager, which *may* have been contributing to the problem. The bigger problem is that screen brightness isn't always being properly restored on boot. In particular, when I unplug the AC adapter, my screen brightness drops to 70%, and when I plug back in it's normally restored to 100%. However, if I unplug (dropping brightness to 70%), shutdown, and then plug in before powering up again, on boot the brightness will be at 70%, not 100%. If I do this same routine again, on the next boot screen brightness will have dropped another 30% or so, to at or around 40%.

My hack was to write a script that runs at startup that sets the screen brightness at 100% if plugged in and at 70% if it's on battery. I made the script executable and placed a link to it as the second-to-last line in /etc/rc.local (before "exit 0"). It seems to be working so far. Here's the script:

```
#!/bin/bash

# AC Adapter

AC_DEVICE=$( hal-find-by-property --key info.category --string ac_adapter | head -n 1 )
[ "${AC_DEVICE}" != "" ] &&
AC_STATUS=$( hal-get-property --udi ${AC_DEVICE} --key ac_adapter.present | sed -e 's/true/on-line/; s/false/off-line/' )

if [ "$AC_STATUS" = "on-line" ]; then
  echo -n 92 > /proc/acpi/video/VGA/LCD/brightness
else
  echo -n 56 > /proc/acpi/video/VGA/LCD/brightness
fi
```

The screen brightness buttons (f7 & f8) work just fine for manual screen brightness adjustments, but because this is my parents' laptop, I want it to work more or less automatically the way they'd expect.

---

