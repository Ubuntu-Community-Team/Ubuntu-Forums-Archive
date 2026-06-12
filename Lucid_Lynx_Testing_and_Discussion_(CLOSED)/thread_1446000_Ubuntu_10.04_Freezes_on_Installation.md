---
title: "Ubuntu 10.04 Freezes on Installation"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by d1gw33d on 2010-04-03
Hello,

Kind of a novice so sorry if I don't provide all the proper information. I've played around with various Ubuntu builds over the years with no issue but I can't seem to install the 10.04 beta. It freezes about 60-90 seconds into the install screen (purple background w/the orange dots... the dots all stop)

The computer becomes unresponsive. I've left it in this state for 20+ minutes. Tapping the power button reveals strange (to me) errors. Not sure how to access any logs or if I'm able to since it doesn't go very far into the installation process.

I wrote down most of whats displayed;

```

Process: 446 getpwuid_r() failed due to unknown user id (0)

init: unreadahead-other main process (1326) terminated with status 4
init: unreadahead-other main process (1327) terminated with status 4
init: unreadahead-other main process (1328) terminated with status 4

acpid: exiting
init: ubiquity main process (1520) killed by TERM signal
tty3: ??? (didn't write down)
tty4: ??? (didn't write down)
tty5: ??? (didn't write down)

modem-manager: Caught Signal 15, shutting down
init: disconnected from system bus
could not write bytes: broken pipe

``` 

Hardware:

Intel Core i7 920
ASRock X58 Extreme
6GB DDR3 OCZ Gold
Nvidia GTX 260
DVD-RW SATA
Intel 80GB SSD (Win7)
WD 750GB SATA (Storage)
WD 320GB SATA (Storage)(Want to use for Ubuntu)

Recent changes since my last successful Ubuntu (9.10) install on this system were adding the Intel SSD and switching drives to AHCI. I had to switch to AHCI to ensure TRIM mode is enabled on the SSD in Windows 7. So I'm not sure if thats the issue or what but its the only change since. I have not attempted to install 9.10 as of yet. Any assistance would be appreciated. Thanks in advance.

EDIT: I get the same errors with the 64 and 32 bit builds.

---

### Post by d1gw33d on 2010-04-04
Seriously? Nothing?

---

### Post by robstel on 2010-04-05
Same here, and Googling shows that we're not the only ones. I found a post that suggested setting the nomodeset boot option, and that worked for me: 

