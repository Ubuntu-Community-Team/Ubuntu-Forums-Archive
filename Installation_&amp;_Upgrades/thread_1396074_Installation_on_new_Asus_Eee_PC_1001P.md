---
title: "Installation on new Asus Eee PC 1001P"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by CaptSaltyJack on 2010-02-01
Anyone know if Ubuntu 9.10 or Ubuntu Netbook Remix 9.10 will install and work properly on the new Asus Eee PC 1001P? Mine arrives tomorrow. I searched the forum and was surprised no one else is talking about this hot new netbook. I figured I'd start the thread myself. :)

Please post your experiences (and any fixes) here. I'll try installing both Ubuntu and UNR as soon as I can and see how it works out.

---

### Post by DarkCanis on 2010-02-02
Installed UNR earlier today, had to use the ndiswrapper and the xp drivers from the Asus site in order to get wireless to work, other than that everything else is working fine.  

The only caveat is that I am only to connect to wireless at work which has no encryption, at home using my router that has dd-wrt I cannot get it to connect.  I didn't have the time to troubleshoot that today:

When I do an lspci this is the output that I get for the wireless

02:00.0 Network controller: Atheros Communications Inc. Device 002c (rev 01)

---

### Post by CaptSaltyJack on 2010-02-02
Cool, good to hear it works!

> **DarkCanis said:**
> Installed UNR earlier today, had to use the ndiswrapper and the xp drivers from the Asus site in order to get wireless to work, other than that everything else is working fine.


So I can install UNR on the 1001P and just do "sudo apt-get install ndiswrapper-common"? or ndiswrapper-utils-1.9? And then it just works? And what do you mean you used XP drivers? How do Windows drivers work on Linux?

> **DarkCanis said:**
> The only caveat is that I am only to connect to wireless at work which has no encryption, at home using my router that has dd-wrt I cannot get it to connect.

So if my router uses WPA2 encryption, I'm screwed? Hmm. I'm sure fixes will surface soon, hopefully...

I'll try my hand at this tomorrow or later this week, and report back in full.

---

### Post by DarkCanis on 2010-02-02
I ran 

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
```I still haven't ruled out that it can't just be some incompatibility between this and ddwrt. 

The windows xp driver that I used with the ndiswrapper is available from the ASUS support site.

Wireless Lan Driver for Win XP (Wlan: NE785H_GE112H)                                                                                 

I haven't tried the madwifi as I was working on this late.   

Using modprobe ath5k or ath9k did nothing.

Took some hints from the link below and other forum posts.  Not much on the 1001P of course but that comes with the territory.

[https://help.ubuntu.com/community/EeePC/Fixes](https://help.ubuntu.com/community/EeePC/Fixes)

---

### Post by DarkCanis on 2010-02-02
I checked my history, this link might actually work for the wireless since the wireless cards appear to be similar:

[http://ubuntuforums.org/showthread.php?t=1390856&highlight=asus+eee](http://ubuntuforums.org/showthread.php?t=1390856&highlight=asus+eee)


output from sudo lspci -vnn

02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:002c] (rev 01)
        Subsystem: Device [1a3b:1112]
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fbff0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Virtual Channel <?>
        Capabilities: [160] Device Serial Number 12-14-24-ff-ff-17-15-00
        Capabilities: [170] Power Budgeting <?>
        Kernel driver in use: ndiswrapper

---

### Post by HomoGleek on 2010-02-02
Good place to look for compatibility is here: [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

---

### Post by DarkCanis on 2010-02-02
I was seeing this in the logs:

ndiswrapper (iw_set_auth:1602): invalid cmd 12 			 		

Which lead me to this:

[http://ubuntuforums.org/showthread.php?p=8426311](http://ubuntuforums.org/showthread.php?p=8426311)

---

### Post by CaptSaltyJack on 2010-02-03
Great news, got wireless working perfectly, even with WPA/WPA2 encryption!

Here's how.

1) Using apt-get, istall the ndiswrapper-common, ndiswrapper-utils-1.9, and ndisgtk packages.
2) Using apt-get, install linux-backports-modules-wireless-karmic-generic.
3) Go to [http://support.asus.com/download/download.aspx](http://support.asus.com/download/download.aspx) and get the WinXP wireless LAN drivers for the 1001P (NE785H_GE112H). Unzip that file to a folder.
4) Run ndisgtk (probably as root to be safe) and install that WinXP driver (select the .inf file). There will be an error, but ignore it, it's fine.

After those steps (possibly after a reboot), I now have wireless and can connect to my Linksys running Tomato firmware & WPA2 encryption.

Now, if I could only get the built-in microphone working, and the multi-touch capability in the touchpad! Oh, and the brightness controls are completely whacked, too, they don't work properly and Ubuntu doesn't memorize the way you have your brightness set.

---

### Post by DarkCanis on 2010-02-03
After losing sleep messing around with this thing since Monday.  At that  point I took my happy behind to ndevil, where they had a nice disassemble presentation video for the Asus 1001P and used the Asus 1201N step by  step video (it was similar) to ripe out the cancer from my netbook. I put  in another atheros card from my  laptop and poof everything worked fine, though this was just temporary  the card was too big for the netbook as it needs a half minpci-e.  The  linux-backports worked with the atheros from the main laptop.

I know it isn't much help, but hey at least it's an option, of course there goes the warranty. That means no dropping it :twisted:

---

### Post by CaptSaltyJack on 2010-02-03
> **DarkCanis said:**
> After losing sleep messing around with this thing since Monday.  At that  point I took my happy behind to ndevil, where they had a nice disassemble presentation video for the Asus 1001P and used the Asus 1201N step by  step video (it was similar) to ripe out the cancer from my netbook. I put  in another atheros card from my  laptop and poof everything worked fine, though this was just temporary  the card was too big for the netbook as it needs a half minpci-e.  The  linux-backports worked with the atheros from the main laptop.

I know it isn't much help, but hey at least it's an option, of course there goes the warranty. That means no dropping it :twisted:

What the heck?? That seems kind of extreme. What kind of WLAN card did you have in your 1001P before?? Mine came with an Atheros so I suppose that's why my fixes were easy, and required no hardware modifications.

---

### Post by DarkCanis on 2010-02-03
Azurewave AR5B95 it's a half minipci-e card.   This is an Atheros card as well. It should be the exact same card if I'm not mistaken.

I actually followed those same steps and got it working briefly.  I'm certain this is probably it's related to the DD-WRT firmware I'm running  which is one of the newer betas but I was able to connect once and then after the reboots it wouldn't work. 

I planned on replacing this with a wireless N card(Dual Band), but I was going to do so after possibly a HDD upgrade later on.  I'm glad you got it working though, I wonder if there's anyway to donate this card so that a proper driver can be written for it.

---

### Post by CaptSaltyJack on 2010-02-03
> **DarkCanis said:**
> Azurewave AR5B95 it's a half minipci-e card.   This is an Atheros card as well. It should be the exact same card if I'm not mistaken.

I guess what I don't understand is, if we both have the same netbook, why did my steps work out for me, but not for you? Unless, like you say, it's your DD-WRT firmware... though that seems strange, I'd figure any router firmware would work fine.

Check out Tomato, it blows DD-WRT away in my opinion. Get it from [www.polarcloud.com](www.polarcloud.com).

---

### Post by DarkCanis on 2010-02-03
I think that firmware isn't compatible with the WRT310N.  OpenWRT might work better, but either way the new card should be here sometime next week.  I'll be experimenting with a bluetooth usb dongle next so we'll see how that goes!

---

### Post by CaptSaltyJack on 2010-02-03
Good luck! I will continue to post updates to this thread as I get other components working 100% (microphone, multi-touch, brightness controls). I also plan on updating the official Wiki to add the 1001P.

---

### Post by Bothi on 2010-02-03
Hi. First of all im quite new to linux so please if you have an idea for the solution to my problempost it. however basic it migth seem.
 
i have a new 1001p and using xubuntu 9.10 (not the netbook edition). and i just cant get the wireless network working.
 
this is from "lspci -vnn"
> 02:00.0 Network controller [0280]_ Atheros Communications Inc. Device [168c:002c] (rev 01)
Subsystem: Device [1a3b:1112]
Flags: bus master, fast devsel, latency 0, IRQ 10
Memory at fbff0000 (64-bit, non-prefetchable) [size=64k]
Capabilities: [40] Power Management version 3
Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
Capabilities: [60] Express Legacy Endpoint, MSI 00
Capabilities: [100] Advanced Error Reporting <?>
Capabilities: [140] Virtual Channel <?>
Capabilities: [160] Device Serial Number 12-14-24-ff-ff-17-15-00
Capabilities: [170] Power Budgeting <?>

 
i tried everything written in the post. quess im missing the line "driver in use: ndiswrapper". i installed the xp drivers with ndiswrapper, but i just cant get it working. in "ifconfig" the wireless controller doesn't show up.
i configured an wireless connection through the NetworkManager. But i cannot activate it (only the wired connections).
 
if you have ANY ideas, pls post. ty

---

### Post by CaptSaltyJack on 2010-02-03
Bothi - did you follow my steps above exactly? Also, have to ask the obvious: have you tried hitting Fn-F2 to turn the wireless device on?

---

### Post by Bothi on 2010-02-03
yep and yep! i also tried windows, the wireless controller works perfectly there...

---

### Post by DarkCanis on 2010-02-04
You'll want to make sure you're selecting the right driver:

\Wlan_NE785H_GE112H-V7_7_0_377_XP\ndis5x

Not the ndis5x64 directory

When doing this you can also check the Log Viewer, you should be seeing something under messages that will give you a clue what's going on.

---

### Post by Bothi on 2010-02-04
Swapped to UNR. Worked perfectly on the first try. Used your guid CptSaltyJack (weird name btw :D )Guess it was an xubuntu issue, despite the fact, that it shouldnt be.
Any progress on gettin the multitouch pad working?

---

### Post by Linux BASHer on 2010-02-04
> **CaptSaltyJack said:**
> Great news, got wireless working perfectly, even with WPA/WPA2 encryption

Here's how...

Thank you very much, CaptSaltyJack. I just got a 1001P as well and I had a hard enough time just making a bootable flash drive. After that, I thought wireless was going to be a struggle. I still have to test it out a bit more, but right now its working perfectly with my school's wi-fi. Running Xubuntu 9.10.

> **CaptSaltyJack said:**
> Now, if I could only get the built-in microphone working, and the multi-touch capability in the touchpad! Oh, and the brightness controls are completely whacked, too, they don't work properly and Ubuntu doesn't memorize the way you have your brightness set.

Agreed. Would be really nice to have all that working. But those are unfortunate annoyances, whereas wireless is absolutely essential on a netbook!

Thanks again!

---

### Post by sneakernet on 2010-02-04
I've got two finger scrolling to work with a script from this [site]("http://blog.twinapex.fi/2009/10/11/setting-up-multi-touch-scrolling-for-ubuntu-9-10-karmic-koala-linux-on-asus-eee-1005ha-netbook/").

---

### Post by CaptSaltyJack on 2010-02-05
> **sneakernet said:**
> I've got two finger scrolling to work with a script from this [site]("http://blog.twinapex.fi/2009/10/11/setting-up-multi-touch-scrolling-for-ubuntu-9-10-karmic-koala-linux-on-asus-eee-1005ha-netbook/").

This worked for me too! It's a little hosed though, the two-finger scrolling. If you do it too slowly, it doesn't seem to register. Also, that link gets you the right-click ability by tapping with two fingers. Nice!

Microphone still isn't working but I don't really care about that too much. My next task is trying to set up CPU scaling so that my minimum CPU freq is around 633MHz or so instead of 1GHz. I get much better battery life out of the 1001P in Windows 7 because of the CPU scaling. Need to get that battery performance in Ubuntu now!

Lastly, getting the screen brightness working would be nice. Currently, if you hit the brightness up/down, it doesn't increase/decrease as you'd expect, it's kind of all over the map.

---

### Post by exquest on 2010-02-06
I'm having issues with a couple things on my new ASUS 1001p after fixing the wireless with the tips from above:

First:  When I try to dim the screen with the dim screen / brighten screen buttons I don't get a smooth dimming of brightening but it seems to randomly jump from bright to dark.  When I go through the power management to dim the screen and move the slider the brightness of the screen has nothing to do with the position of the slider.  When it is a 100% is it 100% bright, but at 97% it is pretty dark, and 60% it is bright again.  I'm not sure what the issue is with this but I would like to darken the screen because it does affect the battery life a lot.

Second:  I've set the computer to go to suspend when I close the screen but when I open it up it doesn't ask me for a password.  I've tried messing around with the settings in the gconf-editor but nothing I do seems to have any affect.

I put 2GB of ram in this and a Solid State Drive and it works great.  I just wish I could do something about the screen dimming thing....

Any tips?

---

### Post by exquest on 2010-02-06
Which script did you use?  There are a bunch of options on that page.

---

### Post by sneakernet on 2010-02-06
I think we will have to wait for an update to fix the display brightness issues. This is the script for two finger scroll:

```
#!/bin/sh
#
# Use xinput --list-props "SynPS/2 Synaptics TouchPad" to extract data
#

