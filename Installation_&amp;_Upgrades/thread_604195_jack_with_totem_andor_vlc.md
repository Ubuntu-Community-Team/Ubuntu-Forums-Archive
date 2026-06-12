---
title: "jack with totem and/or vlc?"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by battles33 on 2007-11-05
i've read up on the net quite a bit, but nothing that i found has seemed to be of much help. what i'm trying to do is set up the audio output from totem and/or vlc to work with jack. so for totem, i found this: [http://packages.debian.org/sarge/gstreamer0.8-jack](http://packages.debian.org/sarge/gstreamer0.8-jack) which would be great except libgstreamer0.10-0 is already installed and 0,8 only seems to want to work with libgstreamer0.8-0 and not 0.10-0. could 0.8-0 be installed along with the currently installed 0.10-0?

also, i found this tutorial for setting up vlc with jack: [http://www.jbkempf.com/blog/post/2007/05/06/Build-VLC-media-player-under-Ubuntu-Feisty-704](http://www.jbkempf.com/blog/post/2007/05/06/Build-VLC-media-player-under-Ubuntu-Feisty-704)

...except once i get to the final step of "make" i get some errors dealing with x264 and possibly the ffmpeg

alongside to the above forum, i also found this: [http://rpm.pbone.net/index.php3/stat/4/idpl/5129050/com/vlc-plugin-jack-0.8.6c-3plf2008.0.x86_64.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/5129050/com/vlc-plugin-jack-0.8.6c-3plf2008.0.x86_64.rpm.html)

which is a jack plug in for vlc. sadly, this is an rpm intended for mandrake and/or ALTLinux. no ubuntu support from that website i tried the mandrake rpm, however ubuntu won't work with the file type.

if anyone could help me in finding out how to solve this problem, it'd be immensely appreciated.

---

### Post by battles33 on 2007-11-06
has anyone read this? any bit of help would be appreciated, i've been trying off and on to figure this out myself and listed below is what else i've accomplished since the last post.


i found gstreamer-jack-0.10 at a mandriva site (i found it very odd that ubuntu doesn't have it, any particular reason?), anyway here's the link: [http://club.mandriva.com/xwiki/bin/view/rpms/Application/gstreamer-jack](http://club.mandriva.com/xwiki/bin/view/rpms/Application/gstreamer-jack)


so with the mandriva file, it's an RPM so i installed Alien to convert the RPM to a deb file so that it can be installed on ubuntu. so now gstreamer's jack plugin is installed. now, just have to connect the gstreamer to jack somehow :s
if anyone happens to know anything about this that'd be awesome i don't think this is hard, just this linux stuff is all quite new to me still and i'm just scratching the very outer layer.

---

### Post by battles33 on 2007-11-06
So me being me, i forgot about that rpm for vlc. so i "aliened" the rpm for the vlc jack plugin, and..... success!

in the terminal, one can type "vlc --aout jack" without the quotes, or instead of that just hit up settings>preferences in vlc and select jack as the audio output (make sure to do advanced options). play a file, and vlc's audio output will be routed out to and will show up in jack. absolutely beautiful. so now, all that's really needed is to crack the gstreamer. i haven't rebooted yet so that might do the trick, but i'm pretty sure there'll be some files to edit or some commands to run in order to get totem working with gstreamer and then outputting to jack.

why am i still interested in totem? because should anyone ever actually read this (and i have in fact found forums where other people have desired the same set-up as i'm trying to get going), they'll have an answer for ubuntu's default video player. also, should anyone encounter problems with vlc there's an alternative video player that'll work with jack as well. i know this can be done because for the distro 64studio totem (and another program i'd like to set up sound juicer) has totem working right out of the installation with jack. once again, should i encounter any progress, i'll type it up and submit my results to anyone who's curious.

---

### Post by DrFunn on 2008-01-22
Thank you for posting your thoughts on this topic for others to find. Just wanted you to know that your effort is helpful to me, so you deserve good karma points! 

I hope to do some live experimental performances using Ubuntu Studio 7.10. I am trying to play multiple high quality FLAC encoded audio files at the same time and get them into the JACK audio system for filtering, reverb, convolution and other treatments.

I was looking to use some sort of media player as an obvious solution. However, now that I am writing my thoughts down, I think that maybe some sort of sound mixer like ardour or audacity might be a better idea. I would assign a FLAC audio file to each mixer channel, loop it, and fade each audio source in and out as needed.

---

### Post by Magzee on 2008-01-23
Hey Battles 33, thanks for your efforts in trying to figure out Jack.  I was about to delete Jack from my system because it just doesnt want to play nice.  But after coming across your (previously unanswered) thread, well I might just mess around with it a bit more.  By the way I changed my sound (drivers?) away from Jack and instead am using Alsa..  all is good in my land of "Doof".  In case that is only an Aussie term, doof is majorly thumping base!!  My preferred ap is vlc, as it seems to work with most media, and I also like a very basic program Beep Media Player.  I go on what my music sounds like, rather than the bells and whistles.  Karma Kudos to you.

---

