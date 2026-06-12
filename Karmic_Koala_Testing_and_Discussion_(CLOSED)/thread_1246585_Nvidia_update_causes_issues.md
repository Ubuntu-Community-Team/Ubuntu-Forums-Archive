---
title: "Nvidia update causes issues"
date: 2009-08-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by froggyswamp on 2009-08-21
Folks,
The new nvidia update (to version 185...31) broke my system. After restart gdm doesn't start, not even in recovery mode. I downloaded and installed a new x64 daily build, but the nvidia (proprietary) drivers won't install. Using x64 Karmic.
I have GeForce 9600GT 512MB

Only thing interesting I found in dmesg:
> 
[ 1075.790906] nvidia: module license 'NVIDIA' taints kernel.
[ 1075.790911] Disabling lock debugging due to kernel taint
[ 1076.043607] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1076.043620] nvidia 0000:01:00.0: setting latency timer to 64
[ 1076.043828] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.31  Tue Jul 28 17:52:27 PDT 2009


---

### Post by rtalcott on 2009-08-21
try this solution...worked for me:
   	
Boots into prompt - no GUI 
[http://ubuntuforums.org/showthread.php?t=1246448](http://ubuntuforums.org/showthread.php?t=1246448)

rt

---

### Post by cornflake000 on 2009-08-21
I just added my input there as well.  It has always worked for me...

---

### Post by froggyswamp on 2009-08-21
> **rtalcott said:**
> try this solution...worked for me:
       
Boots into prompt - no GUI 
[http://ubuntuforums.org/showthread.php?t=1246448](http://ubuntuforums.org/showthread.php?t=1246448)

rt
thanks, that helped, also when i did the dist upgrade I got about 100mb of updates, after restart I did "sudo nvidia-xconfig", restarted again and now nvidia is running.

---

### Post by Regenweald on 2009-08-22
Also, you should "aptitude safe-upgrade" it is currently holding nvidia back for me.

---

### Post by philinux on 2009-08-22
I used synaptic to upgrade and it left me with no driver. Recovery did not work either.
Message
startx - nvidia module does not exist
no drivers
no screens

Short story. It dropped me to a shell where I could login.

sudo apt-get install nvidia-glx-185

Fixed it.

---

### Post by zenarcher on 2009-08-22
> **philinux said:**
> I used synaptic to upgrade and it left me with no driver. Recovery did not work either.
Message
startx - nvidia module does not exist
no drivers
no screens

Short story. It dropped me to a shell where I could login.

sudo apt-get install nvidia-glx-185

Fixed it.

Worked for me, as well! :P

Thanks,
zenarcher

---

### Post by cyberkilla on 2009-08-22
That's what I did too.

Unfortunately, instead of it booting into the command line as it did originally, it boots into X and starts flickering, hanging, randomly rebooting, and when it's not doing any of the above, there are artefacts flying about the screen.

I've tried both the 185 and 190 versions. I've even installed the PPA suggested in another thread, with more recent 185 versions - those fail to provide an acceptable experience either.

It all started a couple of hours ago, when the update manager informed me of a "partial upgrade".

Can anyone shed some light on this? I upgraded to Alpha 4 to get the hotkeys on my Sony Vaio VGN-AR41E working.

The video card is an NVidia GeForce 8400M GT.

---

### Post by fballem on 2009-08-22
I also had the problem, and the fix in post#5 of [http://ubuntuforums.org/showthread.php?t=1246448](http://ubuntuforums.org/showthread.php?t=1246448) didn't work for me.

When my system booted, I was at a console (not a place that I had been before), so:

[LIST=1]
[*]at the login prompt, I type my username, then pressed enter.
[*]At the password prompt, I type my password, then pressed enter.
[*]type 'sudo apt-get autoremove', without the quotes, then pressed enter. This removed a lot of packages. You will have to enter your password when asked, then select 'Y', when asked. The packages that get removed include those that came down in the partial upgrade.
[*]type 'sudo reboot', without the quotes, then pressed enter. This will reboot the machine.
[*]On reboot, I was back at the console. Typed in my userid and password when asked.
[*]typed 'sudo apt-get update', without the quotes, then pressed enter. This will refresh the list of packages.
[*]type 'sudo apt-get intall nvidia-185-kernel-source', without the quotes, then pressed enter. This correctly installs the nvidia driver update that caused the problem in the first place.
[*]type 'sudo reboot', then press enter. This will restart your machine.
[*]On reboot, you should be back at the gui. If you are, then run Update Manager (System > Administration > Update Manager). Make sure that you Check for new software before you select the Install button.
[*]You will need to restart - even if it doesn't tell you to restart.
[*]You should then be good to go.
[/LIST]

---

### Post by cyberkilla on 2009-08-22
> **cyberkilla said:**
> That's what I did too.

Unfortunately, instead of it booting into the command line as it did originally, it boots into X and starts flickering, hanging, randomly rebooting, and when it's not doing any of the above, there are artefacts flying about the screen.

I've tried both the 185 and 190 versions. I've even installed the PPA suggested in another thread, with more recent 185 versions - those fail to provide an acceptable experience either.

It all started a couple of hours ago, when the update manager informed me of a "partial upgrade".

Can anyone shed some light on this? I upgraded to Alpha 4 to get the hotkeys on my Sony Vaio VGN-AR41E working.

The video card is an NVidia GeForce 8400M GT.

Is anybody else getting artefacts, flickering, reboots and hangs?

I can't get it to stop.

---

### Post by cyberkilla on 2009-08-22
Nobody is having this problem?

I can't get a working driver. 173 fails to load X, 185 loads but there are artifacts on the screen after a few seconds, followed by a hard crash that requires me to hold down the off switch.

I am running Karmic Alpha 4, with a Vaio VGN-AR41E laptop and an NVidia GeForce 8400M GT video card.

Can anyone explain to me why my card doesn't work with the latest driver? The laptop is only ~2 years old, if memory serves.

---

### Post by FrancoNero on 2009-08-22
none of the above steps worked for me what now? I've removed and reinstalled the nvidia packages, rebootet, triet to start x etc... all i get is the screen switching off where i should actually be getting to the log-in screen.... bummer.

what's the terminal command to switch back to the pre-installed open source driver instead? i'll just switch to the nvidia driver at a later point then

---

### Post by cariboo on 2009-08-22
I had the same problem, I got dropped to a prompt. I restarted in recovery mode and at the menu selected drop to root prompt. I then renamed /etc/X11/xorg.conf to /etc/X11/xorg.conf.bak

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

then typed exit and selected resume from the menu. I started with out an xorg.conf, once at the desktop I enabled the driver in System-->Administration-->Hardware Drivers. Logged out, then back in again.

---

### Post by cyberkilla on 2009-08-22
Dammit, I can't figure this out.

Every time I install the 185 driver, it boots into X, allows me to log in, but displays artifacts on the screen. After a while it flickers and the computer reboots.

If I install driver 173, it doesn't boot at all. It probably doesn't even support my card.

What can I do to fix this?

NVidia GeForce 8400M GT, Vaio VGN-AR41E

Karmic Alpha 4.

Come on, won't somebody respond?:) I never get a response on these forums.

---

### Post by cariboo on 2009-08-22
You have to have patience, It could be that nobody that has read this thread has had the same problem.

Do you have the same problem if you downgrade to the previous driver?

---

### Post by FrancoNero on 2009-08-22
> **cariboo907 said:**
> I had the same problem, I got dropped to a prompt. I restarted in recovery mode and at the menu selected drop to root prompt. I then renamed /etc/X11/xorg.conf to /etc/X11/xorg.conf.bak

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

then typed exit and selected resume from the menu. I started with out an xorg.conf, once at the desktop I enabled the driver in System-->Administration-->Hardware Drivers. Logged out, then back in again.

that worked, thank you. now i'm hesitant however, to reactivat the nvidia driver. i'll play around with karmic without it for now :)

---

### Post by cyberkilla on 2009-08-22
> **cariboo907 said:**
> You have to have patience, It could be that nobody that has read this thread has had the same problem.

Do you have the same problem if you downgrade to the previous driver?

I cannot downgrade because there is nothing else in the repository except from 173 (which doesn't even compile for this kernel).

---

