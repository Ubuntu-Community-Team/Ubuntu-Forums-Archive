---
title: "So has anybody successfully installed Ubuntu or Kubuntu on a Compaq F700 #f750us ?"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by uncreative on 2008-02-04
Just like the title says, and I knoew there are a few troubleshooting threads but there is NOTHING at the Kubuntu forums about a compaq f700, and at this point I don't even really care what I get on there as long as it isn't windows.  Ubuntu seems to have made headway, but has anyone got it 100% percent working on one yet?

Thanks

---

### Post by wtfacoconut on 2008-02-05
yo, I got this machine and it's given me a headache nut because I'm a noob that might be the reason why. but so far here's wat's up:

I got the WIFI card working but only after installing the Mad-wifi patch for the card.

This thing's got Nvidia graphics so I had to goto Nvidia's site to download and install hte drivers. (only problem now it that every time reboot I think that the kernel modules get erased so I have to go through the install process which wastes like 3 minutes).

Hybernate and sleep don't work. 

And here's the largest problem I have so far. The Sound is kinda weird. When I plug in ma headphones the speakers also keep playing and I see no entries in the volume control.

---

### Post by uncreative on 2008-02-06
Yeah the f750us seems to be a huge pain in the butt right now.  I have absolutely nothing working at the moment and I wouldn't exactly call myself a noob so don't feel bad.

I just wasted all morning on ndiswrapper...that thing aint working for me I have presumed.  Downloading mad wifi now...

Why is this such a pain in the butt?

---

### Post by uncreative on 2008-02-06
I seriously think I am up a creek on this one....there has to be a way to get something going here.  I installed madwifi now that damn thing doesn't even boot to the desktop.

I'd rather sit it here as a paper weight than use anything else

---

### Post by uncreative on 2008-02-07
This is just frikkin great now.  Ubuntu won't work completely, neither will Kubuntu, and HP cleverly didn't packages recovery discs with the system... Honest to god, did they really have to cut costs by a buck on each system to turn a  profit?

I got a new laptop with no OS.  Lovely.

Somebody throw me a bone and help me get wifi working. I went over the ndiswrapper tutorial three times yeterday morning...nothing.

 I should have got the dang ibook like I wanted....

Interjected for future searches on the topic: HP Compaq F750 US Presario f700 stinks as of 2-7-2008

---

### Post by bwtranch on 2008-02-07
They told me a anger management class to take a deep breath when I feel frustrated. But, that just pissed me off:) OK, just a little humor. Can you boot from anything? Live CD? Knoppix? Gentoo? Fedora? Mint? Sprint? (no sorry about the last one)

Best thing to do is get some kind of system up. Then deal with the issues. Beats having a heart attack. Better than a sharp stick in the eye...

---

### Post by uncreative on 2008-02-07
Hi thanks for the reply, I am less caffeinated right now.... I have Ubuntu Gusty installed, and the wired lan is working.

Just looking to get wireless going, and perhaps the nvidia drivers

Like I mentioned its a f750us

---

### Post by bwtranch on 2008-02-07
Sounds great! Glad you got it going. Now you can work out the bugs. Wireless is a pain. I try to help people on the forum with that. So many different variables with hardware and software, it can be a real challenge.

About the NVIDIA drivers, now some people have had success with Envy, I haven't. Actually, it screwed up my system, that's when I became a testing user for Hardy (I was a testing user for Gutsy, also) Guess what? All my problems with Nvidia went away! The thing works great. Now, I'm not saying jump on Hardy, because your mileage may vary, but that's what happened to me. I've always got my Gentoo system to fall back on anyway. Good Luck!

---

### Post by uncreative on 2008-02-08
Any suggestions on how to get the wireless to work?  This is my biggest pain...locating Hardy now.

Thanks!

---

### Post by uncreative on 2008-02-08
hey thanks for the tip on hardy, nvidia seems to be working painlessly...and man this thing looks slick eh?

ok man lets get wireless going!

---

### Post by wtfacoconut on 2008-02-10
yo here's how to get your WiFi card working. Just follow this guide to patch Mad-wifi.[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html]("http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html")

---

