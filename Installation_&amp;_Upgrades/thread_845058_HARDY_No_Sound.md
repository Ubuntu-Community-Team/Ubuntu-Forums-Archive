---
title: "HARDY No Sound"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by l0pt on 2008-06-30
Hi ppl,

Since i made the updates on my new ubuntu i dont get sound. Everything seams to be installed, the driver and even in alsamixer everything is ok.

When i play some sound, it plays but no sound output.
And has nothing to be with bios cause in windows is working.
The device in use is:
_0_: HDA Intel (Alsa Mixer)

Any ideas?

PS: I installed at same day Compiz / Emrald / Wine

---

### Post by Pumalite on 2008-06-30
Post:
lshw -C sound

---

### Post by l0pt on 2008-06-30
*-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel


------------

The card is installed i even can play mp3 files and so on, but no sound output. 
I think it happend when i made the 8.04 latest updates.

thnkx

---

### Post by Pumalite on 2008-06-30
Type in Terminal:
alsamixer
Up all the volunes to 100%

---

### Post by l0pt on 2008-06-30
hi m8, 
Thnkx for the fast reply.
I already tryed it and everything 100 %

---

### Post by Pumalite on 2008-06-30
Go to System>Administration>Software Sources>Open up all your repos, including: proposed, partner, updates and backports. Exclude src. Then do a:
sudo apt-get dist-upgrade

---

### Post by l0pt on 2008-07-02
everything open.
when i made the updates of ubuntu, the sound stoped to play.

l0pt

---

### Post by Pumalite on 2008-07-02
Post:
lshw -C sound

---

### Post by cdawg92 on 2008-07-02
Open the volume control panel, right click the speaker icon on panel select Volume Control, select edit->preferences and look for surround. If you find surround, select it then close. Make sure surround is not muted and crank up the volume. That worked for me.

Note: This keeps the speakers on even with a headphone plugged in. Anyone know how to avoid this?

Acer 5920G
Ubuntu 8.04
Intel ICH8 HD Audio Controller

---

### Post by l0pt on 2008-07-02
Pumalite plz scroll up already made it.

  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

CDAWG92

I dont have the surround option and headset is unselected, and dont work aswell, averything plays and still no sound.

---

### Post by cdawg92 on 2008-07-02
Your sound card is the same as mine.  Have you tried going to System->Preferences->Sounds and trying the tests with various mixers?

---

### Post by l0pt on 2008-07-03
yes tested.

i open an mp3 file for example, i see it playing till the end but i cant listen anything.

---

### Post by l0pt on 2008-07-03
fully reinstalled ubuntu, new fresh instalation.
and the same i see a movie player or a mp3 but no sound output. Strange.

any ideas?

---

### Post by l0pt on 2008-07-03
BTW the computer is a laptop ASUS F3SV.
And i see i am not the only one with same prob?
Anyone with it working?

---

### Post by Aruhn on 2008-07-03
Propably it would work with PulseAudio, the main package is already  installed, but it is needed to install libasound2-plugins and pavucontrol.

Then, you should find in the menu Applicatins the tool "PulseAudioColumeControl". Open that and and by the point "Output Devices" choose with a right click your Soundhardware as Default.

Next, go to System --> Preferences --> Audio and choose PulseAuddio - Soundserver.

Is Sourround-Sound (5.1 or higher) needed, you need to configure the PulseAudio deaemon.conf file.
You find this file by /etc/pulse. 
Change the Line "default-sample-channels = 2" to  default-sample-channels = 6 or like your Soundsystem. 

PulseAudio works with many Applications, but not with all.
Curiosly, by my laptop Rythmbox (all Gstreamer Applications) does not work with PulseAudio - but it does that by my Deskop PC, where PulseAudio is the main soundsystem, too. :confused:

---

### Post by l0pt on 2008-07-03
thnkx for the reply m8 :)

well i reinstaled ubuntu and nothing, no sound but then i made the updates and the sound is working and i see the alsa installed is the .16 and not the .15 as i can remember, anyway maybe it just got a new update today dunno, but i think it was solved by a new version.

Thankx all for the help.

Cheers,
L0pt

---