When the Ubuntu logo comes up, press any key to bring up the boot menu (took me a while to realise that's what the icons at the bottom were trying to tell me!), then F6, select "nomodeset" then ESC and continue running Ubuntu.

---

### Post by d1gw33d on 2010-04-08
I'll give it a shot... thanks.

**UPDATE**

Didn't work. Though instead of going to a black screen with the previous errors, it stays on the 'purple' install screen and outputs these;

```

init: unreadahead-other main process (1326) terminated with status 4
init: unreadahead-other main process (1327) terminated with status 4

```

Then the 4 orange dots stop changing color and the system becomes unresponsive.

---

### Post by null_pointer_us on 2010-04-08
The ureadahead status 4 stuff looks odd, but it is an innocuous bug (see sticky).

Have you tried the media check option (on the boot menu)?

Or, just in case it is a compatibility issue in this release, you might try searching with your ASRock X58 Extreme or the DVD-RW drive model number as keywords.

---

### Post by powder on 2010-04-08
I would wait for the Beta 2 live CD to be released later today and give it a try.  If you still have the problem I would recommend filing a bug.

P.S. AHCI has nothing to do with TRIM.

---

### Post by stilling on 2010-04-08
same to me but i did`it by removing 1 wireless card out from my desktop pc

so maybe you have 1 network card or something that ubuntu does not know

---

### Post by cybrt3k on 2010-04-08
Just Tested with my Asus EEEPC 1005 HA and it is still freezing for me after the keyboard selection with Beta 2.

---

### Post by hornedfiend on 2010-04-09
Hi guys,

I don't know if this makes any difference, but my Ubuntu 10.04 beta 2 install was halting in the purple logo screen (WUBI installation) . The way I solved it ( am now in copying files... Screen) is by selecting verbouse mode. Try this, maybe smth happens.

---

### Post by rajeev_n on 2010-04-12
I tried with beta -2 on my machine which has integrated Via Unichrome. Tried with nomodeset , no luck. !!

Any way to see the logs in live cd?

---

### Post by bluenova on 2010-04-12
I had the same issue. I sorted it by removing 'quiet splash' from the boot command. I read afterwards that there is an issue with having more than 1 monitor connected which I did have, but I don't know if that was the issue though.

---

### Post by nanog on 2010-04-12
try removing plymouth. there seem to be alot of recent issues surrounding plymouth.

---

### Post by garvinrick4 on 2010-04-12
> **d1gw33d said:**
> Hello,

Kind of a novice so sorry if I don't provide all the proper information. I've played around with various Ubuntu builds over the years with no issue but I can't seem to install the 10.04 beta. It freezes about 60-90 seconds into the install screen (purple background w/the orange dots... the dots all stop)

The computer becomes unresponsive. I've left it in this state for 20+ minutes. Tapping the power button reveals strange (to me) errors. Not sure how to access any logs or if I'm able to since it doesn't go very far into the installation process.

I wrote down most of whats displayed;

```

Process: 446 getpwuid_r() failed due to unknown user id (0)

init: unreadahead-other main process (1326) terminated with status 4
init: unreadahead-other main process (1327) terminated with status 4
init: unreadahead-other main process (1328) terminated with status 4

acpid: exiting
init: ubiquity main process (1520) killed by TERM signal
tty3: ??? (didn't write down)
tty4: ??? (didn't write down)
tty5: ??? (didn't write down)

modem-manager: Caught Signal 15, shutting down
init: disconnected from system bus
could not write bytes: broken pipe

``` 

Hardware:

Intel Core i7 920
ASRock X58 Extreme
6GB DDR3 OCZ Gold
Nvidia GTX 260
DVD-RW SATA
Intel 80GB SSD (Win7)
WD 750GB SATA (Storage)
WD 320GB SATA (Storage)(Want to use for Ubuntu)

Recent changes since my last successful Ubuntu (9.10) install on this system were adding the Intel SSD and switching drives to AHCI. I had to switch to AHCI to ensure TRIM mode is enabled on the SSD in Windows 7. So I'm not sure if thats the issue or what but its the only change since. I have not attempted to install 9.10 as of yet. Any assistance would be appreciated. Thanks in advance.

EDIT: I get the same errors with the 64 and 32 bit builds.
Why do you not just try 9.10 with all the new hardware and a Beta
OS of Ubuntu Linux. Try a stable version and see if it is successful so you know where you stand.
It would help to know which gun you are shooting yourself in the foot with, know what a mean.

---

### Post by twisted_steel on 2010-04-12
> **bluenova said:**
> I had the same issue. I sorted it by removing 'quiet splash' from the boot command. I read afterwards that there is an issue with having more than 1 monitor connected which I did have, but I don't know if that was the issue though.

I also had my Beta 2 install lock up last night several times.  I have 2 monitors connected and had no idea that there was even an option to bring up an edit menu.  I saw some icons at the bottom of the screen, but they quickly disappeared.  I will try again with the boot command adjustment.

This is on the 64-bit standard (desktop) installation CD.

---

### Post by twisted_steel on 2010-04-12
> **twisted_steel said:**
> I also had my Beta 2 install lock up last night several times.  I have 2 monitors connected and had no idea that there was even an option to bring up an edit menu.  I saw some icons at the bottom of the screen, but they quickly disappeared.  I will try again with the boot command adjustment.

This is on the 64-bit standard (desktop) installation CD.

Removing the quiet and splash options did the trick.  I had to the freeze again after rebooting into the new installation with Alt+SysReq+K.  Now that I have the nvidia-current drivers in place, it boots up properly every time.

---

### Post by iClouseau88 on 2010-04-12
Right after the installer crashes, the screen momentarily turns off then goes back with a Ubuntu desktop that has 2 folders near the top left corner: "Examples" and "Install Ubuntu 10.04".  On the title bar at the top, hit "Places" then "Home" then "var" then "var/log/syslog", "/var/log/debug", etc.

---

### Post by mpkossen on 2010-04-16
I can confirm that (with the Ubuntu Lucid Beta 2, x64 Desktop image) removing the splash and quiet parameters works.

Thanks for the tip, guys!

---

### Post by madsc89 on 2010-04-18
I've given up installing beta 2 32 bit on an Asus F5R.

I tried removing quiet and spalsh, but every time it hangs, freezes or crashes when the install window appears. 

I also got some unreadahead errors, as well as some errors about drivers not found. This was while loading the system, before it hung.

Hopefully the Final release will be better.

---

### Post by twisted_steel on 2010-04-18
> **madsc89 said:**
> I've given up installing beta 2 32 bit on an Asus F5R.

I tried removing quiet and spalsh, but every time it hangs, freezes or crashes when the install window appears. 

I also got some unreadahead errors, as well as some errors about drivers not found. This was while loading the system, before it hung.

Hopefully the Final release will be better.

I would file a bug with the errors you are seeing if you haven't done so.  The developers may not be aware of the issue.

---

### Post by sirrod on 2010-04-20
One more report of removing "quiet" and "splash" from boot command worked.  I do have two screens (on the same card).  Once everything was done and updated, I installed the proper nvidia drivers (nvidia-current) with apt-get install (instead of the restricted drivers installer that kept failing), rebooted, and made sure they were loaded.  ```
lsmod | grep nvidia
```  From then on, I've been booting cleanly although it is without the "pretty" splash screen even though it is not disabled.

---

### Post by ronparent on 2010-04-20
"From then on, I've been booting cleanly although it is without the "pretty" splash screen even though it is not disabled."

I've noted same. What about that?

---

### Post by twisted_steel on 2010-04-20
> **ronparent said:**
> "From then on, I've been booting cleanly although it is without the "pretty" splash screen even though it is not disabled."

I've noted same. What about that?

It appears that Plymouth and the official drivers do not play nicely.  I bookmarked this tutorial from another thread on how to get it working, but I wanted to wait for the final release to see if it is fixed before I started playing around.  Here it is: [http://www.sucka.net/2010/03/nvidia-drivers-ubuntu-10-04-lucid-lynx/](http://www.sucka.net/2010/03/nvidia-drivers-ubuntu-10-04-lucid-lynx/)

---

### Post by franc00018 on 2010-04-20
All alternate cds won't install on my computer.
The first that worked is Kubuntu 10.04 beta 2
That's what I'm using right now.

---

### Post by thusi87 on 2010-04-23
Well the problem seems to be in the new foss drivers for Nvidia. Apart from disabling "quiet splash" from the boot menu in the installer, insert "nouveau.modset=0"

This did the trick with the installer :) I could successfully install 10.04 RC.
And to get to the boot menu press shift as the thing boots up with the purple screen..and answer no for the first question.

I had to edit the grub after installation as well and repeat the nov....thing and blacklist the foss driver as well to get things smooth....

:@ what a real pain...they better do sm thign in the final release abt this..or all these great efforts will be wasted because of a stupid driver

---

