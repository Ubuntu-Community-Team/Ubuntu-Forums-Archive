---
title: "is anyone else getting hard lockups with the nvidia drivers?"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Polygon on 2009-03-31
This is a deal breaker for me in jaunty. I can't go a day (let alone a few hours) without jaunty crashing completely (where even alt+f1 or alt+sysrq+REISUB don't do anything) 

I know its the nvidia drivers because....with them installed, i crash, when they are not installed, it works fine (ran 2 days straight without a crash)

I tried 180.37 that were installed from jockey-gtk, and 185.13 or whatever is the latest bleeding edge version, and they still all cause jaunty to freeze.

I have a nvidia 9800 gtx, and i get no crashes in intrepid....so It can't be a hardware issue....

and i have been looking in the logs (kern.log and messages ) and it doesn't even give me any clues on why its crashing...i will just be doing something and my computer will stop responding.

Anyone else getting this problem? I really don't want to be stuck using intrepid as jaunty has some cool fixes and updated programs....

---

### Post by RaZoR1394 on 2009-04-02
I've had a partial lockup when using VDPAU. I managed to use MagicSYSRQ SUB. I think it was a conflict with the Jaunty 180.37(?) driver and a manually installed 180.44. I'm currently on 185.13 from thefirstm ppa and have no lockups since installed. I think I've had to use the RESET switch as well but not when using VDPAU (can't remember exactly what happened). It's clear however to me that VDPAU has some problems specially with tearing.

I'm not saying your case is a hardware issue but hardware issues can work in really mysterious ways.

Checked your temps? I'm not exceeding 50C on my 9500GT with passive cooler. There has been several cases where drivers have messed with fans and clock...

---

### Post by GARoss on 2009-04-02
Using 180.37 & no problems.

---

### Post by Polygon on 2009-04-02
my temps are 61 degrees C, just like in windows and previous ubuntu releases. 

And yeah, the nvidia drivers yell at me too about something not being a symbolic link,.....although i doubt that is the problem

---

### Post by Bossieman on 2009-04-02
Same problem here! My system dies really hard with the 180 driver. I use 64 bit Jaunty with a GF 9600 GT card.

---

### Post by philinux on 2009-04-02
And no probs here. System been up 48 hrs using suspend etc.

---

### Post by phenest on 2009-04-02
180.37 & 7950GTX. No problems.

---

### Post by oly on 2009-04-02
I am and its completely random, moving from gnome to kde makes them happen even more frequently and i have desktop effects disabled in gnome to try and stop it from happening.

but same driver and Vidia Corporation G71 [GeForce 7300 GS] (rev a1) card.

I have just updated my nvidia drivers with a ppa version to try out tomorrow to see if it still happens.

---

### Post by kevpan815 on 2009-04-02
No Problems Here With Both My Nvidia GeForce 8300 And My Nvidia GeForce 8800 GT.

---

### Post by Nightstrike2009 on 2009-04-03
I have similar prob with Nvidia 6600GT & 180.44, Hardware driver refuses to activate and crashes X server on restart. Also had the same problem with 180.37 driver. :(

---

### Post by mamamia88 on 2009-04-03
had a few a few days ago installed 173 and it seems to work fine now

---

### Post by Polygon on 2009-04-03
i'm not sure if the recent nvidia update (not the drivers, but something else, forget what it was called) fixed it, i shall leave my computer on while i am at school and work to see if it freezes again while i am away.

---

### Post by RaZoR1394 on 2009-04-03
> **Polygon said:**
> i'm not sure if the recent nvidia update (not the drivers, but something else, forget what it was called) fixed it, i shall leave my computer on while i am at school and work to see if it freezes again while i am away.

I got an almost total freeze recently. Mousepointer could not be moved and there was no input from my keyboard. Numlock did not react. The picture had frozen totally. MagicSYSRQ + SUB saved me again. I was not playing any video at all only browsing with Firefox and downloading with sabnzbdplus in the background.

It's probably something that is hogging an insane amount cpu in the background.

I've seen that java can use a very high amount of cpu out of nowhere.

From my experience with ATI:s buggy drivers (during It's worst times) lockups tend to show up very non-regularly.

I have a terminal open with top running and whenever a process seems to use to much cpu resulting in the system getting slower i kill it, either with killall, kill -9 or xkill. xkill is very useful. There is a little app you can add to your top panel that does the same as xkill. It's included in Ubuntu and you can add it by right-clicking the panel and choosing "Add to panel" (or something like that) and choose it from the list.

edit:

Maybe you can find something on the nvnews forums?

edit2:

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by rubenverweij on 2009-04-03
I have no problems using GeForce N6200 with the 180.37 driver...

---

### Post by bubba_169 on 2009-04-03
I had a problem with the 180.37 driver, integrated 8200 and firefox. Whenever firefox warned me I was closing tabs the system would lock up and only a hard reset would fix it. I could make it do this every time, if it didnt happen straight away as soon as I moved the warning dialog about it would! My solution was to make firefox start with my last used tabs so it doesnt show that warning at all. Its not a great fix, more of a workaround, but does stop about 90% of the crashes.

Not sure if this helps at all?

EDIT: Just tested and it seems this was fixed with 180.44 :D

---

### Post by Polygon on 2009-04-03
it appears that my problem is fixed at least, i just left my computer on all day, seeding a torrent and ripping a dvd, and its still working fine now. I wonder what WAS the problem in the first place...

---

### Post by Polygon on 2009-04-04
nope, nevermind. just got it again

reported a bug this time:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155)

---

### Post by ELD on 2009-04-04
My beta install has hard frozen 3 times in total, no idea if it's nvidia drivers doing it though.

---

### Post by phenest on 2009-04-04
> **ELD said:**
> ...no idea if it's nvidia drivers doing it though.

I doubt it. As I've said on another thread, I had all sorts of problems like the rest of you guys. Now, it runs perfectly and I'm using the same drivers. It's usually an incompatibility between the drivers and the Linux kernel. But seeing as Jaunty is beta, you should take it up with the Ubuntu devs.

---

### Post by Polygon on 2009-04-10
still happening with 185.19 =/

---

### Post by druhboruch on 2009-04-10
Same problem here.
It always happens when I watch few flash movies in a row...
It works fine with xorg nvidia diriver.

---

### Post by davbren on 2009-04-10
I'm not sure its the driver. I'm using an ATI card and I'm getting the same problem... I'm thinking it might be the pulseaudio..

---

### Post by dasunst3r on 2009-04-10
I remember having similar issues with the nVidia driver a bit more than two years ago.  It started with the windows not updating for about 15 seconds and then worsened to the point where the computer would either lock up and restart or lock up and turn off.  Turning off desktop effects in this case really does help, and I just stuck with this problem for several months until they fixed it.

---

### Post by Polygon on 2009-04-10
in my rage i forgot i had already submitted a bug report about this

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155)