### Post by Bozebus on 2008-02-15
I have dual boot with the Vista that came installed and Feisty. I used Kubuntu live cd in safe mode to get to the partition manager and resize my drive. Then I booted Ubuntu in SAFE mode so I could get a desktop. Installed, and was up. However, I am locked in at 800x600 resolution, and no wireless. Tried to instal Gentoo, but is wouldn't see video, network card, or touchpad.

---

### Post by nutz on 2008-03-01
I got this laptop and at first it hung when booting to the live CD. Not sure why it did that but when I selected safe graphics mode it booted no problem. I installed it and everything worked right away...

Everything except the wireless NIC...

Has anyone got the wireless NIC working on this laptop? Other than that it runs Ubuntu 7.10 AMD64 flawlessly and I couldn't be more pleased with it's performance. Any help on getting the wireless NIC working would be highly appreciated!

---

### Post by Bozebus on 2008-03-06
I found these steps in the Linux Mint forums, [COLOR="Blue"](authored by Chi)[/COLOR]:
[B]
Try disabling Restricted Driver for the card if it appears there (admin->restricted drivers manager).

Blacklisting ath_pci from modprobe (add blacklist ath_pci to /etc/modprobe.d/blacklist)
Remove ath_pci module with rmmod ath_pci.

Then admin->Windows Wireless Drivers.
Install New Driver and browse to /usr/lib/linuxMint/mintWifi/drivers/Atheros_AR5007eg/net5211.inf

sudo modprobe ndiswrapper

To make changes permanent add ndiswrapper to /etc/modules

May have to wait a bit to for Mint to pick up the change (ensure wireless is on, maybe switch on and off).

Can always run python /usr/lib/linuxMint/mintWifi/mintWifi.py and see if w0 appears.[/B]

Yes, I did install the Mint Linux, which seems like a polished Ubuntu. Got the wireless working with WPA2, couldn't get WEP to work. Nvidia works fine, I'm running at 1280x800.

Note, however, that this a 32-bit version. I can use this in order to have the portability I desire with this laptop. At least until a stable 64-bit option arrives. Now I want to disable the touchpad, I use a trackball...

Hope this helps!

---

### Post by royconejo on 2008-03-19
Ok  I'm not using Ubuntu but since there is little to none information about F700 series I'd like to share my experience with this laptop and Debian Lenny:


**WiFi works perfectly** (Im not having problems so far) with:
madwifi patched version for Atheros 5007EG/2425, file name "madwifi-ng-r2756+ar5007" (search for it or look at madwifi.org, you'll have to compile the module yourself) 

ndiswrapper 1.52 (remember to backlist ath_pci!) with XP driver from [http://www.atheros.cz/download.php?atheros=AR5007EG&system=1](http://www.atheros.cz/download.php?atheros=AR5007EG&system=1). with version 6.0.3.85 you will even have the red wifi light turned into blue and alternating on net activity =) (I really **dont know** the cause of this behavior, on windows 2000/XP the same driver won't touch the leds ._.)


**Video also works flawlessly**, I'm using Compiz Fusion with TwinView, no problems whatsoever with the official driver from nvidia.com. Just search for GeForceM/Go, GeForce Go 7 Series, Linux 32 bits (as for the Xorg "nv" driver, well it seems that this video card is not recognized by now?).


**I dont have any problem with sound** (snd_hda_intel and conexant kernel driver).

Hibernate works, PowerNow works perfectly (CPU freqency scaling on demand etc) ACPI seems to work too (AC/Battery, button, etc). with lmsensors and hddtemp I can monitor the CPU/hdd temperature. I get 54 MB/sec with hdparm -t /dev/sda. 

Media Keys also works perfectly in Gnome: System->Preferences[Layouts] Keyboard Model: Laptop/notebook Compaq (eg. Presario) Internet Keyboard.

Everything worked just fine with kernel shipped from Lenny (Testing) that is, version 2.6.22.3. Later I downloaded and compiled a vanilla kernel from kernel.org, 2.6.24.3, carefully selected what drivers to compile and it worked too, but it really didnt make any difference at all.


**I DO have a couple of issues with:**

- when plugging headphones the speakers are also on (as some other user reported)

- Backlight control. This is driving me nuts. I can't dim the backlight, this is very unpleasant to the eye in a dark room and it also doesnt help to save battery power =(. I searched now for two weeks, but It seems there is simply no support for it YET.

- Suspend. seems to reach that mode but 2 seconds later it wakes up suddenly.


That's it, overall I'm very happy... the hardware is well supported although there are a couple of issues, specially the backlight control =(


I hope this helps somehow..


PS: if you like to test Debian, download **the same day build** of a netinst image of Lenny. On the official release there is an outdated version of forcedeth that basically **wont detect the wired ethernet card**! remember that with newer hardware very recent versions of software is what runs better (or runs at all).

---

### Post by nutz on 2008-03-19
Are you using 32 bit Debian?

Gutsy 64 bit ran well on this laptop for me also. Only two things didn't work, the wifi and headphone jack.

I know wifi can be made to work under 32 bit Gutsy. So therefore it should also also work under just about any other 32 bit Linux OS.

---

### Post by royconejo on 2008-03-19
> **nutz said:**
> Are you using 32 bit Debian?

Gutsy 64 bit ran well on this laptop for me also. Only two things didn't work, the wifi and headphone jack.

I know wifi can be made to work under 32 bit Gutsy. So therefore it should also also work under just about any other 32 bit Linux OS.

Yes 32 bits.. I don't know if ndiswrapper works with 64 bits drivers or if madwifi has 64 bit support either t.t

btw here is the link for the patched version of madwifi with instructions: [http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

Any of these two options, the patched version of madwifi or ndiswrapper, works perfect for me. I choosed ndiswrapper + XP driver 6.0.3.85 just for the misterious blue led "feature" =)

---

### Post by nutz on 2008-03-19
I tried the 32 bit driver under Gutsy 64 bit and it would work but only with security disabled. With security enabled I could see the network but not connect to it. I hope they have a fix for 64 bit soon because I really dislike Windows Vista. I had to switch back to vista because my laptop was close to useless to me if I had to always be plugged into a wired connection.

---

### Post by ameseisch on 2008-03-20
I recently purchased a Compaq F700. no luck getting the 64 bit live CD to load so far. 

I will try safe graphic mode.

I hope I don't have to resort to Vista to make this laptop useful. Why is linux so poor at handling 64 bit systems? aren't almost all new computers 64 bit?

would the newest 'unstable' releases of hardy be worth a try?

---

### Post by nutz on 2008-03-20
I had the same issue with the install. Just use the safe graphic mode and it will work flawlessly. Once it is installed it will detect the video card and install the drivers. This really is a good laptop and it runs Ubuntu AMD64 flawlessly with the exception of the wireless networking and the headphone jack not working.

This isn't a problem with 64 bit mode but rather the Nvidia driver the installer tries to load doesn't work with this video chipset. The updated one it installs after the OS is installed does work and it works very well.

---

### Post by AlanB66 on 2008-03-25
OK, so I'm not knew to using Linux/Unix, but installing from scratch is very new to me.

I've read this entire thread and wondered if someone can reply with a list of the exact steps needed to load Ubuntu 7.10 AMD64 onto a F750US (F700).

I've got the "boot in video safe mode" down and am currently re-running the Desktop Installer.

Once that's done, I plan to do a full update of all packages.

But, then what? Should my WiFi work? Should my Nvidia-driver-controlled display behave?

When I got as far as I could, I had no WiFi, I was locked at 800x600 and my internal NIC kept going back to DHCP.

Thanks in advance for anyone who replies with these steps requested. I have formatted this system's drive out-of-the-box as there's no way I'm using Vista Anything!

AlanB66

---

### Post by nutz on 2008-03-25
Run this line in the terminal...

sudo gedit /etc/X11/xorg.conf

Then replace the line that says '800x600' with '1280x800'

Then log out and and back in and you should have your res fixed.

I haven't gotten the wlan to work either. And I run the wired connection with DHCP.

---

### Post by AlanB66 on 2008-03-25
Excellent! One down. Resolution as desired. :)

I'm off to chat with HP to make sure I'm think we have the proper WiFi, as there are two driver downloads on HP's site for this system: Atheros and Broadcom.

Thank you "nutz"!

---

### Post by nutz on 2008-03-25
Make sure you do not tell them you have installed Linux on it or they will void your warranty. Your wlan card should be an Atheros 5007EG. To the best of my knowledge that is the only card this notebook ships with.

---

### Post by AlanB66 on 2008-03-25
I only asked them which driver I needed: Broadcom or Atheros. She assured me Atheros.

I then asked if HP would ever support Linux for this hardware and she said no.

When I contact them and they ask what OS I have, I respond, "It came with Vista", which it did. ;-)

---

### Post by nutz on 2008-03-25
> **AlanB66 said:**
> I only asked them which driver I needed: Broadcom or Atheros. She assured me Atheros.

I then asked if HP would ever support Linux for this hardware and she said no.

When I contact them and they ask what OS I have, I respond, "It came with Vista", which it did. ;-)

