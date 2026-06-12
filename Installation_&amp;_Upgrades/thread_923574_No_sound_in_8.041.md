---
title: "No sound in 8.041"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by kjmorris on 2008-09-18
I just installed Ubuntu 8.041 on a dual boot system with two 80 GB hard drives. On Drive 1, I have Windows XP HE SP3 and on Drive 2 I have a tiny FAT16 partition and the rest is Linux. I previously ran SuSE Pro 9.2, which I deleted to install Ubuntu. The system is a P4 2.8 Mhz with 1.5 GB RAM and an Audigy sound card.

I can't get any sound under Linux. When I reboot into Windows, the sound is fine. I checked all physical connections and they are correct as well.

What do I need to do to solve this problem?

TIA   kjmorris

---

### Post by nerdzero on 2008-09-18
Hello,  I have the same card in my dual-boot system and had the same problem.  It turned out not to be a problem with the card, but with some USB headphones I had plugged in.  Ubuntu defaulted to sending the output through the headphones.  When I unplugged them and changed the default audio device it worked.

Do you have any other sound devices plugged in?  Do you have any onboard sound on your motherboard enabled in the BIOS?

---

### Post by kjmorris on 2008-09-18
I did have a USB headset (that I use in Windows) that was plugged-in. I removed it. But how do I re-set the default audio device? I've been rooting around in the menus and can't seem to find it.

Thanks.  kjmorris

---

### Post by Pumalite on 2008-09-18
Post:
lshw -C sound

---

### Post by kjmorris on 2008-09-18
> **Pumalite said:**
> Post:
lshw -C sound

When I do the above, this is what I get:
kelly@kelly-desktop:~$ sudo lshw -C sound
  *-multimedia            
       description: Multimedia audio controller
       product: SB Audigy
       vendor: Creative Labs
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1

kjmorris

---

### Post by nerdzero on 2008-09-18
I fixed the problem on my system a while ago so I don't quite remember what I did.  I tried a lot of things before I figured out it was the dang headset causing the problems :)

I think I installed asoundconf-gtk which put the default sound option in the preferences and then I rebooted and everything was working then.  Can't remember for sure though.

---

### Post by Teetdiro on 2008-09-18
thanks a lot , bump up up up!!When the store manager returned from lunch, he noticed his clerk's hand was bandaged, but before he could ask about the bandage, the clerk said he had some very good news for him."Guess what, sir?" the clerk said. "I finally sold that terrible, ugly suit we've had so long!""Do you mean that repulsive pink-and-blue double-breasted thing?" the manager asked."That's the one!""That's great!" the manager cried, "I thought we'd never get rid of that monstrosity! That had to be the ugliest suit we've ever had! But tell me.Why is your hand bandaged?""Oh," the clerk replied, "after I sold the guy that suit, his guide dog bit me."------------The WOW gold Online Store, Open 24/7 Looking to buy [wow gold](http://www.u4game.com), Items or Accounts? You would find the cheapest gold here. We always online 24 hours a day, 7 days a week, any questions regarding [world of warcraft gold](http://www.u4game.com), powerleveling,wow leveling ,[warcraft gold](http://www.u4game.com), just talk to our representatives using our 24/7 live chat service.[world of warcraft gold](http://www.u4game.com/world-of-warcraft-gold.html),[wow leveling](http://www.u4game.com/Wow_Power_Leveling.html),

---

### Post by Pumalite on 2008-09-18
Type 'alsamixer' in your Terminal and make sure volumes are 100%

---

### Post by kjmorris on 2008-09-18
I ran asoundconf-gtk and set Audigy as the default audio device.

I ran alsamixer and set the volumes to 100%.

