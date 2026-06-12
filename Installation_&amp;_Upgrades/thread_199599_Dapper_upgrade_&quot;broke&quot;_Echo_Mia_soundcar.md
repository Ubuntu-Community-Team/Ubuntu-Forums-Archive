---
title: "Dapper upgrade &quot;broke&quot; Echo Mia soundcard"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by SpectralDesign on 2006-06-19
Well, obviously the soundcard isn't broken, just that it's no longer working.  It was a pain to get it working originally, because apparently I'm the only one using it with Ubuntu, but under 5.10 I did get it working (with help) and it was easy to get it working again when a kernel upgrade broke it.... I made a Wiki page detailing what I did:

**RESOLVED - This wiki page now has complete instructions for Dapper or Badger:**
[https://help.ubuntu.com/community/EchoMia](https://help.ubuntu.com/community/EchoMia)

Well, now I've upgraded to 6.06 and my wife has asked that I set her back up for recordings for Librivox.Org, so here I am, back at it again....

I tried compiling the ALSA driver modules, which seemed to work okay, but I'm still unable to use the Echo Mia.  One change is that I used GCC 4.0 this time, I also notice that there is no longer an /etc/init.d/alsa so I tried a few things I thought would be functionally the same, but to no avail, i.e.:

sudo /etc/init.d/alsasound restart
Shutting down sound driver: !!!alsactl not found!!! done

This does seem to hoze the sound, and even a:

sudo /etc/init.d/alsa-utils restart
 * Shutting down ALSA...                                                 [ ok ]
 * Setting up ALSA...                                                    [ ok ]

doesn't seem to fix that, only a reboot is working of the things I've tried, which re-enables my SiS card, but still leaves the Mia out of the picture :(

Any pointers appreciated!

---

### Post by pekko on 2006-06-21
Unfortunately I can't help, but I have the same problem. I got Mia Midi working in Breezy by following your instructions in earlier thread, but after upgrading to Dapper I can't do it again.

I can compile everything without errors and I can even load the module, but Dapper doesn't seem to recognise the card correctly. I just noticed a kernel update, I might give it a new try tomorrow.

I hope we can find a solution. I'm now using integrated SiS sound in Ubuntu and I really would like to get rid of it.

BR Pekko

---

### Post by SpectralDesign on 2006-06-22
Please keep us posted if you have any success!

On X-Chat 'crimsun' told me that there was no need to do the ```
export CC=gcc-4.0
```now in Dapper, but neither of us is having trouble compiling the module, only getting it to take hold....

I get no error trying:

```
modprobe snd-mia
```

but it doesn't seem to stick, as:

```
cat /proc/asound/cards

```
gives me only:
 0 [SI7012         ]: ICH - SiS SI7012
                      SiS SI7012 with ALC655 at 0xd800, irq 201
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10

In 'hardinfo', I can see the card:

PCI Devices -
    Motorola DSP56361 Digital Signal Processor
    IRQ: 209
    Memory: 1024KB
    Bus master: No
    Device: 9

Hopefully I can work more on this issue soon, but I'm just too busy right now :(

Good luck!

---

### Post by SpectralDesign on 2006-06-27
I haven't had time to do much with this yet, but something I noticed today (again from "hardinfo") is:

Details... Kernel Modules... Echoaudio Mia Soundcard Driver

So, apparently the module *is* loaded, but:

alsamixer -c 0
(loads the mixer for Realtek ALC655)

alsamixer -c 1
"no mixer elems found"

If I've set sound preferences to ESD, then a program like Audacity chokes on startup, if I disable ESD then Audacity shows only one sound device, /dev/dsp

If I learn anything else I'll be posting! (And updating the wiki page.)

---

### Post by rakeen on 2006-06-29
Hi,

I can't help you because I have exactly the same problem with Mia Midi and Ubuntu Dapper.

I can compile driver, libs and utils with no prblem (using GCC 4.0). A "modprobe snd-mia" return no errors, I have selected ALSA in the gnome panel "multimedia systems" but I can't hear any sound...

ALSA seems not to recognize my Mia card... I got an error when I restart Alsa-utils "no device found"...

If You find the solution, you'll be my master ! ;-)

---

### Post by alexmac on 2006-07-02
I'm having similar problems

I tried installing alsa 1.0.11 from source, but when I use insmod to try out the modules the firmware loader can't find the required file:

ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 193
[17179796.492000] ALSA /usr/src/modules/alsa-driver/pci/echoaudio/echoaudio.c:41: get_firmware(): Firmware not available (-2)
[17179796.600000] ACPI: PCI interrupt for device 0000:02:0b.0 disabled
[17179796.600000] Echoaudio Mia: probe of 0000:02:0b.0 failed with error -2

Any ideas?

---

### Post by alexmac on 2006-07-02
I ended up getting the mia going

Currently I have:

alsa-driver-1.0.11
alsa-tools-1.0.11
alsa-firmware-1.0.12rc1

compiled and installed from source from [http://www.alsa-project.org](http://www.alsa-project.org)

I wasn't very tidy with my package management, so the default ubuntu alsa packages are still there.. with a few files and drivers overwritten by the new binaries

The newer alsa-firmware version sorted out the previous error message, only gotcha was that it installed the firmware files into /lib/firmware/ea so i moved the contents of ea into /lib/firmware/2.6.15-25-686 to match my kernel version

now its all working nicely

alex

---

### Post by rakeen on 2006-07-06
[QUOTE=alexmac]I ended up getting the mia going

Currently I have:

alsa-driver-1.0.11
alsa-tools-1.0.11
alsa-firmware-1.0.12rc1

compiled and installed from source from [http://www.alsa-project.org](http://www.alsa-project.org)

I wasn't very tidy with my package management, so the default ubuntu alsa packages are still there.. with a few files and drivers overwritten by the new binaries

The newer alsa-firmware version sorted out the previous error message, only gotcha was that it installed the firmware files into alsa-firmware-1.0.12rc1 so i moved the contents of ea into /lib/firmware/2.6.15-25-686 to match my kernel version

now its all working nicely

alex[/QUOTE]

YES ! I have followed the same method and it works !!! great ! thanks!

I have upgraded my kernel to 2.6.15-25-686 (686 version) and I have compiled and installed alsa driver, libs and utils from source (version 1.0.11, for details see [http://www.alsa-project.org)](http://www.alsa-project.org)). then I have compiled and installed alsa-firmware-1.0.12rc1 and copy the content of /lib/firmware/ea in /lib/firmware/2.6.15-25-686.

I have rebooted my system, launched alsamixer in order to unmute all ouputs and inputs. I have installed alsa-tools-gui package via synaptic. launch echomixer to ajust some details.

I don't know if it's just the kernel version or anything else, but it works fine now!

thank you very much alexmac!

---

### Post by pekko on 2006-07-06
It seems that using alsa-firmware-1.0.12rc1 does the trick. My Mia Midi is also working now. These are the steps it took in my case:

```
sudo apt-get install linux-headers-2.6.15-25-k7

cd /usr/src
sudo mkdir alsa
cd alsa

sudo wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.10.tar.bz2
sudo wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.12rc1.tar.bz2

sudo tar -xjvf alsa-driver-1.0.10.tar.bz2
sudo tar -xjvf alsa-firmware-1.0.12rc1.tar.bz2

cd alsa-driver-1.0.10
sudo ./configure --with-cards=intel8x0,mia --with-oss=yes --with-sequencer=yes
sudo make
sudo make install

cd ..
cd alsa-firmware-1.0.12rc1
sudo ./configure
cd echoaudio
sudo make
sudo make install

cd /lib/firmware/ea
sudo cp * /lib/firmware/2.6.15-25-k7/

sudo modprobe snd-mia
```

At this point I got some warnings, but after reboot everything was working. Gnome's volume control is a mess with Mia, but you can use echomixer instead. As rakeen points out, you can install echomixer with Synaptic.

---

### Post by ombudsmedia on 2006-07-15
Just reporting that it also works with my gina20.
Some months ago I had to use Demudi because I couldn't work in ubuntu with this soundcard.
Just wondering if it would work with my m-audio Ozone...

thanks a lot!!

---

### Post by ronoc on 2006-07-16
Cheers guys for the tips.

I just got my layla 24 cardbus working on a toshiba a100 running dapper. 

Just to add to the info.

I copied the firmware files from the ea folder to the current linux firmware folder as you suggested. The folder in lib/firmware was not 2.6.15-25-686 (686 version) but 2.6.15-23-386. I thought I would mention that incase anyone thought they may have to update this.

I think the problem was the symbolic link with the hotplug/firmware and /lib/firmware.

to check this.
ls -la /lib/firmware

You should see a link to the hotplug/firmware folder

if not
set the link

cd lib/firmware
ls -s /hotplug/firmware

After setting this then recompiling the alsa firmware and copying the files from ea/ as mentioned above, I loaded the module modprobe   snd-layla24. 

Finally
 
echomixer      

now I can use PD wheepee.....!!!

---

### Post by SpectralDesign on 2006-07-25
I've started a page in the Wiki about the EchoMia -- please feel free to edit it, contact me with recommended changes, or copy it wholesale and edit as needed to make it a more generic Wiki page regarding ALSA under Ubuntu!

See here: [https://help.ubuntu.com/community/EchoMia](https://help.ubuntu.com/community/EchoMia)

---

### Post by SpectralDesign on 2006-07-25
After switching to the newest kernel: 2.6.15-26-686 I'm having a spot of trouble with sound....

I re-compiled ALSA, did all the steps, such as copying the firmware files, etc...  My Mia still works fine, the only odd thing is that now it's decided to be /dev/dsp and given /dev/dsp1 to the SiS onboard sound device.

XMMS works too....

However, system sounds are no longer working, and the "System... Preferences... Sound" control panel insists that the Mia is the default card, and wont stay switched to the SiS SI7012... This seems to also be effecting Firefox, Mplayer, etc....

Any tips on getting the default sound device to "stick"?

---

### Post by SpectralDesign on 2006-07-26
well, one issue resolved:

I edited /etc/modprobe.d/alsa-base and added the following:

```
# http://ubuntuforums.org/showthread.php?t=205449
options snd_intel8x0 index=0
options snd_mia index=1

```

Obviously you'd want to modify the snd_* bits to your systems specs.  Now the default sound device is back to the SiS card, and applications that don't let me set the sound device to use seem to be working okay.

I still have a nagging issue though (does it ever end?!?) ](*,) :D 

Something that hasn't been working for me for a while is the "desktop sounds"... to be more specific, when the login-screen loads, I get the bongo sound, but once logged-in I get no further system sounds (System... Preferences... Sound... x-enable ESD, x-enable system sounds)

This is a minor annoyance... Obviously I don't rely on these, but it'd be nice to know why it's not working and get it fixed!

---

### Post by adds2one on 2006-08-05
Hello,

Could anyone who has successfully installed an Echo Audio sound card please check out my post about installing an Indigo IO [http://www.ubuntuforums.org/showthread.php?t=229778](http://www.ubuntuforums.org/showthread.php?t=229778)

Much appreciated, - J

---

### Post by ThrashJazzAssassin on 2006-08-11
I've got an Echoaudio Darla20 card and have some questions

-Will the act of compiling the ALSA drivers have to be done every time there's a kernel update?

-Will Echoaudio cards ever work out the box?

I would love to hear No then Yes:-D. But only if it's true.

---

### Post by alexmac on 2006-08-17
... oops! can't figure out how to delete the message.. time to rtfm

---

### Post by wonea on 2006-08-17
Hello, I've installed my Mia using the latest alsa drivers;

alsa-firmware-1.0.12rc2a
alsa-driver-1.0.12rc3
alsa-lib-1.0.12rc2
alsa-utils-1.0.12rc2

However, I get a nasty ticking sound when I play a mp3 file, and I get no sound whatsoever in games like enemy territory.  Any ideas?  Should I wait for better drivers?

Also when I run Audacity I got the error:

Error Initializing Audio

The was an error initializing the audio i/o layer.  You wil not be able to play or record audio.

Error: Host error

---

### Post by leemckusic on 2006-09-11
Adding to this thread about "sound broke"

--- I upgraded to Dapper and I found RealPlayer would not play sounds.

The problem was to figure out what layer and what item was broken.

Summary of problem observed: 
  Startup sounds working.
  Music CD would play.
  Streamtuner starting XMMS starting a RealPlayer station would not work.
  Browser clicking on a Radio station RealPlayer icon would not work.

   the solution:
   Required a hardware restart afterwards. 
   Re-install a copy of Realplayer version 10 I had in Desktop

sudo ./RealPlayer10.bin            ; answer all questions with "default"

---

### Post by SpectralDesign on 2006-09-12
> **ThrashJazzAssassin said:**
> I've got an Echoaudio Darla20 card and have some questions

-Will the act of compiling the ALSA drivers have to be done every time there's a kernel update?

-Will Echoaudio cards ever work out the box?

I would love to hear No then Yes:-D. But only if it's true.

Sorry to say, yes - when ever you change kernel you need to re-compile.  If you've got a peculiar situation where you're simply switching between say the 386 and 686 kernel regularly for some reason, then you could keep two source directories, and skip right to `make install` in the apropriate directory as needed, but certainly if you do an upgrade then you need to recompile.

For question two -- that's not likely from what I can see, but you could try asking in one of the dev forums and maybe get more information.

---

### Post by ThrashJazzAssassin on 2006-09-28
Apparently the Echoaudio drivers have recently been absorbed by the oficial linux kernel.

Sounds promising, but what does it mean?

---

### Post by pekko on 2007-04-23
It looks like Mia Midi is still not working out of the box. After installing Feisty (clean install), snd-mia module is loaded, but the system can't find the card. Compiling Alsa 1.0.13 doesn't work either. I managed to get the sound running by compiling latest version of alsa. Below you can find two scripts I use for compiling alsa after kernel updates. First is only used once to download and untar source files.

```
cd /usr/src/alsa


wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2
wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.14rc3.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14rc3.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14rc2.tar.bz2
wget ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.14rc3.tar.bz2

tar -xjvf alsa-driver-1.0.14rc3.tar.bz2
tar -xjvf alsa-firmware-1.0.14rc3.tar.bz2
tar -xjvf alsa-lib-1.0.14rc3.tar.bz2
tar -xjvf alsa-utils-1.0.14rc2.tar.bz2
tar -xjvf alsa-tools-1.0.14rc3.tar.bz2
```

```
apt-get install linux-headers-$(uname -r)

modprobe -r snd-mia

cd /usr/src/alsa

cd alsa-driver-1.0.14rc3
make clean
make mrproper
./configure --with-cards=intel8x0,mia --with-oss=yes --with-sequencer=yes
make
make install

cd ../alsa-lib-1.0.14rc3
make clean
./configure
make
make install

cd ../alsa-firmware-1.0.14rc3
make clean
./configure
make
make install

cd ../alsa-utils-1.0.14rc2
make clean
./configure
make
make install


modprobe snd-mia

cat /proc/asound/cards
```

Modprobe returned an error, but after reboot the card got recognised and worked. Only problem now is that master volume goes to zero by itself.

Following packets are needed to compile alsa from source:

build-essential
gettext
libncurses5-dev
libncursesw5-dev

---

