---
title: "Pulseaudio no longer finds Intel HDA only analog"
date: 2009-03-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2009-03-07
Today I was just about to start singing the praises of pulseaudio after having zero success with it in previous ubuntu versions.

I had the audio configured just perfectly with the default sink being my Intel HDA ALC662 Digital.

After a reboot the audio no longer worked with a null output problem. After adding my username to the pulse groups and the audio group the available sinks are the analog version of the driver and my usb audio phone. The Digital connection is now missing.

I can't figure out how to get it back despite it appearing as an option in the sound settings under ALSA.

Can anyone help me?

---

### Post by miegiel on 2009-03-07
You tried selecting sound devices at "System > Preferences > Sound"?

---

### Post by ugkbunb on 2009-03-07
the 0.9.15 testing preview is up to alpha5... I been using a git version on my ArchLinux box, it solved some module loading issues I was having with 0.9.14. There is a PPA for it posted:
[http://ubuntuforums.org/showthread.php?t=1066212&highlight=testing+preview+pulseaudio](http://ubuntuforums.org/showthread.php?t=1066212&highlight=testing+preview+pulseaudio)

---

### Post by sonicb00m on 2009-03-07
> **ugkbunb said:**
> the 0.9.15 testing preview is up to alpha5... I been using a git version on my ArchLinux box, it solved some module loading issues I was having with 0.9.14. There is a PPA for it posted:
[http://ubuntuforums.org/showthread.php?t=1066212&highlight=testing+preview+pulseaudio](http://ubuntuforums.org/showthread.php?t=1066212&highlight=testing+preview+pulseaudio)

I imported the key as described but i get this error on update

Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0B47F0A6B88A1AA8

---

### Post by taavikko on 2009-03-07
> **sonicb00m said:**
> I imported the key as described but i get this error on update

Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0B47F0A6B88A1AA8

```
gpg --recv-keys --keyserver keyserver.ubuntu.com b88a1aa8 --export |sudo apt-key add -
```

---

### Post by dalonso on 2009-03-07
I have the same problem since I did a fresh install of Jaunty. I have the last pulseaudio alpha 5 installed and it does not resolve the problem. Anyway, it is a driver problem, I mean an alsa problem that has nothing to do with pulseaudio. aplay -l shows only the analog device.

Update: I correct myself. It could be a problem in the pulse hal module if you see the digital device in aplay -l but it is not present in pulse device chooser. Reference: [http://www.pulseaudio.org/ticket/139](http://www.pulseaudio.org/ticket/139)

Anyway my problem is that it is missing in alsa itself.

---

### Post by sonicb00m on 2009-03-10
I think the problem is also with alsa.

Since my Jaunty installation was buggered I rebooted back to my working Intrepid installation and reinstalled pulse. I had the sound working just fine with the digital audio from the intel hda onboard card.

I decided to upgrade to the lastest PPA's and after a few reboots everything seemed just dandy.

Yesterday I rebooted the machine and guess what? There's no sound again. Even if i uninstall pulse and switch to alsa in the sound preferences I am not hearing any sound. There are no visible errors...just no sound.

I am beginning to get really tired of the sound problems in Ubuntu. I am almost afraid to reboot the PC because I have experienced many many times the sound just stopping working for what seems to no apparent reason.

How can i fix this?

Last time i got problems of this nature I recompiled alsa myself but the only option that would work for me was compiling with the switch for that specific sound card which meant my USB audio phone was no longer working....so that's not a solution. Compiling with "all" didn't get either working again!

---

### Post by crimsun on 2009-03-10
Have you tried unloading the sound driver, removing /var/lib/alsa/asound.state, and rebooting?

(You can find which sound driver module to unload with `cat /proc/asound/modules'.)

---

### Post by miegiel on 2009-03-10
> **sonicb00m said:**
> I am almost afraid to reboot the PC because I have experienced many many times the sound just stopping working for what seems to no apparent reason.

I had that too for a while, it turned out my soundcard wasn't always found if I started up. All caused by a powersuply that wasn't really strong enough for my pc.

But maybe you have a laptop? Is the Intel HDA is the digital output or the sound channel in a hdmi connector?

Use ```
lspci
``` to make sure soundcard is there when your sound is gone.

---

### Post by sonicb00m on 2009-03-11
> **miegiel said:**
> I had that too for a while, it turned out my soundcard wasn't always found if I started up. All caused by a powersuply that wasn't really strong enough for my pc.

But maybe you have a laptop? Is the Intel HDA is the digital output or the sound channel in a hdmi connector?

Use ```
lspci
``` to make sure soundcard is there when your sound is gone.

Hmmm something is going on though. Yesterday after a reboot it was back to normal. I turned the pc off for the night and again this morning it's not working.

I don't have a laptop, it's a desktop. I already upgraded the PSU so I don't think that should be the problem.


00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)

It's there in the list

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

Don't see the USB one though.

---

### Post by sonicb00m on 2009-03-12
I think something is confusing pulse or alsa and it's to do with my usb phone.

Last night i was still getting no sound but no visible errors and tried to play the sound through the USB phone to see if that worked. It didn't so I arbitrarily pressed the volume control on the phone and then the audio started coming out of the Intel card! Despite the volume settings being set to max on the pulse manager.

It's very odd.

---

### Post by dalonso on 2009-03-12
After downloading alsa 1.0.19 and installing the last snapshots of alsa-drivers-0.1.19 with:

sudo ./configure --with-cards=all -with-card-options=all
sudo make
sudo make install

Since then I'm having the best user experience with the Sigmatel 9872AK in my Vaio. Everything works out-of-the-box, analog and digital outputs, included the audio channel through my HDMI interface, Internal and external mics are recognized. Full sound volume. Pulseaudio shows all its potential now.

I fully recomend to build yourselfs the drivers using those options. For some reason the hda-intel driver in the ubuntu package was not compiled with all available options.

You can use the script at [http://ubuntuforums.org/showthread.php?t=1046137&highlight=jaunty+alsa](http://ubuntuforums.org/showthread.php?t=1046137&highlight=jaunty+alsa) for:

./alsa-upgrade.sh -d *(for downloading the last release of alsa)*
./alsa-upgrade.sh -snap *(for downloading the last snapshot of alsa)*
./alsa-upgrade.sh -i *(for building and installing the last snapshot of alsa)*

This will do the install without all card options, so enter in /usr/src/alsa-drivers and configure and build the drivers again using the instructions at the begining of this post. 

Let's see whether it works for you as it did for me.

Good luck.

---

### Post by sonicb00m on 2009-03-12
So far so good, thanks for the tips.

---

### Post by sonicb00m on 2009-03-13
Loaded up today and now pulseaudio has that null device thing again :( If select the alsa version and open the gnome-alsa mixer and up the volume the sound card is working.

---