# Set multi-touch emulation parameters
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1

# Disable edge scrolling
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 8 0 0 0 

# This will make cursor not to jump if you have two fingers on the touchpad and you list one
# (which you usually do after two-finger scrolling)
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 32 110
```

---

### Post by exquest on 2010-02-07
I'm running into a new bug / issue.  When I try and add something to my "Startup Application" (the two finger scroll script - which works great by the way) I have to add it 3 times before it takes...

I added it the first time and logged out and when I logged back in it had disappeared from the startup applications.  I added it a second time, closed the dialogue and then checked again just to make sure I hadn't hit cancel or something like that and logged out and when I logged back in it wasn't there.  I did it a third time just for fun, and it stayed in the startup menu and worked!

I'm not sure what to make of this but I realized this happened when I was installing Yakuake (a great drop down console) and had to go through the three times in order to get it to stick in the Startup Applications.

Anyone else having similar issues?

---

### Post by Pablo_R on 2010-02-18
Thank you for the detailed explanation (CaptSaltyJack)
I also have an EEE 1001p and the wlan module is working now.
:D

Pablo

---

### Post by noiv on 2010-02-18
[http://ubuntuforums.org/showthread.php?t=1398596](http://ubuntuforums.org/showthread.php?t=1398596)

acpi_osi=Linux makes the hotkeys for brightness control predictable.

---

### Post by exquest on 2010-02-18
> **noiv said:**
> [http://ubuntuforums.org/showthread.php?t=1398596](http://ubuntuforums.org/showthread.php?t=1398596)

acpi_osi=Linux makes the hotkeys for brightness control predictable.


How does this work with GRUB2.  I'm trying to figure this out but GRUB2 seems a lot more complicated than GRUB...

Anyone know of a simple GRUB2 tutorial?

---

### Post by noiv on 2010-02-18
On Karmic press Alt-F2 and enter: gksudo gedit /etc/default/grub
then change the line with GRUB_CMDLINE_LINUX_DEFAULT to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
save the file and run in terminal: sudo update-grub

boot and enjoy!

Does not improve the Power Manager Brightness Applet :(

btw: it seems to me the 1001P and the 1005PE share identical hardware.

---

### Post by dooby91 on 2010-02-21
Just wanted to share with community how i got some things working since this was the first thing google came up with on my search.

Mic (worked out of the box except for skype)
Need to 
sudo apt-get install linux-backports-modules-alsa-karmic-generic
sudo apt-get install pavucontrol
then goto sound and video > pulse audio control
click to shield looking thingy to unlock channels and bring one side down to zero and one all the way up.  (may want to experiment a little to figure out what works best for u)
also check alsamixer to make sure internal mic is selected and input is turned up (press tab after you run alsamixer from terminal)

Native linux drivers for Wireless:
get bleeding from:
[http://linuxwireless.org/en/users/Download#Where_to_download_bleeding_edge](http://linuxwireless.org/en/users/Download#Where_to_download_bleeding_edge)
may need to install patchs:
[http://permalink.gmane.org/gmane.linux.network/151565](http://permalink.gmane.org/gmane.linux.network/151565)
[http://bugzilla.kernel.org/show_bug.cgi?id=15180](http://bugzilla.kernel.org/show_bug.cgi?id=15180) 
(seems that this patch is only partialy applied right now on the bleeding drivers you may need to go in and manualy apply the patches yourself/I just did it on my gf's and 1 of the 4 patches was not applied so i found what line needed to be edited and added it myself/now its working)
to compile drivers
then 
modprobe ath9k
then you need to add that to automate at startup


still need to get backlit working 
please anyone with any knowledge help would be much obliged

---

### Post by sneakernet on 2010-02-24
Thanks, that worked great! I also had to uncheck the box for letting Skype automatically adjust levels before I could actually hear myself on the test call.

---

### Post by ironring1 on 2010-03-04
I've installed karmic (not unr) on my 1001p-mu17-bk, and I'm pretty happy with it.  CaptSaltyJack's instructions for ndiswrapper worked great, thanks!  Adding acpi_osi=Linux to GRUB_CMDLINE_DEFAULT= line in /etc/default/grub followed by grub update gave me usable brightness controls, too.  My webcam worked oob, but I still can't get the internal mic to work.  However, an external mic works great, so I am able to use Skype, but I would like to get the internal mic running.  Any suggestions?  I've tried futzing around with pavucontrol, and no dice.

If I can just get the built in mic and cpu scaling (haven't worked on the latter, yet...), I'll be on cloud 9!  I'm keeping detailed notes of EVERYTHING that I try and modify as I work on this, so I will be able to post exactly what worked, once it works.

BTW, lspci -nn gives (for the sound card):
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)

---

### Post by ironring1 on 2010-03-04
Quick update on the internal mic problem:
I tried explicitly setting the model of the sound card in /etc/modprobe.d/alsa-base.conf by adding the line "options snd-hda-intel model=xyz" to several models: 6stack-dig, 3stack, ref, laptop.  None of these made any difference. 

I guess that I will use a cheapo lapel mic for now :(

---

### Post by ironring1 on 2010-03-04
K.  One more update and then I'm done for the day (promise!).  I installed linux-backports-modules-alsa-karmic-generic, and my microphone is working, sort of...  It works in sound recorder, but not in skype.  However, when I do the skype test call, the "applications" pane of the "sound preferences" app under System->preferences->sound shows that skype is using two channels of the sound card.  One, I assume is the output speakers, the other is what it must think is the mic. 

I suspect that skype is trying to use the external mic jack (since an external mic works with skype) instead of the internal mic.  Any suggestions on how to explicitly tell skype to use the internal mic (command line option, maybe?)?

---

### Post by sneakernet on 2010-03-04
Did you unlock the channels in pavucontrol and set one to zero?

---

### Post by ironring1 on 2010-03-04
Shazaam!  Thanks, sneakernet, that did it.  for the record, I dropped the left channel to zero.  Skype is happy, sound recorder is happy...  Ironring1 is happy!

Here is my full install:
0) Began with ASUS 1001P-MU17-BK with Win 7 installed.

1) changed BIOS settings:  hit F2 during startup, disabled boot->boot_booster and boot->boot_settings->quiet_boot.  F10 to save and exit, booted into windows 7

2) Used usb-creator under windows to make bootable USB stick of Ubuntu 9.10 (NOT UNR)

3) defragged C drive, deleted D: drive, shrunk C drive to 40GB (smallest that it would allow.  I left the recovery partitions in place.  This left me with ~80GB for ubuntu.  Rebooted INTO WINDOWS to let it adjust to shrunken partition (twice, to be safe!).

4) Inserted USB drive, Rebooted netbook, hit esc at bios, selected USB drive and booted ubuntu.  Selected install Ubuntu.

5) Answered generic questions, chose to install Ubuntu to largest available free space.
     -installation proceeded without a hitch.

6) Rebooted into ubunto, opened terminal, $> sudo apt-get update 
     -update repo lists.

7) wireless: sudo apt-get install linux-backports-modules-karmic-generic linux-backports-modules-wireless-karmic-generic
     Tried to get wireless working with ath9k by commenting out "blacklist ath_pci" in /etc/modprobe.d/blacklist-ath_pci.conf and adding ath9k to /etc/modules 
          -did not work.
          Installed linux-backports-modules-karmic just to be sure, still no go; restored blacklist-ath_pci.conf and /etc/modules.
     ndiswrapper:  followed CaptSaltyJack's instructions earlier in this thread (all of the ndiswrapper packages already were installed with 9.10) using winXP driver from ASUS.  SUCCESS, I am now able to log in to unsecured and WEP wifi networks (have not tested WPA/WPA2).  connection seems robust, has yet to drop.

8) brightness control: changed /etc/default/grub line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux", sudo update grup, rebooted and brightness controls work (seems as though sound is louder, too)

9) sound/microphone.  
     sudo apt-get install linux-backports-modules-alsa-karmic-generic
          -Sound recorder now works, but now skype using built in mic.
     sudo apt-get install pavucontrol, unlocked stereo channels on input, dropped right channel to 0%, now I can see the mic response in pavucontrol, confidence is high!
          -Skype now works!  

10) CPU frequency scaling: looked at the available cpu frequencies, 
     cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
          1GHz, 1.33GHz and 1.67GHz are available.
     I am able to change freq via cpufreq_selector -f FREQ, but background utilities seem to reset it in a short time back to 1.67GHz.  I will leave this for another time :)

---

### Post by guwrt on 2010-03-04
Hello,

I just bought a new 1001p in Vancouver few weeks ago during the Olympics when I was in Vancouver. 

The last post of ironring1 is really hot for the community and that's the thing I was looking for before making the step in Ubuntu.

I am running Ubuntu on all my others machines but for my netbook, it will be the first time.

One question. Is it better to install UNR or Karmic?

Thanks and keep on this thread

Andre

---

### Post by ironring1 on 2010-03-05
Hi, Andre; I'm glad that my post was helpful.  I don't know how much of it I actually figured out, I think that I just collected other people's work in one place ;)  I'm in Vancouver, too, btw.  I couldn't turn down $320 (~$310 US) for a 1001p from NCIX, and I am glad that I seem to have gotten most of it up and running in a day.

Regarding karmic or UNR, well, I had some friends that went with UNR, and they weren't terribly impressed.  From what I understand, it's more the graphical front end that differs between the two.  That being said, I don't have any experience with UNR myself.

Just to keep this thread moving, what I am working on now is external displays.  I travel and give conference presentations (I'm an academic researcher), and I intend to use the 1001P for my talks.  

I can get external displays working, but it is hit and miss, and I usually can't get back to the netbook display (just a black screen that I can move a mouse around).  Any suggestions would be appreciated.

---

### Post by ironring1 on 2010-03-05
Man, I should post more.  As soon as I post something, I seem to find a post that solves it.  See [http://ubuntuforums.org/showthread.php?t=1296507](http://ubuntuforums.org/showthread.php?t=1296507) .  Go to System->Appearance->Visual Effects and select "None".  Then Fn+F8 seamlessly steps through netbook display, external display, dual display, mirrored display...

Ironring1 = happy man :D

---

### Post by guwrt on 2010-03-05
Hello Ironring1,

Glad to see you writing such good things about Ubuntu.

If it can help this thread, I want to let you know when I updated my BIOS in Window$, the Asus Update software send me interesting information about the BIOS version. It give the following info:

Model 1005P        (is it the same basic machine as 1001P ?)
version 0804
Date 02/05/2010
Type of BIOS AMI
512K

Also, I want to let the community know that I have try Karmic on a live USB key and it works out of the box for the wireless. But I dont know for the builtin camera, microphone, touchpad, brightness and the cpu scaling issues.

Finally, the model number of my 1001P is SC17-BK and I bought it in Vancouver, BC at Staples (349$) during february 2010.

Keep on ironring1

Andre

---

### Post by guwrt on 2010-03-05
How did you deleted the D partition? 

Gparted ?

Andre

---

### Post by ironring1 on 2010-03-06
I did it in Windows 7.  I read in a few places that Windows 7/Vista get all upset if you don't delete their partitions using Windows. Now, I think that that only applies to the system partition, but since you have to resize the Win7 partition from within Windows (using Disk Management and "shrink"), I did it from inside Windows.  Note that I only deleted the D drive, defragged C and then shrunk C.  I didn't delete the rescue partitions that I would use to reinstall windows...

---

### Post by guwrt on 2010-03-06
wireless and cheese also works with the live usb key and UNR 9.10.

I am proceeding with dualboot Win 7 and Karmic.

Andre

---

### Post by Marcos Marado on 2010-03-06
Heads up: there's a better an easier way to have 1001P wireless working on Ubuntu:
[http://mindboosternoori.blogspot.com/2010/03/howto-have-wireless-working-on-asus-eee.html](http://mindboosternoori.blogspot.com/2010/03/howto-have-wireless-working-on-asus-eee.html)

Basicly the support is already added on the newest kernel versions, so you just need to update your kernel (using the deb's, it's quite easy).

---

### Post by guwrt on 2010-03-06
> **Marcos Marado said:**
> Heads up: there's a better an easier way to have 1001P wireless working on Ubuntu:
[http://mindboosternoori.blogspot.com/2010/03/howto-have-wireless-working-on-asus-eee.html](http://mindboosternoori.blogspot.com/2010/03/howto-have-wireless-working-on-asus-eee.html)

Basicly the support is already added on the newest kernel versions, so you just need to update your kernel (using the deb's, it's quite easy).

Maybe that's why Karmic and UNR on live USB key works out of the "key"

Andre

---

### Post by ironring1 on 2010-03-08
Hey all.  I just tried the new kernel (removed the WinXP driver using ndisgtk first, though), and it didn't work for me.  Has anyone else with a ASUS 1001p-MU17 tried this?  Guwrt, you said that you have a 1001P-SC17, whereas mine is a MU17; does anyone know the difference between these two models?  I can't actually find out anything about the SC17, but given that Guwrt got his wireless working OOB tells me that something is different between his machine and mine.  Perhaps a different wireless card?  Guwrt, what do you get from lspci -nn ?

If I need to do something else to get the wireless card to be recognized by the new kernel, please let me know (thanks in advance!)

I've since removed the newer kernel and gone back to 2.6.31.20-generic and the XP driver under NDISWRAPPER, and I am back up and running with wireless with my 1001P :)

---

### Post by guwrt on 2010-03-08
> **ironring1 said:**
> Hey all.  I just tried the new kernel (removed the WinXP driver using ndisgtk first, though), and it didn't work for me.  Has anyone else with a ASUS 1001p-MU17 tried this?  Guwrt, you said that you have a 1001P-SC17, whereas mine is a MU17; does anyone know the difference between these two models?  I can't actually find out anything about the SC17, but given that Guwrt got his wireless working OOB tells me that something is different between his machine and mine.  Perhaps a different wireless card?  Guwrt, what do you get from lspci -nn ?

If I need to do something else to get the wireless card to be recognized by the new kernel, please let me know (thanks in advance!)

I've since removed the newer kernel and gone back to 2.6.31.20-generic and the XP driver under NDISWRAPPER, and I am back up and running with wireless with my 1001P :)

Okay. I am now running Ubuntu 9.10 Karmic and the kernel is 2.6.31-20 and Gnome is 2.28.1.


Is there any difference between SC17 and MU17 ? Must be some differences but which? How can I know that? Is there a way to know it?

I have to say that during the installation by USB key, the wireless connection was not easy (on and off) specially during the final update. I have use a ethernet cable to finish the installation to prevent a bad installation. After thoses updates, I removed the cable and the wifi connection was stable and fully functionnal.

Did you notice in the system monitoring, there is 2 CPU running in this unit ? I didn't know this before

Andre

---

### Post by nellmathew on 2010-03-08
> **guwrt said:**
> 
Is there any difference between SC17 and MU17 ? Must be some differences but which? How can I know that? Is there a way to know it?

...

Did you notice in the system monitoring, there is 2 CPU running in this unit ? I didn't know this before

The two CPUs are due to hyper-threading, which N450 chip features. This feature tricks the system into thinking there are dual CPUs when in reality there is actually only one. As far as the difference between SC17 and MU17, try "lspci" in terminal and post what it outputs.

---

### Post by guwrt on 2010-03-08
Thanks for the info nellmathew.

My lspci result:

00:00.0 Host bridge: Intel Corporation Pineview DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation Pineview Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation Pineview Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation Tigerpoint LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

Andre

---

### Post by ironring1 on 2010-03-09
Mystery solved!  Here is my lspci (1001P-MU17-BK):

00:00.0 Host bridge: Intel Corporation Pineview DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation Pineview Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation Pineview Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation Tigerpoint LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Atheros Communications Inc. Device 002c (rev 01)

The Atheros 002c, what is in the 1001P-MU17, is the AR2427 (do a search for Atheros Device 30A7, what the 002C is identified as in the netathw.inf on lines 170, 175, 176 and 269).  Ironically this is the wireless card that the link in Marcos Marado's post claimed that the new kernel supports.  The AR928x devices are identified as device 002b, which apparently are what are in the SC17 version of the 1001P, like Andre's.  Well, at least we know that we aren't crazy!  I read something somewhere this evening that the 1005PE's released in Japan have the AR2427 card in them, too.  
 
WRT the PCI devices, the wireless card is the ONLY way that the SC17 and the MU17 seem to differ.

For people with the AR2427, there apparently is support for it in the newest ath9k drivers (linuxwireless.org/en/users/Drivers/ath9k), and there are instructions there on how to get it up and running.  I need stable wireless for the time being, and I'm pretty happy with ndiswrapper for now.  I'm getting the same network speeds according to internet speed test ([www.speedtest.net](www.speedtest.net)) with my 1001P over 802.11g + WEP as I do with my desktop (ethernet cable to my router) tonight, so clearly the windows driver isn't the limiting factor ;)

---

### Post by Fwertz on 2010-03-09
Thanks to you fine people I can now use ubuntu with this glorious note-taking machine. If it weren't for you, I would have wasted a vast amount of my spring break trying to make ends meet with this install and inevitably would of given up. So here's to you (glass *clink*).

Currently everything is working quite well with your suggested fixes. Two things still stand out. One is with audio. With default settings when a headphones are in the jack, the speakers still want to work. If I go to System->Preferences->Sound and change the output from Analog Output to Analog Headphones, the headphones work great but that's the only output. I did install the karm. alsa drivers. Secondly the brightness tends to revert back to full power when the system 'idles' for a few seconds (30? 60?) All else is working well. I noticed that my CPU freq is normal and baselines at 1Ghz. It lists 1.33Ghz as available but seems to always be at 1Ghz or 1.6Ghz. Keep up to great work!

lspci:

[SIZE="2"]00:00.0 Host bridge: Intel Corporation Pineview DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation Pineview Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation Pineview Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation Tigerpoint LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Atheros Communications Inc. Device 002c (rev 01)[/SIZE]

---

### Post by ironring1 on 2010-03-09
Hi, Fwertz; congrats on getting your netbook setup.  I hadn't tried headphones with my netbook before your post, but I was able to reproduce the problem.  Interesting

I haven't had time to try an automatic fix, but if you have pavucontrol installed (sudo apt-get install pavucontrol), then you can click on the "outputs" tab and manually turn down the volume of the speakers and then turn up the headphones jack using the sliders.

I haven't tried this out yet, but if you look here ([http://ubuntuforums.org/showthread.php?t=338987](http://ubuntuforums.org/showthread.php?t=338987)) at post #7, you might be able to turn on the headphone "sense"via alsamixer at the command line.  I'll try this tonight (don't have my netbook at work; if I did, I wouldn't get any work done!) and post my results back.

I have the same occasional flickering of screen brightness, too.  The netbook seems to forget how bright I set it to until I touch the keyboard or trackpad, and then it snaps back to what I had set it to...

---

### Post by Fwertz on 2010-03-09
Good ideas, but no dice yet I'm afraid. There are only two outputs. One is everything, the other is headphones only. I think there is some incompatibility with alsa with this headphone sense output. It's not toggling the headphone output whenever something is connected to phones jack. I don't really know much about alsa, this is just my guess.

Alsamixer gives me:

Master | Headphon |PCM |Mic Boost | Beep |Speaker

---

### Post by Fwertz on 2010-03-10
Alright, got a fix for the headphone sense. I spent most of the night trying to work the kinks out and after much trial and error this snippet seemed to work.

First at a shell do ```
aplay -l
```

If you're like me and have an intel HDA card,

Append the following to **/etc/modprobe.d/alsa-base.conf** ```
options snd-hda-intel model=auto position_fix=1
```

/reboot

---

### Post by ironring1 on 2010-03-10
I can confirm that the solution to headphone sense posted by Fwertz works for me.  I also noticed that my audio output is higher now, which is really nice, too.  Built-in microphone/audio input still work too (including Skype).

Good job!

---

### Post by whit on 2010-03-15
> **ironring1 said:**
> INote that I only deleted the D drive, defragged C and then shrunk C....Does the shrunken C still have enough room to run the occasional Windows app? I've got one of these coming this week, in part because my prior years' tax info is in TaxAct (which used to run fine under wine, but this year reportedly not - and other current US tax software, not at all). I've little other current use for Windows, and plan to clean out all the 30-day trial stuff and the like, but want to end up with a functional Windows system for those rare occasions like tax time, or whatever else comes up.

---

### Post by guwrt on 2010-03-15
> **whit said:**
> Does the shrunken C still have enough room to run the occasional Windows app? I've got one of these coming this week, in part because my prior years' tax info is in TaxAct (which used to run fine under wine, but this year reportedly not - and other current US tax software, not at all). I've little other current use for Windows, and plan to clean out all the 30-day trial stuff and the like, but want to end up with a functional Windows system for those rare occasions like tax time, or whatever else comes up.

On my computer, my C drive is now a 58 Gb. I think you will have plenty of room for your Windows software.

---

### Post by guwrt on 2010-03-15
> **Fwertz said:**
> Thanks to you fine people I can now use ubuntu with this glorious note-taking machine. If it weren't for you, I would have wasted a vast amount of my spring break trying to make ends meet with this install and inevitably would of given up. So here's to you (glass *clink*).

Currently everything is working quite well with your suggested fixes. Two things still stand out. One is with audio. With default settings when a headphones are in the jack, the speakers still want to work. If I go to System->Preferences->Sound and change the output from Analog Output to Analog Headphones, the headphones work great but that's the only output. I did install the karm. alsa drivers. Secondly the brightness tends to revert back to full power when the system 'idles' for a few seconds (30? 60?) All else is working well. I noticed that my CPU freq is normal and baselines at 1Ghz. It lists 1.33Ghz as available but seems to always be at 1Ghz or 1.6Ghz. Keep up to great work!

lspci:

[SIZE="2"]00:00.0 Host bridge: Intel Corporation Pineview DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation Pineview Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation Pineview Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation Tigerpoint LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Atheros Communications Inc. Device 002c (rev 01)[/SIZE]

Same issue for me for the headset. The builtin speakers work when my headset is plugged to the computer jacks. I confirm also the issue for the brightness control. It is rather difficult to control the brightness with F5 and F6 keys.

Andre

---

### Post by guwrt on 2010-03-15
> **ironring1 said:**
> I can confirm that the solution to headphone sense posted by Fwertz works for me.  I also noticed that my audio output is higher now, which is really nice, too.  Built-in microphone/audio input still work too (including Skype).

Good job!

Congradulation Fwertz! It works for me too. Andre

---

### Post by borabosna on 2010-03-16
> **ironring1 said:**
> For people with the AR2427, there apparently is support for it in the newest ath9k drivers (linuxwireless.org/en/users/Drivers/ath9k) ;)
I am trying to use these instructions on that page (I have AR2427), I made and installed compat-wireless, then it tells me to unload all wireless modules by make wlunload, fine, then asks me to load the ones I need. How do I do that? There is a long list, and I guess I need
updates/drivers/net/wireless/ath/ath9k/ath9k.ko
but is that the only one I need? What is the right syntax? I can post the long list of wireless modules if needed.

Really appreciated, beginner here ;) Thanks!

---

### Post by ironring1 on 2010-03-16
Hi, borabosna.  I haven't gotten native support for the AR2427 to work yet either, but honestly, the WinXP driver with NDISWRAPPER works great for me.  I recommend it.  Look to my long post earlier in this thread.

---

### Post by ironring1 on 2010-03-16
I have found a solution the flickering screen brightness problem with the 1001p.  Go into System->Preferences->Power_Management and turn of automatic dimming of screen brightness.  This has solve the problem for me so far.

I found this solution here: [http://vip.asus.com/forum/view.aspx?id=20100203232036890&board_id=20&model=Eee+PC+1005PE&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20100203232036890&board_id=20&model=Eee+PC+1005PE&page=1&SLanguage=en-us) (see post #7).

---

### Post by hoptimusPrime on 2010-03-16
oh my goodness, this sure seems like quite a bit of work to run karmic on this netbook.

i will be buying this same one in the next day or two, and i have a few questions:

first of all, i want to dual boot ubuntu with windows 7.  it seems like all the fixes are here on this thread to get everything running (besides the screen flicker thing).  my question:   is this going to be like a one month, labour-intensive project to finally get this thing to work? or is it fairly quick and painless?

secondly, i noticed there are two different models of the asus eee 1001p. one model has wireless b/g, and the other has b/g/n.  has anybody else noticed this? maybe this is why some people were having proplems connecting to wireless.
here is a link to one with only b/g:
[http://www.memoryexpress.com/Products/PID-MX27313%28ME%29.aspx](http://www.memoryexpress.com/Products/PID-MX27313%28ME%29.aspx)
is this a typo?  or do some come with different wireles cards?

and also, will this netbook be capable of running the 'compiz cube' and awn manager?


this seems like a great little machine for my price range and i would love to be able to go buy it knowing everything is going to be ok

---

### Post by borabosna on 2010-03-16
> **ironring1 said:**
> Hi, borabosna. I haven't gotten native support for the AR2427 to work yet either, but honestly, the WinXP driver with NDISWRAPPER works great for me. I recommend it. Look to my long post earlier in this thread.

I have tried it several times already (ndiswrapper with Win drivers). The driver is called netathr.inf, right? Never works. I also cannot configure it from ndisgtk. I keep getting "could not find a network configuration tool." I tried wirc and network-manager. No cigar.

I can connect to wireless networks with a Wireless USB adapter (SMC EZ Connect) and that is how I am writing now. But the wifi on board doesn't work like it does on my Windows 7 Starter once I unplug the adapter.

I am about to give up and accept a life with this Usb adapter, which gives me really low connection. Or give up on Ubuntu completely. I tried EEEBuntu but that gave the same results. I also tried Zenwalk, which is pretty cool, but again no cigar with the wireless. I mean, it is supposed to work ON ITS OWN, right? Without a usb adapter? Like it does on my Windows?

Maybe I should try what some others did, throwing the warranty out the window...

---

### Post by ironring1 on 2010-03-17
Borabosna, please post the output of lspci -nn so that we can see what hardware you have.   What variant of the 1001p do you have (mine is the 1001p-mu17); we have identified 2 different wireless cards in 1001p variants already...  

I think that everybody gets the "cannot detect hardware" error with ndiswrapper, but it doesn't seem to matter.  Did you follow the detailed instructions that I gave in post #37 in this thread?

---

### Post by ironring1 on 2010-03-17
Quick update to the screen flickering problem; I also had to turn off "reduce backlight brightness", but since disabling that and automatically dim the screen, I have yet to have the screen flicker.

---

### Post by borabosna on 2010-03-17
> **ironring1 said:**
> 7) wireless: sudo apt-get install linux-backports-modules-karmic-generic linux-backports-modules-wireless-karmic-generic
     Tried to get wireless working with ath9k by commenting out "blacklist ath_pci" in /etc/modprobe.d/blacklist-ath_pci.conf and adding ath9k to /etc/modules 
          -did not work.
          Installed linux-backports-modules-karmic just to be sure, still no go; restored blacklist-ath_pci.conf and /etc/modules.
     ndiswrapper:  followed CaptSaltyJack's instructions earlier in this thread (all of the ndiswrapper packages already were installed with 9.10) using winXP driver from ASUS.  SUCCESS, I am now able to log in to unsecured and WEP wifi networks (have not tested WPA/WPA2).  connection seems robust, has yet to drop.

I did all of this. Not working.

I get from lspci -nn : This is different from your cards (two cards that were posted earlier here)
And yes I do have 1001p MU-17.

01:00.0 Ethernet controller [0200]: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)
02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:002c] (rev 01)

I am on Zenwalk now, bye bye Ubuntu :P Still no wifi

EDIT: I'll just use Windows. It's just not working.

EDIT2: Taking isidoro's advice here [http://georgia.ubuntuforums.org/showthread.php?t=1369304&highlight=isidoro](http://georgia.ubuntuforums.org/showthread.php?t=1369304&highlight=isidoro)  I googled and got the 7.7.0.329 WHQL drivers. For the first time my Eee pc recognized the wireless networks. This happened in Zenwalk. But right after, Zenwalk crashed, and after reboot Zenwalk would freeze halfway through loading at the splash screen. Now reinstalled Zenwalk and trying. May need to update the kernel, or something like that.

I found this website very helpful for anyone out there who is also suffering:
[http://www.atheros.cz/](http://www.atheros.cz/)

EDIT3: Sorry to make this long, but I have wireless now on UNR 9.10 ! I used the 7.7.0.456 drivers from the above mentioned Czech website. I experience a lot of breaks and disconnections & the connection strength is nowhere near Windows. But still, I have wireless!

Anybody with Atheros chip, please check out [http://www.atheros.cz/](http://www.atheros.cz/) hope this helps the community a bit :)

---

### Post by ironring1 on 2010-03-18
Borabosna, for the record, my 1001p-mu17 has the same wireless card as yours.  I still can't figure out why ndiswrapper worked for everyone else with the 168c:002c card (including me), but not you. Either way, I'm glad that you've gotten it working :)

BTW, wrt to the XP drivers + ndiswrapper, I have tested it under open networks, WEP enabled and WPA enabled, and it works with them all and has yet to drop a connection.

---

### Post by erm27 on 2010-03-21
[COLOR="Red"]THANKS SO MUCH!! I got this done in less than 30 minutes, if only I had paid attention on my first attempt I wouldn't have downloaded the wrong driver. As a side note, instead of using terminal commands I simply searched and installed the packages through Synaptic Package Manager. Downloaded the driver after completing the package installation.  Unzipped and then used "Windows Wireless Driver" from System > Administration > Windows Wireless Driver. Didn't even have to reboot, the netbook froze for a good 45 seconds(be patient) and then I saw the network start working. Rebooted to confirm the changes worked from boot. THANKS AGAIN:KS[/COLOR]


> **CaptSaltyJack said:**
> Great news, got wireless working perfectly, even with WPA/WPA2 encryption!

Here's how.

1) Using apt-get, istall the ndiswrapper-common, ndiswrapper-utils-1.9, and ndisgtk packages.
2) Using apt-get, install linux-backports-modules-wireless-karmic-generic.
3) Go to [http://support.asus.com/download/download.aspx](http://support.asus.com/download/download.aspx) and get the WinXP wireless LAN drivers for the 1001P (NE785H_GE112H). Unzip that file to a folder.
4) Run ndisgtk (probably as root to be safe) and install that WinXP driver (select the .inf file). There will be an error, but ignore it, it's fine.

After those steps (possibly after a reboot), I now have wireless and can connect to my Linksys running Tomato firmware & WPA2 encryption.


---

### Post by Fwertz on 2010-03-22
Just a quick note, all of the fixes on this thread are in 100% working order in Lucid beta1. Flash is very glitchy though.

---

### Post by olaf-g on 2010-03-28
I solved the issues with the wireless and the screen brightness control. As I am writing down my experiences and fixes in a blog you can find the exact steps over there:

[http://linuxon1001p.blogspot.com]("http://linuxon1001p.blogspot.com")

For wireless I use a self compiled native driver which was really not difficult to do and the brightnes issue is fixed completely including on screen notifications and auto dimming working.

---

### Post by borabosna on 2010-04-01
> **Fwertz said:**
> Alright, got a fix for the headphone sense. I spent most of the night trying to work the kinks out and after much trial and error this snippet seemed to work.

First at a shell do ```
aplay -l
```If you're like me and have an intel HDA card,

Append the following to **/etc/modprobe.d/alsa-base.conf** ```
options snd-hda-intel model=auto position_fix=1
```/reboot

This totally worked for me on my Eee 1001P too! Thank you so much!

---

### Post by danbaatar on 2010-04-05
> **Marcos Marado said:**
> Heads up: there's a better an easier way to have 1001P wireless working on Ubuntu:
[http://mindboosternoori.blogspot.com/2010/03/howto-have-wireless-working-on-asus-eee.html](http://mindboosternoori.blogspot.com/2010/03/howto-have-wireless-working-on-asus-eee.html)

Basicly the support is already added on the newest kernel versions, so you just need to update your kernel (using the deb's, it's quite easy).

I tried this, and wireless does work, but the webcam stops working and the battery life goes way down.

---

### Post by brib on 2010-04-06
Hello all..

I've bought a 1001p black, and its great.  I've installed Backtrack4 which is based on Ubuntu but the screen resolution is horrid.  the screen is capable of 1024x600 I think, but in Linux all I can get is 800x600 or something, and it looks terrible.  Anyone know how I can change the resolution?  maybe I'm missing a driver?  any help much appreciated.

---

### Post by -jay- on 2010-04-06
thank you im posting this on my netbook so far all the guides in this thread have worked only problem i have is i cant use my mic i have no sound at all

---

### Post by MIJ-VI on 2010-04-07
> **-jay- said:**
> thank you im posting this on my netbook so far all the guides in this thread have worked only problem i have is i cant use my mic i have no sound at all

Is the audio muted in Terminal-->alsamixer?

---

### Post by -jay- on 2010-04-07
> **MIJ-VI said:**
> Is the audio muted in Terminal-->alsamixer?

nope its unchecked when i go into soundrecorder record me talking i dont hear anything when i play it back sound does work playing music & watching videos

---

### Post by BensonBear on 2010-04-08
Can people report whether they experience the problem reported at 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/523298](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/523298)

"suspending the lid on an ASUS 1001P cuts off USB".

This is a pretty serious problem.  I presume he means that
any form of suspension has this problem, not just suspension
triggered by closing the lid.

Also, can one disable this apparently automatic suspension
as a temporary, rather unsatisfactory, workaround should
the problem not be solvable at current?

Or better yet, keep most suspension but just prevent the USB
ports from suspending (via /sys/bus/usb/devices:
[http://www.lesswatts.org/projects/devices-power-management/usb.php)?](http://www.lesswatts.org/projects/devices-power-management/usb.php)?)

---

### Post by sneakernet on 2010-04-11
Thanks so much olaf-g, adding "acpi_backlight=vendor" to grub saves current brightness setting. I've been waiting patiently for this fix.

---

### Post by redfish123 on 2010-04-11
As far as the wireless issue goes I found that upgrading to the latest kernel solved the issues with it. Step I took are listed [here.]("http://jasonmccollough.blogspot.com/2010/04/getting-wireless-on-asus-eee-1001p-with.html") I definitely appreciate all the other posts regarding fixing the issues with the Screen Brightnesss (Olaf), and Skype issues.

---

### Post by Mathieup75 on 2010-04-15
I also have a Eee 1001P and this helped a lot.  The following link filled in the gap, like the blacklist.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by CaptSaltyJack on 2010-04-16
Anyone know if all these messy issues will be fixed in Ubuntu 10.04? I have a feeling they will. I've already heard they're fixing the Atheros wireless issue. Hopefully Ubuntu will work right out of the box on the 1001P.

---

### Post by welshmike on 2010-04-18
> **CaptSaltyJack said:**
> Great news, got wireless working perfectly, even with WPA/WPA2 encryption!

Here's how.

1) Using apt-get, istall the ndiswrapper-common, ndiswrapper-utils-1.9, and ndisgtk packages.
2) Using apt-get, install linux-backports-modules-wireless-karmic-generic.
3) Go to [http://support.asus.com/download/download.aspx](http://support.asus.com/download/download.aspx) and get the WinXP wireless LAN drivers for the 1001P (NE785H_GE112H). Unzip that file to a folder.
4) Run ndisgtk (probably as root to be safe) and install that WinXP driver (select the .inf file). There will be an error, but ignore it, it's fine.

After those steps (possibly after a reboot), I now have wireless and can connect to my Linksys running Tomato firmware & WPA2 encryption.

Now, if I could only get the built-in microphone working, and the multi-touch capability in the touchpad! Oh, and the brightness controls are completely whacked, too, they don't work properly and Ubuntu doesn't memorize the way you have your brightness set.

Great stuff CaptSaltyJack. Thank you very very much.
I followed your instructions and I now have my [ASUS Eee PC 1001P]("http://www.amazon.co.uk/s/?ie=UTF8&keywords=asus+1001p&tag=googhydr-21&index=aps&hvadid=5706673606&ref=pd_sl_5vqaq6smfp_b") Ubuntu 9.10 system working with wireless.

Mike

---

### Post by mcaleaa on 2010-04-20
Hi everyone, I just got a new Asus Eee PC 1001P, and I'm about to start installing Ubuntu on it.

After reading this thread, my first instinct is to follow CaptSaltyJack's instructions.

My question: what installation do these instructions relate to? Ubuntu Netbook Remix, or Ubuntu Karmic Desktop?

I just want to be clear about what the starting point is.

Thanks!

---

### Post by welshmike on 2010-04-20
mcaleaa

My message referred to Ubuntu 9.10 (Karmic Koala).
I run Karmic on my 5yo dual boot XP laptop and like it so have installed it on my Asus Eee PC 1001P Netbook.
I'm pleased with 9.10's performance on the Netbook. It runs faster than my Laptop.
One problem with installing Ubuntu dual boot after XP was that my Netbook had 4 primary partitions.
More details if you ask.

Mike

---

### Post by mcaleaa on 2010-04-21
> **welshmike said:**
> mcaleaa

My message referred to Ubuntu 9.10 (Karmic Koala).
I run Karmic on my 5yo dual boot XP laptop and like it so have installed it on my Asus Eee PC 1001P Netbook.
I'm pleased with 9.10's performance on the Netbook. It runs faster than my Laptop.

Mike

Sounds good. Thanks Mike.

> **welshmike said:**
> mcaleaa

One problem with installing Ubuntu dual boot after XP was that my Netbook had 4 primary partitions.
More details if you ask.



Yes please. I haven't started yet, it's going to be on the weekend. I don't use Windows very much but will probably go with a dual-boot.

Michael

---

### Post by welshmike on 2010-04-21
Michael,

Below is the history of the partitioning of my Netbook:

Original out of the box and taken using Ubuntu live CD GParted:

[IMG]http://www.eacott.org.uk/GP%20orig.png[/IMG]

Now taken with GParted after deleting partition 2 (/dev/sda2) and installing Ubuntu dual boot. (Note that I re-sized the XP partition to about 40GB.)

[IMG]http://www.eacott.org.uk/GP%20now.png[/IMG]

Mike

---

### Post by hans75 on 2010-04-30
Hello,

I also have a  1001P and want to install Ununtu on it in dual-mode with XP. I already did the partitioning, I added the SWAP and 2 EXT3 for root and home. The Boot and recovery partitions (see the last partitions above) are untouched. At the moment the Express Gate (left power button) and the recovery mode (F9 at startup) works fine. 
Now my question, if I install Ubuntu on it, does this deselect the boot partition, because it changes the MBR?
My goal is to have the Express Gate and recovery mode working and a dual-boot system with XP and UNR.

Thanks a lot!

Hans

---

### Post by welshmike on 2010-04-30
Hello Hans,

I took a different approach to you about partitioning. I deleted the partition labelled D: by Windows because it was primary.
I also made partition C: smaller. 
When I installed Ubuntu 9.10 I let it do its own partitioning for its ext4 and swap partition using the space I'd deleted.
The changes Ubuntu install makes to the MBR do not affect the function of Express Gate on the 1001P.
As you know, the left power button kicks off Express Gate.
Express Gate is an ASUS rebranding of Splashtop.
You can read about Splashtop here: [http://en.wikipedia.org/wiki/Splashtop](http://en.wikipedia.org/wiki/Splashtop)
in particular:
"Internals

Splashtop seems to work with a 512MB flash memory embedded on the PC motherboard. A proprietary core engine starts at the BIOS boot and loads a specialized Linux distribution called a "Virtual Appliance Environment" (VAE). While running this VAE, the user can launch "Virtual Appliances" (VA). Skype is a VA, for instance."

So left power button does not involve the MBR. 

I hope the above helps.

By the way. I still haven't got the built-in microphone to work on Skype when running 9.10.

Also now that 10.04 LTS is here I'm thinking of upgrading on my 1001P from 9.10 to 10:04 LTS and see if it resolves my Skype microphone problem.

Final info: The 1000P microphone and webcam work problem free on Splashtop so why oh why is 9.10 not the same (maybe a tweaked Skype in Spashtop???).

---

### Post by hans75 on 2010-05-01
Hello welshmike,

thank you very much for these perfect explanation!
Because of  following, I thought Express Gate is deletable[]("http://dict.leo.org/ende?lp=ende&p=Ci4HO3kMAA&search=%26#160;&trestr=0x8002").
[http://www.eeepc.de/thema-9684-Problem_mit_Asus_1001P.html?eee=1&hilight=1001p+Express+Gate](http://www.eeepc.de/thema-9684-Problem_mit_Asus_1001P.html?eee=1&hilight=1001p+Express+Gate)
Did you install UNR or the normal Ubuntu?
I will try it with UNR.

hans

---

### Post by welshmike on 2010-05-03
hans

Sorry about late reply.
I did not try UNR because my main Toshiba laptop runs Ubuntu 9.10 very well.
Normal Ubuntu on 9.10 was fine on my ASUS 1001P netbook until... I upgraded to 10.04.
The upgrade was not successful because I ended up with a black screen. 
So I did a clean install of 10.04 from my USB flash drive, same black screen!!!
I decided to go back to 9.10 and had to start again.
I'm now running 9.10 but cannot get wireless working despite using the same procedure I used before that is detailed in this forum thread.

---

### Post by welshmike on 2010-05-04
I've just booted up Ubuntu 9.10 on my Asus Eee PC 1001P Netbook for the first time since yesterday and here I am with wireless working. 
Yesterday my Netbook kept trying to connect to my Linksys wireless router using its WPA and WPA2 security key and kept disconnecting,
I've changed nothing since then.
It's a mystery.
However, there were 7 local wifi access points running yesterday. ?

---

### Post by niteflier on 2010-05-07
To add my own experiences with my 1001p-MU17:

First round was with wubi/Lucid. Pretty much mirrored the issues other people had. Successfully used ndiswrapper to get wireless working.

Next I used Debian Squeeze (Linux 2.6.32-3-686), wiped the hard drive and did traditional install. Same issues except that wireless now worked out of the box. The fix for screen brightness worked here too. Not so with front mic. 

After taking over the hard drive, the Express Gate does not work. It obviosly is stored on the drive. Both power buttons work the same.

Weird: after a few days of use, my wired ethernet stopped working. Wireless still worked. I restored W7 (ugh) to check. At first it saw no NIC, but after doing "Scan for hardware changes" it returned and came to life. I will try again with Lucid, traditional hard drive install.

---

### Post by hans75 on 2010-05-09
I tried it with UNR, but I don`t like the stile. Now I have Ubuntu 10.4 working. Wireless is working with following howto:
[http://linuxon1001p.blogspot.com/2010/03/fixing-wireless.html](http://linuxon1001p.blogspot.com/2010/03/fixing-wireless.html)
And the brightness thing works with this additional kernel options: "acpi_osi=Linux acpi_backlight=vendor"

---

### Post by welshmike on 2010-05-12
Having failed to install 10.04 on my Netbook from my USB stick due to the monitor staying dim I installed 9.10 on it and ran with 9.10 successfully  for a couple of weeks. 
I have now re-created a bootable 10.04 on a USB stick.
I booted my Netbook from the USB stick and ran 10.04 as one would from a live CD.
Lo and behold the monitor was not dim and wireless worked out of the box once I had supplied my access points SSID and the WPA password.
I had the same results on my Laptop.
Both my Netbook and Laptop have 9.10 installed and I wonder if the 10.04 live USB system is using some of the "stuff" installed on 9.10.
That seems unlikely.

My Netbook hard drive has a spare empty 25GB NTFS partition. If I format that partition as ext3 I'm tempted to install 10.04 side by side with the existing XP and Ubuntu 9.10.
1. Will this be possible (by the default provided by the install)?
2. Will GRUB2 show a boot list choice of 10.04, 9.10 and XP (where the first two "lines" are for 10.04) such as: 

Ubuntu, Linux 2.6.32-21-generic
Ubuntu, Linux 2.6.32-21-generic (recovery mode)
Ubuntu, Linux 2.6.31-21-generic
Ubuntu, Linux 2.6.31-21-generic (recovery mode)
Ubuntu, Linux 2.6.31-21-generic
Ubuntu, Linux 2.6.31-21-generic (recovery mode)
Ubuntu, Linux 2.6.31-20-generic
Ubuntu, Linux 2.6.31-20-generic (recovery mode)
Ubuntu, Linux 2.6.31-19-generic
Ubuntu, Linux 2.6.31-19-generic (recovery mode)
Memory test (memtest86+, serial console 115200)
Memory test (memtest86+)
Microsoft Windows XP Home Edition (on /dev/sda1)

---

### Post by hans75 on 2010-05-13
1. you have to select the manual partitioning mode and then just select the 25GB partition as root with EXT3 or EXT4 plus formatting. 
As home select your home partition from you 9.10 but without formatting!! Thats it, GRUB2 will find all other OS. 

2. Yes GRUB2 adds all OS to the bootloader. 
If you are not able to select a other OS in the bootloader, just disable "fast boot" in bios. 
If you want that a other OS is selectet in default, just change the number 
GRUB_DEFAULT=0 to 3 or what ever you want in the /etc/*default*/*grub file. After that,*[FONT=monospace] [/FONT]sudo update-grub[I].
[/I]

---

### Post by welshmike on 2010-05-13
hans

Below is the current partitioning of my Netbook (running dual boot XP and Ubuntu 9.10).

[IMG]http://www.eacott.org.uk/GP%20now.png[/IMG]

Neither XP Partition Magic nor Ubuntu Gparted will let me delete any of the empty 25GB partitions.

So I will have to go back to restoring the HDD to the image below I took that did not have Ubuntu installed and start from there to install Ubuntu 10.04.

[IMG]http://www.eacott.org.uk/GP%20orig.png[/IMG]

Will it be worthwhile?

---

### Post by John Bean on 2010-05-13
> **welshmike said:**
> Neither XP Partition Magic nor Ubuntu Gparted will let me delete any of the empty 25GB partitions.

They're all mounted. Unmount them: in gparted right-click on a "key" and select "Unmount" - the key will then vanish and you'll find you can edit/delete the unmounted partition.

---

### Post by hoptimusPrime on 2010-05-13
thank you everybody for all the help.

i have the 1001p, and i resolved the screen issue.  there is no applet that pops up anymore showing brightness levels, but it still works.

i still have a few problems:

1.  wireless works *almost* perfectly.  i was still getting about 5-10% better signal using windows 7..  not really a big deal although it would be nice to fix.  i've got the wireless backports and the driver that came 'out of the box' with 10.04..

2.  still dont have 2 finger scrolling working, i couldn't find a solution that seemed foolproof.  

3.  also, i found it isn't possible to use AWN, VNC, and visual effects on EXTRA (apparently some bug with compiz and nvidia drivers or something.).  is there another compositor i can use with AWN.  or should i try using kubuntu?  i want to be able to use these features

4.  i only get about 6 or 7 hours of battery life when i know i can get up to 11 in windows.  this is most likely due to poor cpu scaling.  
there is another button at the top left of the keyboard similar to the power button.  i used to be able to press it and toggle my cpu speed from power save to high speed.  anybody know how to enable this button again in ubuntu 10.04?  or at least improve the frequency scaling / battery life?

5.  i noticed my cpu runs quite hot, it got up to 65 degrees the other night before the fan started...  it there any way to control when the fan kicks in.?

i know this is a lot to ask, but i have been working on this thing for almost a month now and i would appreciate any help.  i have tried to fix these problems myself with no success, so it's time to turn it over to the pros

thanks!

---

### Post by welshmike on 2010-05-13
John Bean

Thanks for your reply.

Now that I have 9.10 working well I'm not sure I want to go to the hassle right now of getting 10.04 to the same stage. Maybe 10.10 Maverick Meerkat will solve out of the box the problems including screen brightness and sound for the 1001P that posters have reported in the Ubuntu forums.:cool:

---

### Post by skyway45 on 2010-05-14
> **CaptSaltyJack said:**
> Bothi - did you follow my steps above exactly? Also, have to ask the obvious: have you tried hitting Fn-F2 to turn the wireless device on?
I followed your steps exactly, Capt'n.  Now I have Win7 (for a while) on one side of my wife's eee 1001p and Ubuntu Netbook Remix 10.04 on the other.  I did not see that error you spoke of, and I was notified I had a connection before I closed the wrapper.  Its people like you that make Ubuntu...  Ubuntu.  Thank You, Captain, for your time and effort for the Ubuntu community.  :)

