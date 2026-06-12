---
title: "&quot;killall pulseaudio&quot; fixed sound on Alpha 3!"
date: 2009-01-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2009-01-29
Yesterday's jaunty updates, sound dead.  Read the jaunty forum, sound worked fine after: 
alsamixer V 
and set everything max.  Sound works fine. Loud!  You tube Shakira ojos asi.

Today's updates 20090129 sound dead again.  Alsamixer V still has everything max.  Read the jaunty forum again:
sudo killall pulseaudio
sound working again! Loud!

Thanks much, keep up the good work, forums!

Jerry

Compaq Presario 3.3 gHz Celeron
Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

---

### Post by marmuta on 2009-01-30
Haha, another great 'fix', good work forums :lolflag:. 
Poor pulseaudio, getting beaten left and right this time.

---

### Post by linux6994 on 2009-01-30
Thanks it worked for me!

killall pulseaudio

---

### Post by Gina on 2009-01-30
Has anyone reported this in Launchpad?

As soon as this bug is fixed we should have PA enabled for testing.

---

### Post by Timon&amp;Pumba on 2009-01-30
Killing an 'essential' (to be) application to work around it only helps yourself. That behavior does not contribute to improvements in general.
So, although it may be a short-term solution (you better try: pulseaudio -k), it is currently been advocated as THE way to go.

So, if you all contribute to the greater purpose, you may even find yourself surprised how good some applications will be in a few months or a year.

---

### Post by Gina on 2009-01-30
Precisely!

Until this last update, PA has been fine in Jaunty. I shall ***[I]not*[/I]** be disabling PA - I have other versions of Ubuntu and other machines to play music on.  I shall be checking for working sound with each update and watching for comments from others.

---

### Post by jerrylamos on 2009-01-31
> **Gina said:**
> Precisely!

Until this last update, PA has been fine in Jaunty. I shall ***[I]not*[/I]** be disabling PA - I have other versions of Ubuntu and other machines to play music on.  I shall be checking for working sound with each update and watching for comments from others.

I try to do most of my linux work with whatever is the latest version that will sort of run.  So I do workarounds for whatever isn't working to try to test the rest.  Yes, I keep trying to see if sound works every couple days and every big update (sometimes it does usually it doesn't) and if Intel graphics works (scrolls very slowly) situations that have been around since before Alpha 2.

I figure the developers work on whatever they want to, which may not be what some in the user community would like to see fixed.  That's the way it is.

It does amuse me that the way to get sound to work is to stop sound in various different ways - some people turn off login sound, others find different workarounds.  Nice to share solutions in the forums.

Jerry

---

### Post by vikrant82 on 2009-02-01
Try changing sound theme to "No Sounds", and try rebooting.

---

### Post by RaZoR1394 on 2009-02-01
> **vikrant82 said:**
> Try changing sound theme to "No Sounds", and try rebooting.

As said before this works just fine. There is no need for killing pulseaudio. :popcorn:

---

### Post by autocrosser on 2009-02-01
Interesting thing---I tried an "experiment"---I pulled the .asoundrc.asoundconf from my Intrepid install & used the .asoundrc that worked there also (I'll post it--I think that it came from the Tutorial for Pulse--just rename it from asoundrc.txt to .asoundrc) & rebooted......I got everything but the login sound without killing Pulse...

I'm sure that this won't work in all cases, but it works in mine---all of you might give it a try--I don't remember if I edited my .asoundrc.asoundconf file--I'm thinking that only the .asoundrc was modified.

I'm very sure that the .conf file is generated for your machine, but if anyone wants mine (if you don't have a Intrepid install)--I'll post it too.....

---

### Post by W2IBC on 2009-02-02
well, now I am dead in the water.

no sound no matter what.

System > Preferences > Sound (will do nothing at all,fails to load the "gui")

all commands that made it work in the past, now will not work.

---

### Post by marmuta on 2009-02-02
The gui seems to need pulseaudio. Try running 'pulseaudio' in a terminal and see if you can open it then.

---

### Post by W2IBC on 2009-02-03
well at 2:00am EST i had updates and "pulseaudio" was one of them.

Installed updates. restarted and now (so far) I have sound.

---

### Post by techdude3177 on 2009-02-03
i ran these updates as well but still no audio unless i had no sound for themes then the sound wouldnt work in firefox.
so i still have to use the kill pulse audio script.

---

### Post by Gina on 2009-02-03
My sound - which was working fine - is now all crackly.  Still using PA.

---

### Post by RaZoR1394 on 2009-02-03
> **KD8HHO said:**
> well at 2:00am EST i had updates and "pulseaudio" was one of them.

Installed updates. restarted and now (so far) I have sound.

Mmm, the update works fine with system sounds turned back on, on at least three systems..

---

### Post by dBuster on 2009-02-03
I had this same problem and if this thread was searched the answer is in my post.  But to make things easier, here is the solution:

This is the bug report and a work around:
[https://bugs.edge.launchpad.net/ubun...io/+bug/322374](https://bugs.edge.launchpad.net/ubun...io/+bug/322374)

A work around, at a terminal type:
```

pulseaudio -k ; start-pulseaudio-x11
```

---

### Post by W2IBC on 2009-02-03
sad news, turned the box on today, no sound. no commands will get sound back..

---

