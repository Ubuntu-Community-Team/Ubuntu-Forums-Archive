---
title: "Sound issue with a 3rd party program called Sense (based on scratch)"
date: 2013-02-23
forum: Installation &amp; Upgrades
---

### Post by mrrobbins1 on 2013-02-23
Hi,
 I currently am running ubuntu 10.04 (Backtrack) and seem to have an  issue when I try to instruct a sense program to run a sound such as  drums.
 I subsequently ran sense.sh from command-line which initially depicts  no errors until I try to execute a sound such as play drums in a sense  script, then I am given the output error messages as follows:
 **/home/doc/dev/squeak/src/squeak-svn/platforms/unix/vm-sound-PA/sqUnixSoundPulseAudio.c:  pa_simple_new() failed: Connection refused.**
 **/home/doc/dev/squeak/src/squeak-svn/platforms/unix/vm-sound-PA/sqUnixSoundPulseAudio.c:  pa_simple_new() failed: Connection refused.**
 The problem seems to be that sense looks for the audio driver/files  perhaps? I have checked to see if the /home/doc/.. directories exist and  I can't seem to find them anywhere.
 I am confident enough to not require the sounds to actually be played  when testing my programs however it would still be nice to fix this  issue.

---