---

### Post by CaptSaltyJack on 2010-05-14
Hey no prob! I help where I can :)

---

### Post by Fwertz on 2010-05-17
I've since moved to 10.04 and I'm loving....every...single...bit. I have it on every machine now with only M$ in VMs. Very stoked about that.

I was helping a friend of mine with the older 1005HA get some features working solid and I found this [http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/]("http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/") post. You can add an authenticated repository to your software sources (System -> Admin -> Software Sources) to download the eeePC 'Super Hybrid Engine'. I'm still running its paces but the battery life has seemed to improve greatly amongst some other nice quick features.

How:

Insert ```
deb http://www.statux.org/software packages main
``` into the third-party tab in Software sources.

Download the authentication key from (Direct link) [http://www.statux.org/software/key/statux.pub](http://www.statux.org/software/key/statux.pub)

In the authentication tab, add that downloaded file. Apply and close. You should be prompted to update repositories and download ~76 packages.

Install ```
EeePC Tray
``` ; Try to avoid the Eee Aplet, it doesn't work for me, but the tray will.

Reboot and enjoy!

---

### Post by niteflier on 2010-05-19
Thanks to the information here, I now have Lucid on my 1001P pretty much the way I want it. 

Did a traditional install to EXT4 partition and using 2G swap partition. Got almost everything working; powersave, standby, hibernation, sound, microphone (skype works great), wireless (ndiswrapper), most of the hot keys. 

Only a few Fn-key combinations are not active: Fn-F7 for turning off screen, Fn-F9 for system monitor and Fn-Space for power profile. Not that I use or miss those functions, but if I get bored I may look into that.

Also dug into GRUB2 and cleaned up the boot menu by removing Memtest and the bogus Windows entries for the EFI and restore partitions.

--------------------------------------------------------------------------------------------------------
Added a couple of live distros in "frugal" install mode to do some non-scientific testing. Here is what I found:

GRUB takes about the same time to load as Express Gate  does, less than 10 seconds.
Other OSs were timed from the GRUB menu to desktop stabilization.
Next, Firefox was launched, closed, then opened again.

Ubuntu 10.04 provides the best overall performance/features ratio.
Win7 was slowest booting, running, and shutting down.
Puppy 5 takes longer to boot and shut down than Ubuntu (which it is based on), but running from RAM, it launches apps quicker.
Tinycore boots quite fast, but provides very little functionality, no network, no Firefox, 800x600 resolution.

```

OS             Boot Shutdown  FF cold/warm
GRUB            8      4          n/a  n/a
Express Gate    8      8           16    5
Win 7 Starter  45     15           10    3
Ubuntu 10.04   35      6            7    3
Puppy 5        37     13            5    3
Tinycore       15      9          n/a  n/a

```

---

### Post by n1ym on 2010-05-21
Thanks for this wonderful thread. I just got an EEEPC 1001P-PU17 for my daughter and wanted to get UNE 10.04 installed.

This is how I got the most important parts working:

Wireless: Updated the kernel to 2.6.34-22, and the wireless came right up and works wonderfully.
Brightness Control: As described in the thread changed the GRUB entry GRUB_CMDLINE_LINUX_DEFAULT to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux". Works well now.
Skype: Installed pavucontrol as described above and reduced one microphone channel to zero. Disabled the "Automatic Audio Volume Controls" in Skype and it works just fine.

A couple of things are left now. The camera works fine under Skype now, but for some reason the "Smile" program coming with the UNE will not work anymore. No big loss, though, as long as it functions with Skype I am fine.

The other thing is Bluetooth. Yes, the PU-17 model has bluetooth as well. The bluetooth module seems to work. I was able to mate my old JABRA 250 headset with the Netbook. However, it seems that Audio is not working propberly, i only hear static and scrambling. The microphone works, however. I will try later and see whether i have the same issues with other headsets, but if anybody has any idea what could cause the audio function to not work please let me know.

You all keep up the great work here, these threads are real lifelines for the folks like me with just limited experience.

W.

Update on the Bluetooth: It appears that the Jabra 250 is too old indeed and is not fully supported by the newer protocols. I tried again with a Jabra BT2080 and it worked wonderfully. Now I can use Skype with my Bluetooth Headset. Great.

---

### Post by welshmike on 2010-05-24
When I boot Express Gate and try to use Skype VOIP for the first time, e.g. clicking the Call Contact button of Echo / Sound Test Service, I get "Problem with Audio Playback".
If I then close Skype, the audio output (and input) works OK.
I looked at the Skype Options Sound Devices for the problematic first run and is showed hdmi for all of Sound In, Sound Out and Ringing. On the successful second run they showed HDA Intel (hw:Intel,0).
Please does anyone have any idea what is happening and how the problem can be corrected for the first run?

Mike

---

### Post by rundee_f on 2010-05-25
Hi guys,

I'm getting my own 1001P in a few days and thinking the Ubuntu Netbook Remix 10.04 in it as a single OS, not dual-booting with Window$. Is it working out of the box or is there any hardware compatibility issue(s) i need to worry?

Thanks guys :guitar:

---

### Post by welshmike on 2010-05-25
rundee_f

UNR did not work out of the box for me.
Also as I used to use XP I did not like the UNR GUI approach. It did not seem to perform any better than the "standard" Ubuntu Karmic 9.10 that I currently have on my 1001P. 
So I'd suggest you don't install UNR. Others may have a different suggestion.
Also I tried Ubuntu Lucid 10.04 on my netbook. I did not work out of the box and needed the wifi, sound and screen brightness tweaks documented in this forum. So I'm sticking with 9.10 and hope that Ubuntu Maverick (10.10?) will work out of the box for my 1001P. 
We shall see.

---

### Post by llenchikk on 2010-05-25
Hello!
I have Asus Eee PC 1001P. I upgrade bios from windowsXP. After that I install Ubuntu 10.04. Brightness control works good out of the box. WiFi doesn't.

Hotkeys Fn+VolumeUp and Fn+VolumeDown don't work. It concerns only me? It works for somebody?

---

### Post by rundee_f on 2010-05-25
> **welshmike said:**
> rundee_f

UNR did not work out of the box for me.
Also as I used to use XP I did not like the UNR GUI approach. It did not seem to perform any better than the "standard" Ubuntu Karmic 9.10 that I currently have on my 1001P. 
So I'd suggest you don't install UNR. Others may have a different suggestion.
Also I tried Ubuntu Lucid 10.04 on my netbook. I did not work out of the box and needed the wifi, sound and screen brightness tweaks documented in this forum. So I'm sticking with 9.10 and hope that Ubuntu Maverick (10.10?) will work out of the box for my 1001P. 
We shall see.

Thank you for sharing, nice input for me.. :)

