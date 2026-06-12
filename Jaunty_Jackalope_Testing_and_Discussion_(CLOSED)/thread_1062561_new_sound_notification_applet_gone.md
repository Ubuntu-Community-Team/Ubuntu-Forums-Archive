---
title: "new sound notification applet gone?"
date: 2009-02-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2009-02-07
Just did updates---noticed that there were several pulse updates & when it was all done the new sound notification applet was gone---anyone else have that problem?

---

### Post by Elfy on 2009-02-07
Yea I've lost it too - I thought it was just me though - fiddling with pulse to stop the stuttering ... again :(

---

### Post by olskar on 2009-02-07
> **forestpixie said:**
> Yea I've lost it too - I thought it was just me though - fiddling with pulse to stop the stuttering ... again :(

Is your loginsound stuttering too?

---

### Post by Elfy on 2009-02-07
> **olskar said:**
> Is your loginsound stuttering too?

I've not noticed it doing it

I tend to listen to quite long tracks, so say I was listening to a 15 minute one - it'll stutter a bit towards the beginning then be ok for a while - but probably 6 or so times before the finish.

Almost makes me nostalgic for old and abused vinyl :)


Edit - appears it was this issue [http://ubuntuforums.org/showthread.php?t=1005668](http://ubuntuforums.org/showthread.php?t=1005668)

---

### Post by bruce89 on 2009-02-07
```

gnome-media (2.25.5-0ubuntu2) jaunty; urgency=low

  * debian/control.in,
    debian/gnome-media-common.install,
    debian/rules:
    - enable the intrepid version of the mixer capplet rather than the new one
      (lp: #324807)

 -- Sebastien Bacher <seb128@ubuntu.com>   Thu, 05 Feb 2009 16:13:35 +0100

```

Typically Ubuntu.

---

### Post by autocrosser on 2009-02-07
So, now I don't seem to have any access to the control panel for sound--I put in the old applet, but it now opens a mixer--not the apply sounds to actions that I would expect.......:(

---

### Post by Vaun on 2009-02-07
The distortion/stutteting a bug in libcanberra 0.11 with event sounds.  It's fixed upstream, but not yet in a release.  I included the patch from upstream on Launchpad.

[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/322344](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/322344)

---

### Post by autocrosser on 2009-02-07
Thanks bruce!!  I've opened a bug report at: [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/326607](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/326607)  about the issue....


> **bruce89 said:**
> ```

gnome-media (2.25.5-0ubuntu2) jaunty; urgency=low

  * debian/control.in,
    debian/gnome-media-common.install,
    debian/rules:
    - enable the intrepid version of the mixer capplet rather than the new one
      (lp: #324807)

 -- Sebastien Bacher <seb128@ubuntu.com>   Thu, 05 Feb 2009 16:13:35 +0100

```Typically Ubuntu.

---

### Post by techdude3177 on 2009-02-07
great so they take away the new sound preferences and give you the old sound control menu but dont give you the old sound preferences menu....

---

### Post by plun on 2009-02-07
> **autocrosser said:**
> Thanks bruce!!  I've opened a bug report at: [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/326607](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/326607)  about the issue....

Well... the sound is there with help from PA volumevontrol

So just install **padevchooser** for everything.

Volume is down to zero and also wrong sink.....

Another "brown bag"..;)

---

### Post by autocrosser on 2009-02-07
The problem is that you can no longer select sound themes, default alert volume or master system volume (at least all in one control panel)--in other words---a severe regression.

Please goto the bug report & add comments

---

### Post by plun on 2009-02-07
> **autocrosser said:**
> The problem is that you can no longer select sound themes, default alert volume or master system volume (at least all in one control panel)--in other words---a severe regression.

Please goto the bug report & add comments

Yeah, but that is obvious and so is the bug report IMHO.

With pavucontrol you can get this "brown bag"thing working....;)


Its Saturday...:D

---

### Post by psych on 2009-02-07
Will the new volume control applet come back???

---

### Post by autocrosser on 2009-02-07
From what I read in the respond to the report---not until 9.10

---

### Post by psych on 2009-02-08
Why???
It worked really good... so what is the problem?

---

### Post by Nullack on 2009-02-08
Hopefully the system sound preferences app will be added to the default build soon so I can turn off system sounds.

---

### Post by autocrosser on 2009-02-08
> **psych said:**
> Why???
It worked really good... so what is the problem?

From the bug report: It has been decided to use the intrepid version because the jaunty ones have several limitations, you can look at the gnome-media buglist, not sure what you consider possible in the jaunty version which was not there in intrepid, the new capplet doesn't work when using alsa directly, doesn't allow to control other channels or numeric sources either (from [Sebastien Bacher]("https://bugs.launchpad.net/%7Eseb128"))


I didn't find limitations, but I guess that people have been complaining.......

---

### Post by Nullack on 2009-02-08
Its more of a limitation not to be able to turn the sounds off or whatever compared to the limiations before so I find it a strange argument.

---

### Post by autocrosser on 2009-02-08
> **Nullack said:**
> Its more of a limitation not to be able to turn the sounds off or whatever compared to the limiations before so I find it a strange argument.


Yes--its not making sense to me either---I really liked the new functionality--at least they could bring back the old control panel....

---

### Post by kabloink on 2009-02-08
> **Nullack said:**
> Hopefully the system sound preferences app will be added to the default build soon so I can turn off system sounds.

You should still be able to turn the sound events off using the gconf-editor. 

desktop>gnome>sound>event_sounds (unselect)

---

### Post by autocrosser on 2009-02-08
True, but we are just "venting" about lost functionality--a regression is a regression & work-arounds after having it are not the same.

---

### Post by Mr. Picklesworth on 2009-02-21
This is a shame. It makes me sad :(
Now we'll have another release where users are encouraged to break their audio setup thanks to the mindless collision of ALSA and PulseAudio controls on  the desktop.

Anyone know if this change is happening upstream? (Personally, I've learned that GNOME is quite trustworthy with regards to releasing solid code, and I tend to agree that their choices should be followed precisely).

Besides that, the existing volume applet is also pretty broken. A user has to head into Preferences and enable a bunch of weirdly named sliders to get control over, for example, the microphone or to enable the headphone switching. The Volume Control -> Preferences thing is completely bizarre.

---

### Post by autocrosser on 2009-02-21
Yes--We've gone back to the "Intrepid" way---I really liked the new applet/caplet & wish that they would have spent more time/resources to move it out this cycle---I guess we need to wait until the next one now :(

I was hoping for at least a PPA so we could keep testing the new way--that would have provided a start for 9.10.......

---

