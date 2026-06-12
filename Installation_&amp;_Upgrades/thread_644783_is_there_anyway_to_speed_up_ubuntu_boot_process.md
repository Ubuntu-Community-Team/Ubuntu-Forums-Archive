---
title: "is there anyway to speed up ubuntu boot process?"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by amixroed on 2007-12-19
i just installed ubuntu and got my brand new router working and its all sweet:D but i do have one question regarding start up time, it takes over 3min to load!! i;m sure i have a problem anyone know how i can speed things up or find out whats making it load so slowly?

---

### Post by tech9 on 2007-12-19
> **amixroed said:**
> i just installed ubuntu and got my brand new router working and its all sweet:D but i do have one question regarding start up time, it takes over 3min to load!! i;m sure i have a problem anyone know how i can speed things up or find out whats making it load so slowly?

what are your hardware specs?

Maybe you need more RAM, better CPU or HD

---

### Post by amixroed on 2007-12-19
i'm not entirly sure about this but i think it only became realy slow after my wireless started working. my system specs arnt the best but it works fine on windows xp with alot of application loaded.
IBM thinkpad T40
1.3ghz M
1.2gb ram
10gb (ubuntu only)

---

### Post by tech9 on 2007-12-19
> **amixroed said:**
> i'm not entirly sure about this but i think it only became realy slow after my wireless started working. my system specs arnt the best but it works fine on windows xp with alot of application loaded.
IBM thinkpad T40
1.3ghz M
1.2gb ram
10gb (ubuntu only)

That's strange, your specs are good! Maybe there is a hardware conflict with the wireless then.

---

### Post by roaldz on 2007-12-19
> **amixroed said:**
> i just installed ubuntu and got my brand new router working and its all sweet:D but i do have one question regarding start up time, it takes over 3min to load!! i;m sure i have a problem anyone know how i can speed things up or find out whats making it load so slowly?

Install bootchart:

¨sudo apt-get install bootchart¨ or look it up in synaptic.

Reboot, and browse to ¨/var/log/bootchart/¨
there you will find a chart made of you boot process. If you post it here, we can see what´s wrong.

Good luck!:)

---

### Post by tech9 on 2007-12-19
> **roaldz said:**
> Install bootchart:

¨sudo apt-get install bootchart¨ or look it up in synaptic.

Reboot, and browse to ¨/var/log/bootchart/¨
there you will find a chart made of you boot process. If you post it here, we can see what´s wrong.

Good luck!:)

nice tip and good advice! :)

---

### Post by jaq on 2008-02-18
> **tech9 said:**
> nice tip and good advice! :)

I have the same problem on my thinkpad t40  as the original poster. 3 minutes or more to boot the Gutsy Gibbon. Bootchart attached. I'd appreciate any advise on how to reduce boot times. Thanks.

---

### Post by roaldz on 2008-02-18
> **jaq said:**
> I have the same problem on my thinkpad t40  as the original poster. 3 minutes or more to boot the Gutsy Gibbon. Bootchart attached. I'd appreciate any advise on how to reduce boot times. Thanks.

Looks like that Usplash problem.

The easy way:
```
gksu gedit /boot/grub/menu.lst
```

Find your kernel command line.

Looks someting like this:
```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6247b01f-c131-4cd0-8491-2407fa491503 ro **quiet splash**
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

```
Remove ¨quiet splash¨ at the end of the ¨kernel¨ line.

Save the file. The next time you boot, you´ll see verbose boot messages, no splash screen. I bet it´ll be faster, but also somekind of ugly.

The good way:
> **LeeAdkins said:**
> Does the black Ubuntu loading splash screen work when you do that?

If not, here is another (slightly longer) fix that was posted elsewhere to fix it for reals. The problem with the slow boot is that the settings in Usplash can sometimes get messed up on install and hang up the boot. Removing some of the lines in menu.lst disables Usplash and fixes the problem. If you like the verbose boot up, then leave it. If you'd like the pretty Ubuntu boot up sequence, try this.

1) Put everything back in /boot/grub/menu.lst that you took out ( "ro quiet splash" in the kernel line and "quiet" at the end)

2) At the very end of the kernel line after  "splash" , add "vga=791" This is the weird part for me, because I'm not exactly sure why the number is 791. Make sure this goes on the same line, though.