---

### Post by welshmike on 2010-05-25
rundee_f

Some things I didn't cover:
I hope you saved some pennies and bought the 1001P with XP installed, not Windows 7.
I happen to run dual boot XP/Ubuntu 9.10 because there are some websites such as [http://www.weather-file.com/hurst/](http://www.weather-file.com/hurst/) that depend on IE.
Also I'm happy to try several different operating systems and releases on my netbook because I have installed a bootable Acronis True Image on a USB flash drive to back up and restore my internal drive.

Mike

---

### Post by diesel_here on 2010-05-25
Hi Everyone

I read this forum for information just before I purchased my 1001p, it came with XP & for information purposes I did the following:

I wanted to avoid altering any anything from a stock install if possible.

Made XP partition 10gb, deleted restore partition. - if xp dies, i'm not fussed (I only kept it for old artwork files I may need to convert).
Iinstalled Kubuntu Lucid 64bit edition from usb drive (did not realise you hit escape to boot from usb)
Install went great, no problems.  Root 10gb, swap 1gb, home rest of available space.
Then updated install & installed kubuntu-netbook & any updates.
After install Wifi did not work - as everyone knows.  Easily fixed - install the kernel-rc candidate kernel from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc7-lucid/")

Simply by clicking on the download in dolphin & using the package installer.

I did use the script alteration for for grub as described in this thread to allow the screen brightness to be more usable.

Installed other packages as required, inkscape, digikam, forefox, cairo-dock, etc.

Conclusion:
I have Kubuntu 64bit Lucid working with only one problem, video.  My vids play with audio only in dragon player but if I import to Kino they play with no problems.  Also the web cam in skype shows a blank screen although the camera led illuminates, tried with an external web cam that works fine on my desktop kubuntu with the same result, again the web cams both work in Kopete but it will not connect with Skype.
I have cairo working with desktop effects in compiz working, no problems at all & very smooth.  Looks great, everyone I show loves it. I put a cool desktop background & altered my colours to the dark theme - wonton I think.  Been playing so much & changing things to alter the look & feel.  But seriously - all works great, new kernel gave me wirless.

Good look & enjoy this great little netbook.

UPDATE:
Did an update from repos, all video inc Skype web cam now works great.
Also did not mention that suspend works but when resumed the login/lock screen only shows as a grey box.  Enter password and all is fine again.
Have also noticed that XP screen is much brighter than in Kubuntu.

---

### Post by welshmike on 2010-05-27
Anyone please?
> **welshmike said:**
> When I boot Express Gate and try to use Skype VOIP for the first time, e.g. clicking the Call Contact button of Echo / Sound Test Service, I get "Problem with Audio Playback".
If I then close Skype, the audio output (and input) works OK.
I looked at the Skype Options Sound Devices for the problematic first run and is showed hdmi for all of Sound In, Sound Out and Ringing. On the successful second run they showed HDA Intel (hw:Intel,0).
Please does anyone have any idea what is happening and how the problem can be corrected for the first run?

Mike

---

### Post by misGnomer on 2010-05-29
> **llenchikk said:**
> Hello!
I have Asus Eee PC 1001P. I upgrade bios from windowsXP. After that I install Ubuntu 10.04. Brightness control works good out of the box. WiFi doesn't. 

Here I first booted Lucid-Netbook image from SD-card, started Gparted and wiped off XP and its default partitions and recreated new partition layout:

sda1=16MB  (as EFI for BootBooster)
sda2=20GB  (/root system)
sda3=20GB  (for another distro, or for system backup until BTRFS)

Logical
sda5=4.2GB  (just over twice my 2GB RAM, for hibernation)
sda6=rest  (/home, multiple users)

Next I updated the BIOS by copying the latest BIOS file(s) to another SD-card (I renamed the file as "1P1103", just in case...) and let the built-in BIOS tool update the BIOS (IIRC it worked by pressing alt-F2 during system start). The version I used was v.1103, dated 12 May 2010.

As with llenchikk above, brightness controls work as expected, but the WIFI WLAN adapter wasn't recognized or the right module loaded. Until a fix is eventually (?) - hopefully for the 10.04.1 refresh already - there are basically two ways of getting WIFI to work:

1) installing a more recent 2.6.34.x kernel as mentioned in this thread (easier but perhaps riskier, as it involves unsupported test kernels), or