I still get no sound.  :-(

kjmorris

---

### Post by Pumalite on 2008-09-18
Open up all your repos; except src. Then run:
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by Cephalophage on 2008-09-18
Hi, I have the same problem with Kubuntu Hardy on my Dell Inspiron 1520. It's the only OS on the computer. The odd thing is that the sound worked for several weeks after the installation, then mysteriously quit. What I get from the command above is this:

  *-multimedia
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

### Post by kjmorris on 2008-09-18
I ran update manager and everything is up-to-date.

kjmorris

---

### Post by Pumalite on 2008-09-19
Do you have sound?

---

### Post by selkie1964 on 2008-09-19
I'm having exactly the same problem.  I was running 7.10 (which came preinstalled on my Dell Inspiron 1525 laptop) under which I had no problem with sound (just a problem with Java, but that's a whole 'nother can of worms).  I recently upgraded to 8.04 (which solved my Java problem) and ever since then, I have no sound at all, anywhere -- no login sound, sound files don't play, YouTube videos play with picture but with no sound.  I get no sound through my headphones when I plug them in either.

When I click on the volume control icon (which now has an X symbol -- I assume for "not functioning" or "disabled" -- next to it, which it did NOT have before I upgraded) I get the following error message:

[INDENT]The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.[/INDENT]

I did a search in Add/Remove Applications for "GStreamer plugins" and they are all installed, so that's not the problem.  I guess I need to configure my sound card, but I have no idea how to even begin doing that.

When I ran  "lshw -C sound" in the terminal window, I got the following:

[INDENT]WARNING: you should run this program as super-user.
[INDENT]  *-multimedia UNCLAIMED  
       [INDENT]description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0[/INDENT][/INDENT]
[/INDENT]
I'm pretty wet-behind-the-ears when it comes to linux, so I have no idea how to fix this problem.  Any help would be appreciated.  :confused:

---

### Post by kjmorris on 2008-09-19
> **Pumalite said:**
> Do you have sound?

No. I ran the updates and I still have no sound and no idea what to do next.

---

### Post by Pumalite on 2008-09-19
Try:
1. change the sound options from auto detect to ALSA
2. sudo pkill pulseaudio

---

### Post by kjmorris on 2008-09-19
> **Pumalite said:**
> Try:
1. change the sound options from auto detect to ALSA
2. sudo pkill pulseaudio

I just did both and still no sound. :-(

I went back to my Windoze partition just to double-check and sound is working normally there.

---

### Post by Pumalite on 2008-09-19
Try:
sudo apt-get install linux-backports-modules-generic
Reboot

---

### Post by kjmorris on 2008-09-19
> **Pumalite said:**
> Try:
sudo apt-get install linux-backports-modules-generic
Reboot

I did the above and still no sound.

---

### Post by nerdzero on 2008-09-19
> **Pumalite said:**
> Try:
1. change the sound options from auto detect to ALSA
2. sudo pkill pulseaudio

Hey this reminded me of something else I did when I had this problem.  I got rid of pulse audio by going to System > Preferences > Sound.  I then changed everything to ALSA.  Hope that helps.

---

### Post by kjmorris on 2008-09-19
> **nerdzero said:**
> Hey this reminded me of something else I did when I had this problme.  I got rid of pulse audio by going to System > Preferences > Sound.  I then changed everything to ALSA.  Hope that helps.

I changed everything from auto-detect to ALSA but still no sound!

---

### Post by nerdzero on 2008-09-19
Not sure, but maybe this will be a clue for someone more knowledgeable in the intricacies of sound drivers.  The configuration reported by 'lshw -C sound' for me showed...

 driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1

Notice the latency is 64 where yours was 32.  I'm not sure if makes a difference though :confused:

---

### Post by nerdzero on 2008-11-06
kjmorris, I recently installed 8.10 and lost my sound again.  I did not have the headphones plugged in this time either.  Here's how I got it back:

System > Preferences > Sound

I changed Sound playback from Autodetect to Audigy 1 [SB0090].....Multichannel Playback(ALSA)

Then, (this is what made it work)  I went to the Volume Control preferences, changed the device to Audigy 1 [SB0090] (Alsa mixer), went to the Switches tab, and unchecked the "Audigy Analog/Digital Output Jack" checkbox.

I still don't have sound in Flash, but everything else seems to be working.

---

