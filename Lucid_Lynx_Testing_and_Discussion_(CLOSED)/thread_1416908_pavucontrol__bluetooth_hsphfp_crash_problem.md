---
title: "pavucontrol / bluetooth hsp/hfp crash problem"
date: 2010-02-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jwssr on 2010-02-26
This problem has been present for quite some time...time to clean it up?

using bt devices...specifically mot S305  and S805 headsets...

when using a2dp services only...no problems..works aok.   but

when trying to use headset services causes pavucontrol to crash...when restarted, pavucontrol shows bt device off  (3 choices here..a2dp,headset,off).

when clicking connection to headset....2/3 secs of sound...then crassh with popup window..clicking close on this terminates window for pavucontrol.

Anyone else see this problem?

I have filed a bug report..

---

### Post by jwssr on 2010-03-01
found the answer to this problem....I believe...

thanks to Boondoklife at the blueman forum....

in /etc/bluetooth/audio.conf

set to false,,,orig is true
:
# Set to true to support HFP, false means only HSP is supported
# Defaults to true
HFP=false

I also changed this:

# Automatically connect both A2DP and HFP/HSP profiles for incoming
# connections. Some headsets that support both profiles will only connect the
# other one automatically so the default setting of true is usually a good
# idea.
AutoConnect=true

---

### Post by xak on 2010-03-24
I'm really curious how you got your S805 headset to work. I have one also, and on Lucid alpha3 and beta1 it pairs fine with the Bluetooth app, but no Output device ever shows up on the Sound Preferences app to send the audio to. What am I missing? :confused:

More info: [http://ubuntuforums.org/showthread.php?t=1425124](http://ubuntuforums.org/showthread.php?t=1425124)

---

### Post by jwssr on 2010-03-24
short answer....paman, which is the pulseaudio volume control...

apt-get install paman.

It will reside in applications/sound and video/pulse audio volume control.
I leave a shortcut for this in my gnome-panel..because you will use it a lot.

I also use blueman from the ppas rather than the gnome bt app. it is more user friendly.

after connection to bt..rightclick on motorola 805 device and connect to ...either 1 headset services or 2 a2dp.  blinking blue button at bottom of app shows connectivity.

now to paman(pulseaudio vol control).
  across the top of app are 5 buttons...
playback   record  output devices  input devices    configuration

the 3 you are interested in are payback   output  and  config

look at output first..it will show you each of your output sinks(devices) and the vol control bar...just for viewing.

next config...looks just like output....but here you an  select your sinks to connect or disconnect.

then fire up vlc to play some good pink floyd...initially the sound sould be coming from the default speakers..

then click on playback....here you will see all apps tat are using any of the sinks...you can have multiple apps playing sound..

left click on the box to the right of : audio stream on       and select where to send sound...   thats it..

I have included some sreenshots for you..

Important...without the blue dot blinking at the bottom right of the Bluetooth Devices (blueman)....it is not connected...

best of luck..

---

### Post by xak on 2010-03-24
Thanks for posting all that info.

I am familiar with this method, in fact I used paman + blueman on Jaunty with the same S805 headphones as well as a similar Belkin A2DP device.

I was just hoping to get my S805's working with the new built-in pulseaudio/bluetooth apps in Lucid, since they work perfectly with my Belkin device. I'll consider filing a bug on launchpad since it looks like an issue with only the S805.

Back to rocking out to Floyd :guitar:

---

