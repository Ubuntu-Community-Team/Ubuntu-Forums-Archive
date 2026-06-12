---
title: "I have scratchy sound coming from the speakers when I mute the volume"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bcasanov on 2008-10-29
Hi, 

I'm having a problem with scratchy, sort of staticky sound coming from the speakers when I mute the volume.  When I unmute the volume, this scratchy noise does not occur, just the normal sound you would expect to hear.  I have upgraded to Ubuntu Intrepid.  I first noticed this problem when I logged in after setting the volume level to mute, and instead of not hearing the login sound, I heard the scratchy noise.

Let me know if you need any more information.

---

### Post by 16777216 on 2008-10-29
You may have to turn up the speakers for the following.


[LIST]
[*]Does the sound "play"[FONT=Arial][SIZE=2] continuously[/SIZE][/FONT]?
[*]Does it change in pitch or "buzz" when moving the mouse or with disk, WiFi, or, CPU activity?
[/LIST]
If so it is probably just [RF noise]("http://en.wikipedia.org/wiki/Electromagnetic_interference") leaking from the components of your computer.

If the above holds true then reducing the volume of the "PCM" or "Main" ( or possibly another ) in the mixer and turning up the volume on your speakers may help reduce the noise you hear, or you may need to do the opposite and turn one or both of those up and use a lower volume on your speakers if they have a volume control.

---

### Post by bcasanov on 2008-10-29
I discovered that the volume buttons on my laptop are connected to the volume levels of the PCM.  When the PCM is on mute, the scratchy sound can be heard if the master volume setting is high enough.  When I lower the level of the master volume, the scratchy sound gets lower and lower until I can no longer hear it.  However, the scratchy sound all but disappears if I unmute the PCM, even if the PCM is set at a low level.  I have set the master volume level to its maximum, and then controlled the volume level I wanted through changing the PCM level.

In response to your questions, the sound plays continuously, and it doesn't change in pitch or "buzz" when moving the mouse or with disk, WiFi, or CPU activity.

As an aside, I haven't had this problem before in Hardy.

---

### Post by bcasanov on 2008-10-29
Just in case you need more information, such as the type of sound card I have, the result of "lspci | grep -i audio" is: 

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

---

### Post by 16777216 on 2008-10-29
A laptop eh?
Still sounds like RF noise but I am not certain why this has started or how to solve it beyond adjusting the mixer levels so that it is not as noticeable. Sorry.

---

### Post by bcasanov on 2008-10-29
Yep, it is a laptop, Dell Inspiron 1420N.  I'm not sure what to make of this problem, since I did not have any worries of this in Hardy, or even Gutsy or Fiesty.

Does anyone else have a similar problem or know what could be causing this that may not necessarily be RF-related?

---

### Post by BackwardsDown on 2008-10-29
Yes, I'm having the same problem. (exactly the same audio-card)

Bug report:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/220842](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/220842)

---

### Post by bcasanov on 2008-10-29
Thank you for that bug report link, BackwardsDown!  I feel a little better knowing that it's not just me having the problem, and that there are actually quite a number of people out there who are in the same boat regarding the crackling, scratchy sound when the volume level is muted. Let's hope and see if anyone can come up with a solution.

---

### Post by bcasanov on 2008-10-29
Well, as a temporary solution until a patch or something might come along, I went to System>Preferences>Sound, and under the Devices tab, where it says "Select the device and tracks to control with the keyboard" I selected Master, instead of PCM.  I set the PCM level to its maximum, and then muted the Master using my keyboard volume button.  There was no crackling/staticky noise when I played a sound and had the volume muted.  I don't know if this will work for you, BackwardsDown, but I think it might have worked for me.

---

### Post by 16777216 on 2008-10-29
You guys are right the problem is not RF.
Sorry I don't have a solution, but, the more you add to the bug report the better the chances it will get fixed.

---

### Post by BackwardsDown on 2008-10-29
> **bcasanov said:**
> Well, as a temporary solution until a patch or something might come along, I went to System>Preferences>Sound, and under the Devices tab, where it says "Select the device and tracks to control with the keyboard" I selected Master, instead of PCM.  I set the PCM level to its maximum, and then muted the Master using my keyboard volume button.  There was no crackling/staticky noise when I played a sound and had the volume muted.  I don't know if this will work for you, BackwardsDown, but I think it might have worked for me.

I've uninstalled intrepid last week (it's just to distracting in my exam-week:)), but I try it when I install the final tomorrow.

---

