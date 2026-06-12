---
title: "Ubuntu, mplayer and Hauppauge HVR 900"
date: 2015-09-02
forum: MINT
---

### Post by denisvh on 2015-09-02
Hello all,
I do not use exactly Ubuntu, but Mint, which is derived from Ubuntu, and I checked that my issue exists as well on Ubuntu (at least KUbuntu 14.04.3).
I capture videos from my Hauppauge HVR 900 device by using mencoder. I give below the command I use for mplayer for simplicity, but the mencoder command is almost the same one and simply adds the output file name et format settings :
mplayer -fps 25 -tv driver=v4l2:width=720:height=570:device=/dev/video1:input=1:audiorate=48000:immediatemode=0:forceaudio:alsa:amode=1:forcechan=2:adevice=hw.1,0 tv:// -aspect 16:9  -ao sdl -vf crop=720:566:0:0,pp=lb
it's not very simple but it works. I should say, it worked.
I use it for a long time with Mint. Recently Mint moved to a new version, obviously starting from a new version of Ubuntu. And with this new version, my capture stopped working.
With the above command, the video and sound are good when I use Mint 17.1 and previous versions. When I use Mint 17.2, or KUbuntu 14.04.3, the images are perfect, but the sound is completely distorted and unusable. For this, Mint 17.2 and KUbuntu 14.04.3 behave exactly in the same (bad) way. This does not come from the sound output. By using mencoder, I get the same distorted sound on the recorded file. This obviously comes form the capture part.
In my opinion, something recently changed in Ubuntu, propagated to Mint 17.2, making mplayer fail for the sound in the configuration I use. My concern is to understand what, in order to find a workaround, or to get a fix. Unfortunately, I do not know which Ubuntu version bring this change. All I know is that the change came to Mint in version 17.2.
For now, the choices I have are :
- keeping the current O.S. version, but it's frustrating as the new one seems to be more robust, and has interesting features, and I'm worrying for the future if no fix is found.
- moving to the new version and double boot to windows for video capturing (of course, the device works on windows as it's designed for it).
But none of these options are really satisfying.
Thanks for help !
D.F.
P.S.: if a fix exists in KUbuntu, it could be a solution, I use Mint because it has a good GUI, but I could use as well KUbuntu which has the same kind if GUI.

---

### Post by howefield on 2015-09-02
Thread moved to the "*MINT*" forum.

---

