---
title: "Acer Aspire One - Success with Jaunty"
date: 2009-03-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bobnutfield on 2009-03-24
Hello Everyone,

This has been covered an awful lot now with the popularity of netbooks, but I just wanted to post MY results with a new installation of Jaunty Alpha 6 on my AAO 120GB HD 1GB mem.

I had continued to use the installed Linpus since buying this netbook last October because so much tweaking was required with Intrepid to get the same functionality that already existed with Linpus.  I didn't have time to do the tweaking necessary.

But, I finally decided I could no longer work with the instability in Linpus, so I installed 9.04 32bit using Unetbootin on a USB stick.  The community documentation covers it pretty thoroughly and I did nothing but follow that.

[https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")

Blacklisted acer_wmi module, and wireless up and running.
Installed Cheese and web-cam was up and running.
Installed linux-backports-modules and the traffic LED is up and running.

No other tweaking was necessary and I have a fully functional, stable netbook.  What an improvement from Intrepid!!

The reason for the post is to strongly recommend that anyone wanting to install Ubuntu (particularly Jaunty) follow the above link word for word.  No issues should be encountered and you will up and running in less than an hour.

And, by the way, the boot time from grub to desktop is 35 seconds.  Pretty darn good.

---

### Post by albandy on 2009-03-24
I'll try it, now I'm using linux4one based in ubuntu 8.04

---

### Post by pjalegria on 2009-03-24
I have Jaunty UNR on my Acer Aspire One 8gb SSD 512ram fully work...:D
Its the best distro i have tried so far without any tweaks...

---

### Post by bobnutfield on 2009-03-24
> **albandy said:**
> I'll try it, now I'm using linux4one based in ubuntu 8.04

If you have the same hardware I described in my AAO, I see no reason why you would not achieve he same results.  I never tried the kernel used by so many other (the "sick boy kernel", I believe) because it appeared to require some tweaking as well. Jaunty "just worked" after doing what I described.  But, keep in mind that this gets you a standard Ubuntu desktop.  No different than you get on any other Jaunty install.

I did not like the Remix desktop, and I am pleased to have a full working Ubuntu desktop

---

### Post by pjalegria on 2009-03-24
Remix desktop is fully Standart desktop + Remix files... and you have "desktop-switcher" that provides single click change between standart desktop and Remix desktop.. netbook with 8,9 screen, "maximus" is amazing.

I fully advise you to try Jaunty UNR image...

---

### Post by bobnutfield on 2009-03-24
> **pjalegria said:**
> Remix desktop is fully Standart desktop + Remix files... and you have "desktop-switcher" that provides single click change between standart desktop and Remix desktop.. netbook with 8,9 screen, "maximus" is amazing.

I fully adivse you to try Jaunty UNR imgage...

I have to admit that I have only ever tried the Remix with a UDB live session.  It just appeared to me that all those huge icons showed little improvement in appearance over Linpus.  Just a preference.  I know many like it.

---

### Post by cleentrax on 2009-03-24
Jaunty is working great on my AAO as well. I'm running the base 8gB ssd model, but with an extra 512mb of RAM.

---

### Post by pjalegria on 2009-03-24
Have someone make any tweak for the SSD ?

---

### Post by bailout on 2009-03-24
Sounds good. I have fedora 10 installed on mine atm which isn't bad but wondering whether to install 9.04. I was hoping that with ubuntu's development for the dell and hp netbooks and Mark's statement that he wanted ubuntu to run well on netbooks that 9.04 should be pretty good out of the box.

Have the tweaks you have had to do been reported to the ubuntu devs? Perhaps things like the wifi drivers and light could be fixed in the default packages?

What are the graphics drivers like? I have seen reports that they are very slow in 9.04.

I was thinking of going back to kde in this release but the netbook specific design of UNR looks good.

---

### Post by bobnutfield on 2009-03-24
> 
What are the graphics drivers like? I have seen reports that they are very slow in 9.04.

The AAO has Intel graphics and these modules are included in a stock install.  No tweaking at all was necessary and graphics are good.    I tried the desktop effects just to see if they work and they do, albeit a little slow.  I don't use desktop effects normally, so this was not an issue for me.  I maily use my netbook for what they were intended for, the net on the move, email, and finances with Gnucash.  It works great and I am greatful to the Jaunty devs for the progress made for netbooks.  I am sure that eventually, a simple stock install will have everything working with NO tweaking.

---

### Post by Sockerdrickan on 2009-03-24
In glxgears I get 300fps with UXA and 800fps without UXA

---

### Post by scaine on 2009-03-24
Don't got by those glxgears numbers - I had similar results from that little useless app and yet when I ran SecondLife with UXA, the difference was remarkable.  It was actually playable.  Also, with UXA, you'll get the ability to run opengl games/apps without any clash with Compiz, which is nice.  Try GoogleEarth with compiz running on EXA to see what I mean.

Of course, your mileage may vary - a lot of people have claimed that UXA is just too unstable to their use, despite the perfomance increases...

---

### Post by apauloisdead on 2009-03-24
Downloading Xubuntu jaunty as we speak, gunna give it a shot, let's see how it goes... :D

---

### Post by doogiekd on 2009-03-26
I'm reading a lot about fan issues regarding aao, and am wondering if this is still an issue in jaunty.

does the fan work? is it working overtime or not enough?

thanks

---

### Post by taavikko on 2009-03-27
Has anyonen tried the Storage expansion slot?
Is it functional out-of-the-box, or does it still require some tweaking?

I'm on vacation and haven't got my SDHC card with me, so cannot test...

OT:
Running with minimal install + e16 and it's been a success with me even on intrepid.
But having trouble with poor performance of the SSD, so installing full blown DE like GNOME or KDE is a big ?

Have tried them but they seem to freeze a lot (issue probably related to SQLite and firefox) should test konqueror and/or opera

And wireless handling CLI and/or Wicd is pain in the ****.
No support for 3G modems (like to use my phone to get access online)
Which doesn't work with e16.

Maybe install openbox or some other minimal WM and needed pgk's, but I'm lazy :D

---

### Post by bobnutfield on 2009-03-27
I have everything working on my AAO except the left SD card slot (doesn't seem to work at all) and the right one only works if a card is inserted before booting.  These are known issues with Intrepidl, and I guess Jaunty has not solved it.  But everything else worked out of the box with very little tweaking as  noted in my opening post.  The internal mic works just fine, as well as the built in web cam.  Still pretty impressed with Jaunty on the AAO.

The fan issue seems to have been an issue for some, but not everyone.  I have never had a fan issue, but the fan is very quiet in my machine.  It Atom processor apparently does not support lm-sensors, so checking the CPU temps seems to be unavailable.

---

### Post by zevans on 2009-03-27
> **bobnutfield said:**
> 
The fan issue seems to have been an issue for some, but not everyone.  I have never had a fan issue, but the fan is very quiet in my machine.  It Atom processor apparently does not support lm-sensors, so checking the CPU temps seems to be unavailable.

Must be an Aspire One issue - I can see the temperature sensors on this Advent 4211 just fine, and that's Atom based. 

2.26.29 has loads of USB bugfixes in it, remember seeing them in the changelogs, so maybe that will get your card slot working finally, could be worth an experiment...

---

### Post by pjalegria on 2009-03-27
Have a look...

[http://piie.net/index.php?section=acerhdf](http://piie.net/index.php?section=acerhdf)

---

### Post by neil_aky on 2009-03-27
OK just updated to Jaunty Beta and wireless doesn't work even when I enter "rmmod acer_wmi@ which worked in Alpha; touchpad vertical scrolling only works the first few time you try it after booting then stops working until reboot and SD Card slots still don't automount.  If Ubuntu are serious about getting onto netbooks they should be able to get this working on the AAO...  Anyway, I am about to restore Linpus Linux I may try the final version of Jaunty when it is launched on a USB but my hopes of this ever working out of the box are fading.  May even consider Windows XP at this rate... Disappointing!

---

### Post by elmago79 on 2009-03-27
I had a similar experience. It was fine in alpha, bt in beta I had no wifi, no scrolling, no SD... really sad, because jaunty is incredibly faster and better looking. I'm using linux4one in the meantime, but I really want all the goodies that jaunty + ext4 could bring to my netbook.

---

### Post by Peter09 on 2009-03-28
I have an Aspire one with Jaunty and somewhere along the line the network stopped working.
Found that you needed to blacklist acer_wmi and acer_hal (think that was it from memory). You should then get wireless working by doing
```
modprobe ath5k
```

Add ath5k to modules and it works on boot.

---

### Post by scaine on 2009-03-28
> **neil_aky said:**
> May even consider Windows XP at this rate... Disappointing!

There are times (very few), where I actually feel a pang of sympathy for Microsoft.  Posts like these make it very clear that no-one has ever actually *bought* a copy of Microsoft XP.  I haven't used a Microsoft product since about 2003 when MS made it clear that even if you bought a PC with XP on it, then you scrapped that PC, you couldn't just re-install your XP onto its replacement device.  You'd already bought the damn O/S and now you had to buy it again???  WTF?

So, no-one ever bought XP - they just ripped it off.  As per the comment above, let's face it - if you'd *actually paid* for a copy of XP, you wouldn't be throwing it away to try Jaunty, would you?

---

### Post by Fernzaty on 2009-03-28
I have the netbook remix installed and although I could see the wireless connection, it was greyed out. I blaclisted the acer_wmi module and I'm a little further forward but not there yet. now it tries to connect, the icon spins round and I get the dialogue where I would set my WEP key. I already had this set so I just clicked okay, and the icon spins again. It does this once or twice, then tells me I have no connection. I checked and I am running with ath5k. Any suggestions anyone?

---

### Post by bobnutfield on 2009-03-28
> **zevans said:**
> Must be an Aspire One issue - I can see the temperature sensors on this Advent 4211 just fine, and that's Atom based. 

2.26.29 has loads of USB bugfixes in it, remember seeing them in the changelogs, so maybe that will get your card slot working finally, could be worth an experiment...

The sensors-detect command runs the script but fails with "no sensors found."  It gives the same type of response that I used to get with mobile Celerons.  Some of the chips just don't work with lm-senosrs.

I plan on trying out the 2.6.29 kernel with the stable Jaunty when it is released.  The Alpha is working so well for me, I may not upgrade for a while.

---

### Post by groggyboy on 2009-03-28
> **neil_aky said:**
> touchpad vertical scrolling only works the first few time you try it after booting then stops working until reboot
+1 to the touchpad issue.  anyone know any fixes? it's quite a nuisance.

otherwise, my experience with the beta has been good.  wireless works out of the box.  i haven't had a chance to test my right card reader, but the left one works fine for my purposes.

---

### Post by alican timur on 2009-03-29
I cannot install that!
I have the jaunty UNR .img file and a 1GB flash drive, and i used unetbootin to (i think) make a bootable flash drive, but i get kicked back to busybox/iniramfs console.
Help please?
I have windows xp preinstalled on the machine

---

### Post by auslander1138 on 2009-03-29
> **alican timur said:**
> I cannot install that!
I have the jaunty UNR .img file and a 1GB flash drive, and i used unetbootin to (i think) make a bootable flash drive, but i get kicked back to busybox/iniramfs console.
Help please?
I have windows xp preinstalled on the machine

I had the exact problem as you, but found [MobileTeam/Mobile/HowTo/ImageWriting]("https://wiki.ubuntu.com/MobileTeam/Mobile/HowTo/ImageWriting") which helps if you're doing this from a linux box, but I had to use [USB Image Tool]("http://www.alexpage.de/?page_id=3") to do this from my Windows laptop.

Once you've 'restored' the image to the USB drive, you're good to go! :)

Huzzah!

aus

---

### Post by auslander1138 on 2009-03-29
> **groggyboy said:**
> +1 to the touchpad issue.  anyone know any fixes? it's quite a nuisance.

otherwise, my experience with the beta has been good.  wireless works out of the box.  i haven't had a chance to test my right card reader, but the left one works fine for my purposes.

I have the 8GB Aspire ONE with the solid state drive...and I am also having the issue with the touchpad and the "left hand" card reaser which doesn't seem to work at all (nothing registered when inserting/ejecting)

I'm running the Ubuntu Netbook Remix--installed from USB drive and everything is so-so for now.

Graphics seem to be a little sluggish, compared with 8.04 which I was running on this before (this is a "fresh install" of jaunty beta)

Not bad so far, but a long ways to go IMHO before release...

Cheers!

aus

---

### Post by Fernzaty on 2009-03-30
In case it helps anyone else, I solved why I still couldn't get a working connection even after blacklisting acer_wmi. Originally, my isp provided wpa encryption, but after my daughters laptop was stolen, we think by someone living locally, I asked my isp if they could help me change the code, but all they could offer was wep so we went with it. That's no longer an issue now though, so I reset the router which took me back to wpa, and as soon as I punched in the code for that, I had a fully working connection.

---

### Post by celticbhoy on 2009-03-31
Is there instruction for getting wireless running if it is an upgrade rather than a fresh install? I have tried all wireless suggestions, but still no luck. I cant reinstall madwifi for a lack of headers, and ath5k is not on the system.

---

### Post by taavikko on 2009-03-31
> **celticbhoy said:**
> Is there instruction for getting wireless running if it is an upgrade rather than a fresh install? I have tried all wireless suggestions, but still no luck. I cant reinstall madwifi for a lack of headers, and ath5k is not on the system.

ath5k should be on the kernel, 
```
locate ath5.ko
```

So try rmmodding acer_wmi and then trying again..
```
sudo rmmod acer_wmi && sudo modprobe ath5k
```

If rmmod works, add acer_wmi to blacklist

This worked on my AA110
Running stock jaunty kernel + KDE

---

### Post by celticbhoy on 2009-03-31
Oops my mistake, forgot to update my grub entry on my main install to use the new kernel for jaunty.

---

### Post by markbuntu on 2009-03-31
Well, now that my aspire one will run all day on its new 9 cell battery I think I will give jaunty a try. It has been sitting in a drawer for a few months because the 3 cell battery made it just not worth me dragging it along or bothering to install ubuntu. But now, thanks to some timely mail from hong kong....

I will run it for a few days on xp just for battery life comparison purposes but then I am kicking xp to the curb, ...friggin spyware...

---

### Post by SlCKB0Y on 2009-04-01
Why not try my custom aspire one kernel?

It has lots of advantages

Faster boot time
Better Aspire One hardware support
Wifi LED functional
TuxOnIce for fast hibernation
Acerhdf for kernel fan control
PHC for undervolting and increased battery life

Jaunty works pretty well with the Aspire One and my kernel makes it better
The latest kernel is available at 
[http://www.ug.it.usyd.edu.au/~scole/releases/linux-image-2.6.28.3.20090331_sickboy.0.6_i386.deb](http://www.ug.it.usyd.edu.au/~scole/releases/linux-image-2.6.28.3.20090331_sickboy.0.6_i386.deb)

and normally they can be found at [www.aspireonekernel.com](www.aspireonekernel.com)

---

### Post by celticbhoy on 2009-04-01
Hi Sickboy, are the optimum PHC values known for the one ???

---

### Post by SlCKB0Y on 2009-04-02
> **celticbhoy said:**
> Hi Sickboy, are the optimum PHC values known for the one ???

They seem to be different from aa1 to aa1 as no two cpus are exactly the same

[http://ubuntuforums.org/showthread.php?t=786402&highlight=undervolt](http://ubuntuforums.org/showthread.php?t=786402&highlight=undervolt)

---

### Post by celticbhoy on 2009-04-02
Thanx for the advice, now setup with my new values. Has there been a comparison done for battery life with your new kernel running ?

---

### Post by albinootje on 2009-04-03
> **bobnutfield said:**
> I have everything working on my AAO except the left SD card slot (doesn't seem to work at all) and the right one only works if a card is inserted before booting.  

Got it working on Jaunty Beta, see here :
[http://ubuntuforums.org/showthread.php?p=7003373#post7003373](http://ubuntuforums.org/showthread.php?p=7003373#post7003373)

---

### Post by Damien Kane on 2009-04-08
I don't post much - but hope all the previous issues with AAO are resolved with Jaunty and everything works 'out of the box'. Have been waiting for this release for a while: looking forward to throwing Windows out the -- window.

---

### Post by lizardmenke on 2009-04-08
Does anyone know if the touchpad issue has been resolved yet?
I'd love to put Jaunty on my AAO, but last time i tried the beta (live) the touchpad didn't work and I have no idea how to get it working... :(

---

### Post by jbernardo on 2009-04-08
> **lizardmenke said:**
> Does anyone know if the touchpad issue has been resolved yet?
I'd love to put Jaunty on my AAO, but last time i tried the beta (live) the touchpad didn't work and I have no idea how to get it working... :(

Here it works with the last beta iso. In fact, I only had to:

[LIST]
[*]blacklist acer_wmi
[*]add "options sdhci debug_quirks=1"  to a /etc/modprobe.d/ file (the same I had added the blacklist command)
[*]add "pciehp.pciehp_force=1" to the default grub options in /boot/grub/menu.lst
[*]install linux-modules-backport-jaunty (this only to activate the wifi led)
[/LIST]
And that was it. Even leaving xorg to use exa acceleration gives me 29fps in glblur (but unfortunately only 2.7 in gldragon).

I also did some changes to /etc/intramfs-tools/modules, but that was only to install jaunty in the sdhc key.

---

### Post by SlCKB0Y on 2009-04-08
> **lizardmenke said:**
> Does anyone know if the touchpad issue has been resolved yet?
I'd love to put Jaunty on my AAO, but last time i tried the beta (live) the touchpad didn't work and I have no idea how to get it working... :(

Mine is working fine since the last updates

---

### Post by pjalegria on 2009-04-08
> # add "options sdhci debug_quirks=1" to a /etc/modprobe.d/ file (the same I had added the blacklist command)
# add "pciehp.pciehp_force=1" to the default grub options in /boot/grub/menu.lst

Why you do that?

---

### Post by mxboy15u on 2009-04-08
Neither of my card readers will recognize my card. I know I talked to Sickboy about doing his Kernal but I am hesitant to mess up my computer. I am running a wubi install of 9.04, does your kernal fix the card reader issue sickboy? It is the only things left not working on my Aspire One, everything else, camera, mic etc. works great.

---

### Post by celticbhoy on 2009-04-08
Can you tell where to get the header files for your posted kernel sickboy?

---

### Post by iheartubuntu on 2009-04-08
My dad just bought one for $350 on Amazon (the 10.1" inch)... which included a 2GB chip for free (instead of 1GB)... what a great deal! We wiped out XP and I just put The newest beta of Jaunty on and everything works great "out of the box". No tweaking needed. My dad is really pleased as he will use this when he travels to europe to see family in the summer. Thanks UBUNTU!!!!!

---

### Post by honest spoony on 2009-04-08
I installed the Jaunty Beta over the weekend. Linpus needed to be restored 3 times in the last month, so I couldn't wait till the 23rd.

Install from usb stick took about 20 minutes.
Updates from web took about 20 minutes to download, over an hour to install updates (there were a ton).

Screen size during and after install was perfect.
Sound output worked perfectly.
Sound input not tested.
Webcam not tested
Hotkeys for sound and lcd brightness need adjusted (inaccurate but working)
WiFi worked perfect out of the box, however ubuntu suggested a restricted driver which crashed the wifi. After deactivating the restricted driver wifi worked perfectly again with WPA.
SD cards (left AND right) fail to work. I understand that there might be some tweaking to do but this tweaking must be fixed before the 23rd. Not everyone is willing to tweak them, and not working on install prevent the LH SD from being mounted as /home
Touchpad worked perfectly.

Crash detection kept repeating that crashes were taking place even though the program was still in use and functional.
GUI feedback for sound and lcd hotkeys were annoying and would not fade out within a reasonable time. Remained onscreen for >30 seconds.
Firstboot from install had the user-switcher and battery monitor report that they were unusable.(I forget the exact lingo). Upon additional reboot (before updates) everything was perfect.

I applaud the devs for getting it 99% there. 8.10 was miserable for netbooks (just look at the number of guides to get things to work) but as far as Jaunty and the AAO this is dang close.

---

### Post by mxboy15u on 2009-04-08
> **honest spoony said:**
> I installed the Jaunty Beta over the weekend. Linpus needed to be restored 3 times in the last month, so I couldn't wait till the 23rd.

Install from usb stick took about 20 minutes.
Updates from web took about 20 minutes to download, over an hour to install updates (there were a ton).

Screen size during and after install was perfect.
Sound output worked perfectly.
Sound input not tested.
Webcam not tested
Hotkeys for sound and lcd brightness need adjusted (inaccurate but working)
WiFi worked perfect out of the box, however ubuntu suggested a restricted driver which crashed the wifi. After deactivating the restricted driver wifi worked perfectly again with WPA.
SD cards (left AND right) fail to work. I understand that there might be some tweaking to do but this tweaking must be fixed before the 23rd. Not everyone is willing to tweak them, and not working on install prevent the LH SD from being mounted as /home
Touchpad worked perfectly.

Crash detection kept repeating that crashes were taking place even though the program was still in use and functional.
GUI feedback for sound and lcd hotkeys were annoying and would not fade out within a reasonable time. Remained onscreen for >30 seconds.
Firstboot from install had the user-switcher and battery monitor report that they were unusable.(I forget the exact lingo). Upon additional reboot (before updates) everything was perfect.

I applaud the devs for getting it 99% there. 8.10 was miserable for netbooks (just look at the number of guides to get things to work) but as far as Jaunty and the AAO this is dang close.

I would love to hear a solution to the card readers issue...that needs to get fixed pronto, especially when everything else works so well!

---

### Post by honest spoony on 2009-04-08
> **mxboy15u said:**
> I would love to hear a solution to the card readers issue...that needs to get fixed pronto, especially when everything else works so well!

Agreed. Maybe the AAO users with the 120gb drive don't find the SD readers as crucial, but those of us with the 8gb ssd NEED those cards to work. 

I don't need a lot of space to function since I ssh into my desktop, but I DO need some.

---

### Post by albinootje on 2009-04-08
> **honest spoony said:**
> 
SD cards (left AND right) fail to work. I understand that there might be some tweaking to do but this tweaking must be fixed before the 23rd. Not everyone is willing to tweak them, and not working on install prevent the LH SD from being mounted as /home

This works for me (Found on launchpad.net) :

```

Add "options sdhci debug_quirks=1" (without double quotes) as seperate line to a new file in directory "/etc/modprobe.d" so that the "sdhci" kernel module loads with this module parameter.

```

It's recommended to create a filename with .conf in the end, just like the other files which are already in /etc/modprobe.d/

---

### Post by mxboy15u on 2009-04-08
> **albinootje said:**
> This works for me (Found on launchpad.net) :

```

Add "options sdhci debug_quirks=1" (without double quotes) as seperate line to a new file in directory "/etc/modprobe.d" so that the "sdhci" kernel module loads with this module parameter.

```

It's recommended to create a filename with .conf in the end, just like the other files which are already in /etc/modprobe.d/

Care to tell a newb how to proceed with this?

---

### Post by albinootje on 2009-04-08
> **mxboy15u said:**
> Care to tell a newb how to proceed with this?

Sure. Here's an example :
1) Fire up a terminal (or hit alt-F2)
2) Type in :
```

gksudo gedit /etc/modprobe.d/aceraspireone.conf
3) Fill in that new text file the following :
[code]
options sdhci debug_quirks=1

```
4) Save the file, and exit the gedit text editor.
5) Reboot, and test it

Step 5 *might* be successfully replaced by running the following commands in a terminal :
```

sudo modprobe -r sdhci
sudo modprobe sdhci

```
But I (/me sleepy) haven't tested that yet.

---

### Post by albinootje on 2009-04-08
I found out about this, because the command "dmesg" showed the same error as is mentioned here :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/327130](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/327130)

The command (solution) is also mentioned here :
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by mxboy15u on 2009-04-08
Unfortunately that did not do it for me, neither is hot plugable with a 8GB SDHC card that I am using to test.

---

### Post by albinootje on 2009-04-08
> **mxboy15u said:**
> Unfortunately that did not do it for me, neither is hot plugable with a 8GB SDHC card that I am using to test.
Hmmm :( Can you post the output of the command :
```

dmesg

```

And did this card work before in 8.10 or 8.04 ?

---

### Post by mxboy15u on 2009-04-09
Here is with no cards in the ports.

```

[    1.181465] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    1.181476] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    1.181487] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    1.181498] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    1.181509] pci 0000:00:1f.2: reg 20 io port: [0x60a0-0x60af]
[    1.181539] pci 0000:00:1f.2: PME# supported from D3hot
[    1.181546] pci 0000:00:1f.2: PME# disabled
[    1.181615] pci 0000:00:1f.3: reg 20 io port: [0x6000-0x601f]
[    1.181715] pci 0000:00:1c.0: bridge io port: [0x5000-0x5fff]
[    1.181723] pci 0000:00:1c.0: bridge 32bit mmio: [0x57300000-0x583fffff]
[    1.181735] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x50000000-0x50ffffff]
[    1.181808] pci 0000:02:00.0: reg 10 io port: [0x3000-0x30ff]
[    1.181840] pci 0000:02:00.0: reg 18 64bit mmio: [0x51010000-0x51010fff]
[    1.181863] pci 0000:02:00.0: reg 20 64bit mmio: [0x51000000-0x5100ffff]
[    1.181878] pci 0000:02:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
[    1.181897] pci 0000:02:00.0: supports D1 D2
[    1.181901] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.181910] pci 0000:02:00.0: PME# disabled
[    1.181998] pci 0000:00:1c.1: bridge io port: [0x3000-0x4fff]
[    1.182007] pci 0000:00:1c.1: bridge 32bit mmio: [0x56300000-0x572fffff]
[    1.182019] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x51000000-0x520fffff]
[    1.182163] pci 0000:03:00.0: reg 10 64bit mmio: [0x55200000-0x5520ffff]
[    1.182385] pci 0000:00:1c.2: bridge io port: [0x2000-0x2fff]
[    1.182393] pci 0000:00:1c.2: bridge 32bit mmio: [0x55200000-0x562fffff]
[    1.182405] pci 0000:00:1c.2: bridge 64bit mmio pref: [0x52100000-0x530fffff]
[    1.182473] pci 0000:00:1c.3: bridge io port: [0x1000-0x1fff]
[    1.182482] pci 0000:00:1c.3: bridge 32bit mmio: [0x54100000-0x551fffff]
[    1.182493] pci 0000:00:1c.3: bridge 64bit mmio pref: [0x53100000-0x540fffff]
[    1.182569] pci 0000:00:1e.0: transparent bridge
[    1.182620] bus 00 -> node 0
[    1.182634] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.183275] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    1.183747] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    1.184077] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    1.184390] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    1.184698] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    1.190505] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    1.190783] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    1.191058] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    1.191330] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    1.191603] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    1.191879] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    1.192165] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    1.192444] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    1.192958] ACPI: WMI: Mapper loaded
[    1.193081] SCSI subsystem initialized
[    1.193081] libata version 3.00 loaded.
[    1.193081] usbcore: registered new interface driver usbfs
[    1.193081] usbcore: registered new interface driver hub
[    1.193081] usbcore: registered new device driver usb
[    1.193081] PCI: Using ACPI for IRQ routing
[    1.200022] Bluetooth: Core ver 2.13
[    1.200060] NET: Registered protocol family 31
[    1.200060] Bluetooth: HCI device and connection manager initialized
[    1.200060] Bluetooth: HCI socket layer initialized
[    1.200060] NET: Registered protocol family 8
[    1.200060] NET: Registered protocol family 20
[    1.200082] NetLabel: Initializing
[    1.200086] NetLabel:  domain hash size = 128
[    1.200089] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.200114] NetLabel:  unlabeled traffic allowed by default
[    1.200145] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.200156] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    1.204115] AppArmor: AppArmor Filesystem Enabled
[    1.208022] Switched to high resolution mode on CPU 0
[    1.208387] Switched to high resolution mode on CPU 1
[    1.212026] pnp: PnP ACPI init
[    1.212050] ACPI: bus type pnp registered
[    1.214138] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.3 BAR 7 (0x1000-0x1fff), disabling
[    1.215425] pnp: PnP ACPI: found 9 devices
[    1.215430] ACPI: ACPI bus type pnp unregistered
[    1.215436] PnPBIOS: Disabled by ACPI PNP
[    1.215462] system 00:01: ioport range 0x200-0x20f has been reserved
[    1.215469] system 00:01: ioport range 0x600-0x60f has been reserved
[    1.215475] system 00:01: ioport range 0x610-0x610 has been reserved
[    1.215481] system 00:01: ioport range 0x800-0x80f has been reserved
[    1.215487] system 00:01: ioport range 0x400-0x47f has been reserved
[    1.215492] system 00:01: ioport range 0x500-0x53f has been reserved
[    1.215500] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    1.215507] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.215513] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    1.215520] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    1.215526] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    1.215533] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    1.215539] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    1.250477] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    1.250485] pci 0000:00:1c.0:   IO window: 0x5000-0x5fff
[    1.250495] pci 0000:00:1c.0:   MEM window: 0x57300000-0x583fffff
[    1.250504] pci 0000:00:1c.0:   PREFETCH window: 0x00000050000000-0x00000050ffffff
[    1.250519] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    1.250525] pci 0000:00:1c.1:   IO window: 0x3000-0x4fff
[    1.250534] pci 0000:00:1c.1:   MEM window: 0x56300000-0x572fffff
[    1.250543] pci 0000:00:1c.1:   PREFETCH window: 0x00000051000000-0x000000520fffff
[    1.250554] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    1.250561] pci 0000:00:1c.2:   IO window: 0x2000-0x2fff
[    1.250570] pci 0000:00:1c.2:   MEM window: 0x55200000-0x562fffff
[    1.250578] pci 0000:00:1c.2:   PREFETCH window: 0x00000052100000-0x000000530fffff
[    1.250590] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    1.250596] pci 0000:00:1c.3:   IO window: 0x1000-0x1fff
[    1.250605] pci 0000:00:1c.3:   MEM window: 0x54100000-0x551fffff
[    1.250614] pci 0000:00:1c.3:   PREFETCH window: 0x00000053100000-0x000000540fffff
[    1.250625] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    1.250629] pci 0000:00:1e.0:   IO window: disabled
[    1.250638] pci 0000:00:1e.0:   MEM window: disabled
[    1.250645] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.250674] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.250683] pci 0000:00:1c.0: setting latency timer to 64
[    1.250699] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.250707] pci 0000:00:1c.1: setting latency timer to 64
[    1.250722] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.250730] pci 0000:00:1c.2: setting latency timer to 64
[    1.250745] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.250753] pci 0000:00:1c.3: setting latency timer to 64
[    1.250765] pci 0000:00:1e.0: setting latency timer to 64
[    1.250773] bus: 00 index 0 io port: [0x00-0xffff]
[    1.250778] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.250783] bus: 01 index 0 io port: [0x5000-0x5fff]
[    1.250788] bus: 01 index 1 mmio: [0x57300000-0x583fffff]
[    1.250793] bus: 01 index 2 mmio: [0x50000000-0x50ffffff]
[    1.250797] bus: 01 index 3 mmio: [0x0-0x0]
[    1.250802] bus: 02 index 0 io port: [0x3000-0x4fff]
[    1.250806] bus: 02 index 1 mmio: [0x56300000-0x572fffff]
[    1.250811] bus: 02 index 2 mmio: [0x51000000-0x520fffff]
[    1.250816] bus: 02 index 3 mmio: [0x0-0x0]
[    1.250820] bus: 03 index 0 io port: [0x2000-0x2fff]
[    1.250825] bus: 03 index 1 mmio: [0x55200000-0x562fffff]
[    1.250830] bus: 03 index 2 mmio: [0x52100000-0x530fffff]
[    1.250834] bus: 03 index 3 mmio: [0x0-0x0]
[    1.250839] bus: 04 index 0 io port: [0x1000-0x1fff]
[    1.250843] bus: 04 index 1 mmio: [0x54100000-0x551fffff]
[    1.250848] bus: 04 index 2 mmio: [0x53100000-0x540fffff]
[    1.250853] bus: 04 index 3 mmio: [0x0-0x0]
[    1.250857] bus: 05 index 0 mmio: [0x0-0x0]
[    1.250861] bus: 05 index 1 mmio: [0x0-0x0]
[    1.250865] bus: 05 index 2 mmio: [0x0-0x0]
[    1.250869] bus: 05 index 3 io port: [0x00-0xffff]
[    1.250874] bus: 05 index 4 mmio: [0x000000-0xffffffff]
[    1.250894] NET: Registered protocol family 2
[    1.264134] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.264675] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.265560] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.266048] TCP: Hash tables configured (established 131072 bind 65536)
[    1.266054] TCP reno registered
[    1.272187] NET: Registered protocol family 1
[    1.272405] checking if image is initramfs... it is
[    2.296614] Freeing initrd memory: 7633k freed
[    2.296683] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    2.296689] Simple Boot Flag at 0x44 set to 0x1
[    2.297062] cpufreq: No nForce2 chipset.
[    2.297333] audit: initializing netlink socket (disabled)
[    2.297371] type=2000 audit(1239263900.296:1): initialized
[    2.311807] highmem bounce pool size: 64 pages
[    2.311818] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.314607] VFS: Disk quotas dquot_6.5.1
[    2.314731] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.316052] fuse init (API version 7.10)
[    2.316242] msgmni has been set to 1724
[    2.316604] alg: No test for stdrng (krng)
[    2.316635] io scheduler noop registered
[    2.316639] io scheduler anticipatory registered
[    2.316643] io scheduler deadline registered
[    2.316683] io scheduler cfq registered (default)
[    2.316706] pci 0000:00:02.0: Boot video device
[    2.317312] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.317326] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14cc0), AE_ALREADY_EXISTS
[    2.317341] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    2.318828] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.318841] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14cc0), AE_ALREADY_EXISTS
[    2.320203] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.320263] pcieport-driver 0000:00:1c.0: found MSI capability
[    2.320308] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    2.320328] pci_express 0000:00:1c.0:pcie00: allocate port service
[    2.320363] pci_express 0000:00:1c.0:pcie02: allocate port service
[    2.320390] pci_express 0000:00:1c.0:pcie03: allocate port service
[    2.320486] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    2.320542] pcieport-driver 0000:00:1c.1: found MSI capability
[    2.320582] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X
[    2.320602] pci_express 0000:00:1c.1:pcie00: allocate port service
[    2.320629] pci_express 0000:00:1c.1:pcie02: allocate port service
[    2.320655] pci_express 0000:00:1c.1:pcie03: allocate port service
[    2.320751] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    2.320806] pcieport-driver 0000:00:1c.2: found MSI capability
[    2.320846] pcieport-driver 0000:00:1c.2: irq 2301 for MSI/MSI-X
[    2.320865] pci_express 0000:00:1c.2:pcie00: allocate port service
[    2.320904] pci_express 0000:00:1c.2:pcie02: allocate port service
[    2.320932] pci_express 0000:00:1c.2:pcie03: allocate port service
[    2.321045] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    2.321101] pcieport-driver 0000:00:1c.3: found MSI capability
[    2.321141] pcieport-driver 0000:00:1c.3: irq 2300 for MSI/MSI-X
[    2.321160] pci_express 0000:00:1c.3:pcie00: allocate port service
[    2.321190] pci_express 0000:00:1c.3:pcie02: allocate port service
[    2.321222] pci_express 0000:00:1c.3:pcie03: allocate port service
[    2.321343] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.321525] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.321538] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14cc0), AE_ALREADY_EXISTS
[    2.321828] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.321842] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14cc0), AE_ALREADY_EXISTS
[    2.322122] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.322134] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14cc0), AE_ALREADY_EXISTS
[    2.322414] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.322426] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14cc0), AE_ALREADY_EXISTS
[    2.322560] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.323892] ACPI: AC Adapter [ACAD] (on-line)
[    2.324068] ACPI: Battery Slot [BAT1] (battery absent)
[    2.324222] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.324228] ACPI: Power Button (FF) [PWRF]
[    2.324319] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.324325] ACPI: Power Button (CM) [PWRB]
[    2.324420] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    2.325276] ACPI: Lid Switch [LID0]
[    2.325370] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    2.325376] ACPI: Sleep Button (CM) [SLPB]
[    2.326524] ACPI: SSDT 3F380C90, 0239 (r2  PmRef  Cpu0Ist     3000 INTL 20051117)
[    2.327212] ACPI: SSDT 3F37FE10, 01C7 (r2  PmRef  Cpu0Cst     3001 INTL 20051117)
[    2.328066] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.328119] processor ACPI_CPU:00: registered as cooling_device0
[    2.328128] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.328818] ACPI: SSDT 3F380F10, 00D0 (r2  PmRef  Cpu1Ist     3000 INTL 20051117)
[    2.329485] ACPI: SSDT 3F37EF10, 0083 (r2  PmRef  Cpu1Cst     3000 INTL 20051117)
[    2.330375] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.330417] processor ACPI_CPU:01: registered as cooling_device1
[    2.330425] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.332732] isapnp: Scanning for PnP cards...
[    2.686634] isapnp: No Plug & Play device found
[    2.701510] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.703395] brd: module loaded
[    2.704066] loop: module loaded
[    2.704220] Fixed MDIO Bus: probed
[    2.704233] PPP generic driver version 2.4.2
[    2.704368] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.704432] Driver 'sd' needs updating - please use bus_type methods
[    2.704452] Driver 'sr' needs updating - please use bus_type methods
[    2.704603] ata_piix 0000:00:1f.2: version 2.12
[    2.704631] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.704639] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    2.704703] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.704869] scsi0 : ata_piix
[    2.705109] scsi1 : ata_piix
[    2.707289] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x60a0 irq 14
[    2.707297] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x60a8 irq 15
[    2.868369] ata1.00: ATA-8: ST9120817AS, 3.AAA, max UDMA/133
[    2.868376] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.884397] ata1.00: configured for UDMA/133
[    3.040299] scsi 0:0:0:0: Direct-Access     ATA      ST9120817AS      3.AA PQ: 0 ANSI: 5
[    3.040507] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[    3.040549] sd 0:0:0:0: [sda] Write Protect is off
[    3.040555] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.040625] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.040773] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[    3.040813] sd 0:0:0:0: [sda] Write Protect is off
[    3.040819] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.040888] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.040897]  sda: sda1 sda2
[    3.052338] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.052441] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.053841] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.053882] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.053916] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.053923] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.054044] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1

```

Here is with a card in the left port

```
[    1.181465] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    1.181476] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    1.181487] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    1.181498] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    1.181509] pci 0000:00:1f.2: reg 20 io port: [0x60a0-0x60af]
[    1.181539] pci 0000:00:1f.2: PME# supported from D3hot
[    1.181546] pci 0000:00:1f.2: PME# disabled
[    1.181615] pci 0000:00:1f.3: reg 20 io port: [0x6000-0x601f]
[    1.181715] pci 0000:00:1c.0: bridge io port: [0x5000-0x5fff]
[    1.181723] pci 0000:00:1c.0: bridge 32bit mmio: [0x57300000-0x583fffff]
[    1.181735] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x50000000-0x50ffffff]
[    1.181808] pci 0000:02:00.0: reg 10 io port: [0x3000-0x30ff]
[    1.181840] pci 0000:02:00.0: reg 18 64bit mmio: [0x51010000-0x51010fff]
[    1.181863] pci 0000:02:00.0: reg 20 64bit mmio: [0x51000000-0x5100ffff]
[    1.181878] pci 0000:02:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
[    1.181897] pci 0000:02:00.0: supports D1 D2
[    1.181901] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.181910] pci 0000:02:00.0: PME# disabled
[    1.181998] pci 0000:00:1c.1: bridge io port: [0x3000-0x4fff]
[    1.182007] pci 0000:00:1c.1: bridge 32bit mmio: [0x56300000-0x572fffff]
[    1.182019] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x51000000-0x520fffff]
[    1.182163] pci 0000:03:00.0: reg 10 64bit mmio: [0x55200000-0x5520ffff]
[    1.182385] pci 0000:00:1c.2: bridge io port: [0x2000-0x2fff]
[    1.182393] pci 0000:00:1c.2: bridge 32bit mmio: [0x55200000-0x562fffff]
[    1.182405] pci 0000:00:1c.2: bridge 64bit mmio pref: [0x52100000-0x530fffff]
[    1.182473] pci 0000:00:1c.3: bridge io port: [0x1000-0x1fff]
[    1.182482] pci 0000:00:1c.3: bridge 32bit mmio: [0x54100000-0x551fffff]
[    1.182493] pci 0000:00:1c.3: bridge 64bit mmio pref: [0x53100000-0x540fffff]
[    1.182569] pci 0000:00:1e.0: transparent bridge
[    1.182620] bus 00 -> node 0
[    1.182634] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.183275] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    1.183747] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    1.184077] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    1.184390] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    1.184698] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    1.190505] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    1.190783] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    1.191058] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    1.191330] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    1.191603] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    1.191879] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    1.192165] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    1.192444] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    1.192958] ACPI: WMI: Mapper loaded
[    1.193081] SCSI subsystem initialized
[    1.193081] libata version 3.00 loaded.
[    1.193081] usbcore: registered new interface driver usbfs
[    1.193081] usbcore: registered new interface driver hub
[    1.193081] usbcore: registered new device driver usb
[    1.193081] PCI: Using ACPI for IRQ routing
[    1.200022] Bluetooth: Core ver 2.13
[    1.200060] NET: Registered protocol family 31
[    1.200060] Bluetooth: HCI device and connection manager initialized
[    1.200060] Bluetooth: HCI socket layer initialized
[    1.200060] NET: Registered protocol family 8
[    1.200060] NET: Registered protocol family 20
[    1.200082] NetLabel: Initializing
[    1.200086] NetLabel:  domain hash size = 128
[    1.200089] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.200114] NetLabel:  unlabeled traffic allowed by default
[    1.200145] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.200156] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    1.204115] AppArmor: AppArmor Filesystem Enabled
[    1.208022] Switched to high resolution mode on CPU 0
[    1.208387] Switched to high resolution mode on CPU 1
[    1.212026] pnp: PnP ACPI init
[    1.212050] ACPI: bus type pnp registered
[    1.214138] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.3 BAR 7 (0x1000-0x1fff), disabling
[    1.215425] pnp: PnP ACPI: found 9 devices
[    1.215430] ACPI: ACPI bus type pnp unregistered
[    1.215436] PnPBIOS: Disabled by ACPI PNP
[    1.215462] system 00:01: ioport range 0x200-0x20f has been reserved
[    1.215469] system 00:01: ioport range 0x600-0x60f has been reserved
[    1.215475] system 00:01: ioport range 0x610-0x610 has been reserved
[    1.215481] system 00:01: ioport range 0x800-0x80f has been reserved
[    1.215487] system 00:01: ioport range 0x400-0x47f has been reserved
[    1.215492] system 00:01: ioport range 0x500-0x53f has been reserved
[    1.215500] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    1.215507] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.215513] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    1.215520] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    1.215526] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    1.215533] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    1.215539] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    1.250477] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    1.250485] pci 0000:00:1c.0:   IO window: 0x5000-0x5fff
[    1.250495] pci 0000:00:1c.0:   MEM window: 0x57300000-0x583fffff
[    1.250504] pci 0000:00:1c.0:   PREFETCH window: 0x00000050000000-0x00000050ffffff
[    1.250519] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    1.250525] pci 0000:00:1c.1:   IO window: 0x3000-0x4fff
[    1.250534] pci 0000:00:1c.1:   MEM window: 0x56300000-0x572fffff
[    1.250543] pci 0000:00:1c.1:   PREFETCH window: 0x00000051000000-0x000000520fffff
[    1.250554] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    1.250561] pci 0000:00:1c.2:   IO window: 0x2000-0x2fff
[    1.250570] pci 0000:00:1c.2:   MEM window: 0x55200000-0x562fffff
[    1.250578] pci 0000:00:1c.2:   PREFETCH window: 0x00000052100000-0x000000530fffff
[    1.250590] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    1.250596] pci 0000:00:1c.3:   IO window: 0x1000-0x1fff
[    1.250605] pci 0000:00:1c.3:   MEM window: 0x54100000-0x551fffff
[    1.250614] pci 0000:00:1c.3:   PREFETCH window: 0x00000053100000-0x000000540fffff
[    1.250625] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    1.250629] pci 0000:00:1e.0:   IO window: disabled
[    1.250638] pci 0000:00:1e.0:   MEM window: disabled
[    1.250645] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.250674] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.250683] pci 0000:00:1c.0: setting latency timer to 64
[    1.250699] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.250707] pci 0000:00:1c.1: setting latency timer to 64
[    1.250722] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.250730] pci 0000:00:1c.2: setting latency timer to 64
[    1.250745] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.250753] pci 0000:00:1c.3: setting latency timer to 64
[    1.250765] pci 0000:00:1e.0: setting latency timer to 64
[    1.250773] bus: 00 index 0 io port: [0x00-0xffff]
[    1.250778] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.250783] bus: 01 index 0 io port: [0x5000-0x5fff]
[    1.250788] bus: 01 index 1 mmio: [0x57300000-0x583fffff]
[    1.250793] bus: 01 index 2 mmio: [0x50000000-0x50ffffff]
[    1.250797] bus: 01 index 3 mmio: [0x0-0x0]
[    1.250802] bus: 02 index 0 io port: [0x3000-0x4fff]
[    1.250806] bus: 02 index 1 mmio: [0x56300000-0x572fffff]
[    1.250811] bus: 02 index 2 mmio: [0x51000000-0x520fffff]
[    1.250816] bus: 02 index 3 mmio: [0x0-0x0]
[    1.250820] bus: 03 index 0 io port: [0x2000-0x2fff]
[    1.250825] bus: 03 index 1 mmio: [0x55200000-0x562fffff]
[    1.250830] bus: 03 index 2 mmio: [0x52100000-0x530fffff]
[    1.250834] bus: 03 index 3 mmio: [0x0-0x0]
[    1.250839] bus: 04 index 0 io port: [0x1000-0x1fff]
[    1.250843] bus: 04 index 1 mmio: [0x54100000-0x551fffff]
[    1.250848] bus: 04 index 2 mmio: [0x53100000-0x540fffff]
[    1.250853] bus: 04 index 3 mmio: [0x0-0x0]
[    1.250857] bus: 05 index 0 mmio: [0x0-0x0]
[    1.250861] bus: 05 index 1 mmio: [0x0-0x0]
[    1.250865] bus: 05 index 2 mmio: [0x0-0x0]
[    1.250869] bus: 05 index 3 io port: [0x00-0xffff]
[    1.250874] bus: 05 index 4 mmio: [0x000000-0xffffffff]
[    1.250894] NET: Registered protocol family 2
[    1.264134] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.264675] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.265560] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.266048] TCP: Hash tables configured (established 131072 bind 65536)
[    1.266054] TCP reno registered
[    1.272187] NET: Registered protocol family 1
[    1.272405] checking if image is initramfs... it is
[    2.296614] Freeing initrd memory: 7633k freed
[    2.296683] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    2.296689] Simple Boot Flag at 0x44 set to 0x1
[    2.297062] cpufreq: No nForce2 chipset.
[    2.297333] audit: initializing netlink socket (disabled)
[    2.297371] type=2000 audit(1239263900.296:1): initialized
[    2.311807] highmem bounce pool size: 64 pages
[    2.311818] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.314607] VFS: Disk quotas dquot_6.5.1
[    2.314731] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.316052] fuse init (API version 7.10)
[    2.316242] msgmni has been set to 1724
[    2.316604] alg: No test for stdrng (krng)
[    2.316635] io scheduler noop registered
[    2.316639] io scheduler anticipatory registered
[    2.316643] io scheduler deadline registered
[    2.316683] io scheduler cfq registered (default)
[    2.316706] pci 0000:00:02.0: Boot video device
[    2.317312] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.317326] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14cc0), AE_ALREADY_EXISTS
[    2.317341] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    2.318828] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.318841] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14cc0), AE_ALREADY_EXISTS
[    2.320203] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.320263] pcieport-driver 0000:00:1c.0: found MSI capability
[    2.320308] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    2.320328] pci_express 0000:00:1c.0:pcie00: allocate port service
[    2.320363] pci_express 0000:00:1c.0:pcie02: allocate port service
[    2.320390] pci_express 0000:00:1c.0:pcie03: allocate port service
[    2.320486] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    2.320542] pcieport-driver 0000:00:1c.1: found MSI capability
[    2.320582] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X
[    2.320602] pci_express 0000:00:1c.1:pcie00: allocate port service
[    2.320629] pci_express 0000:00:1c.1:pcie02: allocate port service
[    2.320655] pci_express 0000:00:1c.1:pcie03: allocate port service
[    2.320751] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    2.320806] pcieport-driver 0000:00:1c.2: found MSI capability
[    2.320846] pcieport-driver 0000:00:1c.2: irq 2301 for MSI/MSI-X
[    2.320865] pci_express 0000:00:1c.2:pcie00: allocate port service
[    2.320904] pci_express 0000:00:1c.2:pcie02: allocate port service
[    2.320932] pci_express 0000:00:1c.2:pcie03: allocate port service
[    2.321045] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    2.321101] pcieport-driver 0000:00:1c.3: found MSI capability
[    2.321141] pcieport-driver 0000:00:1c.3: irq 2300 for MSI/MSI-X
[    2.321160] pci_express 0000:00:1c.3:pcie00: allocate port service
[    2.321190] pci_express 0000:00:1c.3:pcie02: allocate port service
[    2.321222] pci_express 0000:00:1c.3:pcie03: allocate port service
[    2.321343] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.321525] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.321538] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14cc0), AE_ALREADY_EXISTS
[    2.321828] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.321842] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14cc0), AE_ALREADY_EXISTS
[    2.322122] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.322134] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14cc0), AE_ALREADY_EXISTS
[    2.322414] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.322426] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14cc0), AE_ALREADY_EXISTS
[    2.322560] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.323892] ACPI: AC Adapter [ACAD] (on-line)
[    2.324068] ACPI: Battery Slot [BAT1] (battery absent)
[    2.324222] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.324228] ACPI: Power Button (FF) [PWRF]
[    2.324319] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.324325] ACPI: Power Button (CM) [PWRB]
[    2.324420] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    2.325276] ACPI: Lid Switch [LID0]
[    2.325370] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    2.325376] ACPI: Sleep Button (CM) [SLPB]
[    2.326524] ACPI: SSDT 3F380C90, 0239 (r2  PmRef  Cpu0Ist     3000 INTL 20051117)
[    2.327212] ACPI: SSDT 3F37FE10, 01C7 (r2  PmRef  Cpu0Cst     3001 INTL 20051117)
[    2.328066] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.328119] processor ACPI_CPU:00: registered as cooling_device0
[    2.328128] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.328818] ACPI: SSDT 3F380F10, 00D0 (r2  PmRef  Cpu1Ist     3000 INTL 20051117)
[    2.329485] ACPI: SSDT 3F37EF10, 0083 (r2  PmRef  Cpu1Cst     3000 INTL 20051117)
[    2.330375] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.330417] processor ACPI_CPU:01: registered as cooling_device1
[    2.330425] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.332732] isapnp: Scanning for PnP cards...
[    2.686634] isapnp: No Plug & Play device found
[    2.701510] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.703395] brd: module loaded
[    2.704066] loop: module loaded
[    2.704220] Fixed MDIO Bus: probed
[    2.704233] PPP generic driver version 2.4.2
[    2.704368] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.704432] Driver 'sd' needs updating - please use bus_type methods
[    2.704452] Driver 'sr' needs updating - please use bus_type methods
[    2.704603] ata_piix 0000:00:1f.2: version 2.12
[    2.704631] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.704639] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    2.704703] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.704869] scsi0 : ata_piix
[    2.705109] scsi1 : ata_piix
[    2.707289] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x60a0 irq 14
[    2.707297] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x60a8 irq 15
[    2.868369] ata1.00: ATA-8: ST9120817AS, 3.AAA, max UDMA/133
[    2.868376] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.884397] ata1.00: configured for UDMA/133
[    3.040299] scsi 0:0:0:0: Direct-Access     ATA      ST9120817AS      3.AA PQ: 0 ANSI: 5
[    3.040507] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[    3.040549] sd 0:0:0:0: [sda] Write Protect is off
[    3.040555] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.040625] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.040773] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[    3.040813] sd 0:0:0:0: [sda] Write Protect is off
[    3.040819] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.040888] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.040897]  sda: sda1 sda2
[    3.052338] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.052441] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.053841] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.053882] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.053916] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.053923] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.054044] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.057966] ehci_hcd 0000:00:1d.7: debug port 1
[    3.057976] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.058008] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x58544400
[    3.072023] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.072168] usb usb1: configuration #1 chosen from 1 choice
[    3.072224] hub 1-0:1.0: USB hub found
[    3.072241] hub 1-0:1.0: 8 ports detected
[    3.072461] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.072500] uhci_hcd: USB Universal Host Controller Interface driver
[    3.072565] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.072578] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.072584] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.072676] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.072711] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00006080
[    3.072866] usb usb2: configuration #1 chosen from 1 choice
[    3.072919] hub 2-0:1.0: USB hub found
[    3.072944] hub 2-0:1.0: 2 ports detected
[    3.073104] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.073115] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.073122] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.073218] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.073267] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006060
[    3.073413] usb usb3: configuration #1 chosen from 1 choice
[    3.073466] hub 3-0:1.0: USB hub found
[    3.073479] hub 3-0:1.0: 2 ports detected
[    3.073645] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.073656] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.073662] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.073751] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.073797] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006040
[    3.073951] usb usb4: configuration #1 chosen from 1 choice
[    3.074010] hub 4-0:1.0: USB hub found
[    3.074024] hub 4-0:1.0: 2 ports detected
[    3.074182] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.074194] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.074200] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.074285] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    3.074330] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006020
[    3.074483] usb usb5: configuration #1 chosen from 1 choice
[    3.074536] hub 5-0:1.0: USB hub found
[    3.074551] hub 5-0:1.0: 2 ports detected
[    3.074808] usbcore: registered new interface driver libusual
[    3.074873] usbcore: registered new interface driver usbserial
[    3.074895] USB Serial support registered for generic
[    3.074926] usbcore: registered new interface driver usbserial_generic
[    3.074930] usbserial: USB Serial Driver core
[    3.075007] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    3.075408] i8042.c: Warning: Keylock active.
[    3.084162] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.089383] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.089396] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.089403] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.089410] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.089418] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.092095] mice: PS/2 mouse device common for all mice
[    3.112139] rtc_cmos 00:03: RTC can wake from S4
[    3.112209] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.112252] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    3.112405] device-mapper: uevent: version 1.0.3
[    3.112613] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.112794] device-mapper: multipath: version 1.0.5 loaded
[    3.112800] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.112993] EISA: Probing bus 0 at eisa.0
[    3.113006] Cannot allocate resource for EISA slot 1
[    3.113013] Cannot allocate resource for EISA slot 2
[    3.113019] Cannot allocate resource for EISA slot 3
[    3.113025] Cannot allocate resource for EISA slot 4
[    3.113031] Cannot allocate resource for EISA slot 5
[    3.113036] Cannot allocate resource for EISA slot 6
[    3.113051] EISA: Detected 0 cards.
[    3.113316] cpuidle: using governor ladder
[    3.113550] cpuidle: using governor menu
[    3.114668] TCP cubic registered
[    3.114923] NET: Registered protocol family 10
[    3.115794] lo: Disabled Privacy Extensions
[    3.116490] NET: Registered protocol family 17
[    3.116531] Bluetooth: L2CAP ver 2.11
[    3.116535] Bluetooth: L2CAP socket layer initialized
[    3.116541] Bluetooth: SCO (Voice Link) ver 0.6
[    3.116544] Bluetooth: SCO socket layer initialized
[    3.116652] Marking TSC unstable due to TSC halts in idle
[    3.116672] Bluetooth: RFCOMM socket layer initialized
[    3.116685] Bluetooth: RFCOMM TTY layer initialized
[    3.116689] Bluetooth: RFCOMM ver 1.10
[    3.117808] Using IPI No-Shortcut mode
[    3.117985] registered taskstats version 1
[    3.118205]   Magic number: 5:844:975
[    3.118275] button PNP0C0E:00: hash matches
[    3.118347] rtc_cmos 00:03: setting system clock to 2009-04-09 07:58:21 UTC (1239263901)
[    3.118355] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.118360] EDD information not available.
[    3.118783] Freeing unused kernel memory: 532k freed
[    3.119090] Write protecting the kernel text: 4128k
[    3.119199] Write protecting the kernel read-only data: 1532k
[    3.134114] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.497061] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    3.547038] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.547086] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.547134] r8169 0000:02:00.0: setting latency timer to 64
[    3.547370] r8169 0000:02:00.0: irq 2299 for MSI/MSI-X
[    3.548866] eth0: RTL8102e at 0xf7c5c000, 00:1e:68:d3:74:8f, XID 24a00000 IRQ 2299
[    3.845914] usb 1-5: configuration #1 chosen from 1 choice
[    4.132111] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    4.289534] usb 2-1: configuration #1 chosen from 1 choice
[    4.676559] kjournald starting.  Commit interval 5 seconds
[    4.676606] EXT3-fs: mounted filesystem with ordered data mode.
[    9.777642] udev: starting version 140
[   10.248047] intel_rng: FWH not detected
[   10.430472] cdc_acm 2-1:1.0: ttyACM0: USB ACM device
[   10.433168] usbcore: registered new interface driver cdc_acm
[   10.433254] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   10.536225] cfg80211: Using static regulatory domain info
[   10.536240] cfg80211: Regulatory domain: US
[   10.536250] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.536266] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[   10.536281] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   10.536295] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   10.536311] 	(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   10.536326] 	(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   10.536350] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[   10.536468] cfg80211: Calling CRDA for country: US
[   10.722524] Linux agpgart interface v0.103
[   10.841982] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19/input/input6
[   10.857401] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
[   10.933159] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   10.948305] acer-wmi: Acer Laptop ACPI-WMI Extras
[   10.995921] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[   10.996275] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   10.999468] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[   11.003589] cfg80211: Regulatory domain changed to country: US
[   11.003598] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.003605] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   11.003611] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   11.003616] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.003621] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.003627] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   11.049065] Linux video capture interface: v2.00
[   11.181567] iTCO_vendor_support: vendor-support=0
[   11.207498] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   11.207971] iTCO_wdt: Found a ICH7-M or ICH7-U TCO device (Version=2, TCOBASE=0x0460)
[   11.208557] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   11.270898] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.270942] ath5k 0000:03:00.0: setting latency timer to 64
[   11.271371] ath5k 0000:03:00.0: registered as 'phy0'
[   11.343082] phy0: Selected rate control algorithm 'minstrel'
[   11.355706] uvcvideo: Found UVC 1.00 device Acer Crystal Eye webcam (064e:d101)
[   11.357187] input: Acer Crystal Eye webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input8
[   11.360682] usbcore: registered new interface driver uvcvideo
[   11.360786] USB Video Class driver (v0.1.0)
[   11.451685] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.489799] Registered led device: ath5k-phy0::rx
[   11.489969] Registered led device: ath5k-phy0::tx
[   11.489979] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   11.687436] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.687588] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.998810] lp: driver loaded but no devices found
[   12.409010] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000
[   12.464278] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9
[   12.713241] EXT3 FS on loop0, internal journal
[   20.521485] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k
[   20.979994] type=1505 audit(1239278319.358:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1864
[   21.100874] type=1505 audit(1239278319.481:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1868
[   21.101194] type=1505 audit(1239278319.481:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1868
[   21.101316] type=1505 audit(1239278319.481:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1868
[   21.101419] type=1505 audit(1239278319.481:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1868
[   21.418572] type=1505 audit(1239278319.797:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1873
[   21.418986] type=1505 audit(1239278319.797:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1873
[   21.483668] type=1505 audit(1239278319.861:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1877
[   24.910300] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.910306] Bluetooth: BNEP filters: protocol multicast
[   24.954896] Bridge firewalling registered
[   26.875089] ppdev: user-space parallel port driver
[   28.289391] [drm] Initialized drm 1.1.0 20060810
[   28.328715] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.328728] pci 0000:00:02.0: setting latency timer to 64
[   28.330342] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   28.335753] [drm:i915_setparam] *ERROR* unknown parameter 4
[   28.335832] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   29.583408] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   30.619617] r8169: eth0: link down
[   30.620158] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.652329] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   59.849306] PPP BSD Compression module registered
[   59.892846] PPP Deflate Compression module registered
```

And here is the right port.

```
[    1.181465] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    1.181476] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    1.181487] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    1.181498] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    1.181509] pci 0000:00:1f.2: reg 20 io port: [0x60a0-0x60af]
[    1.181539] pci 0000:00:1f.2: PME# supported from D3hot
[    1.181546] pci 0000:00:1f.2: PME# disabled
[    1.181615] pci 0000:00:1f.3: reg 20 io port: [0x6000-0x601f]
[    1.181715] pci 0000:00:1c.0: bridge io port: [0x5000-0x5fff]
[    1.181723] pci 0000:00:1c.0: bridge 32bit mmio: [0x57300000-0x583fffff]
[    1.181735] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x50000000-0x50ffffff]
[    1.181808] pci 0000:02:00.0: reg 10 io port: [0x3000-0x30ff]
[    1.181840] pci 0000:02:00.0: reg 18 64bit mmio: [0x51010000-0x51010fff]
[    1.181863] pci 0000:02:00.0: reg 20 64bit mmio: [0x51000000-0x5100ffff]
[    1.181878] pci 0000:02:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
[    1.181897] pci 0000:02:00.0: supports D1 D2
[    1.181901] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.181910] pci 0000:02:00.0: PME# disabled
[    1.181998] pci 0000:00:1c.1: bridge io port: [0x3000-0x4fff]
[    1.182007] pci 0000:00:1c.1: bridge 32bit mmio: [0x56300000-0x572fffff]
[    1.182019] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x51000000-0x520fffff]
[    1.182163] pci 0000:03:00.0: reg 10 64bit mmio: [0x55200000-0x5520ffff]
[    1.182385] pci 0000:00:1c.2: bridge io port: [0x2000-0x2fff]
[    1.182393] pci 0000:00:1c.2: bridge 32bit mmio: [0x55200000-0x562fffff]
[    1.182405] pci 0000:00:1c.2: bridge 64bit mmio pref: [0x52100000-0x530fffff]
[    1.182473] pci 0000:00:1c.3: bridge io port: [0x1000-0x1fff]
[    1.182482] pci 0000:00:1c.3: bridge 32bit mmio: [0x54100000-0x551fffff]
[    1.182493] pci 0000:00:1c.3: bridge 64bit mmio pref: [0x53100000-0x540fffff]
[    1.182569] pci 0000:00:1e.0: transparent bridge
[    1.182620] bus 00 -> node 0
[    1.182634] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.183275] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    1.183747] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    1.184077] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    1.184390] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    1.184698] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    1.190505] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    1.190783] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    1.191058] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    1.191330] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    1.191603] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    1.191879] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    1.192165] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    1.192444] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    1.192958] ACPI: WMI: Mapper loaded
[    1.193081] SCSI subsystem initialized
[    1.193081] libata version 3.00 loaded.
[    1.193081] usbcore: registered new interface driver usbfs
[    1.193081] usbcore: registered new interface driver hub
[    1.193081] usbcore: registered new device driver usb
[    1.193081] PCI: Using ACPI for IRQ routing
[    1.200022] Bluetooth: Core ver 2.13
[    1.200060] NET: Registered protocol family 31
[    1.200060] Bluetooth: HCI device and connection manager initialized
[    1.200060] Bluetooth: HCI socket layer initialized
[    1.200060] NET: Registered protocol family 8
[    1.200060] NET: Registered protocol family 20
[    1.200082] NetLabel: Initializing
[    1.200086] NetLabel:  domain hash size = 128
[    1.200089] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.200114] NetLabel:  unlabeled traffic allowed by default
[    1.200145] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.200156] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    1.204115] AppArmor: AppArmor Filesystem Enabled
[    1.208022] Switched to high resolution mode on CPU 0
[    1.208387] Switched to high resolution mode on CPU 1
[    1.212026] pnp: PnP ACPI init
[    1.212050] ACPI: bus type pnp registered
[    1.214138] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.3 BAR 7 (0x1000-0x1fff), disabling
[    1.215425] pnp: PnP ACPI: found 9 devices
[    1.215430] ACPI: ACPI bus type pnp unregistered
[    1.215436] PnPBIOS: Disabled by ACPI PNP
[    1.215462] system 00:01: ioport range 0x200-0x20f has been reserved
[    1.215469] system 00:01: ioport range 0x600-0x60f has been reserved
[    1.215475] system 00:01: ioport range 0x610-0x610 has been reserved
[    1.215481] system 00:01: ioport range 0x800-0x80f has been reserved
[    1.215487] system 00:01: ioport range 0x400-0x47f has been reserved
[    1.215492] system 00:01: ioport range 0x500-0x53f has been reserved
[    1.215500] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    1.215507] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.215513] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    1.215520] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    1.215526] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    1.215533] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    1.215539] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    1.250477] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    1.250485] pci 0000:00:1c.0:   IO window: 0x5000-0x5fff
[    1.250495] pci 0000:00:1c.0:   MEM window: 0x57300000-0x583fffff
[    1.250504] pci 0000:00:1c.0:   PREFETCH window: 0x00000050000000-0x00000050ffffff
[    1.250519] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    1.250525] pci 0000:00:1c.1:   IO window: 0x3000-0x4fff
[    1.250534] pci 0000:00:1c.1:   MEM window: 0x56300000-0x572fffff
[    1.250543] pci 0000:00:1c.1:   PREFETCH window: 0x00000051000000-0x000000520fffff
[    1.250554] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    1.250561] pci 0000:00:1c.2:   IO window: 0x2000-0x2fff
[    1.250570] pci 0000:00:1c.2:   MEM window: 0x55200000-0x562fffff
[    1.250578] pci 0000:00:1c.2:   PREFETCH window: 0x00000052100000-0x000000530fffff
[    1.250590] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    1.250596] pci 0000:00:1c.3:   IO window: 0x1000-0x1fff
[    1.250605] pci 0000:00:1c.3:   MEM window: 0x54100000-0x551fffff
[    1.250614] pci 0000:00:1c.3:   PREFETCH window: 0x00000053100000-0x000000540fffff
[    1.250625] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    1.250629] pci 0000:00:1e.0:   IO window: disabled
[    1.250638] pci 0000:00:1e.0:   MEM window: disabled
[    1.250645] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.250674] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.250683] pci 0000:00:1c.0: setting latency timer to 64
[    1.250699] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.250707] pci 0000:00:1c.1: setting latency timer to 64
[    1.250722] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.250730] pci 0000:00:1c.2: setting latency timer to 64
[    1.250745] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.250753] pci 0000:00:1c.3: setting latency timer to 64
[    1.250765] pci 0000:00:1e.0: setting latency timer to 64
[    1.250773] bus: 00 index 0 io port: [0x00-0xffff]
[    1.250778] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.250783] bus: 01 index 0 io port: [0x5000-0x5fff]
[    1.250788] bus: 01 index 1 mmio: [0x57300000-0x583fffff]
[    1.250793] bus: 01 index 2 mmio: [0x50000000-0x50ffffff]
[    1.250797] bus: 01 index 3 mmio: [0x0-0x0]
[    1.250802] bus: 02 index 0 io port: [0x3000-0x4fff]
[    1.250806] bus: 02 index 1 mmio: [0x56300000-0x572fffff]
[    1.250811] bus: 02 index 2 mmio: [0x51000000-0x520fffff]
[    1.250816] bus: 02 index 3 mmio: [0x0-0x0]
[    1.250820] bus: 03 index 0 io port: [0x2000-0x2fff]
[    1.250825] bus: 03 index 1 mmio: [0x55200000-0x562fffff]
[    1.250830] bus: 03 index 2 mmio: [0x52100000-0x530fffff]
[    1.250834] bus: 03 index 3 mmio: [0x0-0x0]
[    1.250839] bus: 04 index 0 io port: [0x1000-0x1fff]
[    1.250843] bus: 04 index 1 mmio: [0x54100000-0x551fffff]
[    1.250848] bus: 04 index 2 mmio: [0x53100000-0x540fffff]
[    1.250853] bus: 04 index 3 mmio: [0x0-0x0]
[    1.250857] bus: 05 index 0 mmio: [0x0-0x0]
[    1.250861] bus: 05 index 1 mmio: [0x0-0x0]
[    1.250865] bus: 05 index 2 mmio: [0x0-0x0]
[    1.250869] bus: 05 index 3 io port: [0x00-0xffff]
[    1.250874] bus: 05 index 4 mmio: [0x000000-0xffffffff]
[    1.250894] NET: Registered protocol family 2
[    1.264134] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.264675] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.265560] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.266048] TCP: Hash tables configured (established 131072 bind 65536)
[    1.266054] TCP reno registered
[    1.272187] NET: Registered protocol family 1
[    1.272405] checking if image is initramfs... it is
[    2.296614] Freeing initrd memory: 7633k freed
[    2.296683] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    2.296689] Simple Boot Flag at 0x44 set to 0x1
[    2.297062] cpufreq: No nForce2 chipset.
[    2.297333] audit: initializing netlink socket (disabled)
[    2.297371] type=2000 audit(1239263900.296:1): initialized
[    2.311807] highmem bounce pool size: 64 pages
[    2.311818] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.314607] VFS: Disk quotas dquot_6.5.1
[    2.314731] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.316052] fuse init (API version 7.10)
[    2.316242] msgmni has been set to 1724
[    2.316604] alg: No test for stdrng (krng)
[    2.316635] io scheduler noop registered
[    2.316639] io scheduler anticipatory registered
[    2.316643] io scheduler deadline registered
[    2.316683] io scheduler cfq registered (default)
[    2.316706] pci 0000:00:02.0: Boot video device
[    2.317312] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.317326] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14cc0), AE_ALREADY_EXISTS
[    2.317341] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    2.318828] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.318841] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14cc0), AE_ALREADY_EXISTS
[    2.320203] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.320263] pcieport-driver 0000:00:1c.0: found MSI capability
[    2.320308] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    2.320328] pci_express 0000:00:1c.0:pcie00: allocate port service
[    2.320363] pci_express 0000:00:1c.0:pcie02: allocate port service
[    2.320390] pci_express 0000:00:1c.0:pcie03: allocate port service
[    2.320486] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    2.320542] pcieport-driver 0000:00:1c.1: found MSI capability
[    2.320582] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X
[    2.320602] pci_express 0000:00:1c.1:pcie00: allocate port service
[    2.320629] pci_express 0000:00:1c.1:pcie02: allocate port service
[    2.320655] pci_express 0000:00:1c.1:pcie03: allocate port service
[    2.320751] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    2.320806] pcieport-driver 0000:00:1c.2: found MSI capability
[    2.320846] pcieport-driver 0000:00:1c.2: irq 2301 for MSI/MSI-X
[    2.320865] pci_express 0000:00:1c.2:pcie00: allocate port service
[    2.320904] pci_express 0000:00:1c.2:pcie02: allocate port service
[    2.320932] pci_express 0000:00:1c.2:pcie03: allocate port service
[    2.321045] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    2.321101] pcieport-driver 0000:00:1c.3: found MSI capability
[    2.321141] pcieport-driver 0000:00:1c.3: irq 2300 for MSI/MSI-X
[    2.321160] pci_express 0000:00:1c.3:pcie00: allocate port service
[    2.321190] pci_express 0000:00:1c.3:pcie02: allocate port service
[    2.321222] pci_express 0000:00:1c.3:pcie03: allocate port service
[    2.321343] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.321525] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.321538] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14cc0), AE_ALREADY_EXISTS
[    2.321828] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.321842] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14cc0), AE_ALREADY_EXISTS
[    2.322122] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.322134] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14cc0), AE_ALREADY_EXISTS
[    2.322414] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    2.322426] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14cc0), AE_ALREADY_EXISTS
[    2.322560] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.323892] ACPI: AC Adapter [ACAD] (on-line)
[    2.324068] ACPI: Battery Slot [BAT1] (battery absent)
[    2.324222] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.324228] ACPI: Power Button (FF) [PWRF]
[    2.324319] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.324325] ACPI: Power Button (CM) [PWRB]
[    2.324420] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    2.325276] ACPI: Lid Switch [LID0]
[    2.325370] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    2.325376] ACPI: Sleep Button (CM) [SLPB]
[    2.326524] ACPI: SSDT 3F380C90, 0239 (r2  PmRef  Cpu0Ist     3000 INTL 20051117)
[    2.327212] ACPI: SSDT 3F37FE10, 01C7 (r2  PmRef  Cpu0Cst     3001 INTL 20051117)
[    2.328066] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.328119] processor ACPI_CPU:00: registered as cooling_device0
[    2.328128] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.328818] ACPI: SSDT 3F380F10, 00D0 (r2  PmRef  Cpu1Ist     3000 INTL 20051117)
[    2.329485] ACPI: SSDT 3F37EF10, 0083 (r2  PmRef  Cpu1Cst     3000 INTL 20051117)
[    2.330375] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.330417] processor ACPI_CPU:01: registered as cooling_device1
[    2.330425] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.332732] isapnp: Scanning for PnP cards...
[    2.686634] isapnp: No Plug & Play device found
[    2.701510] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.703395] brd: module loaded
[    2.704066] loop: module loaded
[    2.704220] Fixed MDIO Bus: probed
[    2.704233] PPP generic driver version 2.4.2
[    2.704368] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.704432] Driver 'sd' needs updating - please use bus_type methods
[    2.704452] Driver 'sr' needs updating - please use bus_type methods
[    2.704603] ata_piix 0000:00:1f.2: version 2.12
[    2.704631] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.704639] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    2.704703] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.704869] scsi0 : ata_piix
[    2.705109] scsi1 : ata_piix
[    2.707289] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x60a0 irq 14
[    2.707297] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x60a8 irq 15
[    2.868369] ata1.00: ATA-8: ST9120817AS, 3.AAA, max UDMA/133
[    2.868376] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.884397] ata1.00: configured for UDMA/133
[    3.040299] scsi 0:0:0:0: Direct-Access     ATA      ST9120817AS      3.AA PQ: 0 ANSI: 5
[    3.040507] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[    3.040549] sd 0:0:0:0: [sda] Write Protect is off
[    3.040555] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.040625] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.040773] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[    3.040813] sd 0:0:0:0: [sda] Write Protect is off
[    3.040819] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.040888] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.040897]  sda: sda1 sda2
[    3.052338] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.052441] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.053841] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.053882] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.053916] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.053923] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.054044] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.057966] ehci_hcd 0000:00:1d.7: debug port 1
[    3.057976] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.058008] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x58544400
[    3.072023] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.072168] usb usb1: configuration #1 chosen from 1 choice
[    3.072224] hub 1-0:1.0: USB hub found
[    3.072241] hub 1-0:1.0: 8 ports detected
[    3.072461] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.072500] uhci_hcd: USB Universal Host Controller Interface driver
[    3.072565] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.072578] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.072584] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.072676] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.072711] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00006080
[    3.072866] usb usb2: configuration #1 chosen from 1 choice
[    3.072919] hub 2-0:1.0: USB hub found
[    3.072944] hub 2-0:1.0: 2 ports detected
[    3.073104] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.073115] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.073122] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.073218] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.073267] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006060
[    3.073413] usb usb3: configuration #1 chosen from 1 choice
[    3.073466] hub 3-0:1.0: USB hub found
[    3.073479] hub 3-0:1.0: 2 ports detected
[    3.073645] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.073656] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.073662] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.073751] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.073797] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006040
[    3.073951] usb usb4: configuration #1 chosen from 1 choice
[    3.074010] hub 4-0:1.0: USB hub found
[    3.074024] hub 4-0:1.0: 2 ports detected
[    3.074182] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.074194] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.074200] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.074285] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    3.074330] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006020
[    3.074483] usb usb5: configuration #1 chosen from 1 choice
[    3.074536] hub 5-0:1.0: USB hub found
[    3.074551] hub 5-0:1.0: 2 ports detected
[    3.074808] usbcore: registered new interface driver libusual
[    3.074873] usbcore: registered new interface driver usbserial
[    3.074895] USB Serial support registered for generic
[    3.074926] usbcore: registered new interface driver usbserial_generic
[    3.074930] usbserial: USB Serial Driver core
[    3.075007] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    3.075408] i8042.c: Warning: Keylock active.
[    3.084162] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.089383] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.089396] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.089403] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.089410] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.089418] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.092095] mice: PS/2 mouse device common for all mice
[    3.112139] rtc_cmos 00:03: RTC can wake from S4
[    3.112209] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.112252] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    3.112405] device-mapper: uevent: version 1.0.3
[    3.112613] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.112794] device-mapper: multipath: version 1.0.5 loaded
[    3.112800] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.112993] EISA: Probing bus 0 at eisa.0
[    3.113006] Cannot allocate resource for EISA slot 1
[    3.113013] Cannot allocate resource for EISA slot 2
[    3.113019] Cannot allocate resource for EISA slot 3
[    3.113025] Cannot allocate resource for EISA slot 4
[    3.113031] Cannot allocate resource for EISA slot 5
[    3.113036] Cannot allocate resource for EISA slot 6
[    3.113051] EISA: Detected 0 cards.
[    3.113316] cpuidle: using governor ladder
[    3.113550] cpuidle: using governor menu
[    3.114668] TCP cubic registered
[    3.114923] NET: Registered protocol family 10
[    3.115794] lo: Disabled Privacy Extensions
[    3.116490] NET: Registered protocol family 17
[    3.116531] Bluetooth: L2CAP ver 2.11
[    3.116535] Bluetooth: L2CAP socket layer initialized
[    3.116541] Bluetooth: SCO (Voice Link) ver 0.6
[    3.116544] Bluetooth: SCO socket layer initialized
[    3.116652] Marking TSC unstable due to TSC halts in idle
[    3.116672] Bluetooth: RFCOMM socket layer initialized
[    3.116685] Bluetooth: RFCOMM TTY layer initialized
[    3.116689] Bluetooth: RFCOMM ver 1.10
[    3.117808] Using IPI No-Shortcut mode
[    3.117985] registered taskstats version 1
[    3.118205]   Magic number: 5:844:975
[    3.118275] button PNP0C0E:00: hash matches
[    3.118347] rtc_cmos 00:03: setting system clock to 2009-04-09 07:58:21 UTC (1239263901)
[    3.118355] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.118360] EDD information not available.
[    3.118783] Freeing unused kernel memory: 532k freed
[    3.119090] Write protecting the kernel text: 4128k
[    3.119199] Write protecting the kernel read-only data: 1532k
[    3.134114] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.497061] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    3.547038] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.547086] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.547134] r8169 0000:02:00.0: setting latency timer to 64
[    3.547370] r8169 0000:02:00.0: irq 2299 for MSI/MSI-X
[    3.548866] eth0: RTL8102e at 0xf7c5c000, 00:1e:68:d3:74:8f, XID 24a00000 IRQ 2299
[    3.845914] usb 1-5: configuration #1 chosen from 1 choice
[    4.132111] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    4.289534] usb 2-1: configuration #1 chosen from 1 choice
[    4.676559] kjournald starting.  Commit interval 5 seconds
[    4.676606] EXT3-fs: mounted filesystem with ordered data mode.
[    9.777642] udev: starting version 140
[   10.248047] intel_rng: FWH not detected
[   10.430472] cdc_acm 2-1:1.0: ttyACM0: USB ACM device
[   10.433168] usbcore: registered new interface driver cdc_acm
[   10.433254] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   10.536225] cfg80211: Using static regulatory domain info
[   10.536240] cfg80211: Regulatory domain: US
[   10.536250] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.536266] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[   10.536281] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   10.536295] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   10.536311] 	(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   10.536326] 	(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   10.536350] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[   10.536468] cfg80211: Calling CRDA for country: US
[   10.722524] Linux agpgart interface v0.103
[   10.841982] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19/input/input6
[   10.857401] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
[   10.933159] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   10.948305] acer-wmi: Acer Laptop ACPI-WMI Extras
[   10.995921] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[   10.996275] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   10.999468] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[   11.003589] cfg80211: Regulatory domain changed to country: US
[   11.003598] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.003605] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   11.003611] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   11.003616] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.003621] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.003627] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   11.049065] Linux video capture interface: v2.00
[   11.181567] iTCO_vendor_support: vendor-support=0
[   11.207498] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   11.207971] iTCO_wdt: Found a ICH7-M or ICH7-U TCO device (Version=2, TCOBASE=0x0460)
[   11.208557] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   11.270898] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.270942] ath5k 0000:03:00.0: setting latency timer to 64
[   11.271371] ath5k 0000:03:00.0: registered as 'phy0'
[   11.343082] phy0: Selected rate control algorithm 'minstrel'
[   11.355706] uvcvideo: Found UVC 1.00 device Acer Crystal Eye webcam (064e:d101)
[   11.357187] input: Acer Crystal Eye webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input8
[   11.360682] usbcore: registered new interface driver uvcvideo
[   11.360786] USB Video Class driver (v0.1.0)
[   11.451685] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.489799] Registered led device: ath5k-phy0::rx
[   11.489969] Registered led device: ath5k-phy0::tx
[   11.489979] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   11.687436] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.687588] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.998810] lp: driver loaded but no devices found
[   12.409010] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000
[   12.464278] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9
[   12.713241] EXT3 FS on loop0, internal journal
[   20.521485] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k
[   20.979994] type=1505 audit(1239278319.358:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1864
[   21.100874] type=1505 audit(1239278319.481:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1868
[   21.101194] type=1505 audit(1239278319.481:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1868
[   21.101316] type=1505 audit(1239278319.481:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1868
[   21.101419] type=1505 audit(1239278319.481:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1868
[   21.418572] type=1505 audit(1239278319.797:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1873
[   21.418986] type=1505 audit(1239278319.797:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1873
[   21.483668] type=1505 audit(1239278319.861:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1877
[   24.910300] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.910306] Bluetooth: BNEP filters: protocol multicast
[   24.954896] Bridge firewalling registered
[   26.875089] ppdev: user-space parallel port driver
[   28.289391] [drm] Initialized drm 1.1.0 20060810
[   28.328715] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.328728] pci 0000:00:02.0: setting latency timer to 64
[   28.330342] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   28.335753] [drm:i915_setparam] *ERROR* unknown parameter 4
[   28.335832] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   29.583408] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   30.619617] r8169: eth0: link down
[   30.620158] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.652329] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   59.849306] PPP BSD Compression module registered
[   59.892846] PPP Deflate Compression module registered
```


I never used this computer with any version besides 9.04, but both readers worked fine with XP for whatever that is worth. Thanks again for the help.

---

### Post by inearlygaveup on 2009-04-10
> **honest spoony said:**
> I installed the [COLOR="Black"]_Jaunty_[/COLOR] Beta over the weekend. Linpus needed to be restored 3 times in the last month, so I couldn't wait till the 23rd.



Hi you Guys - I have been watching this thread but can you help.

Is Jaunty the same as the "Ubuntu Netbook Remix" as I am looking for a replacement for my wife's Acer Aspire One OS

If so is the 23rd the official release date and is that the 23rd of April

---

### Post by albinootje on 2009-04-10
> **mxboy15u said:**
> Here is with no cards in the ports.

I'm not an expert at all on this, but I don't see any interesting/useful error messages :(
Can you check whether the kernel module for it is loaded :
```

lsmod|grep sdhci

```
If not, load it with :
```

modprobe sdhci

```
and see whether anything shows up in the log files.

---

### Post by albinootje on 2009-04-10
> **inearlygaveup said:**
>  Is Jaunty the same as the "Ubuntu Netbook Remix" as I am looking for a replacement for my wife's Acer Aspire One OS

Yes and no, the difference is that Jaunty is the name of the currently beta release for the next official Ubuntu release.
Jaunty will be released for Ubuntu,Kubuntu,Xubuntu,Edubuntu, and Ubuntu Netbook Remix i assume.
The Netbook Remix has amongst other the netbook-launcher package installed, which can also be installed in the other Ubuntu flavors.
> 
If so is the 23rd the official release date and is that the 23rd of April
Yes. See also : [http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr)

---

### Post by jbernardo on 2009-04-10
> **pjalegria said:**
> Why you do that?
To have both card readers working? :)

My problem now is suspend crashes the one. Maybe it is because I have installed jaunty on a sdhc formatted ext4...

---

### Post by inearlygaveup on 2009-04-10
> **albinootje said:**
> Yes and no, the difference is that Jaunty is the name of the currently beta release for the next official Ubuntu release.
Jaunty will be released for Ubuntu,Kubuntu,Xubuntu,Edubuntu, and Ubuntu Netbook Remix i assume.
The Netbook Remix has amongst other the netbook-launcher package installed, which can also be installed in the other Ubuntu flavors.

Yes. See also : [http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr)

Thanks  albinootje

---

### Post by sky5564 on 2009-04-10
everything works great with my UNR jaunty install except the card readers don't seem to be working.

anyone know how to get them working?

edit* 

the left card reader works but the right multi card reader does not

---

### Post by sky5564 on 2009-04-11
> **albinootje said:**
> I'm not an expert at all on this, but I don't see any interesting/useful error messages :(
Can you check whether the kernel module for it is loaded :
```

lsmod|grep sdhci

```
If not, load it with :
```

modprobe sdhci

```
and see whether anything shows up in the log files.


i tried it this is what i got.

```
sdhci_pci         15232 0
sdhci             23940 1 sdhci_pci
```

it's still not detecting it =(

---

### Post by albinootje on 2009-04-12
> **sky5564 said:**
>  it's still not detecting it =(

Can you file a bug report at [http://launchpad.net](http://launchpad.net) ?

---

### Post by sky5564 on 2009-04-15
> **albinootje said:**
> Can you file a bug report at [http://launchpad.net](http://launchpad.net) ?

i guess i don't need to someone else beat me to it.

here is the link 

[https://bugs.launchpad.net/ubuntu/+source/mobile-meta/+bug/360676/]("https://bugs.launchpad.net/ubuntu/+source/mobile-meta/+bug/360676/")

i wish someone would fix that then i would have everything working 100% on my acer aspire one.

---

### Post by mxboy15u on 2009-04-15
> **sky5564 said:**
> i guess i don't need to someone else beat me to it.

here is the link 

[https://bugs.launchpad.net/ubuntu/+source/mobile-meta/+bug/360676/]("https://bugs.launchpad.net/ubuntu/+source/mobile-meta/+bug/360676/")

i wish someone would fix that then i would have everything working 100% on my acer aspire one.

Considering what an important component of the computer the readers are the importance really should be elevated. The popularity of these computers cannot be ignored.

---

### Post by teh603 on 2009-04-15
> **mxboy15u said:**
> Considering what an important component of the computer the readers are the importance really should be elevated. The popularity of these computers cannot be ignored.
Maybe the problem is getting drivers? I wouldn't put it past Acer to have used the binary blob method of putting its drivers into their Linpus distro.

---

### Post by joe_newbie on 2009-04-16
My jaunty netbook remix experience on 8 GB SSD acer aspire one:

Installed Jaunty beta with ext4, used wired connection to install all updates.

Updates fixed wireless issues. However default wireless driver (ath5k) does seem to have problems when doing a lot of downloading, I have resorted to using wired connection for installing some software

Left card reader works, hotpluggable.
Right card reader works, hotpluggable, if card inserted at boot time. 

Webcam works, sound works, internal mic works. 
Bluetooth dongle works.

3d acceleration works, average about 40 FPS in gltron.

Only real problem for me so far: AMAROK2 seems broken.
MP3s will not play, even after installing ubuntu-restricted-extras. Missing functionality from 1.4 (ie Ipod integration)

So now I am trying amarok alternatives.



Overall, fairly happy with jaunty UNR on my acer aspire one!

Joe

---

### Post by gmc on 2009-04-16
Speaking of the SDHC card's.

 I've got a problem with a Verbatim 8GB MicroSDHC card. If I plug it into the right slot and try copying or deleting data from it in Jaunty it causes all sorts of I/O errors and hangs the system. However if I boot my AAO into Windows XP, it works just fine.

This is annoying as I need to use Gpodder to manage podcasts on the card. Anyone else experiancing similar problems?

G

P.S. Forgot to mention that I added the setpci fix from the aa0 wiki.. to /etc/modprobe.d/aa0.conf

options acerhdf interval=2 fanon=65 fanoff=60
options pciehp pciehp_force=1
# Enable sdhc support
options sdhci debug_quirks=1
install sdhci for i in 2381 2382 2383 2384; do /usr/bin/setpci -d 197b:$i AE=47; done; /sbin/modprobe --ignore-install sdhci

---

### Post by inearlygaveup on 2009-04-16
The advice I got from launchpad about installing Jaunty Remix was -

**> If you going to install Ubuntu netbook remix beta,i advice you don't because is not stable enough (i installed it in a tosiba netbook and i had many problems) wait a few days for the stable versios 9.04 which supports many drivers.**

So not being that technical, I am waiting until the 23 before I install it, till then I am running it from a USB stick.

---

### Post by sky5564 on 2009-04-16
> **joe_newbie said:**
> My jaunty netbook remix experience on 8 GB SSD acer aspire one:

Installed Jaunty beta with ext4, used wired connection to install all updates.

Updates fixed wireless issues. However default wireless driver (ath5k) does seem to have problems when doing a lot of downloading, I have resorted to using wired connection for installing some software

Left card reader works, hotpluggable.
Right card reader works, hotpluggable, if card inserted at boot time. 

Webcam works, sound works, internal mic works. 
Bluetooth dongle works.

3d acceleration works, average about 40 FPS in gltron.

Only real problem for me so far: AMAROK2 seems broken.
MP3s will not play, even after installing ubuntu-restricted-extras. Missing functionality from 1.4 (ie Ipod integration)

So now I am trying amarok alternatives.



Overall, fairly happy with jaunty UNR on my acer aspire one!

Joe

AMAROK is for kde. it's not designed for gnome so that might be why its not working right.

unr jaunty comes with rhythm box music player wich is good enough for me it has radio streaming pod casts etc etc .

---

### Post by pjalegria on 2009-04-16
Why you dont try Banshee???, it works very well for me.;)

---

### Post by KhanTG on 2009-04-16
Well... I have an AAO with the 8G-SSD... other than general performance issues associated with the SSD, I'd say that it is running great.  I have Jaunty installed with the standard updates (need to get wireless) and I then installed sickboy's kernel (should have done that first... but it works anyway).  The only major issue that I have is the Right SD card reader (just like the rest of you), but that's not too big an issue for me as I use USB sticks for my portable storage needs.  I have also installed Jaunty on 2 other machines (desktop and laptop) and both are working fine.

Go here for sickboy's kernel (it didn't mess up MY machine): [http://www.aspireonekernel.com/](http://www.aspireonekernel.com/)

---

### Post by sky5564 on 2009-04-16
> **KhanTG said:**
> Well... I have an AAO with the 8G-SSD... other than general performance issues associated with the SSD, I'd say that it is running great.  I have Jaunty installed with the standard updates (need to get wireless) and I then installed sickboy's kernel (should have done that first... but it works anyway).  The only major issue that I have is the Right SD card reader (just like the rest of you), but that's not too big an issue for me as I use USB sticks for my portable storage needs.  I have also installed Jaunty on 2 other machines (desktop and laptop) and both are working fine.

Go here for sickboy's kernel (it didn't mess up MY machine): [http://www.aspireonekernel.com/](http://www.aspireonekernel.com/)

i have the 120gb hdd 1gb ram it came with windows xp pre-installed but after about 5 minutes of using it with xp i realized after i installed avg anti-virus it took forever to boot up and daily virus scanning took its toll on the battery life to.

i don't see why some people are saying jaunty unr is unstable i have been using it daily for the past week and i have 0 complaints .except for the right card slot ofcourse

---

### Post by elmago79 on 2009-04-16
It's really sad Jaunty won't work out of the box with the AAO. Talk about a missed oportunity.

---

### Post by teh603 on 2009-04-16
Its still a beta. Give the devs some time.

At least we've got the option for the sickboy kernel and Ndiswrapper. I'm actually using Ndiswrapper wifi right now under eeebuntu 8.10, and my wifi's working smoothly.

I know, I should be using the Array or Sickboy kernel, but maybe later when I'm more experienced with getting under the metaphoric hood.

---

### Post by sky5564 on 2009-04-16
> **teh603 said:**
> Its still a beta. Give the devs some time.

At least we've got the option for the sickboy kernel and Ndiswrapper. I'm actually using Ndiswrapper wifi right now under eeebuntu 8.10, and my wifi's working smoothly.

I know, I should be using the Array or Sickboy kernel, but maybe later when I'm more experienced with getting under the metaphoric hood.

i would just hold off on using someones custom kernel because you never know the devs might just throw in a driver for the card reader in the next update .

im just using flash drives right now but it would be nice to not have to use my bulky usb card reader adapter just to transfer images off my camera.

---

### Post by elmago79 on 2009-04-16
The thing is, in the RC notes you can read:

> Ubuntu Netbook Remix is known to work on these netbook models:
Asus Eee PC 900
Acer Aspire One
Dell Mini 9


But it's sadly not true. :( I do trust the devs, but it seems I will have to wait until Karmic to have an out of the box Ubuntu experience in my Aspire One. I'll continue to use Linux4one in the meantime ;)

---

### Post by teh603 on 2009-04-17
Has anyone tried the NBR? Maybe there's an NBR-specific bugfix that isn't in the mainline Ubuntu?

I'm personally boycotting all NBRs, because someone might look at a netbook running an NBR and think "Oh, its just an overgrown PDA, not a real computer." When someone looks over my shoulder, I want them to actually see Ubuntu or eeebuntu working. Not some wonky netbook interface.

---

### Post by danni-la on 2009-04-18
> **teh603 said:**
> Has anyone tried the NBR? Maybe there's an NBR-specific bugfix that isn't in the mainline Ubuntu?

I'm personally boycotting all NBRs, because someone might look at a netbook running an NBR and think "Oh, its just an overgrown PDA, not a real computer." When someone looks over my shoulder, I want them to actually see Ubuntu or eeebuntu working. Not some wonky netbook interface.

By NBR I assume you mean the netbook remix (UNR)? 

I have it on my one and love it... in general I find people ask what I am running rather than assuming its an 'overgrown PDA' the interface makes it incredibly easy and fast to use... though I am more interested in how well it works than what people might think...

---

### Post by teh603 on 2009-04-18
Ironically, I have the exact opposite experience. Most people say "ZOMG that can't be an actual computer," and really have trouble believing that its really a full-powered laptop running a full-powered OS.

Although its funny that netbooks with no CD or Floppy are finally becoming popular. Apple's Powerbook 2400 was arguably the first netbook ever, but the critics panned the hell out of it.

'Course, the 2400 also came out well before wifi and USB.

---

### Post by Xyphoid on 2009-04-19
I installed Jaunty Beta and got everything working (except for right cardreader). Installed Madwifi, because with the ath5k driver I couldn't copy large files over my LAN, disabled ath5k. With Madwifi my wireless works, but it will only transfer up to 1Mb/s (LAN).

I already changed my router from 11b/g to 11g.
Set wifi bitrate to 54Mb in Jaunty.

Anybody knows if this will be fixed in the final release or that I have done something wrong? Or am I too demanding and should I be happy with 1Mb/s file transfer?

---

### Post by gadjou on 2009-04-20
Be carefull: never suspend with an external SD card inserted
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/342096]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/342096")

---

### Post by mxboy15u on 2009-04-20
I have given up and gone back to XP. I was going to do a Ubuntu only install on this computer but the card readers are just too important to my everyday use. They are a major piece of hardware for small computers like this and must work correctly. I will monitor this thread for a solution and re-install if things look promising, but unfortunately I cannot mess around and must uninstall for the time being. There is no benefit to using Ubuntu on the Aspire One.

---

### Post by bennachie on 2009-04-20
The problems reported here appear to affect only those who have chosen to use the external SD card as an integral part of their system installation, usually to hold the /home partition. 

I use my external SD card only as a separately mounted HD. The card holds all my current documents and archives. I have not experienced any problems on my eeePC 701 4G similar to those reported in this thread. One of many nice features of Jaunty is that the vanilla Gnome system can easily run entirely within the internal SSD, and works straight out of the box. 

Yes, I know that the SSD will wear out at some stage, but I paid so little for the device that even an 18 month working life (which has already been successfully completed) would be enough to repay my original investment many times over. That is really what netbooks are about.

---

### Post by mxboy15u on 2009-04-20
> **bennachie said:**
> The problems reported here appear to affect only those who have chosen to use the external SD card as an integral part of their system installation, usually to hold the /home partition. 

I use my external SD card only as a separately mounted HD. The card holds all my current documents and archives. I have not experienced any problems on my eeePC 701 4G similar to those reported in this thread. One of many nice features of Jaunty is that the vanilla Gnome system can easily run entirely within the internal SSD, and works straight out of the box. 

Yes, I know that the SSD will wear out at some stage, but I paid so little for the device that even an 18 month working life (which has already been successfully completed) would be enough to repay my original investment many times over. That is really what netbooks are about.

I send a lot of pictures for my job. I need those readers to be hot plugable.

---

### Post by teh603 on 2009-04-20
> **mxboy15u said:**
> I have given up and gone back to XP. I was going to do a Ubuntu only install on this computer but the card readers are just too important to my everyday use. They are a major piece of hardware for small computers like this and must work correctly. I will monitor this thread for a solution and re-install if things look promising, but unfortunately I cannot mess around and must uninstall for the time being. There is no benefit to using Ubuntu on the Aspire One.

If having tons upon tons of free software, digital camera access that seems to actually work (as opposed to Xandros, where its borked like so many other things), linux printing that actually works, easy printer sharing with Macs, and all those other benefits aren't worth it, then what is?

Its just a module that's missing from the kernel. It'll probably be added in a month or two, if not sooner.

---

### Post by mxboy15u on 2009-04-20
> **teh603 said:**
> If having tons upon tons of free software, digital camera access that seems to actually work (as opposed to Xandros, where its borked like so many other things), linux printing that actually works, easy printer sharing with Macs, and all those other benefits aren't worth it, then what is?

Its just a module that's missing from the kernel. It'll probably be added in a month or two, if not sooner.

I like Ubuntu on my other computers, but I have all the software I need with this computer and I don't plug cameras directly in, I plug the memory cards into the slots. This saves me from carrying a cable. I don't own a mac, and don't know anyone that does. I have never had an issue printing with either windows xp or ubuntu. 

I want to switch on this computer, but this card reader issue has been an issue for a long time now with no end in sight. I cannot switch from XP and still use this computer effectively. This card reader bug needs an upgrade because it is getting absolutely no attention where it is at right now.

---

### Post by HankB on 2009-04-20
> **mxboy15u said:**
> I send a lot of pictures for my job. I need those readers to be hot plugable.

My son is running Xubuntu on his AAO (110, I think - 4GB flash and 512M RAM)

On his there must be a card in the right SD slot at boot or it will not work. After that, it seems to work well, even following suspend/resume cycles with no card inserted. This seems to be an AAO quirk.

There were a couple tweaks I applied to get everything tto work, but I cannot now find them. I left notes on his desktop and don't have access now.

HTH,
hank

---

### Post by mxboy15u on 2009-04-20
On mine neither right nor left is pluggable. I have not tried it on boot because that is not really what I use it for. If just the left worked...as some report it does (not for me)...that would be fine with me.

---

### Post by scaine on 2009-04-20
I'll try to find the bug report, but the problem is that unless there is something in the right-reader on boot, neither reader will work.  Try putting a tiny, old SD card in the right reader and leaving it there to see if that activates the left reader.  If I remember correctly, that's all you need to make the left reader work and be hot pluggable.

Or use Sickboy's kernel, which I believe fixes both readers to be hot-pluggable, as noted earlier in this thread.

---

### Post by mxboy15u on 2009-04-20
If this is true then I may be able to make this work. I tried the sickboy kernel and it tanked my wireless and usb modem support for some reason.

---

### Post by honest spoony on 2009-04-20
Update from earlier in the thread.

So apparently the AAO is now working to my father's satisfaction. (I haven't seen it since I added the following)

add "options sdhci debug_quirks=1" to a /etc/modprobe.d/ file
add "pciehp.pciehp_force=1" to the default grub options in /boot/grub/menu.lst 

The pciehp.pciehp_force=1 in the grub added some warnings to the boot that are visible for only a fraction of a second. I can't even read them that fast. I didn't dmesg cause I can't get the AAO back from him.

I asked him about the functionality of the SDs and left works hotplug. Right works on boot. He did not test the Right for hotplug. I did not add the backports to get the wifi LED working, I just don't care about it that much. I still have yet to try hibernation. Suspend has not deleted anything from the SD cards. Suspend worked on menu only, not on lid shut. But I have yet to fully test it... again... he's so pleased that I can't get it back.

I'm happy cause he's happy. 

Anyone know how to make a custom image on a USB that would include all these tweaks like the linpus restore DVD? I doubt that ubuntu will crash like linpus did, but he did ask me about it. If he could just use the ubuntu "restore" usb key like he did the linpus one, that would be enough.

Oh, and those still freakin out about jaunty not working on the AAO the first time, there are only 3 more days till the official release and my issues were resolved HERE in the community.... give it time.

:popcorn:

---

### Post by scaine on 2009-04-20
> **honest spoony said:**
> add "options sdhci debug_quirks=1" to a /etc/modprobe.d/ file
add "pciehp.pciehp_force=1" to the default grub options in /boot/grub/menu.lst 


Cool.  I mentioned a "bug report" in my earlier post - sorry for the confusion, but what I read was actually form this :
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

...which also details the pciehp settings above.  Good luck with it!

---

### Post by mxboy15u on 2009-04-21
> **honest spoony said:**
> Update from earlier in the thread.

So apparently the AAO is now working to my father's satisfaction. (I haven't seen it since I added the following)

add "options sdhci debug_quirks=1" to a /etc/modprobe.d/ file
add "pciehp.pciehp_force=1" to the default grub options in /boot/grub/menu.lst 

The pciehp.pciehp_force=1 in the grub added some warnings to the boot that are visible for only a fraction of a second. I can't even read them that fast. I didn't dmesg cause I can't get the AAO back from him.

I asked him about the functionality of the SDs and left works hotplug. Right works on boot. He did not test the Right for hotplug. I did not add the backports to get the wifi LED working, I just don't care about it that much. I still have yet to try hibernation. Suspend has not deleted anything from the SD cards. Suspend worked on menu only, not on lid shut. But I have yet to fully test it... again... he's so pleased that I can't get it back.

I'm happy cause he's happy. 

Anyone know how to make a custom image on a USB that would include all these tweaks like the linpus restore DVD? I doubt that ubuntu will crash like linpus did, but he did ask me about it. If he could just use the ubuntu "restore" usb key like he did the linpus one, that would be enough.

Oh, and those still freakin out about jaunty not working on the AAO the first time, there are only 3 more days till the official release and my issues were resolved HERE in the community.... give it time.

:popcorn:

For the people who are useless with a command line and not really used to creating or editing files in the guts of their system (me :) ) could you please post a quick step by step to doing this?

---

### Post by celticbhoy on 2009-04-21
I have just found another small problem with Jaunty, in Ibex I could use the Configure Display Settings option to rotate my screen to use it for viewing documents like a book. When I click on Configure Display Settings in my panel it says that rotation is not supported.

---

### Post by Shaga on 2009-04-21
Installed Jaunty Jackalope rc 3 days ago for my netbook(aa1/8gb ssd/512mb). Yesterday again.

Things that doesn't work as should out-of-box:
- I-mic: sound quality is unclear. It doesn't work for any purpose. No idea how to fix this.
- No wlan led, haven't tried fixing it.
- Killswitch doesn't give any message on screen, dont know if it works. Afraid on using it as it has really killed my network couple times so that pc required many reboots.
- Waking after sleep mode killed network. Required two reboots to accept my wlan wpa2 key. Haven't tried fixing this.

Everything else works and I love using it.

---

### Post by lzfy on 2009-04-21
So for I have the following problems with Jaunty (Kubuntu)

- No sound with most apps (only pure KDE apps give sound)
- Flash is choppy and has no sound
- Can't copy files over LAN

I'll wait for the final version before I try to fix the problems.

---

### Post by Xyphoid on 2009-04-21
I fixed the "copying large files over wifi in LAN" problem.
I mounted the shared XP folder in fstab with CIFS and used mount -a instead of **Places/Network**.
Now I get between 600KB/s and 1,6MB/s instead of 1Mb/s.

---

### Post by Davsdu on 2009-04-22
> **Shaga said:**
> Installed Jaunty Jackalope rc 3 days ago for my netbook(aa1/8gb ssd/512mb). Yesterday again.

Things that doesn't work as should out-of-box:
- I-mic: sound quality is unclear. It doesn't work for any purpose. No idea how to fix this.
- No wlan led, haven't tried fixing it.
- Killswitch doesn't give any message on screen, dont know if it works. Afraid on using it as it has really killed my network couple times so that pc required many reboots.
- Waking after sleep mode killed network. Required two reboots to accept my wlan wpa2 key. Haven't tried fixing this.
I had the same few issues. I upgraded to a newer kernel and wifi led's now working (during traffic). Killswitch doesn't work. Network after resume/suspend works. This on the AAO D150 model. YMMV.

---

### Post by mxboy15u on 2009-04-22
Ok I have the definitive fix for the card readers thanks so Alvaro on Identica. I will use the directions he gave me, which are good enough for any newb, and post a writeup here shortly.

---