2) by building a newer ath9k WIFI module from compat-wireless sources (requires build-essentials package and simple compiling; must be redone every time when Ubuntu releases kernel updates - unless a new kernel includes a fix of course; )

I chose the latter method and WIFI works like a champ.


> Hotkeys Fn+VolumeUp and Fn+VolumeDown don't work. It concerns only me? It works for somebody?

Hardware volume controls work just fine here.

Headset sensing also works; when plugged in the netbook speakers switch off, and return when headset is unplugged.

Headset and mic combo works fine as well, in both recorder and Skype.

The current driver for the built-in mic is unfortunately half-baked and requires a klutzy fix by using PulseAudio Volume Control ("sudo apt-get install pavucontrol") and switching off one of the stereo channels. The result is noisy and barely useful audio input so getting an external mic or headset/mic is recommended at the moment.

Suspend (to RAM) works fine.

Hibernation works, I guess (or not). After selecting Hibernate from the menu the system churns for nearly a minute and goes into deep sleep. Pressing the power button, the system restarts by displaying BIOS messages (should it?) before soon resuming a totally blank screen which requires a touchpad or mouse action to display the log-in screen. After logging in the system does remember my last session and opens up where I left it.

Update: after resuming from hibernation it appears that X (windowing system) became flaky and the system went spontaneously into low-res mode. Selecting "restart X" from the given options resulted in the display of kernel boot messages and the system stuck at "Checking battery state..." stage. Pressing power button again at least powered down the system gracefully.


