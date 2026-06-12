---
title: "Startup, anyone getting a black screen for ages between logo and xsplash?"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-10-16
White logo appears then black screen for about 12 seconds then xsplash shows up briefly before gdm.

[edit] Checked timings with stopwatch
Usplash logo is on screen for 12.5 secs.

Blank screen for 9.4 secs.

xsplash to gdm for 6.6 secs.


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453337)

**Can anyone who voted yes or this affects you, please go to the bug report and click "This bug affects me too"**

---

### Post by Giwex on 2009-10-16
I do

---

### Post by pulpo69 on 2009-10-16
i do too

---

### Post by Podex on 2009-10-16
Isn't this related to your other problem with couchdb (which I had as well) here: [http://ubuntuforums.org/showthread.php?t=1291930&highlight=couchdb](http://ubuntuforums.org/showthread.php?t=1291930&highlight=couchdb) ?

When I removed couchdb this black screen went away and my boottime was reduced by about 40 seconds I think :O

---

### Post by philinux on 2009-10-16
> **Podex said:**
> Isn't this related to your other problem with couchdb (which I had as well) here: [http://ubuntuforums.org/showthread.php?t=1291930&highlight=couchdb](http://ubuntuforums.org/showthread.php?t=1291930&highlight=couchdb) ?

When I removed couchdb this black screen went away and my boottime was reduced by about 40 seconds I think :O

Well not sure. I've done as asked and removed couchdb and left couchdb-bin installed as it is it's replacement.

I'm testing ubuntu-one which needs couchdb-bin.

---

### Post by cecilpierce on 2009-10-16
I removed couchdb and black screen is still there and boot time is about the same, 1:15 ???

---

### Post by philinux on 2009-10-16
I'd already removed couchdb but just removed couchdb-bin too and it knocked 2 seconds of the boot time. However the long time looking at a black screen was still there.

---

### Post by Podex on 2009-10-16
Ok, in that case it is a different problem. What does your bootchart look like?

---

### Post by philinux on 2009-10-16
Here's the latest with couchdb-bin reinstalled.

Is anybody **not** getting this black screen I wonder?

---

### Post by rburkartjo on 2009-10-16
same problem on  my end

---

### Post by philinux on 2009-10-16
I'll have a look through launchpad see if it's been reported. Not sure what package that would be though. :confused:

---

### Post by null_pointer_us on 2009-10-16
> **philinux said:**
> 
Is anybody **not** getting this black screen I wonder?

I'm not getting a black screen, but the period of CPU/disk activity has increased by about 5 seconds since yesterday's bootcharts. 23s -> 28s (in vbox 64-bit guest/host). Updates as of a few minutes ago did not change this.

---

### Post by xebian on 2009-10-16
I think I'm getting the same lag.  I thought X failed so I went on to log on the CL and then KDM start showing up.  No couchdb installed. :confused:

---

### Post by EmmEff on 2009-10-16
Same thing here too...  everything else works great so I live with it :)

---

### Post by philinux on 2009-10-16
Ok this needs bugging but before that I've added a poll. Please vote.
Maybe is a spec thing or 64 bit v 32. Who knows.
Whatever it is it's not a good first timer experience.

---

### Post by wnelson on 2009-10-16
I tried something I modified /etc/usplash.conf from the original values xres=1440 yres=900 to xres=1024 yres=768 and the delay seemed less.

---

### Post by davidryderuk on 2009-10-16
Hi,
Just a random question, but is anyone else using a graphics card that supports kernel mode setting and UXA? 

My netbook has this problem and also supports kernel mode setting, so I was just wondering whether there was a connection.

---

### Post by philinux on 2009-10-16
Ok I've bugged this. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453337). Could someone confirm this bug.

There is a similar bug reported 3/10/09 but that one involves a lot of boot messages being displayed. I'm just seeing a blank screen.

---

### Post by Anubis on 2009-10-16
"blank screen for ages"

What does that mean in English?

How long does your bootchart say it takes to boot?
:confused:

Mine says 1:22

I rebooted yesterday, and don't remember what it looked like. I don't recall having much time to look at it.

---

