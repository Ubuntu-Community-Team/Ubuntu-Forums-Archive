---
title: "Brand new laptop + UBUNTU (feisty) = NO SOUND? (please help me!)"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by matheuu on 2007-05-10
That says it all!

Ok then, its a Toshiba Satellite A200, It did have sound when Vista was on it. All the volumes are turned up and I played with the sound prefs in preferences.

My Desktop also has a sound problem and a wireless problem... 

Any ideas?

Cheers
Mat

---

### Post by Monstroxus on 2007-05-10
Same happened with me.. but a different brand though.. (now everything is working, sound and wireless) I just want to let you know that there is no need to worry, sooner or later there will be a fix. Just keep in searching and a solution will present itself... btw. did you try Ndiswrapper?

---

### Post by Monstroxus on 2007-05-10
another thing you can try first is to install an Alsa GUI... there is one in synaptic as well. After installing run it and check if the volume is not muted. Since sometimes the volume is muted. Even though the regular sound settings are looking fine.

---

### Post by matheuu on 2007-05-10
Thanks mate,
Hacking away at the moment, will try the GUI see if that helps. I am trying to see if the install has found the sound card
cheers
Mat

---

### Post by fuzzyBSc on 2007-05-19
matheuu...

I have recently purchased a similar (identical?) model, the A200/L01 from my local Dick Smith (tricky dickie). I have a similar problem with the sound. My card is detected and the volume controls apparently work, but no sound. Perhaps there is some kind of initialisation problem specific to this line of machines.

On the network front, I originally thought I had a problem. However, I found that the wireless network is actually working on mine. I just had to make sure that the network kill switch wasn't on. On my machine the wireless card is located between the blue Satellite leds and main power and other leds on the left-hand side of the front of the machine. When wireless is active I see a green led under the machine. I haven't actually used it to log onto any networks, but once enabled network manager shows me a range of secured and unsecured networks around my aparment.

I have started looking into getting the fingerprint scanner on this machine working. If I have any success I'll let you know.

Benjamin.

---

### Post by matheuu on 2007-05-19
Hi Benjamin,

Found that Switch! Cheers.

I bought this A200 from Dick Smith (very tricky) as well. Its the cheapest one they sell. It was meant to be a work computer took it home and tried loading up Ubuntu accidentally wiped Vista totally off the Hard drive. 
Man! No way to get it back without buying a new copy of vista...unfortunately I need windows to run this bloody bigpond next-g crap. 
So I bought another laptop for work that doesn't have Ubuntu on it, Vista only (still won't hook up to the telstra network)

Got this Ubuntu Laptop Working great now...except for the sound! AHHHHrgggg. 
Been a over a week now... getting really painful.

Tried a whole heap of "fixes" nothing. Have had to reinstall Feisty about 5 times so far because I stuffed something up while attempting a fix.

Not giving up!
Will put anything up I find, Its kind of good to know someone else has the same dilemma.... If you know what I mean. 

Cheers! Here's to music and movies again!

Mat

---

### Post by tormentum on 2007-05-20
Hi Mat,

Welcome to the world of Ubuntu :)

The problem with really new hardware is that it's not always instantly supported and can sometimes take a few releases to get supported.  The first thing to do would be to find out what kind of soundcard you have and see if it's supported.  Can you post the output from the following command here for us?  It will give us a summary of your laptop's hardware.

```
sudo lspci
```

Good luck!

---

### Post by matheuu on 2007-05-20
HI Mate.

here goes:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4353 (rev 14)
03:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller


Hope this helps

---

### Post by fuzzyBSc on 2007-05-21
My audio looks identical. I guess we don't have exactly the same model of laptop, though. Here is my diff against matheuu's lspci:

18c18
< 03:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
---
> 03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
20a21,22
> 07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
> 07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

This might explain my network card working, while you have had some issues.

I reported my setup through the ubuntu device database. Is this the equivalent of a bug-tracking tool, or would another channel be more likely to see development activity?

Benjamin

---

### Post by luctor on 2007-05-21
please post the output of
```

cat /proc/asound/cards

```

---

### Post by matheuu on 2007-05-21
There you go.
By the way, the laptop wireless is running fine(once I switched it on-cheers Ben). although one of the fixes killed it (modprobe.d auto ).   
But Feisty did kill the sound on the Desk top, I think that one's going back to Edgy.