UNRESOLVED AND OFF-TOPIC ISSUES:

1) Touchpad multi-touch features. Do the older tips for pre-Lucid releases still work for two-finger scrolling etc.? Ubuntu's built-in "one-finger side-scrolling" works quite handily though.

2) Switching between CPU performance profiles or CPUFreq.

By default the top-left hardware button does nothing (i.e. no switching between power profiles). I wonder if the tips for Jaunty etc. still work under Lucid?

Nevertheless, when idle the system does at least go down to 1000Mhz.

3) Lucid Netbook-Edition issues with handling multiple users.

Possibly an issue with Netbook-Edition's package dependencies, but trying to follow the guide for "Sharing Folders" resulted in some authentication gremlins and apparently misconfigured SMB. FAIL.

Also, after switching user sessions the second user (whether admin or not) loses the network icon from the top panel, meaning he/she couldn't log in and out of networks. Switching back to the first logged-in user returns the network icon.

4) Netbook-Edition's top panel is too locked down. User can not add useful panel applets (such as the [improved battery status applet]("http://www.webupd8.org/2010/05/battery-status-01-released-improved.html")) without jumping through some humongous loops.

5) There is no consistent way to follow "Netbook-Edition" (specific version) discussions or bugs in the forum nor in LaunchPad...

Some of the last items are rather off topic from the installation issue at hand here, but where else am I supposed to put them...  ;)

