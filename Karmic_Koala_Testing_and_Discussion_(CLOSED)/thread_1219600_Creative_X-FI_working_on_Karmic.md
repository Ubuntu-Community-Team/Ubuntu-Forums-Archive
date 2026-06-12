---
title: "Creative X-FI working on Karmic?"
date: 2009-07-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by PRGUY85 on 2009-07-21
Hey:

Just read somewhere that Karmic already has native X-FI support out of the box since July 12th...with multichannel support.  Can anyone confirm? Also, does this mean the Drive-bays docked with some X-FIs work as well, for example, being able to listen to a Optical cable input through it?

---

### Post by PRGUY85 on 2009-07-22
Anyone?

---

### Post by cheesypoof on 2009-07-22
I can confirm that, yes the sound works. With regards however to multichannel and optical cable input, I am a simpleton when it comes to sound so, not sure. Unfortunately every time I boot my sound is muted, not sure why... Also, there is this odd one second high pitched tearing noise after you login.

---

### Post by PRGUY85 on 2009-07-22
> **cheesypoof said:**
> I can confirm that, yes the sound works. With regards however to multichannel and optical cable input, I am a simpleton when it comes to sound so, not sure. Unfortunately every time I boot my sound is muted, not sure why... Also, there is this odd one second high pitched tearing noise after you login.

I will test it out tomorrow when Alpha 3 is released.

---

### Post by Afi on 2009-07-22
My sound kinda works with X-fi in kubuntu. Spdif seems to output only 96 kbit stereo and i don't know how to configure that. Analog outputs work but are separated: front, surround, back, front+lfe. With pulse I get all outputs together but it's not perfect, it might be my configs. There is sound coming out of the card anyway :D

---

### Post by taavikko on 2009-07-22
X-Fi support was just introduced in ALSA and in kernel, so give it time to mature...
At least atm the owners of card in question have sound through with this chip. :)

---

### Post by Reiger on 2009-07-22
Which is *much* better than having to patch the Creative ALSA driver yourself ... hoping it will still compile against the current kernel. (That is: no 2.6.31 for you!) :P

---

### Post by Joe_Bishop on 2009-07-22
ASUS Xonar is better. Switched to it.

---

### Post by PRGUY85 on 2009-07-23
Just tested a Live USB with Alpha 3.  Sound works, yet I didn't see all the channels available, just stereo.  Also, the Drivebay didn't work for Optical Input.  Don't know if this would change if I install Alpha 3 directly to hard drive instead of testing Live USB.

---

### Post by iandotcom on 2009-07-23
Hopefully when I get home from the Philippines I'll be able to give this a spin on my home computer. X-Fi has been a little bit of a trouble since adopting Ubuntu, and it's nice to see support has come a long way since the days of 7.10. :)

---

### Post by doctordruidphd on 2009-07-23
X-fi support is there, and works. But there appears to be no support for the CMDSS or Crystallizer functions. There is a "surround" channel in the mixer, but it doesn't seem to do anything. Yet.

---

### Post by PRGUY85 on 2009-07-23
> **doctordruidphd said:**
> X-fi support is there, and works. But there appears to be no support for the CMDSS or Crystallizer functions. There is a "surround" channel in the mixer, but it doesn't seem to do anything. Yet.

Has anyone tested Optical Input on the Drive bays?

---

### Post by KhaaL on 2009-07-24
I just tested karmic and can confirm that X-Fi is working fine. But under jaunty with kernel 2.6.31-rc4 I'm getting nowhere. Anyone who can tell me how i can get X-Fi working there?

---

### Post by taavikko on 2009-07-24
> **KhaaL said:**
> I just tested karmic and can confirm that X-Fi is working fine. But under jaunty with kernel 2.6.31-rc4 I'm getting nowhere. Anyone who can tell me how i can get X-Fi working there?

ALSA 1.0.20 is needed also.

---

### Post by KhaaL on 2009-07-24
> **taavikko said:**
> ALSA 1.0.20 is needed also.

Thanks, now i just need to figure out how to squeeze it into my box :D

---

### Post by KhaaL on 2009-07-24
I just used [this script]("http://ubuntuforums.org/showpost.php?p=6589810&postcount=1") to get alsa 1.0.20 installed but X-Fi dosen't show yet. Here's some possibly intresting output:

> 
khaal@X:~/Desktop$ lspci |grep eative
03:07.0 Multimedia audio controller: Creative Labs SB X-Fi

khaal@X:~/Desktop$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

uname -r
2.6.31-020631rc4-generic


---

### Post by PRGUY85 on 2009-07-25
Will we be able to get true 5.1 surround sound out of movies with Dolby Digital/DTS when Karmic gets out the gate?  

Also, for those not aware, when I talk about Optical In on Drive-Bay for X-Fi, this is what I'm talking about:

[IMG]http://www.madboxpc.com/news/xfi_drive_bay.jpg[/IMG]

Has anyone gotten that to work?

---

### Post by bjorkiii on 2009-07-27
Could someone help me work out hot to configure spdif in my x-fi to output 441000 rather than 960000 , i'm running spdif out to a dacmagic i wonder if thats whats causing the problem ? i did use padevchooser to switch output to digital stereo but only the right speaker worked when i did that , its not a major problem but if its possible to output 441000 it would be delightful :D

---

### Post by Afi on 2009-09-01
In current Karmic X-fi spdif pass-thru is working and analog 5.1 is working with pulseaudio. :popcorn:

---

### Post by Capt. Blackwood on 2009-09-12
How much of the card is working out of the box now?
 
And does it include the front panel?

---

### Post by KhaaL on 2009-09-12
card is working fine OOTB. I have my headset connected to the front panel without a problem.

---

### Post by Capt. Blackwood on 2009-09-12
what profile do you select...cos my front's not working atm.

---

### Post by PRGUY85 on 2009-09-12
> **KhaaL said:**
> card is working fine OOTB. I have my headset connected to the front panel without a problem.

Do you have all front panel working? Including Digital In/Out?

---

### Post by PRGUY85 on 2009-09-12
Anyone?

---

### Post by PRGUY85 on 2009-09-12
I tested the Alpha 5 and I could get sound working yet it only allows for Analog Input, not Digital Input.

---

### Post by dext on 2009-09-12
> **PRGUY85 said:**
> I tested the Alpha 5 and I could get sound working yet it only allows for Analog Input, not Digital Input.
same with me in Fedora12, but i think thats the beloved PulseAudio at fault, it just will not allow Digital

---

### Post by KhaaL on 2009-09-13
I have only tested analogue output/input. I didnt choose anything or fiddle whatsoever, it just worked...

---

### Post by Capt. Blackwood on 2009-09-13
> **PRGUY85 said:**
> Do you have all front panel working? Including Digital In/Out?
 
My front panel is NOT working at this time...but 5.1 is.

---

