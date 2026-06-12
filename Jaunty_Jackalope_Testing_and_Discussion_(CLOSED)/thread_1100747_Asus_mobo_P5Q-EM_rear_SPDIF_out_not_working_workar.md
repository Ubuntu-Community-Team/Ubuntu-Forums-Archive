---
title: "Asus mobo P5Q-EM rear SPDIF out not working workaround"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rperkins on 2009-03-19
Hello
I have the Asus P5Q-EM mobo and the spdif audio output jack at the rear of the mobo was not working.  I got it working by adding this line at bottom

/etc/modprobe.d/alsa-base.conf

```
options snd-hda-intel model=6stack-dig
```


Note that the rear spdif output works under Intrepid, but not Jaunty.
This mobo has two spdif outputs.  the rear one and another one that is accessed thru a header on the mobo, typically to be used on a front panel.

I believe this issue came about due to an alsa patch introduced Nov 2008.
[COLOR="Orange"][patch/58025]("http://thread.gmane.org/gmane.linux.alsa.devel/58025").[/COLOR]
I believe confusion came about because the OP was using the internal header spdif, not the rear panel spdif, hence the output nid was changed to  0x10 from 0x06.

I looked recent commits in this area over at alsa and it looks like they are working on multiple spdif's for the snd_hda_intel.  maybe Ill see if i can give them a go.

My question is what does ubuntu want to do about this because currently( well except I havent gotten todays updates yet :) ) the rear spdif, which is the one most people would want working, is  broken?  I imagine other mobos that are using ALC1200 this would also apply to.  I dont know how much more updates are going into Jaunty, but would like it to ship with a working rear spdif for this motherboard

i'm guessing another workaround would be to utilize the internal header spdif .  i have ordered one of these [COLOR="Orange"][Asus SPDIF modules]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=300280713203")[/COLOR] to verify this.

thanks

let me know if I can help out

Randy

---

### Post by rperkins on 2009-03-19
compiling and installing alsa-driver-20090319.tar.gz from the alsa website gave me access to both spdif ports.  So I take it the alsa code handles the mobo properly, but all the changes arent in Jaunty.  

I'm thinking I'll wait for the next kernel update and then open a bug report, but I am open to suggestions also

thanks

randy

---

### Post by Oncle Ben on 2009-03-22
Hey randy,

I can't get my rear spdif to work on the same mobo either, but on Intrepid. This thread is probably not the best place to talk about that as I'm not even testing Jaunty but I thought maybe you could suggest a few things ? Note that I'm a complete Linux newb so I may have overlooked something obvious.

Thanks,
Ben

---

### Post by rperkins on 2009-03-23
ben

have you went thru setting up gnome to use the spdif ?

top right of screen , right click on the speaker.
left click on 'open volume control'
lower right of volume control, left click on preferences.
scroll towards bottom of list and check the switches for IEC958.
this is another name for spdif.  this will allow you to see the switches.
now on the volume control you will have a tab labeled 'switches'
select the IEC958 switches.  see if that helps.

the second thing is to use the top left menu
System-->preferences--> sound
change the settings for various types of sound playback to the digital output.  mine is called 'HDA Intel ALC1200 Digital ( ALSA ) but it wasnt called that when i was on intrepid.

hth

randy

---

### Post by Oncle Ben on 2009-03-23
Hey randy,

I had done the second but not the first. It works, hourray :D

Now I hope this will still work with Jaunty !
Thanks a bunch,

Ben

---

### Post by grigio on 2009-03-27
Is there an open bug to fix this in Jaunty?

---

### Post by rperkins on 2009-03-28
no i havent opened a bug.
currently I'm on vacation .
maybe I'll get a chance this week

---

### Post by grigio on 2009-03-31
[https://bugs.launchpad.net/ubuntu/+bug/352556](https://bugs.launchpad.net/ubuntu/+bug/352556)

I've opened a bug and I linked this thread as reference becauce I'd like to not compile alsa when Jaunty will be released.

---

### Post by rperkins on 2009-03-31
thank you
i confirmed your bug and added my 2 cents :)
glad you are now working properly.

spdif to my denon receiver is golden.

---

