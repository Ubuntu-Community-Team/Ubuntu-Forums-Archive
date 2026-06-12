---
title: "auto play mp3 doesn't work for me"
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-05
i have been told by a friend that in ubuntu you only need to put the mouse over an mp3 file an it should play on is own and it doesn't why is that?

thanks in advance.

---

### Post by cgroza on 2010-04-05
what version of ubuntu are you using?

---

### Post by aviramof on 2010-04-05
lates 10.04 beta1 of course will all updates till now.

---

### Post by cariboo on 2010-04-05
Have you got all the proper codecs installed? I usually install the ubuntu-restricted-extras meta package.

---

### Post by aviramof on 2010-04-05
yes i do i even made my self a command i use to install everything tell me what you think of it:


sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update && sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo aptitude install ubuntu-restricted-extras avidemux wireshark axel axel-kapt gnome-alsamixer amule p7zip-full p7zip-rar gparted gbackground Screenlets startupmanager acpi gnome-device-manager apt-p2p smplayer wine human-theme x264 python python-gtk2 intltool gettext nfoview icedtea assogiate system-config-samba fusion-icon simple-ccsm emerald vlc picasa pppoe cheese compiz ubuntu-tweak compiz-fusion-plugins-extra gmountiso subversion rar apache2.2-bin libapache2-mod-dnssd git-core gimp w32codecs skype alsa-oss shutter faac gnome-themes-more faad flashplugin-nonfree gstreamer0.10-ffmpeg samba gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse git-core wine gstreamer0.10-plugins-ugly gshare gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs unrar && sudo aptitude install xfonts-terminus compiz-fusion-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool libgl1-mesa-dev and libglu1-mesa-dev && sudo fc-cache -fv && svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer

---

### Post by Lollerke on 2010-04-05
It's working for me. I only have gstreamer ffmpeg and gstreamer ugly installed.

---

### Post by cariboo on 2010-04-05
Make sure you have preview set properly in Nautilus->Edit->Preferences->Preview. See screenshot.

---

### Post by jfernyhough on 2010-04-05
[s]You also need mpg123 installed for the sound preview to work.

$ sudo aptitude install mpg123[/s]

--edit
Oops, was a very old fix (7.04?). :-\" Not needed!

---

### Post by cariboo on 2010-04-05
I don't have mpg123 installed, and it works for me.

---

### Post by fluteflute on 2010-04-05
> **jfernyhough said:**
> You also need mpg123 installed for the sound preview to work.

$ sudo aptitude install mpg123
Was mpg123 once in main? Because I'm sure this used to be default functionality! I feel a bug report coming on if Nautilus has settings that don't work without this package...

EDIT: Preview doesn't work for me with or without mpg123 installed.

---

### Post by aviramof on 2010-04-05
it doesn't work for me with or without mpg123 i see a small icon on the mp3 file icon when i move the mouse over the mp3 file but it doesn't play.

when i check in gnome-volume-control application audio preview i can see it but i can't change the volume or anything because i can't move the 

mouse of course or it would disappear.

---

### Post by aviramof on 2010-04-05
Update:

problem solved i managed to increase the volume in gnome-volume-control application audio preview without moving the mouse but you really need 

to make up your mind about something in gnome-volume-control full blue line is sound and an  empty one is mute in GNOME-Alsa Mixer it's the other

way around empty  line is sound and full blue one is mute.

---

### Post by aviramof on 2010-04-05
i just want to empathize that this small problem should be fixed so please don't forget about it.:)

---

### Post by cariboo on 2010-04-05
Doesn't turning up the volume in the indicator bar applet, then previewing the song work? Unless you have 2 mice connected it would be pretty hard to turn up the volume while previewing a song. Personally I use the volume control keys on my keyboard to set the volume levels.

The idea is that with pulseaudio, there should be no need to use the alsamixer to adjust the volume levels

**Edit**: I was just playing with things on my netbook and ran in to the same problem. With the Sound Preferences->Applications window open, I used the tab key to get to the volume control, then used the right and left arrow keys to turn the preview volume up and down.

---

### Post by aviramof on 2010-04-06
i already knew that and that is what i did the confusing part is that in  gnome-volume-control full line mean audio but in my other audio controler GNOME-Alsa Mixer it's the other way around.

---

