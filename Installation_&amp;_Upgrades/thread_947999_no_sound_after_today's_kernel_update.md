---
title: "no sound after today's kernel update"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by steveneddy on 2008-10-14
I'm sure that I'm not the only one, but after today's update, a new kernel image came down.

```
2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux
```

after the restart I didn't have any sound and clicking the volume applet tells me that I don't have any gstreamer plugins installed, but when I open up synaptic the gstreamer plugins are all there, installed.

any help appreciated.

I think my laptop uses intel sound.

maybe the devs just need a little more time with this kernel upgrade.

in the meantime I will use the -19 kernel.

---

### Post by linux_lover69 on 2008-10-14
Try reinstalling the drivers.

---

### Post by steveneddy on 2008-10-14
I don't think that the kernel modules are installing with the kernel.

I also noticed that the 

linux-ubuntu-modules

for the -21 kernel weren't installed

and when I try and install them I have boot issues and the nvidia video driver isn't recognized.

I uninstalled the linux-ubuntu-modules for the -21 kernel for the time being and am booting into the -19 kernel.

---

### Post by steveneddy on 2008-10-15
I was wondering if anyone else is having any issues with the -21 kernel?

I am using 8.04.

Is there a solution to the no sound issue with the -21 kernel?

Surely I'm not the only one with these issues.

---

### Post by lapor on 2008-10-15
I am having some issues with -21 kernel. When ubuntu comes to my desktop it is blank. Just white screen with mouse pointer. But everything is working, because I can play music (rhythembox starts automaticlly when I turn on computer).

For now I am back on -19 kernel. If anyone has an solution for my problem, I'd be glad.

ps: I'm using 8.04

---

### Post by MaindotC on 2008-10-15
I just downloaded the updates and rebooted - nothing special - and my sound seems to be working alright.  Perhaps you need to go to System -> Preferences -> Sound and select a different driver?

---

### Post by sandy8925 on 2008-10-15
hey i'm having some problems too.
installed the new kernel and many things have gone haywire.
first if i click the power button at the top right the upper bar that holds all the menus and the taskbar disappear. I can't logout or restart unless I use ctrl+alt+backspace.
nautilus doesnt seem to work properly either.it gives an error message sometimes and suggests that I kill bonobo-activation-server and restart nautilus.

I use emerald for themes and the themes arent getting applied properly.

in firefox my bookmarks have all disappeared and I can't add any more. what's going on ?

I searched over here and some other guy mentioned problems with sound.
So I removed the new kernel and then did gksu-nautilus.
Then removed the -21 kernel listing from grub.

But the problems still persist even in the -19 kernel.

Can anyone help me ?

---

### Post by RobOrr on 2008-10-15
I have all the same problems as you sandy, afraid I have no idea what's going on. 

firefox bookmarks have gone, and I've lost the ability to create new ones. the quit button in the top right now makes all the panels quit, nautilus occasionally fails, and reverting to the .19 kernel doesnt solve the problem. it makes me think this isnt due to the kernel update but rather one of the other updates that came with it.

---

### Post by MaindotC on 2008-10-15
One thing I'm noticing is that all of a sudden VirtualBox is freezing when I try starting it.  I have it running on 4 different machines, two desktop production machines, one laptop T60, and one personal 64-bit desktop (both in my sig, respectively) and VBox freezes at "dora:spawning session" when I start a VM.  I'll start a separate thread.

---

### Post by steveneddy on 2008-10-15
WOW! At least I'm glad that I'm not the only one with this issue.

I have seen this type of behavior in the past with other kernel updates wreaking havoc on systems.

I just hope that they fix this one soon. I have work to do.

Those without out a volume manager applet, can you still play music or hear the system sounds?

I don't have any sound at all. I noticed immediately after the restart that there was no sound and it said that the gstreamer plugins were not installed.

Just frustrating.

:)

---

### Post by raynedanser on 2008-10-15
Nope, you are definitely the only one with problems. Fortunately, the only thing that seems to be horked so far is my audio. *knocks on wood*

Still. Not impressed as this is what I use for my primary music listening. :mad:

Den

---

### Post by anpu1 on 2008-10-15
i have the same problem with ubuntu 8.10!! after the last update the sound is no longer present!! and there is another problem but it doesn't affect on comp work! the LED light that indicaates ON/OFF of WIFI is blinking! the internet is working and wifi is fine it just blinks! But the bigest problem for now is that the sound is gone :)

---

### Post by sandy8925 on 2008-10-15
yeah I installed some other bunch of updates just before the kernel update through apt-get and I think nautilus was part of that.

it asked me to restart after installing those updates but I installed the kernel update and then only restarted. I guess that might have caused the problem.......

---

### Post by sandy8925 on 2008-10-15
here's what I used to remove the new kernel:
"sudo apt-get remove linux-restricted-modules-2.6.24-21-generic"

