---
title: "Acer Aspire 3680 - Edgy Install Guide"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by Hase on 2007-03-24
**Acer Aspire 3680-2022**
Intel® Celeron® M Processor 430
512MB PC4200 DDR2 RAM
Combo 8x DVD-ROM; 24x24x24 CD-RW
80GB 4,200RPM Ultra ATA Hard Drive
14.1" WXGA CrystalBrite, 1280 x 800 at 24-bit
Intel® Graphics Media Accelerator 950 Video Chipset
Acer InviLink 802.11b/g Wi-Fi CERTIFIED Wireless Network

**Ubuntu 6.10 Edgy Eft**

**Wireless** - Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
I was pleasantly surprised to find that such a cheap system would be sporting an Atheros wireless chipset and that it worked perfectly after install.  Additionally, I was even more pleased to see that it was an 802.11a/b/g chipset, not just b/g as advertised.  I have also noticed that the WiFi switch on the front of the machine *does* actually work despite the fact that the light does not come on or go off.  If anyone has a fix for that, please let me know.  I was pleased to find wpa_supplicant installed by default in Edgy.  This meant all I had to do to get it working was  create /etc/wpa_supplicant.conf and re-write /etc/network/interfaces.  Examples to follow.  My configuration uses the interface file to defer to the settings in wpa_supplicant.conf, which in my opinion offers far more and more powerful options to automate login with WPA, WEP and unprotected networks.  Ask if you have any config questions.

/etc/wpa_supplicant.conf
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1

network={
	ssid="home_network"
	psk=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
	key_mgmt=WPA-PSK
	proto=WPA
	priority=5
}

network={
	ssid="friends_network"
	key_mgmt=NONE
	wep_key0=XXXXXXXXXXXXXXXXXXXXXXXXXXX
	wep_tx_keyidx=0
	priority=4
}

network={
	ssid=""
	key_mgmt=NONE
	priority=2
}
```

/etc/network/interfaces
```
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
pre-up wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

**Video** - Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
Default drivers work perfectly, except for resolution.  See next.

**Display** -  14.1" WXGA 1280 x 800 at 24-bit
The default install left the display a little weird so I apt-got (apt-getted?) “915resolution”.  I then configured it to use the appropriate resolution at the correct color depth.  I've seen where others have had to do other stuff to get it to stick after reboot but I haven't needed to.  The following two commands worked all by themselves.

```
sudo apt-get install 915resolution
sudo 915resolution 3c 1280 800 24
```

