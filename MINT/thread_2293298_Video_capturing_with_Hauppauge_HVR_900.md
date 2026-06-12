---
title: "Video capturing with Hauppauge HVR 900"
date: 2015-09-04
forum: MINT
---

### Post by denisvh on 2015-09-04
I use an operating system derived from Ubuntu, Mint, but I checked that my problem exists as well on Ubuntu, at least on KUbuntu 14.04.
I record videos for a long time by using an Hauppauge HVR 900 device and the mencoder software. The mencoder command for doing so is as follows (for a one hour record):
mencoder -fps 25 -tv driver=v4l2:width=720:height=570:device=/dev/video1:input=1:audiorate=48000:immediatemode=0:forceaudio:alsa:amode=1:forcechan=2:adevice=hw.1,0 tv:// -vf pp=lb -aid 1 -o "output.avi" -ovc xvid -xvidencopts bitrate=3000:turbo:vhq=0 -oac mp3lame -lameopts cbr:br=128:mode=0 -endpos "01:00:00"
Not as simple that I would like, but it works very well, or I should say it worked very well.
Mint published a new version, 17.2. And with this new version, the command above records videos with a very good image, and a completely distorted sound, completely unusable.
Same thing of course when using mplayer just for viewing videos from the device.
This seems to come from a recent change in Ubuntu, propagated to Mint in version 17.2. I Checked that this very bad sound is present as well with KUbuntu 14.04, so clearly, its a common issue to Ubuntu and Mint, coming from a change in Ubuntu.
My concern is to find a workaround for this, working or not with Mint but at least working for KUbuntu (I can move from Mint to KUbuntu, as in terms of GUI they are not so different from each other).
For now my only options are :
- To stay in Mint 17.1 (the capture works perfectly with this version), but it's not a good solution if the problem I'm facing is never fixed in Ubuntu/Mint.
- To move to a newer version and to dual boot to Windows for video capturing, but this is not as well a satisfying solution.
Thanks for help.

---

### Post by howefield on 2015-09-04
Thread moved to the "*MINT*" forum.

---

### Post by denisvh on 2015-09-04
Understood, but the same problem exists in KUbuntu, it's not a Mint issue. I'm looking for a solution for any Ubuntu derived system having a "start" menu (like Mint or Kubuntu). I'm wondering about the fact that no fix will come from this forum, and will stay without any solution, either for Mint or for Ubuntu.

---

### Post by howefield on 2015-09-04
As you are using *MINT* you are very welcome to post in this *MINT* forum, however you may also consider supporting the [MINT]("http://forums.linuxmint.com/") forums.

---

### Post by denisvh on 2015-09-04
Yes, I'm too fair. As I tested the same issue on KUbuntu I should not have talked at all about Mint. I talked about Mint because I can say exactly in which version the change which broke the recording activity occured.
The problem wiith Mint specialists is that they are mainly working on what they add to Ubuntu : Cinnamon or Mate.
But the issue is clearly not in these parts of Mint, it's in the part coming from Ubuntu. I posted as well a message in the Mint forum, but I'm not sure that this will help a lot. I would not like to be forced to switch back to Windows because of this issue. I switched to linux when I saw that it was possible to capture videos with this O.S. (a long work to find the right way). If Linux becomes unable to do it (it seems to be the case in recent versions), I will have to reconsider it and may be move back to windows. A sad end of the story. Really hoping to have some help from the Ubuntu community, as it's clearly an Ubuntu issue.

---

### Post by howefield on 2015-09-04
Duplicate thread closed.

---

