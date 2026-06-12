---
title: "No Sound After Upgrade to The Latest Alpha"
date: 2009-01-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by iaskedalice09 on 2009-01-16
Hello,
I don't have any sound for alpha 3. Any idea why? I do want sound back. The only error I got was updating mysql. That didn't work. Everything else after the upgrade works, except sound.

---

### Post by panaut0lordv on 2009-01-16
install gnomealsa-mixer and turn da volume up ;)

---

### Post by tawmas on 2009-01-16
There have been a few good posts on this a few days ago. A quick search returned [this post]("http://ubuntuforums.org/showpost.php?p=6506156&postcount=9"). Fire up the first command given, and you'll probably discover you need to pump up the volume of a few channels.

There were other useful threads as well.

---

### Post by iaskedalice09 on 2009-01-16
Sorry, there's still no sound. I'm not sure what this is. Launchpad time?

---

### Post by taavikko on 2009-01-17
I have similar issue, laptop with external speakers plugged in as headphones
After every reboot, headphone channel is muted.

```
alsamixer -Dhw
```
And unmute, this fixes it for me.

---

### Post by ShirishAg75 on 2009-01-17
I think it is something to do with gstreamer. I also have no sound. I did put up a bug about it in [lpbug]317537[/lpbug] . Perhaps you can add some more info. or make a new bug-report. 

It is possible you may need to file a bug at launchpad. 

something like say, 

```
$ ubuntu-bug rhythmbox
```

and give the details.

---

### Post by iaskedalice09 on 2009-01-17
Hello,
I tried the alsa-mixer fix and it didn't work. The volumes are turned up. Watchjing the bug report. Let's hope it's found and destroyed soon.

---

### Post by iaskedalice09 on 2009-01-17
I'm pretty sure it's a gstreamer error because a while back a message popped about about it in Totem. *sigh* Since I don't know how to duplicate it, I can't report it. BTW, I use Totem most of the time. I'm odd.

---

### Post by macaholic on 2009-01-17
I have no sound at all, for any application, not just gstreamer ones, and none of the alsamixer fixes work for me either.
EDIT: A complete reinstall of all pulse packages solved the gstreamer application issues, but now flash 10 is the only stickler...

---

### Post by macaholic on 2009-01-17
Gah this is worse than I had thought, not only does Flash 10 audio not work; it shows up under volume control as firefox through ALSA, but no sound comes out, but after flash audio is attempted, no other audio will be palyed at all.

---

### Post by ShirishAg75 on 2009-01-17
you didn't have to do a reinstall. I don't know whether you tried or not. 

```
$ sudo /etc/init.d/pulseaudio restart
```This worked for me.

Then unmute the speaker icon and you are good to go.

---

### Post by gspat on 2009-01-17
Is there a file where the initial settings for alsamixer are stored? If there is, maybe just change that to something other than everything muted by default?

.:Edit

OK, I think I may have figured this one out...

It seems the alsa-init scripts were not being run on my machine, and maybe that is what is causing everyone else grief too.

to check if this might work for you, try this:

```
ls /etc/rcS.d/*alsa-utils*
```

Can someone else please try the following steps if they also get the error message?

first off, run alsamixer and get your settings right using:

```
alsamixer -D hw:0
```

then save the settings using:

```
sudo alsactl store
```

Next, set up a symlink to run your alsa-init script:

```
sudo ln -s ../init.d/alsa-utils /etc/rcS.d/S50alsa-utils
```

now when you reboot, you should have sound already setup for you.

---

### Post by panaut0lordv on 2009-01-17
Maybe you should install esound and remove pulseaudio?
For me it works much better and is more compatible.

---

### Post by vishalrao on 2009-01-18
This is why there is no sound :D