I got this command from this thread:
[http://ubuntuforums.org/showthread.php?t=948302&highlight=kernel+update](http://ubuntuforums.org/showthread.php?t=948302&highlight=kernel+update)

---

### Post by anpu1 on 2008-10-15
did help? got the sound back?

---

### Post by raynedanser on 2008-10-15
> **sandy8925 said:**
> here's what I used to remove the new kernel:
"sudo apt-get remove linux-restricted-modules-2.6.24-21-generic"

I got this command from this thread:
[http://ubuntuforums.org/showthread.php?t=948302&highlight=kernel+update](http://ubuntuforums.org/showthread.php?t=948302&highlight=kernel+update)


Did it help?

---

### Post by NE Key on 2008-10-15
> **strAlan said:**
> I just downloaded the updates and rebooted - nothing special - and my sound seems to be working alright.  Perhaps you need to go to System -> Preferences -> Sound and select a different driver?

Sadly not. All the options were blanked out. 

removed the new kernel;

"sudo apt-get remove linux-restricted-modules-2.6.24-21-generic"

then "gksu nautilus" to edit boot/grub/menu.lst and remove the -21 option.

Now every thing works perfectly
 [http://ubuntuforums.org/showthread.php?p=5968800#post5968800](http://ubuntuforums.org/showthread.php?p=5968800#post5968800)

---

### Post by sandy8925 on 2008-10-15
mine still aint working properly....
sound works alright but everything else is still the same.....

---

### Post by RobOrr on 2008-10-15
whatever our problem is sandy, it's not the updated kernel. its the other stuff that we updated as well. sadly, i cant seem to find an easy option to tell package manager "revert to couple of days ago" etc. i think there were dbus updates, among other things. hopefully because this problem is widespread, the devs will be able to fix it fairly quickly in another update.

---

### Post by sandy8925 on 2008-10-15
yeah I installed those updates too.

things have changed now however-
emerald themes properly now.
firefox bookmarks works.
sound works alright.
i can use the back and forward buttons on firefox.
still not sure abt the power button.will check out and tell.

---

### Post by MaindotC on 2008-10-15
I'm not having any issues w/ sound whatsoever.  So those of you that are - try and figure out what you have in common.  Post hardware like I do in my sig?

---

### Post by sandy8925 on 2008-10-15
hey my power button works properly too.
guess all my problems got solved after uninstalling the kernel.
thanks for the suggestions and advice (if any).

---

### Post by harvixen on 2008-10-15
hi ..
please look here, not for a solution yet or even any clue, but for similar problems:

[http://ubuntuforums.org/showthread.php?t=945386](http://ubuntuforums.org/showthread.php?t=945386)

i just switched to -20 kernel and it all works.
dbus got updated today..i thought that could be proble..but - no cigar.

i would say let us wait for -22 and avoid -21 all together..

i was more interested in really finding a solution..looked thru all possible logs and messages..couldn't determine anything.

i am still curious..what and why?

---

### Post by raynedanser on 2008-10-15
> **harvixen said:**
> hi ..
please look here, not for a solution yet or even any clue, but for similar problems:

[http://ubuntuforums.org/showthread.php?t=945386](http://ubuntuforums.org/showthread.php?t=945386)

i just switched to -20 kernel and it all works.
dbus got updated today..i thought that could be proble..but - no cigar.

i would say let us wait for -22 and avoid -21 all together..


*nods* You beat me to it, although I switched back to 19 and rebooted. ;-) Everything is fine again!

---

### Post by steveneddy on 2008-10-15
I will wait for the -21 kernel to be fixed by the Ubuntu devs.

The odd numbered kernel releases (-19, -21) are the stable releases with the even numbered kernel updates unstable.

I'm on Windows here at work today and I need to get home and tweak the laptop a little I suppose.

---

### Post by ohiomoto on 2008-10-15
> **sandy8925 said:**
> hey i'm having some problems too.
installed the new kernel and many things have gone haywire.
first if i click the power button at the top right the upper bar that holds all the menus and the taskbar disappear. I can't logout or restart unless I use ctrl+alt+backspace.
nautilus doesnt seem to work properly either.it gives an error message sometimes and suggests that I kill bonobo-activation-server and restart nautilus.

I use emerald for themes and the themes arent getting applied properly.

in firefox my bookmarks have all disappeared and I can't add any more. what's going on ?

I searched over here and some other guy mentioned problems with sound.
So I removed the new kernel and then did gksu-nautilus.
Then removed the -21 kernel listing from grub.

But the problems still persist even in the -19 kernel.

Can anyone help me ?
I went through hell with an update a while back that caused many of the same problems.  Every time I though I fixed it, it would come back.  I really don't have an answer for you, but maybe someone can look at the clues and figure it out.  

Here is the thread: [http://ubuntuforums.org/showthread.php?t=818241](http://ubuntuforums.org/showthread.php?t=818241)

I gave up an ended up doing a fresh install.  It updated just fine after that.  

For the record, I did not do the latest update.  I came here first to see if anyone had any trouble.  Looks like I'll be waiting.

Tim

---

### Post by lapor on 2008-10-15
thanks. I dont have time now for reinstall. Ill just wait for Ubutnu 8.10 and then Ill just update it from -19 kernel. I hope everything is going to be OK.
For now Im using -19 kernel. And everything works fine.

---

### Post by steveneddy on 2008-10-16
I'm using an 18 month old System76 laptop that when I installed Hardy, everything was supported so that I actually didn't have to use the System76 driver.

The -19 kernel works great.

The -21 kernel is starting to hose more than a few people's laptops and desktops.

Others are having graphics issues with this new kernel release.

Intel Core 2 Duo
Intel sound
Nvidia graphics

This is just a basic laptop that should have all of the hardware supported.

This is just wrong for an LTS release.

These types of issues will not help our cause.

Just my opinion here.

---

### Post by bark50 on 2008-10-16
> **steveneddy said:**
> I'm sure that I'm not the only one, but after today's update, a new kernel image came down.

```
2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux
```

after the restart I didn't have any sound and clicking the volume applet tells me that I don't have any gstreamer plugins installed, but when I open up synaptic the gstreamer plugins are all there, installed.

any help appreciated.

I think my laptop uses intel sound.

maybe the devs just need a little more time with this kernel upgrade.

in the meantime I will use the -19 kernel.

Sounds like a lot of machines had problems with the latest kernel change.  Going back to the original posting of this thread, I didn't encounter any sound problems with the new kernel, but I have had sound problems with previous kernel changes.  At those times, I was able to get my sound back by following the instructions here:  [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