**Sound** - Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
The sound was muted by default.  You have to activate the “surround” slider (From the volume control GUI, edit > preferences > check “Surround”), un-mute it and adjust it.  Sound! (Though still not as loud as I'd like, it is acceptably audible.)  Initially I tried new drivers as suggested in the forthcoming link, then tried the "surround" unmute.  AlexTheMad helped isolate the fix as only needing the "surround" unmuted.  (Thanks for the help, AlexTheMad!)
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
A kernel and header update broke my audio.  The following instructions reinstalled the appropriate drivers and got me noisy again.
[Drivers]("http://www.alsa-project.org/alsa/ftp/driver/")
[Library]("http://www.alsa-project.org/alsa/ftp/lib/")
[Utils]("http://www.alsa-project.org/alsa/ftp/utils/")

```
sudo apt-get install build-essential ncurses-dev
sudo apt-get install linux-headers-`uname -r`
```
```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp /*whereveryouputthedownloads*/* .
sudo tar xjf alsa-driver-1.0.14rc3.tar.bz2
sudo tar xjf alsa-lib-1.0.14rc3.tar.bz2
sudo tar xjf alsa-utils-1.0.14rc2.tar.bz2
```
```
cd alsa-driver-1.0.14rc3
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
```
```
cd ../alsa-lib-1.0.14rc3
sudo ./configure
sudo make
sudo make install
```
```
cd ../alsa-utils-1.0.14rc2
sudo ./configure
sudo make
sudo make install
```


**Multimedia**
In order to get Totem to play all my favorite Divx .avi files, as well as getting them to show up as thumbnail frames from the video, I followed the instructions [here]("https://help.ubuntu.com/community/RestrictedFormats") (Restricted Formats) and then [here]("https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs") (Windows Codecs).  If your movies still don't become thumbnails, clear out "/home/[username]/.thumbnails/fail/gnome-thumbnail-factory/".  When Gnome tries and can't make a thumbnail, it notes it there and never tries again.  Emptying that directory will make it retry all the failed files.

```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
```

```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
sudo dpkg -i w32codecs_20061022-0.0_i386.deb
```

**Flash**
```
sudo apt-get install flashplugin-nonfree
```

**ACPI**
Works straight out of the box (Thanks Mugster!).  I thought I'd see if the Acer ACPI package added functionality or improved anything and it does not appear to do anything other than waste your time installing it.

---

### Post by javatoast on 2007-03-30
Great how-to. This solved my problem with the resolution after days of searching... Question for you. On the Acer Aspire 3680, how do I get the system to recognize an external monitor. Specifically, how can I make it automatically adjust the resolution correctly?

Thanks

---

### Post by Hase on 2007-03-30
I've not yet tried that function. When I get home I'll tackle it.  If you get that running, post the solution here or send it to me so that I can add it to the tutorial.  It'd be great if we can get all the relevant info assembled here.
Stuff I'm still looking for and will add when the opportunity presents itself:
[B]Better keyboard setup
Bluetooth setup
Four-way scroll button below touchpad setup[/B]
(By the way, I'll be sure to credit anyone for their submissions and help!)

---

### Post by AlexTheMad on 2007-04-07
> **Hase said:**
> **Acer Aspire 3680-2022**
I may not have needed to install the new drivers so, try the “Surround” slider thing first, then let me know.


I just did this without installing any new drivers and it worked. What bugs me though is that when I plug in headphones the PC speakers still sings. I have to mute "Surround" every time I use headphones.

---

### Post by Hase on 2007-04-07
> **AlexTheMad said:**
> What bugs me though is that when I plug in headphones the PC speakers still sings. I have to mute "Surround" every time I use headphones.
I have noticed this on two other laptops I've owned (IBM and HP).  I've never come across a fix for this though.  Thanks for the answer about the drivers!

---

### Post by Hase on 2007-04-11
How-To revised to reflect remedial steps taken after an update to headers broke the sound.

---

### Post by Mugster on 2007-04-14
First of all, extremely nice guide, and the only one i could find on the web for this model laptop. I took the $399 deal...

I'd advise not using the acer acpi, as it was originally coded to get the wireless going on a 64 bit OS, and is evidently no longer maintained. All the power management stuff works out of the box, at least on fc6 (same kernel). These celeron M chips do not implement speedstep anyway from what i can tell. 

I left a little room on my hd to install edgy and give it a go. Mebbe i'll be a new convert :)

Keep up the good work!

---

### Post by pavelchjen on 2007-05-14
Nice. What BIOS version do you have? I find in store same model ACER laptop. but it have preinstalled windows vista, don't know will it have troubles with booting.. (cause of "bios vista oriented" problem")

---

### Post by Hase on 2007-05-14
Mine did come loaded with Vista as well. I don't have the unit with me right now but when I get it I will find out the specific information for you!

---

### Post by pavelchjen on 2007-05-16
does your laptop have a Windows Vista BASIC label ?

---

### Post by mrojas73 on 2007-05-16
I have an Acer Aspire and eventhough mine use the 950GMA card I think that the driver is the same for the 945.  I may be wrong though.  But here is what I would do before trying 915 resolution which I used for a long time but then realized that I was using the wrong driver.

Try this first and if it doesn't work, go back with the original driver and try 915 resolution.

In Synaptic search for Intel, go to the bottom of the page and install xserver-xorg-video-intel.  It will promt you to uninstall the i810 driver, accept it and when you are done installing it reboot the computer.

You should be able to change your resolution after you restart.

---

### Post by Hase on 2007-05-18
Sorry for the delay, I just moved and started a new job.  Pretty chaotic.
Yes, it has a Windows Vista Basic sticker on the left palm rest under the Intel Celeron M sticker.

---

### Post by mrojas73 on 2007-05-19
> **Hase said:**
> Sorry for the delay, I just moved and started a new job.  Pretty chaotic.
Yes, it has a Windows Vista Basic sticker on the left palm rest under the Intel Celeron M sticker.

I was in the same situation 6 weeks ago!

---

### Post by n8bounds on 2007-06-16
Thanks for all your notes, they helped me a lot!

---

### Post by Hase on 2007-06-22
Glad to have been a help!  If you think you might have anything to contribute, we'd love it!

---

### Post by DarkStarAeon on 2007-06-23
Dude, thank you SO much for your guide here! :D

Don't get me wrong, I've installed Ubuntu on dozens of machines, but your shortcuts saved me so much time, which is quite simply awesome.

Fortunately Feisty seems to have taken care of a few issues itself, but I'd have been lost a few times without your step by step here.

Thanks again!

---

### Post by DarkStarAeon on 2007-06-23
Note for anyone else this may matter to:

I wanted to use my Logitech headset/mic so I could use Gizmo on my laptop and make phone calls.
I plugged in the mic and headphone plugs into the jacks on the front of the laptop and got nada.

I went into the sound mixer/volume control, and hit edit > preferences then selected the mic, front mic, capture, capture, mic boost, etc. and unmuted them and adjusted the levels. I then opened Audacity, hit record, and sure enough they work.

I know it all seems very obvious, but just in case someone missed those details, that's how you get it to work. ;)

---

### Post by cvcuse on 2007-07-16
> **DarkStarAeon said:**
> Dude, thank you SO much for your guide here! :D

Don't get me wrong, I've installed Ubuntu on dozens of machines, but your shortcuts saved me so much time, which is quite simply awesome.

Fortunately Feisty seems to have taken care of a few issues itself, but I'd have been lost a few times without your step by step here.

Thanks again!

Hello....considering 3680, will I be able to pull off dual boot of 'feisty fawn' from live cd.......also your thoughts concerning laptop.
thanks

---

### Post by Hase on 2007-07-18
I love the laptop, especially for the price.  I am quite happy running Ubuntu with Beryl on it though when I run VMs on it, I wish I had more than the half-gig of ram.  Other than that, it does everything I need it to do, well and at a very reasonable price.

As for the dual boot, I'm not sure, it's not something I've ever done.

---

### Post by Siph0n on 2007-07-18
Im getting this laptop on my way home from work today! This guide will really help me, thanx!!! :) Circuit City has it for $450, with an $80 mail in rebate = $370 ....

---

### Post by Siph0n on 2007-07-19
lol of course I get this Acer Aspire 3680 and it has the Broadcom chipset, and not the atheros :(

---

### Post by tdrusk on 2007-08-06
does anyone have a guide for the wireless?

---

### Post by nezumish on 2008-02-24
Thanks for posting this. I have hated my acer aspire 3680 ever since I got it. I was easily able to install Ubuntu on it and now I do not hate my laptop lol.... However, I am having some trouble getting the wireless to work but I am sure I will figure it out soon.

---

### Post by mi_were on 2008-02-28
don't hate on this spunky laptop! I love the damn thing, I bought it for my wife as a gift and kind of never got to gifting it once I got Ubuntu installed.

The only problem I have is that the external speaks don't work yet! Everything else is working perfectly in Ubuntu 7.10.

> **nezumish said:**
> Thanks for posting this. I have hated my acer aspire 3680 ever since I got it. I was easily able to install Ubuntu on it and now I do not hate my laptop lol.... However, I am having some trouble getting the wireless to work but I am sure I will figure it out soon.

---

### Post by Hase on 2008-03-04
Glad to help all.  I don't have the laptop anymore but will still help out any way I can!

---

### Post by georgeguitar on 2008-05-11
It's a very good tutorial, I used it since I bought my laptop.

It just needs the part of how to enable the CPU frequency scaling.

To enable the frequency scaling just follow the instructions from this page:

HowTo: Configure Cpu Frequency Scaling for Celeron M's with Control of the Governors
[http://ubuntuforums.org/showthread.php?t=582069]("http://ubuntuforums.org/showthread.php?t=582069")

And if you need a more visual tool to set the frequency, follow the instructions from this page:

Howto Change CPU Frequency Scaling in Ubuntu
[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html]("http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html")

Enjoy your laptop and Ubuntu, it works really good.

---

### Post by georgeguitar on 2008-05-11
It's a very good tutorial, I used it since I bought my laptop.

It just needs the part of how to enable the CPU frequency scaling.

To enable the frequency scaling just follow the instructions from this page:

HowTo: Configure Cpu Frequency Scaling for Celeron M's with Control of the Governors
[http://ubuntuforums.org/showthread.php?t=582069]("http://ubuntuforums.org/showthread.php?t=582069")

And if you need a more visual tool to set the frequency, follow the instructions from this page:

Howto Change CPU Frequency Scaling in Ubuntu
[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html]("http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html")

Enjoy your laptop and Ubuntu, it really works!

---

