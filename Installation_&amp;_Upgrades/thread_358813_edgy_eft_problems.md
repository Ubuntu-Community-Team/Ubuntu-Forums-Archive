---
title: "edgy eft problems"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by drayan69 on 2007-02-11
Hi all, earlier I was having ubuntu ver. 6.06 and 5.10 on two of partititions. I decided to overwrite ver. 5.10 with ver 6.10. Despite going thru unofficial support pages on web and doing all suggested I am facing following problems in ver 6.10(. Ver. 5.10 was far better. I regret removing the same):

(1) despite all the multimedia codecs as well gxine libxine installed, whenevr i I try to play video files with .wmv and .mov extensions FROM DVD, the video and audio do not go in unison. I mean there is no synch. between sound and video. The progress bar of Totem Movie Player(ver 2.16.2) oscillates forward and backward. Some times it plays for 3 to 4 secs. and then automatically is PAUSED reset to begining. In xine movie player the movies open in BLACK AND WHITE instead of colour.

(2) i can not open video or audio files on websites inside firefox.

(3) flashplayer does not work in opera. in firefox it works but the window is too tiny and i can not resize it. clicking, right clicking and selecting settings has no effect. 

To sort out the problems I followed the following from " Unofficial Ubuntu 6.10 (Edgy Eft) Starter Guide" but to no avail: QUOTE

[   Multimedia Players & Browser Plug-ins
[edit][COLOR="Red"]
How to install Multimedia Codecs[/COLOR]

    * Read #General Notes
    * Read #How to add extra repositories 

sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 

    * Read #How to restart GNOME without rebooting computer 

Stubby: All known codecs work except for wmv.

TTo: To enable WMV9 playback, you can try:

sudo aptitude install gstreamer0.10-pitfdll && rm -r ~/.gstreamer-0.10/
[COLOR="Red"]
How to install DVD playback capability
[/COLOR]
ironss: gstreamer dvd plugin is available as part of plugins-bad (or ugly?) and does not work reliably. However, Totem works with the xine backend to play back DVDs. This will keep you going until gstreamer gets dvd playback. Note that you do not have to install xine-ui or mplayer as suggested in

    * Read #General Notes
    * Read #How to add extra repositories 

sudo aptitude install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo aptitude install totem-xine

Stubby: gstreamer dvd plugin not ported to Edgy yet. following instructions will not work properly

    * Read #General Notes
    * Read #How to add extra repositories 

sudo aptitude install libdvdcss2 ] UNQUOTE

PLEASE HELP ME and suggest workarounds these problems.

Thanks in advance:
[COLOR="Blue"][I]
System PIII 450, COMPAQ 100P, RAM (64+128+128 MB); 
hda1 - windows 98se; hda2 - ubuntu 6.10; hda3 - Mandriva 2006 and hda6 - ubuntu 6.06[/I][/COLOR]

---