3) Save that file, close it, and open up /etc/usplash.conf

4) Change the screen resolution to the resolution you are actually using. Save it and close it.

5) Grub won't know anything about this until you rebuild the boot, so do the following commands.

uname -r
This lists your current kernel version.

sudo update-initramfs -u -k *<insert results from uname -r here>*

This rebuilds the image that Grub uses to start the system.

Voila, you have fixed the boot speed issue and gotten the splash screen back. Reboot and enjoy the fruits of your labor. Your mileage may vary, but it worked for me on the first try and for quite a few other people throughout the forum.  This only works if Usplash is what was broken, which sounds right for all of you.  Also, you can always hit CTRL-F1 when the splash is running to get back to your verbose mode.

Hope it helped, if so, please thank me.

Roald

---

### Post by jaq on 2008-02-18
Wow, that was weird. I tried the easy way since I actually prefer the verbose boot over a fancy splash screen that hides what's going on. The boot itself was much faster - under a minute (from over 3 minutes).

The problem was after logging in. It took FOREVER to load my desktop, and it somehow didn't feel right. This was confirmed when I launched terminal, firefox, gedit which were all without any window decorations. I then opened 'menu.lst' and replaced the 'quiet splash' I had removed from the kernel line, rebooted and now everything is back the way it was.

I guess there's more to these long boot times than 'quiet splash'. I'm not sure if I should attempt the good way until I know more. In any case Roaldz, I appreciate your fast response and attempt to help. Any further insight would be great.

---

### Post by wpshooter on 2008-02-18
Have you checked the video related parameters in your BIOS ?

In particular, see if there is a parameter related to aperature size.

Make sure that you write down any settings that you might make a change to before you do so, so that you can put everything back to the way it was before you attempted to make changes.

---

### Post by roaldz on 2008-02-18
> **jaq said:**
> Wow, that was weird. I tried the easy way since I actually prefer the verbose boot over a fancy splash screen that hides what's going on. The boot itself was much faster - under a minute (from over 3 minutes).

The problem was after logging in. It took FOREVER to load my desktop, and it somehow didn't feel right. This was confirmed when I launched terminal, firefox, gedit which were all without any window decorations. I then opened 'menu.lst' and replaced the 'quiet splash' I had removed from the kernel line, rebooted and now everything is back the way it was.

I guess there's more to these long boot times than 'quiet splash'. I'm not sure if I should attempt the good way until I know more. In any case Roaldz, I appreciate your fast response and attempt to help. Any further insight would be great.

Let us look at the difference in the boot process. Can you post the bootchart from the boot without splash screen? 
The long waiting time after logging in bugs me too. I bet you have AWN running too:)

---

### Post by frankos44 on 2008-02-18
Not sure if this helps.

Very slow boot on one of my laptops was caused by setting in /etc/usplash.conf

$ gksudo gedit /etc/usplash.conf 

Correct the resolution and save, then run:

$ sudo update-initramfs -u

---

### Post by roaldz on 2008-02-18
> **frankos44 said:**
> Not sure if this helps.

Very slow boot on one of my laptops was caused by setting in /etc/usplash.conf

$ gksudo gedit /etc/usplash.conf 

Correct the resolution and save, then run:

$ sudo update-initramfs -u

That was posted on the previous page too.

---

### Post by frankos44 on 2008-02-18
> **roaldz said:**
> That was posted on the previous page too.

Sorry, I missed that

---

### Post by jaq on 2008-02-19
> **roaldz said:**
> Let us look at the difference in the boot process. Can you post the bootchart from the boot without splash screen? 
The long waiting time after logging in bugs me too. I bet you have AWN running too:)

Bootcharts attached. I hope I'm overdoing sending 5 of them...
(prior to removal of 'quiet splash', see 19-1)

I again removed 'quiet splash' from the kernel line in menu.lst to reboot and generate the bootchart you asked for. (see 19-2)

Both the boot and the log in were much faster. The problem I had yesterday with the long delay after log-in and the windows without decorations didn't happen this time. I was very happy with the result until my dial-up connection started crapping out on me as it sometimes does. For some reason KPPP crashed and attempts to reconnect made it crash again. I decided to reboot but it would just hang, so I did a cold reboot. Same problem with KPPP and normal reboot, so did another cold boot (see 19-3, 19-4).

