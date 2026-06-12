---
title: "Audio/sound not working Ubuntu 10.04 B1"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bastones on 2010-03-21
Hi,

I'm trying out the beta and before and after installation sound/audio appears not to work. I've tried watching a youtube video and other stuff to test if audio works but there's no audio output at all. I did the lspci command via terminal and it shows my audio:

> 00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)

...but it appears not to work?

Any help appreciated, thanks :),
Ben.

---

### Post by strombom on 2010-03-21
To get audio back I clicked on the sound icon->Sound preferences->Output.

In the connector selection box I changed from "Analog output" to "Analog speakers". Then I restarted the web browser and now I get audio...

---

### Post by bastones on 2010-03-21
> **strombom said:**
> To get audio back I clicked on the sound icon->Sound preferences->Output.

In the connector selection box I changed from "Analog output" to "Analog speakers". Then I restarted the web browser and now I get audio...

Mine was already set to "Analog speakers", I changed to "Analog output" but still doesn't work. I've tried watching a video off browser and youtube video in FireFox and sound definitely still doesn't work.

---

### Post by lidex on 2010-03-21
So did it work on the alpha builds, or is this your first lucid install? It's likely an EAPD issue which is discussed here:
[http://ubuntuforums.org/showthread.php?t=1427902&page=2]("http://ubuntuforums.org/showthread.php?t=1427902&page=2")
Beginning at post #13

---

### Post by bastones on 2010-03-21
> **lidex said:**
> So did it work on the alpha builds, or is this your first lucid install? It's likely an EAPD issue which is discussed here:
[http://ubuntuforums.org/showthread.php?t=1427902&page=2]("http://ubuntuforums.org/showthread.php?t=1427902&page=2")
Beginning at post #13

I followed the steps there and EAPD was already checked? I think this may be a different issue, audio won't work (as far as I've tried so far) for headphones and internal laptop speakers. Btw, this is on a Sony Vaio VPCEB1E0E with Intel HD Audio. Thanks for your help so far to both of you! Any other solutions anyone?

---

### Post by lidex on 2010-03-21
You should run the alsa-info script so we can get the full picture. Right-click the link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```

Post a link to the script output in your next post.

---

### Post by Cuppa-Chino on 2010-03-22
the problem with the vaio (like mine !) is that the sound chip amp is not correctly addressed, if you plug in headphones you can just barely hear a tiny bit of sound.

when you try to manipulate the individual volumes in alsamixer, they end up being linked -- if I move PCM it moves master -- I think it is a question of controlling the amp in the chip therefore.


alsa info attached:

---

### Post by Cuppa-Chino on 2010-03-22
after reading this post:
[http://ubuntuforums.org/showpost.php?p=8976320&postcount=32]("http://ubuntuforums.org/showpost.php?p=8976320&postcount=32")

> Re: No sound anymore (but volume app works!)
The problem:

My internal speakers were not producing sound, however, the headphone jack was. HDA-Intel seemed to be the culprit.

The solution:

Download hda_analyzer from [http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)
Enabled EAPD (for me it was Node 0x15), and viola, internal speakers are producing sound.

I download the hda analyser and find that in NODE 0x19 Widget Control VREF needs to be changed to HIZ or GRD from 50. This turns on the amplifier!!

No how is this integrated into alsa and how do I need to ask for help ??

diff spat out by the analyser:
```
Diff for codec 0/0 (0x10ec0269):
---  
+++  
@@ -165,17 +165,17 @@
   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
   Amp-Out vals: [0x80 0x80]
   Pincap 0x00003734: IN OUT Detect
     Vref caps: HIZ 50 GRD 80 100
   Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
     Conn = 1/8, Color = Black
     DefAssociation = 0xf, Sequence = 0x0
     Misc = NO_PRESENCE
-  Pin-ctls: 0x24: IN VREF_80
+  Pin-ctls: 0x60: IN OUT VREF_HIZ
   Unsolicited: tag=0x00, enabled=0
   Connection: 2
      0x0c* 0x0d
 Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
   Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
   Amp-In vals: [0x00 0x00]
   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
   Amp-Out vals: [0x80 0x80
```

as said that diff came from the analyser

---

### Post by lidex on 2010-03-22
OK lets try this:
[http://ubuntuforums.org/showpost.php?p=8528280&postcount=32]("http://ubuntuforums.org/showpost.php?p=8528280&postcount=32")
Same chipset

---

### Post by Cuppa-Chino on 2010-03-23
> **lidex said:**
> OK lets try this:
[http://ubuntuforums.org/showthread.php?p=8528280#post8528280]("http://ubuntuforums.org/showthread.php?p=8528280#post8528280")
Same chipset

eehm, I think it would be best to figure out what exactly to do, the hda-analyser method works on very reliable, how can I get this diff setup? how can I find out if this diff is already in one of the options ?

---

### Post by lidex on 2010-03-23
Sorry, meant to refer to a single post with the main point being this:
In a terminal:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

Scroll to the bottom and insert these lines just below 
"options snd-pcsp index=-2":
```
options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv5
```

Save, then close. Reboot.

---

### Post by Cuppa-Chino on 2010-03-25
that does nothing, still had to change pin 19 amplifier setting to grd / hiz from numerical value for any sound.

with that done, am getting consistent sound and jack sense

---

### Post by lidex on 2010-03-25
> **Cuppa-Chino said:**
> that does nothing, still had to change pin 19 amplifier setting to grd / hiz from numerical value for any sound.

with that done, am getting consistent sound and jack sense

Great. Is it persistent through rebooting?

---

### Post by Cuppa-Chino on 2010-03-25
> **lidex said:**
> Great. Is it persistent through rebooting?

no as said before I need to run hda-analyser every boot to change the pin 19 amplifier setting. I do not know who I need to contact about implementing the change in alsa // setting up the option for this variant of alc269 -- anybody here now where to go?

thanks

---

### Post by Gorgonzalo on 2010-03-29
The setting you need to change can be scripted using hda-verb as explained here:
[https://bugzilla.redhat.com/show_bug.cgi?id=509542#c5](https://bugzilla.redhat.com/show_bug.cgi?id=509542#c5)

Running the following command as root fixes sound on my laptop:
```
# hda-verb /dev/snd/hwC0D0 0x19 SET_PIN_WIDGET_CONTROL 0x22
```The 0x22 represents VREF_GRD from my hda-analyze diff. It seems you can also use 0x60 (which is VREF_HIZ) instead of 0x22. I have no idea what either mean.

---

### Post by grandtoubab on 2010-03-29
another idea
[http://www.webupd8.org/2010/03/how-to-switch-to-alsa-or-oss-instead-of.html](http://www.webupd8.org/2010/03/how-to-switch-to-alsa-or-oss-instead-of.html)

---

### Post by ultiva on 2010-04-01
> **Gorgonzalo said:**
> The setting you need to change can be scripted using hda-verb as explained here:
[https://bugzilla.redhat.com/show_bug.cgi?id=509542#c5](https://bugzilla.redhat.com/show_bug.cgi?id=509542#c5)

Running the following command as root fixes sound on my laptop:
```
# hda-verb /dev/snd/hwC0D0 0x19 SET_PIN_WIDGET_CONTROL 0x22
```The 0x22 represents VREF_GRD from my hda-analyze diff. It seems you can also use 0x60 (which is VREF_HIZ) instead of 0x22. I have no idea what either mean.

Hello !
I can confirm that this command also enables sound on by laptop Vaio VPCEB1S1E (ALC269). Installing backported alsa drivers as described in other tutorials didn't worked. This fix works as long as I don't mess with mixer controls, then sound disappear and it's necessary to reenter command to restore it again.

Hope this fix will be includes in final Lucid.

---

### Post by Riot@ct on 2010-04-01
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4934](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4934)
There is a patch that fix the bug.
> 
kaeso's patch compiles and work fine for me, thanks kaeso!

I have Vaio VPC EB1J1E and I'm using Kubuntu 10.04 (lucid) beta1. Applied the patch on alsa-driver-1.0.22.1.90.g32fde.390.gffdb8.


---