---

### Post by TejasRider on 2010-05-29
> **n1ym said:**
> Thanks for this wonderful thread. I just got an EEEPC 1001P-PU17 for my daughter and wanted to get UNE 10.04 installed.

This is how I got the most important parts working:

Wireless: Updated the kernel to 2.6.34-22, and the wireless came right up and works wonderfully.
Brightness Control: As described in the thread changed the GRUB entry GRUB_CMDLINE_LINUX_DEFAULT to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux". Works well now.
Skype: Installed pavucontrol as described above and reduced one microphone channel to zero. Disabled the "Automatic Audio Volume Controls" in Skype and it works just fine.

A couple of things are left now. The camera works fine under Skype now, but for some reason the "Smile" program coming with the UNE will not work anymore. No big loss, though, as long as it functions with Skype I am fine.

The other thing is Bluetooth. Yes, the PU-17 model has bluetooth as well. The bluetooth module seems to work. I was able to mate my old JABRA 250 headset with the Netbook. However, it seems that Audio is not working propberly, i only hear static and scrambling. The microphone works, however. I will try later and see whether i have the same issues with other headsets, but if anybody has any idea what could cause the audio function to not work please let me know.

You all keep up the great work here, these threads are real lifelines for the folks like me with just limited experience.

W.

Update on the Bluetooth: It appears that the Jabra 250 is too old indeed and is not fully supported by the newer protocols. I tried again with a Jabra BT2080 and it worked wonderfully. Now I can use Skype with my Bluetooth Headset. Great.

I'm trying to get my daughter's 1001P working with 10.04 and am trying to sort out the various tweeks.  The most important right now is the wireless piece.  Specifically I think I want to go the 2.6.34-22 kernel route as mentioned above.  Can someone point me to the proper steps for doing this?

Thanks.

---

### Post by I_am_DLR on 2010-06-24
> **ironring1 said:**
> Adding acpi_osi=Linux to GRUB_CMDLINE_DEFAULT= line in /etc/default/grub followed by grub update gave me usable brightness controls, too. 

I'm resurrecting this thread, hope someone's paying attention. :)

I hope this isn't a stupid question, but I'm as new as you can get to using any flavor of linux. I installed 10.04 LTS a few days ago, and got wireless working via ndiswrapper. However, I'm still having problems with the display brightness.

I've tried the above quoted solution to no avail. When I update grub I get this spit out at me:

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-22-generic
Found kernel: /boot/vmlinuz-2.6.32-21-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Of course, I rebooted after updating, but still no change do the brightness controls. I don't know that that's any help to anyone, but I'm stumped. It seems to have worked for several other people in this thread. Any ideas as to what I'm doing wrong?

---

### Post by niteflier on 2010-07-03
@I_am_DLR: 10.04 uses grub2. Looks like you are trying "legacy grub" procedures?

I came back here to report satisfaction with the Jupiter utility on my machine.
[http://sourceforge.net/projects/jupiter/](http://sourceforge.net/projects/jupiter/)

It provides several nice features. Fn-Space cycles through power profiles. I mapped a keyboard shortcut to the touchpad on/off script. You can quickly change screen resolutions (some times 1024x768 is needed to reach a button on a properties page). Haven't found a need for rotating the display, but it works.

---

### Post by whit on 2010-07-19
> **I_am_DLR said:**
> I'm resurrecting this thread, hope someone's paying attention. :)

I hope this isn't a stupid question, but I'm as new as you can get to using any flavor of linux. I installed 10.04 LTS a few days ago, and got wireless working via ndiswrapper. However, I'm still having problems with the display brightness.

It just worked for me, on a fresh install of the Netbook remix (plus a custom compile of the 2.6.34.1 kernel to get the wireless going - yeah, it took hours to compile, but I like custom kernels). Anyway, in /etc/default/grub I edited GRUB_CMDLINE_LINUX_DEFAULT to be "quiet acpi_osi=Linux" (left out the splash screen just because I'd rather watch the messages) and then issued "update-grub", rebooted, and brightness adjustment is happy.

Still don't have multi-touch though. That's a bother. Even my old Eee 701 has multitouch working, for a center-click with two fingers anyway, which I use frequently. Annoying.

---

### Post by whit on 2010-07-19
> **niteflier said:**
> I came back here to report satisfaction with the Jupiter utility on my machine.
[http://sourceforge.net/projects/jupiter/](http://sourceforge.net/projects/jupiter/)

It provides several nice features. Fn-Space cycles through power profiles. I mapped a keyboard shortcut to the touchpad on/off script. You can quickly change screen resolutions (some times 1024x768 is needed to reach a button on a properties page). Haven't found a need for rotating the display, but it works.
Did you install 
jupiter-support-eee_0.0.12_all.deb or jupiter_0.0.36_all.deb? Or an older version of one or the other? Was there additional setup needed? Does it get two-finger stuff working on the touchpad? Thanks.

Update: I installed both, along with acpid and another dependency. The results: terrible! It screws with the screen resolution. Although you can cycle through the screen resolutions, for the "native" resolution of 1024x600 it squashes the screen - that is, it's conventing a 1024x768 screen into it, which makes everything fuzzy and the bars top and bottom barely readable (standard Gnome display - the Netbook Remix is not my idea of functional design). That can be fixed by turning off acpid - but then the cursor is broken. Although strangely, plugging in a USB mouse both worked, and restored the trackpad.

It can be removed with dpkg --purge for first the eee deb, then the main jupiter one. A manual rm -r /usr/lib/jupiter is also required (as root or sudo). After doing that, I found on next startup I also had to purge the acpid stuff, or else it was blocking wireless from working properly.

---

### Post by misGnomer on 2010-08-25
Just a brief public service message.

There is another [BIOS update]("http://support.asus.com/download/download.aspx?model=EEE+PC+1001P") available for 1001P/1005P:

BIOS 1202
Update EC firmware
File Size 	418.78 (KBytes)
2010/08/04 update

I don't know what it might fix (or break) as I've no known issues with the previous version 1103, but *sometimes* it may be beneficial to update to the latest version prior to installing.

The [ASUS BIOS can update itself]("http://vip.asus.com/forum/view.aspx?id=20100601113805984&board_id=20&model=Eee+PC+1001P&page=1&SLanguage=en-us") by loading the files (which I rename to shortened names such as "1P1103.ROM" etc.) from an SD card so have a couple of BIOS versions handy just in case.

---

### Post by CaptSaltyJack on 2010-08-25
How does one update the BIOS for the 1001P that's running Linux?

---

### Post by misGnomer on 2010-08-26
IIRC the advice in Asus forum (second link in my previous post) ought to work just fine.

Here's what I'd do:

1) First restart system, press F2 to go into BIOS Setup and make sure that Boot Booster (under Boot menu) and Quiet Boot (under Boot - > Boot Settings Configuration) are both disabled, just in case. While there check your current BIOS version (under Main).

**2)** Have a standard FAT-formatted SD card handy (I use an old 512MB card with misc Asus related files, manuals and a few BIOS versions on it) and copy the downloaded and extracted ROM file (e.g. *1005P-ASUS-1202.ROM*") to it - root directory if there are folders) and rename the ROM file to **1005P.ROM**.

**3)** Restart the 1001P/1005P with the SD card in the slot and **press ALT-F2** to invoke the built-in BIOS update utility.

The BIOS utility automatically searches the card for a file named 1005P.ROM, churns for some 20 seconds and asks you to switch off power. That was it.

4) Restart, press F2 and confirm new BIOS version.