Replaced 'quiet splash' & rebooted (see 19-5).
No more KPPP crashes once quiet splash was replaced.

Not sure if the above problems have anything to do with changes made to 'menu.lst' but it's rather curious. Looking forward to any insights. Thanks.

---

### Post by roaldz on 2008-02-20
> **jaq said:**
> Bootcharts attached. I hope I'm overdoing sending 5 of them...
(prior to removal of 'quiet splash', see 19-1)

I again removed 'quiet splash' from the kernel line in menu.lst to reboot and generate the bootchart you asked for. (see 19-2)

Both the boot and the log in were much faster. The problem I had yesterday with the long delay after log-in and the windows without decorations didn't happen this time. I was very happy with the result until my dial-up connection started crapping out on me as it sometimes does. For some reason KPPP crashed and attempts to reconnect made it crash again. I decided to reboot but it would just hang, so I did a cold reboot. Same problem with KPPP and normal reboot, so did another cold boot (see 19-3, 19-4).

Replaced 'quiet splash' & rebooted (see 19-5).
No more KPPP crashes once quiet splash was replaced.

Not sure if the above problems have anything to do with changes made to 'menu.lst' but it's rather curious. Looking forward to any insights. Thanks.

Well.. Since you prefer the verbose boot messages, I think you should just remove quiet splash permanently. I have no other solution.
A few tips:
You can edit your kernel command line by pressing Esc. in the 3 seconds grub gives you before booting the kernel.
Go to the line you want to edit, Press ¨e¨ (**E**dit). You can edit it the way you want. Press enter to commit. Then press B to boot.
These changes will not be saved, menu.lst will not be affected.

If you get no window borders, you have to restart your window manager. There are 3 options. 
-Metacity
-Compiz
-Compiz with emerald

 If you´re using Compiz in combination with emerald, you have to execute ```
emerald --replace
```
 It can be you can´t type it in a run dialog, so you have to run it in a terminal. After that, you can run it in a run dialog (ALt-F2). Then you can close the terminal.
The same goes for ```
compiz --replace
```for compiz without emerald, and ```
metacity --replace
``` for metacity.

About your Kppp.. I´m sorry, I haven´t dialed in for 7 or 8 years.. Make sure your cables are good and your settings are correct. This can not be caused by the splash screen.  I can´t help you further on this.

Hope this wel helpfull, if so, please thank me.

Roald

---

### Post by goofydawg on 2008-02-20
I was watching your posts with interest in that my machine is giving me a split login screen at 640x480 resolution.  using an old monitor so this is a must...  after logging in the screen is fine.. following the screen settings from the desktop.   i can see well enough to login but it is annoying.   it would seem that   quiet and   splash  are two separate yet related  options.   if at end of kernel line it reads   ro   only   i get boot messages and no ubuntu splash.   with    " ro  splash "   it get the splash screen and boot messages  in the splash screen.   the login screen is split with all settings..  .etc/usplash.conf is 640x480 and the update command has been executed.   only thing remaing is to fix the login screen.

Thanks in advance for any insight

Jim

---

### Post by fmc6338 on 2008-02-20
> **roaldz said:**
> Looks like that Usplash problem.

The easy way:
```
gksu gedit /boot/grub/menu.lst
```

Find your kernel command line.

Looks someting like this:
```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6247b01f-c131-4cd0-8491-2407fa491503 ro **quiet splash**
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

```
Remove ¨quiet splash¨ at the end of the ¨kernel¨ line.

Save the file. The next time you boot, you´ll see verbose boot messages, no splash screen. I bet it´ll be faster, but also somekind of ugly.

The good way:


Hope it helped, if so, please thank me.

Roald

I have ibm t40
1gig ram
ati 7500
40 gig hdd 
ubuntu 710

eureka thanks for the tip.  I went into synaptic package manager and deleted the quiet splash¨ program,  now my laptop boots in a furious hurry.

---

### Post by Partyboi2 on 2008-02-21
[here]("http://ubuntuforums.org/showthread.php?t=89491") is a useful link to speed up boot process

---

### Post by fallsoff on 2008-03-02
Helo
Please check this post [on the same forum page you posted to but up a bit]: 

[SOLVED] VERY SLOW start up on Acer laptop? . 

It will give you a simple way to reset the video settings if they are off. Worked for me!
Good luck
fallsoff

---

