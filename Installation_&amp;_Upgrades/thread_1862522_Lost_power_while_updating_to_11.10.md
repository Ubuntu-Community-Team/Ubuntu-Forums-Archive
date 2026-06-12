---
title: "Lost power while updating to 11.10"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by drummynator on 2011-10-16
Hey everyone. I was updating to 11.10 today and the power to my house was lost. When it came back, I booted up my computer and it just sits at a screen displaying this: (I'm showing as much as possible)
```

* Starting CPU interrupts balancing daemon     [ OK ]
 [ OK ]
* Starting ACPI daemon [ OK ]
* Starting save kernel messages [ OK ]
* Starting anac(h)ronistic cron [ OK ]

* PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned
* Starting regular background program processing daemon [ OK ]
* Starting deferred execution scheduler [ OK ]
Rather than invoking init scripts through init.d, use the service(8) utility, e.g. service S90binfmt-support start

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start S90binfmt-support
start: Unknown job: S90binfmt-support
No apache MPM package installed
* Stopping save kernel messages [ OK ]
* Stopping anac(h)ronistic cron [ OK ]
* Starting anac(h)ronistic cron [ OK ]
* Stopping anac(h)ronistic cron [ OK ]
* Checking battery state... [ OK ]
* Starting TiMidity++ ALSA midi emulation... [ OK ]
* Stopping System V runlevel compatibility [ OK ]
_

```And that's it. It just hangs there. What can I do?

---

### Post by 23dornot23d on 2011-10-16
can you do 
ctrl+alt+f1 

and LOGIN ...

---

### Post by frenzy50187 on 2011-10-18
I've got the same thing.  Did it on a computer that wasn't of too high importance, upgrade x86, and it's all messed up now.  video was really irratic, reset it multiple times.  Now been trying to just wipe it and start fresh, but it won't startup from the cd.  Or it is, and whenever it goes to video it comes up with that error instead

unknown job: s90infmt-support
checking battery state  [ok]

and then nothing.  

i've logged in and tried to do gdm restart, start,  ctrl alt+F7,  keep getting nothing.

---

### Post by irongiant14 on 2011-10-20
I am having the same problem, unfortunately. Except mine stops at "Checking battery state [ok]"

---

### Post by frenzy50187 on 2011-10-20
yeah im still stuck in the same boat.  Has anyone upgraded successfully?  Or have you all done fresh installs?

---

### Post by eridout on 2011-10-24
Me too, as above.

Except per 23d's suggestion of 
   can you do 
   ctrl+alt+f1 
   and LOGIN ...

Yes, that worked, thank you.
So I guess I can cancel plans to take out the battery and go buy a new one. That's good news.

But what now? I don't speak Linux command prompt.
Can I get my gui back?

---

### Post by frenzy50187 on 2011-10-24
yeah i can do that, but there appears to be no gui to startup.  I'm trying to wipe and load new OS from the dvd drive, but it doesn't even recognize it.  I'm going to try a different dvd drive.

---

### Post by TBABill on 2011-10-24
drummynator, if your machine borked during the upgrade process I'd recommend you not even try to recover it. If you can start a live session and get any files you may have on the drive recovered (your personal files if you didn't back them up before the upgrade), then I'd just reinstall and copy your saved files back to the proper directories they came from once finished. Trying to recover a machine that did not complete an upgrade is a recipe for further disaster and instability even if you got it running to some degree.

---

### Post by frenzy50187 on 2011-10-24
> **frenzy50187 said:**
> yeah i can do that, but there appears to be no gui to startup.  I'm trying to wipe and load new OS from the dvd drive, but it doesn't even recognize it.  I'm going to try a different dvd drive.

UPDATE:  other dvd drive worked, apparently  the drive...
[LIST]
[*]ND1100A  from NEC Corporation  
[*]DVD R/RW & CD-R/RW drive
[/LIST]

doesn't like DVD +R's.  On install with a different drive it came up with the Natty 11.10 OS.  It does give an option to install next to the other OS (11.10  that failed at battery state), but i opted for a fresh install. It's working right now, but still early in testing. 11.04 Natty reported I was unable to use Unity, and I heard from before 11.10 forces unity upon you (no classic looks??)  It looks nice, but the dash is extremely slow due to onboard graphics.

---

### Post by 23dornot23d on 2011-10-24
> 
 I heard from before 11.10 forces unity upon you (no classic looks??)
You can still install the fallback ..... to get Classic looks ..... This is 11.10 ..... on mine ...

[IMG]http://img268.imageshack.us/img268/1183/classic1110.jpg[/IMG]


sudo apt-get install gnome-session-fallback

---

### Post by frenzy50187 on 2011-10-24
wow, is that the tron background theme?   got a link? 

I think Im going to install different video card, but what i have is a pci and i'm not sure if it's going to be any better.

---

### Post by 23dornot23d on 2011-10-24
I use Gnome Shell most of the time ..... but here is the link as it links to the wallpaper too

[http://half-left.deviantart.com/art/GNOME-Shell-Tron-Legacy-208220836](http://half-left.deviantart.com/art/GNOME-Shell-Tron-Legacy-208220836)

My graphics are always run using Nvidia ...... ones AGP x8 old 6200 and the other built in pci 9300 .....

both work well for old cards ..... both can run compiz too ....

---

### Post by mascip on 2011-11-05
> **TBABill said:**
> drummynator, if your machine borked during the upgrade process I'd recommend you not even try to recover it. If you can start a live session and get any files you may have on the drive recovered (your personal files if you didn't back them up before the upgrade), then I'd just reinstall and copy your saved files back to the proper directories they came from once finished. Trying to recover a machine that did not complete an upgrade is a recipe for further disaster and instability even if you got it running to some degree.

I have the same problem.

What if we started a previous version of Linux, and restart an upgrade? i'm going to try that. if it doesn't work, then format and install...

---

### Post by fireoftroy on 2011-11-06
> **eridout said:**
> I don't speak Linux command prompt.
Can I get my gui back?

My update froze, and I had the same battery message others are experiencing upon reboot.  If you use Ctrl+Alt+F1, it will allow you to log in to the console.  From there, enter 'startx' and the GUI will load (a bit crude with base graphics, but it loaded).  Once I was in the GUI, I launched the software update tool, it recognized I had only completed a partial update, and asked if I wanted to continue.  I did and it then verified everything that had already been completed, corrected what failed, and continued on from there.  One more reboot and it was fully updated.

Now, when GRUB came up, the first option was for kernel 3.0-pae and the other was kernel 3.0-generic (I'm ignoring the recovery options for now).  I don't know what PAE stands for, but my guess would be Piece of Anal Excrement as it doesn't do much.  When I load this option, it doesn't recognize my display (which every version of Ubuntu on it up until now has) and loads the desktop at some pathetically low resolution.  I then tried the generic option and it works fine.

So, to answer your question, *startx *from the command line will launch the GUI you're used to, and hopefully if all goes well, you'll be able to follow my experience and be up and running in no time.

---

### Post by Gadgetinator on 2012-03-07
I have this issue, but I wasn't upgrading. I was changing settings on Ubuntu Tweak, and suddenly the unity sidebar and the dash at the top dissapeared, all my windows went to one workspace, and I did not have the option to close any windows, the x, and the minimise bar went away. I forced shutdown because I couldn't do anything, and when i restarted it I got the same error messages as before, stopping at 
Mountall: Dissconnected from Plymouth [ok]
and then it sits there forever. Ctrl+Alt+Del makes it shutdown and restart, but it just does the same thing as before. Please help!

---

