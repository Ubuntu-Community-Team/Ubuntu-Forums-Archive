---
title: "WOAH!  Edgy update broke my X Server!!"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by Ubuntu Joe on 2007-02-15
So, this morning I installed the updates I was shown on my panel just like always . . . wasn't really watching . . . I think I noticed some nvidia related packages being installed . . . a restart was required . . . . BAM!  X server broken!

What happened

Now I can't start the Ubuntu GUI at all . . . it gets stuck just before the login screen is supposed to appear.  And tells me . . . well tells me a lot . . . I didn't have time to read it all, but the gist is that X server isn't configured correctly.

Hmmmmm . . .

:popcorn:

---

### Post by renzokuken on 2007-02-15
can you get into a terminal (Ctrl+Alt+F1), login and run

```
sudo nano /etc/X11/xorg.conf
```

post the contents of that file here

---

### Post by Ubuntu Joe on 2007-02-15
How do I log in . . . I'm kinda useless without my guides I have bookmarked at home . . . which I can't get to here at work nor at home due to the issue . . .

What I'll have to do is print out your suggestions as a guide and then take *that* home and tinker . . .

---

### Post by Ubuntu Joe on 2007-02-15
Any other ideas for me to try while I'm dark at home?

---

### Post by Ben Branch on 2007-02-15
When the attempt to start the X server fails, you need to get to a command-line
login prompt. By default you can to this by typing Alt-F1, Alt-F2, up to Alt-F7 because
terminal login sessions are up in the background behind your desktop, as it were. Or
you can reboot but use the arrow keys to select the recovery mode kernel, which
also puts you at a terminal login.

After reading another thread, I solved this problem by installing the linux-restricted-modules
for the new kernel (it ought to be done by default, but it's not :( ). This means installing,
to be precise, linux-restricted-modules-2.6.17-11-generic (assuming you're running generic).
Then reboot.

Another workaround when you've got nvidia driver problems is to switch to the Xorg
nvidia driver, at least until you've got the problem solved (I also did this). All this takes
is to edit /etc/X11/xorg.conf and in the Section "Device" change the line that reads
```
Driver "nvidia" 
```to ```
Driver "nv"
``` (Copy and comment out the previous entry with a # for easy switching
back and forth).

---

### Post by IgnorantGuru on 2007-02-15
Yeah this will probably fix it, if you can get to a console... (if X doesn't start, just press enter and you should be in one)
```

apt-get install linux-restricted-modules-2.6.17-11-generic linux-restricted-modules-2.6.17-11-386

```

Or if you're using 64 bit, adjust accordingly.

---

### Post by Ubuntu Joe on 2007-02-15
I follow everything but the "generic" thing . . . what do you mean, ". . . assuming you're running 'generic?'"

---

### Post by IgnorantGuru on 2007-02-15
enter
```
uname -r
```

to see what kernel you're running (generic or 386)

---

### Post by Ubuntu Joe on 2007-02-15
All right . . . I got Ubuntu up and running no prob with

```
apt-get install linux-restricted-modules-2.6.17-11-generic
```

Even though, I'm pretty certain I'm using a x86 motherboard . . . does it matter, and more importantly, can I actually change the kernel underneath Ubuntu?  Scary . . .

ANYWAY!  Now, I have NO SOUND!  WTF?!?!?

Any ideas?

:popcorn:

---

### Post by IgnorantGuru on 2007-02-15
I'll pass on the kernel question - don't know the answer to that.

As for the sound issue, I've been hearing that a lot today (no pun intended!)  I suggest you look through some of the 'sound' posts hear and see if they've found a solution.

---

### Post by IgnorantGuru on 2007-02-15
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by Motoxrdude on 2007-02-15
Yeah, i am having a sound issue too but for some reason Movie Player works for sound, but nothing else works, even system sounds.

---

### Post by renzokuken on 2007-02-16
> **Ubuntu Joe said:**
>  and more importantly, can I actually change the kernel underneath Ubuntu?  Scary . . .


you can definately change the kernel underneath ubuntu. alot of people install ubuntu then replace it with a "vanilla" kernel. you can have as many kernels as you like for one install of ubuntu.

two things to bear in mind though.......

1. if you installed 32 bit, you can only use 32 bit kernels and if you installed 64 bit you can only use 64-bit kernels........

2. certain 3rd party drivers/kernel modules have to be installed for each kernel. an example of this is the nvidia driver, where it has to be installled for each kernel.

....i have a 386, 686 and a k7 kernel for my desktop dapper install.......i dont use the 386 and 686 ones anymore but they are there none-the-less.......you get to choose which kernel you want to use with GRUB

---

### Post by abzolutxero on 2007-02-16
> **Motoxrdude said:**
> Yeah, i am having a sound issue too but for some reason Movie Player works for sound, but nothing else works, even system sounds.
i dont have any sound at all, i attempted the fix's on the [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide) page, to no avail.  After i finished that fix though, i realized that i didnt even have my system to use alsa, mainly because oss worked better for wine, and i never needed two apps to access the sound card.  so all of my sound settings were set to oss.  now that i ran through that guide, i have them set to alsa, and i still dont get sound...


UPDATE!!!!

I got my sound back, and hopefully this is all it is for you folks... Maybe try it before going through the above guide.

open up Volume Control Manager ---- i did by right clicking on the sound icon next to the clock.  

go to edit>preferences

check the PCM option

unmute and crank to volume of PCM to 100%  

Hopefully that will work out for you, as it did for me.  Thanks for the help guys!!

---

### Post by Ubuntu Joe on 2007-02-16
Dude . . . your volume was muted?

:popcorn:

---

### Post by Ubuntu Joe on 2007-02-16
I better not make fun of you . . . that may be my problem too . . .

:lolflag:

---

### Post by abzolutxero on 2007-02-16
haha, yeah... it wasnt before all the updates, so hadnt even considered that.  i know the volume was up before the last restart i did. 

let me know what you find out though. hahaha

---

### Post by Ubuntu Joe on 2007-02-16
OH MY GOD!!!

MY VOLUME WAS TOTALLY MUTED!!!

I'm so glad I'm not the only one . . . holy crap . . . at least it was PLUGGED IN!!!


:lolflag:

---

### Post by renzokuken on 2007-02-17
hahaha, brilliant..........we never think of the obvious till the last minute do we........

anyways, congrats guys

---

