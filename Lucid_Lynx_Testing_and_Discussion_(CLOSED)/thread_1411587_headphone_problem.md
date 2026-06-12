---
title: "headphone problem"
date: 2010-02-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Tompalaz on 2010-02-20
I can no longer use the headphone jack on my MacBook. It worked just a few days ago. Havn't seen any update that might have killed it.

Before, all I had to do was to go through alsamixer and enable/unmute S/PDIF and raise the volume on the HP bar. 

A red LED light turns on in the headphone slot when I activate S / PDIF, so I can see that it is enabled but no sound goes through.
[See picture ]("http://processrants.files.wordpress.com/2009/01/ibam-macbook-headphone-jack.jpg?w=440&h=200")

I've killed pulseaudio and removed the .pulse folder.

Have I missed something?
Anyone have the same problem?

---

### Post by JCoster on 2010-02-20
Please can you confirm that audio works through your speakers?

---

### Post by Tompalaz on 2010-02-20
Yes, it works through MacBooks speaker, just not through the headphone jack.
I use the external speakers connected to my mobile right now...

---

### Post by mpires on 2010-02-20
I have an ASUS A6VA with a similar problem, all is fine on speakers but could not hear anything from headphones.

I added in /etc/modprobe.d/alsa-base.conf the line:
options snd-hda-intel model=z71v position_fix=1

Now after a restart it fully works, I don't know which sound module you use so you best not use this one but at least you get an idea of what might be a solution.

---

### Post by Tompalaz on 2010-02-21
Thank you mpires. Is there a way to know what module to load?

I've had problems with the applesmc module before so I removed it. But I guess it doesn't have anything to do with this.

Edit: You might want to know whan audo card I have.
Card: HDA NVidia                                  
Chip: Realtek ALC889A 

OT: is there something similar alsamixer for pulseaudio?
They've replaced alsa with pulse, right? 
Why is alsamixer still in Ubuntu?

---

### Post by Tompalaz on 2010-02-21
Okay, got it to work...
1) I added options snd-hda-nvidia model=auto to /etc/modprobe.d/alsa-base.conf
2) restart X
3) went in to alsamixer and pressed M on the HP bar..

It would've probably worked without the two first steps.:oops:

---

