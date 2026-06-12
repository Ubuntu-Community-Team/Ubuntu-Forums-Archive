---
title: "PulseAudio MAGIC"
date: 2009-09-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jwssr on 2009-09-07
First of all, a hugh pat on the back of the developers/contributors of this project...

I have been putting PA thru some heavy testing the past few months...seeing...like most of you...many ups and downs...mostly ups!

I am testing on two different boxes,which both triple boot win7, jaunty and Karmic.

     box 1.   amd64, video=hdmi output to 47in lcd.....sound=hdmi to spks on lcd..
              sound=analog steroe to reg small computer speakers   
              sound=bluetooth...mot s305 headset.
---------------part of my lspci output--------------------------------------
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
-----------------------------------------------------------------------------------

     karmic alpha4...daily updates (alpha5 installs.. but will not pass login...loops).
     bluetooth..both gnome and blueman.
     vlc,rythmbox,movieplayer only.

just a wee note about bluetooth here..not to digress.
Reading thru this forum..the developers think that Blueman is not up to snuff to put into karmic...but gnome BT manager lacks capabilities..such as... allowing a2dp connections..which blueman does...without blueman, I could not connect my BT device. 
-------------------------------------------------------
-------------------------------------------------------
     box 2    intel 64, video nvidea 8400  (hdmi,dvi,db14 connectors) using dvi to 24in lcd
               sound=analog stereo  alc888 to reg stereo spks
                sound=usb headset
                Hauppauge Dig TV pci-e card (another story)

               karmic alpha5  daily updates (thru9/7)
                bluetooth...both gnome and blueman
                vlc,rythmbox,movieplayer
-----------------------------------------------------------
-------------------------------------------------------------

     apps that I RELY on.and believe are mandatory...

                   paman           shows you everything!
                   pavucontrol     (apps/sound&video/pulseaudio volume control)
                   gnome alsamixer (apps/sound&video/gnome alsa mixer)

       apt-get install paman....will install pavucontrol 
       apt-get install gnome-alsamixer  
                 
                     (to get digital sound....ice958 has to be checked in gnome alsa mixer)

                     to run paman  terminal  no root  $paman...a control box pops up
                     pavucontrol   MENU  apps/sound&video/Pulseaudio Volumn Control
                     gnome alaa    MENU  apps/sound&video/Gnome ALSA Mixer  
-----------------------------------------------
I try to run the same test on win 7....realteks apps for sound and control panel app looks good and works good...
I dont know yet whether win7 will play sound thru multiple sinks SIMUTANEOUSLY as KARMIC IS NOW DOING..

This discussion applies to Box 1 only...

After updating to PA..test7 .....2 days ago...AND the (NEW ati)FGLRX drivers.
THE MAGIC has arrived...well somewhat!
 
ati 3d starting working again...(first time since kernel 6.2?..lots of discussion in this forum about this...since my digital sound (ati azalia) goes thru hdmi...crutial).

I can now have one app... vlc... playing sound thru hdmi or BT headset (mot s305) 
AND rythmbox sending sound thru analog speakers SIMUTANEOUSLY...
when I try to add a 3rd app..firefox (youtube)...evrything breaks...no sound at all...

this may be a function of my cpu not having the horsepower?????

NO fear...just kill all apps running sound...vlc  rythmbox  ff....fire them up again...all is ok.....

and we are not even to BETA yet...tks again guys!

I noticed some time back..with all of the small changes to the desktop...the speaker icon on taskbar disappeared....but...for a good reason...which I have discovered...

Just...leftclick /apps/sounds&video/pulseaudio voulume controll....then "add this launcher to panel".....

VIOLA!!!!  your NEW VOLUMN CONTROL ICON
SINCE we can now have multiple apps running sound...SIMUTANEOUSLY...you can controll the sound for each app by clicking on this ICON .....which opens this control box..click on playback tab..select which app you want to control.

Before...one icon to control only one sound output.....
NOW......one icon to controll Multiple sound output....

we no longer live in the "one man band world"....how friggin cool is THIS?

There are still some hiccups happening to me...such as ..when..vlc is outputting to BT headset and rythmbox is outputting to analog spks and if I go into paman while both apps running.
both apps..vlc and rythmbox break...cracklingg sound...shuts down both apps..

I hope this small tidbit helps others who may be wrestling with PA...

AGAIN thanks devs/contributors.   

---------------------------------------------------------------
Things I plan on testing in the very near future.

1. multiple BT adaptors in this box to allow multiple connections to softphone apps...ie ekiga, xten-xlite, gizmo, and my fav toy...asterisk.

2. streaming-in audio/video thur vlc (using one of the two sinks on this box)...from boxes on this lan ...while other sound apps are utilizing the other sink.

---

### Post by hugmenot on 2009-09-07
I&#8217;m glad that you have a good experience, but your post looks somewhat disorganized.
Is this stream-of-consciousness or your lab notebook?

---

### Post by jwssr on 2009-09-07
whatever you deem it to be!

obviously your intellect is superior to mine.

post was meant to be helpful to most of the newbies to Ubuntu...
not to the uber-intellect, such as yourself.

sorry for your inconvenience.

---