That was a very smart way to handle that. I did not handle my support call on this as intelligently. I actually slipped and told them I had installed Linux on it. Check my posts and you will get the whole story on that.

I actually called them to see if it was possible to swap this wlan card out for a different one that has better driver support under Linux. I now know it is not possible because they have engineered the bios to stop the computer from booting if any other card is present. I even verified this by swapping the card for several others and each time I was stopped by a bios message that indicated an unauthorized wireless device was detected and the notebook would go no further.

---

### Post by AlanB66 on 2008-03-25
Two things I forgot to mention/ask:

1. Which way does that switch on the front slide for the Wireless card to be "on"? Towards the orange light or away? Since I never booted a single time into Vista, I never had it enabled to know.

2. I am making an image of my drive now that I've gotten everything correct with Ubuntu 7.10 AMD64, sans the wireless and static IP for the wired LAN. Once I get a good image from which, at worst, I could more readily get back to this know, good point, I'm going to try to follow this page word for word:
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

If it works I will post my success here, as well as here:
[http://ubuntuforums.org/showthread.php?t=734638](http://ubuntuforums.org/showthread.php?t=734638)

---

### Post by nutz on 2008-03-25
Toward the light is on.

Good luck with the wlan. Let me know if you are successful.

By the way, Partimage is a good program for making your image.

---

### Post by AlanB66 on 2008-03-25
OK, I just did all of these steps and it still didn't work.
So, I'm off to format my drive and see if 8.04beta works out of the box, so to speak.

What a mess!


--- for reference only, as it did NOT work ---
1. sudo apt-get update && sudo aptitude install build-essential
   a. insert your Ubuntu 7.10 CD when prompted and hit <enter>

2. [http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)
   a. sudo apt-get install linux-restricted-modules-$(uname -r)
   b. disable ath_hal in /etc/default/linux-restricted-modules-common

3. Untar latest MadWifi bundle into a directory, go into that directory, type: make
   * If the make runs w/o errors, reboot INTO SINGLE USER MODE

4. Reboot the system and watch for the "Press ESC" message to interrupt GRUB ...
   a. Highlight the first Kernel line and press "e"
   b. Again, highlight the first Kernel line and press "e"
   c. Backspace over "quiet splash" and type "single" (no quotes), then hit <Enter>
   d. Press "b" to boot with the change you just made

5. (Shouldn't be necessary in Single User mode) First, set all your MadWifi devices down: 
   a. ifconfig ath0 down
   b. ifconfig wifi0 down
   #Repeat these 2 ifconfig lines for every MadWifi device you have

6. Assuming that you're inside the MadWifi directory, execute the following scripts to remove the current modules from your system and its memory: 
   a.  cd scripts
   b.  ./madwifi-unload.bash
   c.  ./find-madwifi-modules.sh $(uname -r)
       (press "r" to remove)
   d.  cd ..

7. Make and Make Install
   a.  make
   b.  make install
   c.  reboot (allow to boot into GRUB normally and log in)

8. Carry out these commands at a shell prompt:
   - sudo modprobe ath_pci
   
9. Any attempt with "ath0" in the command failed with "ioctl no such device found", or such.
--- reference end ---

---

### Post by nutz on 2008-03-25
I followed the same guide and got a similar result. I could see the AP but couldn't connect to it. So I tried disabling security and that would allow me to connect but the connection constantly dropped. Either way running wireless without security is unacceptable. So in other words that guide did not work.

---

### Post by AlanB66 on 2008-03-25
Nutz, et al.

Move to 8.04beta and beyond, if appropriate.

I just used an XP disc to delete all partitions on my hard drive and then rebooted before installing XP to install Ubuntu 8.04 beta.

Note: I pressed F4 to startup Ubuntu in Safe Video mode.

After it started up clean, I used the "Install" desktop icon.

After full initial installation and reboot, the wireless card is seen in the list of hardware devices (next to the graphics accelerator that is initially disabled).

I'm doing updates now, but it's looking much, much better.

Read the upgrade instructions if you cannot format your drive and, thus, lose data. But, I just started this endeavor a day or two ago and I've nothing to lose in that regard.

:guitar:

---

### Post by AlanB66 on 2008-03-25
**NOTE**: It's not 100% out of the box. I'm still hacking at it.

The wireless drivers are seen in the drivers GUI, but I cannot see/get ath0 into the network devices file.

More later.

---

### Post by nutz on 2008-03-25
That is the same issue 7.10 had. It needs a HAL update from Atheros.

---

### Post by AlanB66 on 2008-03-25
I didn't see this wireless LAN driver in 7.10, but did in 8.04 beta. Something was different.

I just found this link - still reading - thought you might be interested:
[http://ubuntuforums.org/archive/index.php/t-662877.html](http://ubuntuforums.org/archive/index.php/t-662877.html)

---

### Post by AlanB66 on 2008-03-25
:mad:
I am giving up very soon.
I just tried that whole mess with 8.04beta to no avail.
Somebody is missing a step in the things they state they've done.

I am downloading and will attempt 8.04beta for x86.
I'm finding snippets everywhere that the 64-bit OS is a problem for MadWifi and our Atheros card.

I will let you know, tomorrow, if that works.

If it doesn't, I'm going to load XP Pro SP2 and be done with this mess.

:mad:

---

### Post by nutz on 2008-03-25
> **AlanB66 said:**
> :mad:
I am giving up very soon.
I just tried that whole mess with 8.04beta to no avail.
Somebody is missing a step in the things they state they've done.

I am downloading and will attempt 8.04beta for x86.
I'm finding snippets everywhere that the 64-bit OS is a problem for MadWifi and our Atheros card.

I will let you know, tomorrow, if that works.

If it doesn't, I'm going to load XP Pro SP2 and be done with this mess.

:mad:

I can save you some trouble and let you know that to the best of my knowledge nobody has gotten it to actually work as designed with the 64bit OS. Many have said they got it to work with the 32bit version but I have followed their guides many times and at this time mine still does not work. I have spent the last month on this and at this time even though I can connect with security disabled it only stays connected for a few minutes at best. And I have verified it is not a signal or AP issue by testing it under Vista. Even though I dislike Vista very much and I truly miss all my Linux apps until this card has better driver support under Linux I am going to continue to run Vista. I still have Linux on my file server/media PC but I spend more time on my laptop because it can go on the road with me.

Under Vista this wlan card works extremely well, even better than the Broadcom card that is in my Dell. In fact it gets a better connection than any wlan card I have ever had in a notebook and since it is a single chip design it runs cooler and uses less power. It really is a good card so I hope the reputation for it in the Linux community isn't hurt by this little driver issue.

---

### Post by nutz on 2008-03-25
Double post.

---

### Post by AlanB66 on 2008-03-26
Got It!!!! :)

Install 8.04 Beta x86 (NOT AMD64!)
Login and Update everything.
**Reboot**

Login and load up:
  sudo apt-get update && sudo aptitude install build-essential
  sudo apt-get install subversion

Open /etc/default/linux-restricted-modules-common:
  Put ath_hal and ath_pci in the double quotes of DISABLE_MODULES

Disable, via Driver Manager, HAL and Wireless Driver.

**Reboot**

cd /tmp
sudo svn checkout [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk) madwifi-ng
cd madwifi*
sudo make all
sudo make install
sudo modprobe -v ath_pci

Take ath_pci out of DISABLE_MODULES in linux-restricted-modules-common.

sudo vi /etc/network/interfaces (add these lines)
[I]iface wifi0 inet dhcp
wireless-key XXXXXX
wireless-keymode open
wireless-essid <name of network>
auto wifi0 [/I]

**Reboot**

sudo modprobe -v ath_pci

ifconfig Should reveal your wireless wifi0 entry, finally.

Now, use the Network Manager to connect to your wireless network.
You have to enter all of this info all over again, so I may go back and remove the key, keymode and essid from that file and see if things stick.

Let me know, yo!:guitar:

---

### Post by AlanB66 on 2008-03-26
Seems I'm going to have to create an /etc/init.d/eth0 to run "modprobe -v ath_pci", as I had to re-run this manually after reboot to reconnect to my wireless.  FYI.

---

### Post by royconejo on 2008-03-26
> **AlanB66 said:**
> 
I am downloading and will attempt 8.04beta for x86.
I'm finding snippets everywhere that the 64-bit OS is a problem for MadWifi and our Atheros card.

To my knowledge AMD64 runs perfect on dual core systems with official nvidia drivers.. I've installed some in the past.. but here the problem is a specific ndiswrapper or MadWifi driver problem with AMD64, it is not an AMD64 linux problem in itself.

As said before you wont get any perceptible performance gain with AMD64. but you'll run in much less problems for everything from ndiswrapper drivers to firefox or Totem video plugins imported from XP.

I think everybody should install x86 versions first unless they know the implications of installing AMD64. Then if you really need a system running on AMD64 and you can live without those XP 32 bits drivers.. well you can install AMD64 then =)

---

### Post by AlanB66 on 2008-03-26
**NOTE: I have noticed that if my wired NIC is attached, my wireless NIC fails to get an IP address.**

Once you've done all of the above, try to see if your wireless behaves after unplugging the wired NIC and rebooting.

You may have to run the modprobe command at the intial login, thereafter.

---

### Post by nutz on 2008-03-26
I had one other issue with this laptop. Every time it booted up the wired NIC would get a new device name. It started at eth0 and every boot would climb one number higher until finally I was at eth47...

Can you confirm whether or not that is happening to you?

---

### Post by AlanB66 on 2008-03-26
Ah Ha! I wondered why my router kept seeing the system as a new system and, thus, gave it an incremented IP address! :confused:

I know that stopped happening in 8.04beta. Are you up to 8.04b?

---

### Post by nutz on 2008-03-26
Nah, I am on 7.10 AMD64.

I plan to wait for the official release before I switch to 8.04.

---

### Post by AlanB66 on 2008-04-04
For anyone reading this thread, here's another FYI.


I tried to use my wife's Presario V6000US mini-pci-express card in my
F750US laptop. When I went to reboot, I got a message:
[INDENT]*104-Unsupported wireless network device detected. System halted. Remove device and re-start.*[/INDENT]
So, using an alternate mini-pci-express wireless card is **not **an option, unfortunately.

---

### Post by AlanB66 on 2008-04-04
One last thing ...

I just re-installed, from scratch, Ubuntu 8.04-beta with a
Linksys WUSB54GC plugged in during the install.

I am able, out of the gate, to use this wireless USB connection
and it finds my network in non-broadcast mode, as well.

:guitar:

---

### Post by nutz on 2008-04-04
> **AlanB66 said:**
> One last thing ...

I just re-installed, from scratch, Ubuntu 8.04-beta with a
Linksys WUSB54GC plugged in during the install.

I am able, out of the gate, to use this wireless USB connection
and it finds my network in non-broadcast mode, as well.

:guitar:


Is that AMD64 or i386?

---

### Post by AlanB66 on 2008-04-04
I used 8.04-beta i386.

---

### Post by nutz on 2008-04-04
I wonder if you would have the same result with AMD64. In regards to the USB dongle...

---

### Post by mdramige on 2008-04-04
> **nutz said:**
> I can save you some trouble and let you know that to the best of my knowledge nobody has gotten it to actually work as designed with the 64bit OS.

Ndiswrapper and the XP 64-bit 5007eg driver (net5211) work great in Hardy amd64.

---

### Post by nutz on 2008-04-04
And where did you get this 64 bit driver?

---

### Post by AlanB66 on 2008-04-04
A friend of mine just sent me this link:
[http://www.rechner.org/b1800_bios.html](http://www.rechner.org/b1800_bios.html)

It's an instructional on how to fix our BIOS so that we CAN boot with a different mini-pci-express card.

However, I'm not up for this task right now.

---

### Post by nutz on 2008-04-04
> **AlanB66 said:**
> A friend of mine just sent me this link:
[http://www.rechner.org/b1800_bios.html](http://www.rechner.org/b1800_bios.html)

It's an instructional on how to fix our BIOS so that we CAN boot with a different mini-pci-express card.

However, I'm not up for this task right now.


Give it a try and let me know how it works. I have an extra card or two here that I would love to use.

---

### Post by AlanB66 on 2008-04-04
Not me. I'm done testing for awhile.

I just ran thru that test with the Linksys - rebuilding the system from scratch - only to hit a partition size issue with trying to restore my older installation with madWifi and the internal Atheros card.

I'm toast and am not up to this endeavor. Maybe someone else will run with this and make it happen ;-)

---

### Post by nutz on 2008-04-04
> **AlanB66 said:**
> Not me. I'm done testing for awhile.

I just ran thru that test with the Linksys - rebuilding the system from scratch - only to hit a partition size issue with trying to restore my older installation with madWifi and the internal Atheros card.

I'm toast and am not up to this endeavor. Maybe someone else will run with this and make it happen ;-)


Perhaps I will give it a try when I get home. I would love to have my wireless back...

---

### Post by SilkBC on 2008-04-05
OK, I just purchased one of these units, and following the various posts in this thread, I have the ADM64 version of the latest Hardy Beta installed and almost everything working (yes, even the wireless, using ndiswrapper)

The only thing not working is the webcam.  Has anyone got this to work?  A look through dmesg shows the following:

```

uvcvideo: Found UVC 1.00 device Webcam-101 (064e:a102)
input: Webcam-101 as /devices/pci0000:00/0000:00:04.1/usb4/4-2/4-2:1.0/input/input10
usbcore: registered new interface driver uvcvideo
USB Video Class driver (SVN r198)

```

The driver loaded is compiled from the latest SVN source.  Attempting to use the 'luvcview' program for testing results in the following:

```

luvcview version 0.2.1
 size width: 640 height: 480
Video driver: x11
A window manager is available
video /dev/video0
Unable to set format: 22.
 Init v4L2 failed !! exit fatal

```

A look on the linux-uvc site at compatible devices doesn't actually show this one specifically (064e:a102), though it has ones that is *very* close: 064e:a101 (it belongs to an Acer, apparently, though)

Anyway, I was hoping maybe the SVN was ahead of the site docs,  but I guess not.  I was kinda hoping someone had been able to get this working?

Other than that though, quite pleased overall, as everything else is working fine! :-)

TIA for your help :-)

-SilkBC

---

### Post by nutz on 2008-04-05
I didn't know the F750us came with a webcam. What driver did you use with Ndiswrapper?

---

### Post by AlanB66 on 2008-04-07
SilkBC,

Could you please post the steps you followed to load the drivers for the WiFi using ndiswrapper, please?

Did you uninstall anything? What did you load? Any and all commands in the order necessary would be greatly appreciated!

Oh, and to add to Nutz's post, did you get the AR5007 for XP off of mediafire.com? If not there, where, please?

Thanks!

---

### Post by AlanB66 on 2008-04-08
Cross Post:

[[COLOR="Blue"]_How To: Ubuntu 8.04-beta i386 on Compaq F750US_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=4678580#post4678580")

---

### Post by tewest99 on 2008-05-01
> **uncreative said:**
> Yeah the f750us seems to be a huge pain in the butt right now.  I have absolutely nothing working at the moment and I wouldn't exactly call myself a noob so don't feel bad.

I just wasted all morning on ndiswrapper...that thing aint working for me I have presumed.  Downloading mad wifi now...

Why is this such a pain in the butt?

NVidia graphics will work if you install the peoper nvidia and glx packages from synaptic. Wireless is anotherstory ...

---

### Post by AlanB66 on 2008-05-01
It works just fine if you follow the instructions I posted to: [http://ubuntuforums.org/showthread.php?p=4678580#post4678580](http://ubuntuforums.org/showthread.php?p=4678580#post4678580)

---

### Post by SilkBC on 2008-06-25
> **AlanB66 said:**
> SilkBC,

Could you please post the steps you followed to load the drivers for the WiFi using ndiswrapper, please?

Did you uninstall anything? What did you load? Any and all commands in the order necessary would be greatly appreciated!

Oh, and to add to Nutz's post, did you get the AR5007 for XP off of mediafire.com? If not there, where, please?

Thanks!

Actually, it doesn't quite work so well.  It connected all fine the first time or two but now, while it does see all APs in the area, it won't connect to any of them.  I am actually contemplating installing the i386 version of Hardy and following the MadWiFi instructions.

-SilkBC

---