### Post by davidmohammed on 2009-10-16
have confirmed this also - seems to be getting worse as the beta progresses not better :(

If this is not resolved by release I think I'll go back to jaunty.

---

### Post by hanzomon4 on 2009-10-16
Can you switch to a tty? I have a similar bug with the rt kernel but I can't do anything with the system except force a reboot.

---

### Post by davidmohammed on 2009-10-16
'fraid not - can only switch to tty6 when GDM is fully up.

looking at my boot chart (posted in bug report above) xsplash starts 20 seconds after xorg starts - what on earth is xorg trying to do?  Can anybody point me in the right direction on what to look for in the logs?

---

### Post by arpanaut on 2009-10-16
I don't know if this is related to this problem or will help, but I was having the logo hang for 30 sec. then flash a couple of times, then black for 5 sec. then to progress bar, then another momentary black screen, then to login...

So just to see what was up I took quiet and splash out of the boot parameters (editing at the grub2 screen) hit Control-x and it wasn't 10-15 sec. until the login screen was up.

Probably 45 sec. faster than usual????
Weird! I'll have to do some comparative boot charts and see... 
Later

Edit:
My Bad... I guess it was just a matter of perception, just seeing something going by on the screen made me believe it was going faster. Someday I will learn to not get too excited and test further before I post. My Apologies

1st chart normal
2nd w/o quiet splash
alas not much difference, thought I was on to something  :redface:

---

### Post by philinux on 2009-10-16
Glad I'm not alone on this.

Did a stopwatch test.

Usplash logo is on screen for 12.5 secs.

Blank screen for 9.4 secs.

xsplash to gdm for 6.6 secs.

No error messages at all. Boot time is 1.07 seconds same as always.

---

### Post by null_pointer_us on 2009-10-16
philinux, if I'm interpreting your bootchart correctly, it shows that your cpu spends a lot of time idle while waiting on disk i/o. Conversely, the top bar on my system (even in a VM) and many other systems (in the boot chart thread) is almost entirely blue during boot activity. Maybe getting boot charts from other people who have the bug would show the same thing?

EDIT: Yeah, DavidM (in your bug report) also shows a bootchart with loads of pink in the top graph.

---

### Post by philinux on 2009-10-17
Could someone who's not getting this post a bootchart.

---

### Post by null_pointer_us on 2009-10-18
bump

BTW:

This might be an unrelated issue...

This morning, a partial upgrade removing rtkit (which had been enabled by mistake and wasting CPU cycles according to a bug report), seems to have reduced my boot time to about 20s (from 28s).

Have you noticed any improvement?

Attached are boot charts from before and after the update.

---

### Post by philinux on 2009-10-18
Boot time pretty consistent at 1.04 but lots of i/o wait.

---

### Post by philinux on 2009-10-19
Anyone else like to comment?

---

### Post by kestal on 2009-10-20
its odd, as with my desktop this is not a problem, but on laptop (where I'd probably need Ubuntu the most) I wait over a minute for it to get into the desktop. Live CD boots about the same time almost, unfortunetely.

Hopefully they take a look at this. I mean, according to the poll 75% of the people see this horrid transition.. I mean, call me a windows freak but XP has a better transition than this.

We'll see how this goes for RC. Its being released in the next day or two.

---

### Post by philinux on 2009-10-20
Still happening with all the latest updates. :confused:

---

### Post by philinux on 2009-10-21
**Can anyone who voted yes or affects you, please go to the bug report and click "This bug affects me too"**

---

### Post by Niko Johnson on 2009-10-21
i dont really have any problems with slow startup... yet

---

### Post by gjoellee on 2009-10-21
I get a black screen in about 3-10 sec

---

### Post by nanog on 2009-10-21
Anecdotally, getting this only only on computers that are running amd64 and nvidia proprietary.  Boxes with intel graphics seem to be fast, very fast. Since I use suspend its not been a bother.

---

### Post by philinux on 2009-10-21
> **nanog said:**
> Anecdotally, getting this only only on computers that are running amd64 and nvidia proprietary.  Boxes with intel graphics seem to be fast, very fast. Since I use suspend its not been a bother.

Interesting, I'm on 64 bit. I just deactivated the nvidia driver, rebooted, and the black screen event was 4.6 seconds. Cut down by half, but still a long wait between the ubuntu logo and xsplash.

---

### Post by philinux on 2009-10-22
Respectful Bump.

---

### Post by caryb on 2009-10-22
Just in case you are thinking it's a GDM/Gnome thing it's not as I'm on Kubuntu KDM/KDE & have the same problem.


Cary

---

### Post by philinux on 2009-10-22
Ok in that case pop along to the bug and click the affects me too. Or better still ```
apport-collect 453337
```

Cant see any signs of a fix yet.

---

### Post by crjackson on 2009-10-22
I can't even install.  Mine goes black and never comes back (we're talking liveCD).

I installed an old GeForce2 card to manage an install, but re-installing the normal Video card (Nvidia 6100A) and it's all black, all the time.

Works perfect in Jaunty however.

---

### Post by philinux on 2009-10-23
> **crjackson said:**
> I can't even install.  Mine goes black and never comes back (we're talking liveCD).

I installed an old GeForce2 card to manage an install, but re-installing the normal Video card (Nvidia 6100A) and it's all black, all the time.

Works perfect in Jaunty however.

Different problem then I think.

---

### Post by desperado666 on 2009-10-23
Try this

```
sudo gedit /etc/default/grub
```

then change the line 
> #GRUB_GFXMODE=640x480
to 
> GRUB_GFXMODE=640x480

---

### Post by chiisu on 2009-10-23
> **crjackson said:**
> I can't even install.  Mine goes black and never comes back (we're talking liveCD).

I installed an old GeForce2 card to manage an install, but re-installing the normal Video card (Nvidia 6100A) and it's all black, all the time.

Works perfect in Jaunty however.

When I boot the LiveCD I get constant flickering after the initial loading process.  Have a 6600GT.

---

### Post by philinux on 2009-10-26
I hope this gets a bit of priority.

---

### Post by philinux on 2009-10-27
> **chiisu said:**
> When I boot the LiveCD I get constant flickering after the initial loading process.  Have a 6600GT.

Not the same problem.

---

### Post by philinux on 2009-10-28
Last bump and still not fixed. :rolleyes:

---