[http://0pointer.de/blog/photos/india-again](http://0pointer.de/blog/photos/india-again)

[http://0pointer.de/blog/photos/brazil](http://0pointer.de/blog/photos/brazil)

---

### Post by crimsun on 2009-01-18
> **macaholic said:**
> Gah this is worse than I had thought, not only does Flash 10 audio not work; it shows up under volume control as firefox through ALSA, but no sound comes out, but after flash audio is attempted, no other audio will be palyed at all.

This symptom is bug 314739 ([https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/314739](https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/314739)).

---

### Post by crimsun on 2009-01-18
> **iaskedalice09 said:**
> Hello,
I don't have any sound for alpha 3. Any idea why? I do want sound back. The only error I got was updating mysql. That didn't work. Everything else after the upgrade works, except sound.

Please download and execute the bash script at [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)

---

### Post by crimsun on 2009-01-18
> **gspat said:**
> Is there a file where the initial settings for alsamixer are stored? If there is, maybe just change that to something other than everything muted by default?

.:Edit

OK, I think I may have figured this one out...

It seems the alsa-init scripts were not being run on my machine, and maybe that is what is causing everyone else grief too.

to check if this might work for you, try this:

```
ls /etc/rcS.d/*alsa-utils*
```

Can someone else please try the following steps if they also get the error message?

first off, run alsamixer and get your settings right using:

```
alsamixer -D hw:0
```

then save the settings using:

```
sudo alsactl store
```

Next, set up a symlink to run your alsa-init script:

```
sudo ln -s ../init.d/alsa-utils /etc/rcS.d/S50alsa-utils
```

now when you reboot, you should have sound already setup for you.

This is bug 316430 ([https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/316430](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/316430)).

---

### Post by gspat on 2009-01-18
> **crimsun said:**
> This is bug 316430 ([https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/316430](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/316430)).

Yup, it sure is!

Wonder why I didn't find it when searching launchpad?

Oh, well... It was worth it to me to do the searching and figure out the problem!

---

### Post by iaskedalice09 on 2009-01-19
@crimsun [ALSA Bash Script Results](http://www.alsa-project.org/db/?f=c8b245390ecc081a352b166baecdc1dc8d559ddd)

@Everyone else - sorry, but STILL no sound. Thanks for your help.

---

### Post by iaskedalice09 on 2009-01-19
Not sure if this will help, but here are results of the ALSA-mixer after a fresh reboot in the attachment (text file). Scroll down please, I wasn't sure how to get all the whitespace out.

---

### Post by taavikko on 2009-01-19
Does this look familiar to you?
[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/316430](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/316430)

---

### Post by The Cokeaholics on 2009-01-19
> **panaut0lordv said:**
> install gnomealsa-mixer and turn da volume up ;)

Unbelievable, that is what I have been looking for so long. Thanks. 

"PCM Front" on my Audigy2 was lowered. I must say this alsa-pulseaudio extension has made it quite challenging.

---

### Post by iaskedalice09 on 2009-01-19
> **taavikko said:**
> Does this look familiar to you?
[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/316430](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/316430)
Yes, but I don't know how to properly implement the fix. Would someone here mind walking me through how to? Thanks. I'll let you know how it goes on Saturday.

---

### Post by taavikko on 2009-01-19
> **iaskedalice09 said:**
> Yes, but I don't know how to properly implement the fix. Would someone here mind walking me through how to? Thanks. I'll let you know how it goes on Saturday.

Just apply updates and issue should be solved.

---

### Post by gspat on 2009-01-19
grr.. bunged up again after latest updates and reboot!

This time is different though...

alsamixer shows all levels up

playback tab on volume controls shows system sounds (should it show this? I don't recall it showing that before) and totem-audio-preview when I mouse over a sample audio file I have on the desktop for testing.

all show the levels turned up... 

I seem to recall someone finding system sounds were doing something bad a while ago, gonna have to look for that I guess...

...off to launchpad I go after I get off work...

---

### Post by iaskedalice09 on 2009-01-23
Updated, but there's still no sound. *sigh*

---

### Post by scradock on 2009-01-23
The alsa-utils update did nothing to resolve the same problem for me. Installing gnome-alsamixer was the key move. It's a bore to have to run g-am from the terminal, but it did allow me to un-mute several channels which did not need to be muted. The _three_ pulse-audio control widgets (Pulseaudio Preferences from System | Preferences; Volume Control from System | Preferences or from Speaker Applet | Volume Control; Preferences from Speaker Applet Right Click menu) didn't seem to allow these channels to be un-muted.

Why is this a problem, so long after it was first reported, here and on launchpad? A nice new control widget is fine, but shouldn't it be checked to see if it works before being released instead of the boring old one that does?

/rant

---

### Post by momo54 on 2009-01-24
> **taavikko said:**
> I have similar issue, laptop with external speakers plugged in as headphones
After every reboot, headphone channel is muted.

```
alsamixer -Dhw
```
And unmute, this fixes it for me.
I did that, and it worked...
Strangely, the problem was not on "Master" but on "PCM out".
"PCM out" was set on "pre 3D". I set it on "post 3D" and the sound
came back.

I hope it can help someone else...

---

### Post by iaskedalice09 on 2009-01-24
There's nothing that's working for me here. :(

---

### Post by iaskedalice09 on 2009-01-24
Fixed! I was still using the alsamixer command in Terminal. Had to type ALT + F2 and type gnome-alsamixer and uncheck all the muted mute boxes. Thanks!

---

### Post by iaskedalice09 on 2009-01-24
Here's the graphical solution for those who need it: [Fixed: No sound on Ubuntu 9.04 (Alpha2) | Platonic](http://platonic.techfiz.info/2009/01/22/fixed-no-sound-on-ubuntu-904-alpha2/)

---

### Post by iaskedalice09 on 2009-01-31
There's no sound again after the recent upgrade. gnome-alsamixer looks fine.

---

### Post by jerrylamos on 2009-01-31
Some people must be putting a lot of time and effort into PulseAudio since it keeps breaking for lots of us.  

Maybe it works on their equipment.  I have four ordinary user computers, Compaq, IBM tower & laptops which it's usually broken on.  

Kudo's to the forums on how to get audio working again.  I like the "sudo killall pulseaudio" method.

Now if someone could get Intel video working again....Option "NoAccel" is dreadfully slow scrolling.

Jerry

---

### Post by iaskedalice09 on 2009-01-31
Killing pulseaudio worked for me. I did it "the Idiot's Way" and it now works. Thanks.

---

### Post by gletob on 2009-01-31
I tried killing pulseaudio and my sound is still broken after the update.

EDIT: Nevermind I'm a dummy

---

### Post by Gina on 2009-02-01
I think we all get those "dummy" moments at times :lol:

---