> 


I had the same problem. It appear after update from 2.6.28-6 on 2.6.28-8 kernel and upper.
Firstly I've think it's video driver related but with 2.6.28-6 kernel, on the same driver it's work very stable.
I find in kernel.log this lines:

kernel: [ 21.198429] Marking TSC unstable due to cpufreq changes
kernel: [ 23.588616] agpgart-nvidia 0000:00:00.0: AGP 3.0 bridge
kernel: [ 23.588633] agpgart-nvidia 0000:00:00.0: putting AGP V3 device into 8x mode
kernel: [ 23.588689] nvidia 0000:02:00.0: putting AGP V3 device into 8x mode
kernel: [ 31.732343] Clocksource tsc unstable (delta = -63230109 ns)

After adding notsc clocksource=acpi_pm to grub kernel boot parameters. It stop freezing.

Hope it's help somehow.


so i tried adding 'notsc clocksource=acpi_pm' to my kernel line in my menu.lst. i shall see if that magically fixes it

---

### Post by Anubis on 2009-04-10
None on a 8400gs NVIDIA Driver Version: 180.44

---

### Post by Akita on 2009-04-10
Solid as a rock here on 8800GT, 8600GT and a pair of laptop 7600's.

180.x and 185.x.

---

### Post by vyruss on 2009-04-13
I'm getting hard lockups too on 2 PCs, one with a 8600GT and the other with a 6600LE.

I believe the common factor is Jaunty amd64. Both are using all the latest packages.

---

### Post by Nightstrike2009 on 2009-04-13
The Nvidia 173 driver works fine on my Ubuntu 9.04 with Nvidia 6600GT, the 180 drivers upwards just bork my xorg up. Not happy thought these probs had been overcome before with 8.10 obviously not! :(

I has a set of drivers from a launchpad ppa that worked think it was 180.35 these worked fine I think it's the Ubuntu repo files that are borked, I maybe wrong though.

---

### Post by hufferd on 2009-04-13
This has been what has happened to me I have had the same issue with a "hard lockup" I have had to do a hard shut down.  This was happening any time I was doing anything that was REALLY video intensive.  Temps are around 60c when this happens that's where they have always been... when I stress the card. 

I was / am using CPU scaling........  I have found that if I let it throttle the CPU THAT'S when I have the issue.  If I set CPU at a fixed speed I no longer have the issue 

Just what I have found

---

### Post by gnomeuser on 2009-04-13
Since Ubuntu kept begging me to install this driver, I did it just to shut up that restricted driver program (it really needs a "I love my kernel developers and wish you would fix the real problem, now stop bothering me" option.

It ran fine for a while, then it just randomly rebooted taking with it a rather large amount of work. I promptly removed the nvidia driver, it has now been going to days. I would much rather have a stable machine.

And remember the nvidia cannot be fixed by anyone by nvidia themselves, in addition it will cause crashes in other applications as well as the kernl due to it's poor adherence to stack usage rules in the kernel. I really would not recommend using it anywhere one is fond of stability.

---

### Post by olskar on 2009-04-13
I just want to remind people of the [I]nvidia-bug-report.sh 
[/I] command :)

---