The update also turns Boot Booster and Quick Boot back on so if you're next going to proceed with partitioning you should turn them off for the moment. In the early days those settings may also have interfered with some of the hardware (Fn) key functions but brightness and sound Fn-keys work fine now.

Fn-WIFI key still toggles wired ethernet connection on/off though...

Steps 2 and 3 (FAT-formatted SD card with ROM file renamed 1005P.ROM and restart system with ALT-F2) are the short, sharp and simple of it. This 1001P has never seen an MS logo, apart from the sticker which I stuck on a metallic garbage bin (above the foot pedal) the first thing...  ;)

---

### Post by simonjo on 2010-08-29
> **misGnomer said:**
> IIRC the advice in Asus forum (second link in my previous post) ought to work just fine.

Here's what I'd do:

1) First restart system, press F2 to go into BIOS Setup and make sure that Boot Booster (under Boot menu) and Quiet Boot (under Boot - > Boot Settings Configuration) are both disabled, just in case. While there check your current BIOS version (under Main).

**2)** Have a standard FAT-formatted SD card handy (I use an old 512MB card with misc Asus related files, manuals and a few BIOS versions on it) and copy the downloaded and extracted ROM file (e.g. *1005P-ASUS-1202.ROM*") to it - root directory if there are folders) and rename the ROM file to **1005P.ROM**.

**3)** Restart the 1001P/1005P with the SD card in the slot and **press ALT-F2** to invoke the built-in BIOS update utility.

The BIOS utility automatically searches the card for a file named 1005P.ROM, churns for some 20 seconds and asks you to switch off power. That was it.

4) Restart, press F2 and confirm new BIOS version.

The update also turns Boot Booster and Quick Boot back on so if you're next going to proceed with partitioning you should turn them off for the moment. In the early days those settings may also have interfered with some of the hardware (Fn) key functions but brightness and sound Fn-keys work fine now.

Fn-WIFI key still toggles wired ethernet connection on/off though...

Steps 2 and 3 (FAT-formatted SD card with ROM file renamed 1005P.ROM and restart system with ALT-F2) are the short, sharp and simple of it. This 1001P has never seen an MS logo, apart from the sticker which I stuck on a metallic garbage bin (above the foot pedal) the first thing...  ;)

I tried this to my Asus eee 1001PX, but at step 3 the bios update won't stop programming. "Start Programming. . ./" has been promted for about half an hour now. Can anyone please tell me what to do?

Edit: After one hour nothing happed, so I took out the battery and plugged in a memory stick with the BIOS version that was installed from the beginning. Now everything works fine, but I still have the same BIOS as I started with.

---

### Post by misGnomer on 2010-08-31
simonjo, the 1001**PX** is actually internally different model from the 1001**P**/1005P and shares BIOS version with 1001PX/R101/1005PX/R105. Considering that the R10*x* models came earlier the name of the .ROM file the BIOS (or the built-in EZ Flash utility) is searching for is very possibly different from *1005P.ROM* used for the 1001P/1005P models.

Did the update utility tell you what ROM file it was looking for? (e.g. "searching for xxxxx.ROM")

If you were using a standard unpartitioned FAT16-formatted SD card I'd guess that there was a problem with the ROM filename.

The 1001P/1005P ROMs are originally named in the format *1005P*-ASUS-1202.zip/ROM (becoming *1005P.ROM* after unzipping and renaming) and apparently for the 1001PX in the format *1001PX*-ASUS-0802.zip/ROM. Maybe you could try renaming the ROM as 1001PX.ROM and hope for the best. Or ask the hapless Asus tech support a pointed question. :-\"


Btw. I've also seen it mentioned that the power adaptor needs to be plugged in during BIOS flashing...

---

### Post by niteflier on 2010-08-31
> **whit said:**
> Did you install 
jupiter-support-eee_0.0.12_all.deb or jupiter_0.0.36_all.deb? Or an older version of one or the other? Was there additional setup needed? Does it get two-finger stuff working on the touchpad? Thanks.

This reply is probably way too late, but still.. my Jupiter version is 0.0.35, jupiter-support-eee version 0.0.11.

I did not do any additional configuration. No two-finger scroll (I have tried it and don't like it). My screen normally runs at 1024x600 and looks good. Very rarely do I run into a need for 1024x768, but there are times when a dialog box is taller than 600, making a button on the bottom inaccessible. Forcing the higher res allows me to see/click it.

---

### Post by HonzaPokorny on 2010-09-21
> **Fwertz said:**
> Alright, got a fix for the headphone sense. I spent most of the night trying to work the kinks out and after much trial and error this snippet seemed to work.

First at a shell do ```
aplay -l
```

If you're like me and have an intel HDA card,

Append the following to **/etc/modprobe.d/alsa-base.conf** ```
options snd-hda-intel model=auto position_fix=1
```

/reboot

Unfortunately, this didn't work for me. I'm running UNR 10.04.

I have tried

```

snd-hda-intel model=lifebook
snd-hda-intel model=fujitsu
snd-hda-intel model=auto

```

Nothing worked. I can only get mic+speakers, or headphones. But not the two together. 

I tried the fix at the end of [this post]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183"), but it didn't work either.


Ideas what to try next?

---

### Post by welshmike on 2010-09-23
> **niteflier said:**
> 
I came back here to report satisfaction with the Jupiter utility on my machine.
[http://sourceforge.net/projects/jupiter/](http://sourceforge.net/projects/jupiter/)

It provides several nice features. Fn-Space cycles through power profiles. **I mapped a keyboard shortcut to the touchpad on/off script**. You can quickly change screen resolutions (some times 1024x768 is needed to reach a button on a properties page). Haven't found a need for rotating the display, but it works.

Please will you let me know how you mapped a keyboard shortcut to the touchpad on/off script and also what the script is and where it should be saved?

---

### Post by bj20017 on 2010-10-03
I'm trying to work out whether to install Ubuntu on my 1001p - it came with win7, which I'm not enjoying very much at all.
Sorry if I'm asking this in the wrong place, but the people in this thread seem to be the absolute right people to ask - how does ubuntu affect the battery life in these machines, as opposed to win7 starter? after whatever tweaks need to be made get made. If it's a good ratio, then hopefully I'll be alright following all the detailed instructions in this thread to get everything going! :) Thanks for this thread.

---

### Post by welshmike on 2010-10-03
This is probably the right place to ask. It is a very informative thread and thanks to CaptSaltyJack for starting it.
My 1001p came with XP. It was easy to install Ubuntu 10.04 dual boot.
In my experience with Ubuntu 9.10, and maybe earlier on my old Toshiba laptop, was that the fan runs less often and more slowly and the CPU works less hard on Ubuntu than XP. So I would expect a fully charged battery to take longer to discharge when running Ubuntu vs XP. I would also expect Win7 to be no less demanding of a CPU than XP.

---

### Post by niteflier on 2010-10-19
> **welshmike said:**
> Please will you let me know how you mapped a keyboard shortcut to the touchpad on/off script and also what the script is and where it should be saved?

System > Preferences > Keyboard Shortcuts > Add
Script: sudo /usr/lib/jupiter/scripts/touchpad 

I can't remember if I manually added this line or if the script did it, but visudo shows this line:
```
%jupiter ALL=NOPASSWD: /usr/lib/jupiter/scripts/bluetooth, /usr/lib/jupiter/scripts/camera, /usr/lib/jupiter/scripts/cpu-$
```

---

### Post by sej7278 on 2010-11-29
sorry if the answer is already in this thread, but i read a few pages and didn't find the answer....

anyway, what i want to know is what can safely be done with the partitions.

from what i've heard if you want to do a system restore by pressing f9 or if you want to use boot-booster or express-gate, you have to be very careful about what partitions you remove/resize.

when my 1001p turns up first thing i'm going to do before booting winxp is clonezilla it, so if anything goes wrong i've got my disk image anyway.

i don't mind nuking the winxp partition if updates can be done fine from linux - i know bios upgrades can be done by booting from sdhc/usb, but are there any other things that can only be upgraded from windows (express gate or chipset/wifi firmware maybe?)

ideally i'd like to dual boot linux and macosx.

from some other website it seems the disk layout is like this (my theories in brackets):
```

Pri _  1,023       Unused          (?)
Pri 1  83,885,056  NTFS            (windows c:)
Pri 2  61,898,752  NTFS            (windows d:)
Pri 3  10,485,760  Hidden Fat-32   (f9 restore or express gate?)
Pri 4  17,760      Unknown (0xEF)  (efi boot booster?)
Pri _  2,551       Unused          (?)
```

can anyone confirm what the partitions are for, and which ones are safe to nuke?

---

### Post by welshmike on 2010-11-30
My message 88 in this thread may help.

---

### Post by sej7278 on 2010-11-30
> **welshmike said:**
> My message 88 in this thread may help.

so looking at this, as long as you don't touch the fat32 partition, expressgate will still work:

[http://ubuntuforums.org/showpost.php?p=9152984&postcount=88](http://ubuntuforums.org/showpost.php?p=9152984&postcount=88)

has anyone tried installing linux into the c:\ partition instead of windows, and seeing if f9-restore still works? does restore completely reinstall windows, or does it just reset the existing windows install?

i had heard something about express-gate not working if you format c:\ and f9-restore not working if you deleted d:\

well i guess i'll find out when i try it, i suspect i'll put linux and macosx in c:\ and d:\, possibly merge the recovery partition into d:\ and leave the efi partition alone.

---

### Post by ahab_orr on 2010-12-15
Hello This in my first post on this forum.
Just wanted to say that I installed 10.10 yesterday and WiFi works out of the box - some problems with screen brightness - no biggie. My 1001p came with win7 - ubuntu is much much faster - the computer seems much more responsive, loading of documents is much faster - everything up to the point that I wonder why did Asus install Win7 on such an underfed computer - ubuntu gives a much better user experience.
The only issue was that my computer came with four primary partitions - one for Win7, one for D: drive, one for sytem restore and one for asus own system. So I had to remove my data from D: drive, reformat and install ubuntu there. Thanks to this thread I finally took the plunge (didnt want to screw up my new toy), and I am loving it. Still keeping Win7 though - at least until I figure out how to get some GPS ubuntu software. Thanks to everybody contributing to this thread - you rock.

---

### Post by welshmike on 2010-12-15
> **ahab_orr said:**
> ...
The contributors to this thread have been immensely helpful.
See my message 88 for the partioning of my 1001P.
My 1001P came from Amazon.co.uk for £229 with XP installed.
My neighbour bought his yesterday for £212 from [https://www.simplyasus.com/ASUS_EEE_PC_1001P_738269.html](https://www.simplyasus.com/ASUS_EEE_PC_1001P_738269.html) . It came with XP set up for non-UK language and keyboard. So it was possibly part of a large import order.

Perhaps Microsoft's dominance in PC operating systems requires ASUS to provide MS Windows XP or 7. With Microsoft's marketing of W7, that's what one will get.

I didn't want to pay for yet another MS Windows CD and licences so when I bought a new laptop I got an XP/Vist/W7 free MSi CR620 (aka Novatech i3) from Novatech.co.uk .

---

### Post by guwrt on 2010-12-25
Hello everybody,

Need help to solve my problem with my netbook 1001P. If my laptop go in sleep mode (FN+1) and after a while I get my laptop out of sleep mode, It cannot connect to my router. My laptop seem to search for an address from my router but it does not connect to it. But my laptop can see the wireless network. 
If I turn off and on the antenna (FN+2), the connection with the network work ok. Also, when I boot my laptop, everything works fine.

Ubuntu 9.10 32 bits in dual boot with Win xp

Thanks for your support

Andre

---

### Post by sej7278 on 2010-12-27
when running XP has anyone else seen the screen going blue/white when you switch to SHE auto or power saving mode?

i only get a display in high/super performance mode on my brand new 1001p.

note its not a BSOD, its just like its turned on some sort of screensaver.

---