Here is Mats Output:
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0b40000 irq 21

Cheers
Mat

---

### Post by luctor on 2007-05-22
try this :
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

it looks like hda-intel has some problems, a lot of posts in the forum with "no sound" seem to have to do with the hda-intel module.

---

### Post by blop on 2007-05-23
that did not work for me although it has no provided a driver for my sound card.....so it shows up in aplay -l. But still no sound


as there is alot of issues with HDA-INTEL can we report it.....will it fixed?

---

### Post by luctor on 2007-05-23
I think it's already being worked on.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92825](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92825)

---

### Post by blop on 2007-05-23
ace, how will i know when it is resolved will there be a system update via the auto ubuntu update thingy?

---

### Post by luctor on 2007-05-24
bug 92825 refers to 94373 ...
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94373](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94373)

says fix commited but not released yet.

---

### Post by fuzzyBSc on 2007-05-25
Here is another data point for the experts:

I was playing around with loading and unloading the snd-hda-intel kernel module with various settings in alsa-base. I haven't gotten any sound out, but the following message is displayed on the prompt on module load:

si3054: cannot initialize. EXT MID = 0000

dmesg has some additional output each time the module is loaded:
[ 3715.184000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[ 3716.656000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[ 3716.660000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[ 3717.980000] si3054: cannot initialize. EXT MID = 0000

Benjamin.

---

### Post by kevinfishburne on 2007-06-01
I have the same problem as the other two and the same Intel card. Here's the results of the above:

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdc440000 irq 21

My laptop is also a Toshiba.

[edit]

Ignore that, somehow this was posted to the wrong thread after i registered.

---

### Post by kuscsik on 2007-06-03
Hi,

The problem was same with my Toshiba Satellite A200-10W.
The audio device:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

doesn't work under feisty. I tried to recompile the latest alsa drivers, without success.
Upgrading  feisty to  Gutsy solved my problem. Nevertheless, firefox at now very unstable in the gutsy respository, but I am sure, this will be solved in few days or hours.
The sound is O.K.  Sometimes, the card is muted without reason. In this case try to restart the alsa server.

For the  4965AGN intel wireless card I compiled the latest ndiswrapper 1.45. Its web site: [http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

While the hardware is recognized properly by using the XP drivers, ndiswrapper doesn't seems to be stable with this driver. 
Turning OFF physically the device before Start and Halt partially solved the problem.

---

### Post by blop on 2007-06-03
also need help with sound on a p200 toshiba...

i got sent this link by a forum user....has not helped me as im to noob to get the commands to work...

[http://linux.dobeyracing.net/how_to/toshiba_p200_laptop/Linux_on_Toshiba_Satellite_P200.php](http://linux.dobeyracing.net/how_to/toshiba_p200_laptop/Linux_on_Toshiba_Satellite_P200.php)

---

### Post by kuscsik on 2007-06-03
Hi,

it seems that it is the same problem. You can try to update your system to gutsy, but be carefull: gutsy is the development version of ubuntu and some things may be temporary broken.
You can upgrade your system by editing
 
```
gksudo gedit /etc/apt/sources.list
```

and replacing every feisty word to gutsy inside. The last steps are the update and dist-upgrade

```
sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by sprint4 on 2007-06-03
blop

Is this just a sound issue?

I wrote the "How-To" you got sent, and it's open for improvements...  ;-)

What commands wouldn't work?

---

### Post by kuscsik on 2007-06-03
I was searching on forums. Some sites reported that the audio card (82801G) has a problem with alsa 1.0.13 included in feisty and  also in gutsy.  Interestingly, after the update to Gutsy the sound card was ok, even if I run Gutsy with the old feisty kernel (2.6.20). 

Wireless card:
Few days ago come out the new release of  Ndiswrapper. The card is identified, but if it is enabled  some kernel process consumes the 30% of CPU. 

I read your How-To and I have one more comment, the Chicony cam included in my Toshiba works well with ekiga and linphone (using the v4l2 driver). I have no success to capture video with dvr and mplayer.

---

### Post by blop on 2007-06-03
Sprint4:

Hi, thanks for spending the time posting how you got the p200 working with Debian hope it helps with Ubuntu...

Well like your setup with Debian i dont have the 5-1 card reader / camera / sound working. As far as i know everything else is ok.

Where 'the how to' did not work for me was in the section SOUND - INTEL HD AUDIO / ALSA

second command:

rsync -avz --delete --exclude=.hg* rsync://alsa.alsa-project.org/hg alsa

gives me no output :(

i think that its to do with getting the actual drivers?

---

### Post by sprint4 on 2007-06-03
blop - 
Yep, you're right.  rsync will copy the source tree from the server to your laptop.  But it sounds like you might not have it installed.

First, let's see if you have rsync installed.

```
$ rsync --version
rsync  version 2.6.9  protocol version 29
Copyright (C) 1996-2006 by Andrew Tridgell, Wayne Davison, and others.
<http://rsync.samba.org/>
Capabilities: 64-bit files, socketpairs, hard links, symlinks,
              batchfiles, inplace, IPv6, ACLs,
              64-bit system inums, 64-bit internal inums

rsync comes with ABSOLUTELY NO WARRANTY.  This is free software, and you
are welcome to redistribute it under certain conditions.  See the GNU
General Public Licence for details.
```

If you don't see a version, try running these commands.  It updates your package list, and installs rsync, and some other sound libraries.  

```
# apt-get update
# apt-get install subversion rsync libtool autoconf jackd pkg-config libsndfile1 libsndfile1-dev \ 
  mffm-libsndfilew-dev sndfile-programs libjackasyn-dev libjack-dev libjack0.100.0-dev pkg-config \
  libusb-0.1-4 libusb-dev libasound2 libasound2-dev
```

kuscsik - 
I took another stab at the camera using the apps you noted, but still no love.  I still can't seem to get Ekiga to recognize my camera with v4l...  Could it be that I'm missing a step?  Did you have to do anything special to configure v4l to recognize the camera?

---

### Post by kuscsik on 2007-06-04
Hi Sprint4,

the camera works only with the v4l2 driver. With the optional v4l  in ekiga I had no success. Try to switch in ekiga preferences the plugin v4l to v4l2.
By **lsusb** command my camera device is recognized as:
```
Bus 005 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 

```

---

### Post by Allysan on 2007-06-04
> **sprint4 said:**
> blop

Is this just a sound issue?

I wrote the "How-To" you got sent, and it's open for improvements...  ;-)

What commands wouldn't work?


Hello sir, I used your How-To as well... or at least attempted to do so and came across several errors.  When I got to the step where I'm supposed to compile and install alsa-driver (as well as alsa-lib and alsa-utils), I get this message:

tar: alsa-driver-1.0.14rc4.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I did make sure that the correct directory WAS in fact being accessed (I didn't use ~/downloads, I just used /home/(username)).  I decided to try and continue anyway, only to be told that the next directory I am supposed to access does not exist.  

Thank you for your time :)

---

### Post by blop on 2007-06-04
Sprint14 : cheers for the help...

i get this:

matt@matt-laptop:~$ rsync
rsync  version 2.6.9  protocol version 29
Copyright (C) 1996-2006 by Andrew Tridgell, Wayne Davison, and others.
<http://rsync.samba.org/>
Capabilities: 64-bit files, socketpairs, hard links, symlinks,
              batchfiles, inplace, IPv6, ACLs,
              64-bit system inums, 64-bit internal inums

rsync comes with ABSOLUTELY NO WARRANTY.  This is free software, and you
are welcome to redistribute it under certain conditions.  See the GNU
General Public Licence for details.


so i have rsync....so not sure why the command does not work, im doing a straight copy and paste of it :

rsync -avz --delete --exclude=.hg* rsync://alsa.alsa-project.org/hg alsa

cheers

---

### Post by sprint4 on 2007-06-04
Allysan,

Thank you for the feedback, however, I can not seem to find a place in my How-To, that instructs the reader to work with any alsa tarballs.  The instructions on the [Matrix:Module-hda-intel Page]("http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-hda-intel") refer to tar files.

I also tried modules that I made using the 1.0.14rc4 version of source that I downloaded from ALSA's website, and still had no sound.  After several days of work, I found that a developmental snapshot worked for me, and that is why I suggested that the reader use rsync. ;-)


blop,

I need to know exactly what happens when you run the rsync command...  

Are you running the commands as root?

I have tried again on three different machines, at different locations, without issue.  

For example, when I copied the rsync command that you had correctly copied into this thread, I get this:

```

impala:/# cd /usr/src/
impala:/usr/src# mkdir alsa
impala:/usr/src# rsync -avz --delete --exclude=.hg* rsync://alsa.alsa-project.org/hg alsa
receiving file list ... done

created directory alsa

./

alsa/

alsa-driver/

alsa-driver/acore/

alsa-driver/acore/ioctl32/

alsa-driver/acore/oss/

...

...another 3007 lines...

...
alsa/test.txt

hg-rsync

hgweb.config

hgwebdir.cgi



sent 54050 bytes  received 10387801 bytes  104943.23 bytes/sec

total size is 37574118  speedup is 3.60

```

Then, when I look at the contents of /usr/src/alsa I get this:
```

impala:/usr/src# ls /usr/src/alsa/

alsa  alsa-driver  alsa-firmware  alsa-git  alsa-kernel  alsa-lib  alsa-oss  alsa-plugins  alsa-python  alsa-tools  alsa-utils  hg-rsync  hgweb.config  hgwebdir.cgi

```


Then I'm able to change into the alsa-driver directory and continue the install...  If you don't see something like my example when you run rsync, please copy the output in your response.  

Thanks! :-D

---

### Post by blop on 2007-06-05
hey sprint4, thanks for your continued help and patience....

Well, when i run that command as root or as normal i get literally nothing... i hit enter and the cursor drops to a new line and just flashes....nothing is outputted and seemingly nothing is happening.

I think im gonna reinstall...

can do any harm....

---

### Post by fuzzyBSc on 2007-06-15
I haven't gotten any joy by following these instructions:

[http://linux.dobeyracing.net/how_to/toshiba_p200_laptop/Linux_on_Toshiba_Satellite_P200.php#sound1](http://linux.dobeyracing.net/how_to/toshiba_p200_laptop/Linux_on_Toshiba_Satellite_P200.php#sound1)

I had to install some extra packages to get the build going:
build-essential autoconf libtool automake gettext

rsync was already installed. I had to run "sudo bash" to become root and allow the relevant operations to occur.

I ran through most of the instructions without hassle with these packages installed. I was able to get through the driver and library installs, however the utils didn't seem to work for me. I think I'm continuing to use the existing installation of these files. I included the relevant lines in /etc/modules, rebooted.. and.. no sound. I'm not sure whether the drivers I built are being used or not.

My laptop model is A200/L01, purchased from Dick Smith in Australia.

Benjamin.

---

### Post by matheuu on 2007-06-16
Hi Benjamin,

Still no luck? Same here.
I have installed the latest alsa stuff. I think feisty 7.10 is already up to date. So this was a waste of time.  I found a list of different lines to add to the end of that file... but I lost it. I am thinking of finding it again and trying all the different combos. 

I am still not sure if the hardware that is being detected is correct.
Here is some stuff. Probably the same as yours. 

mat@mat-laptop:~$ lsmod | grep hda
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm


No idea what any of that means.
I will put up some other info I found.

---

### Post by fuzzyBSc on 2007-08-26
Hey, did you ever raise an official bug for this problem matheuu?

---

### Post by matheuu on 2007-09-09
Yeah I did ....a couple of times...on launchpad.

just sent you a reply on another thread Ben... forgot what it was about.... ah well it was probably about this bloody sound issue.

Hey Ben have you seen a few people out there with A200s saying they have fixed the sound?

M

---

### Post by Prymalfury on 2007-09-14
I had the same issue with Fiesty when I installed it. Try changing the settings by going to the terminal and typing " alsamixer " no quotes though. You can manually adjust the settings in there. Keep adjusting, and you will eventually have sound.

~Toad

---

### Post by fuzzyBSc on 2007-10-13
See:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/120302/comments/33](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/120302/comments/33)

---

### Post by taecha on 2007-10-20
I had a similar problem with my sound card which I could solve by adding the following to **/etc/modprobe.d/alsa-base**:

```
options snd-hda-intel model=acer
```

My computer has the following Subsystem installed:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 4540
Flags: bus master, fast devsel, latency 0, IRQ 21
Memory at d0440000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied> 

Hope that helps.

Cheers

---

### Post by blop on 2007-10-23
yea that worked...

but Gutsy has the problem solved so now need to tweak anything anymore!

---

