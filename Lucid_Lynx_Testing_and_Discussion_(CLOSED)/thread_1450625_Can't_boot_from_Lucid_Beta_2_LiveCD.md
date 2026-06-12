---
title: "Can't boot from Lucid Beta 2 LiveCD"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Sennaista on 2010-04-09
Hi everyone,

First just let me say that I have searched the forums and although there seems to be a lot of threads about the same issue I don't think they quite explain my problem.

I have tried to boot from a LiveCD and a USB drive, with and without nomodset but in all cases it fails. The purple screen comes and goes then I get some lines on top of my screen with this message printed underneath them:
```

(process:418): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
```Process number changes from boot to boot I think.

The screen stays like that for a while, then it goes to blank and after sometime I start getting lines back on the screen but they keep flashing on and off. It stays like this for ever.

My system:

Intel i5
ATI Radeon HD4730
4GB RAM
Dual monitors

Any ideas what could be wrong?

---

### Post by cristianrosa on 2010-04-09
I am not completly sure about this, but I think that error message has nothing to do with the real problem. I've seen tons of posts and bug reports about boot problems with that message showing, but in my case the system boots and works fine even with that message being shown (I see it at shutdown/reboot).

---

### Post by Sennaista on 2010-04-09
I removed one of the monitors as somebody suggested that might be the issue in a different thread but still no luck. I don't see the error message any more but the screen just keeps flashing on and off with broken graphics after plymouth has done its work.

Even tried with a the daily build from two days ago but it's the same. :(

---

### Post by -Robert- on 2010-04-09
I don't know if it solves your problem, but did you try this: [http://ubuntuforums.org/showthread.php?t=1450179&page=3](http://ubuntuforums.org/showthread.php?t=1450179&page=3) (post #22) ?

---

### Post by Sennaista on 2010-04-09
Yeah, done that as well. I know the ISO is sound because I can boot into Lucid Live on my laptop without doing any of those things.

I had the same issue last year when trying to boot Karmic LiveCD on my desktop but then using safe-mode did the trick and I could load the Live Session. This time around using nomodeset doesn't help at all. Very frustrating.

---

### Post by Sennaista on 2010-04-10
I have done more testing by dropping down to terminal (Ctrl+Alt+F1) and executing

```
dmesg | grep drm
```See those messages at the bottom of the screen?

]

I think my problem is related to this [bug]("https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/509273?comments=all") which is supposedly fixed. I download the daily build from today (10/04/2010) but still can't boot with the same error messages. Either the bug is still there or the fix hasn't been incorporated into the daily build.

---

### Post by Sir Rodness on 2010-04-10
I'm waiting for the final release hoping it will have the safe mode option. Without safe-mode I will not be able to install or even see Lucid on my machine.

---

### Post by eltonw on 2010-04-10
> **Sennaista said:**
> Hi everyone,

First just let me say that I have searched the forums and although there seems to be a lot of threads about the same issue I don't think they quite explain my problem.

I have tried to boot from a LiveCD and a USB drive, with and without nomodset but in all cases it fails. The purple screen comes and goes then I get some lines on top of my screen with this message printed underneath them:
```

(process:418): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
```Process number changes from boot to boot I think.

The screen stays like that for a while, then it goes to blank and after sometime I start getting lines back on the screen but they keep flashing on and off. It stays like this for ever.

My system:

Intel i5
ATI Radeon HD4730
4GB RAM
Dual monitors

Any ideas what could be wrong?
Possibly it might be just a bad burn of the CD. Did you verify the MD5 sums after downloading the iso image?

HTH...

---

### Post by cariboo on 2010-04-10
> **Sir Rodness said:**
> I'm waiting for the final release hoping it will have the safe mode option. Without safe-mode I will not be able to install or even see Lucid on my machine.

There already is that option available. At the initial screen press any key and you should see the menu options (note: I haven't tried this myself) Press F6 and select nomodeset, then continue on with your installation.

---

### Post by Sennaista on 2010-04-11
I managed to find a work around for it, here's what I did:

When the GPU beings to reset every few second press Ctrl+Alt+F1 to drop to terminal then do

```
sudo stop gdm

sudo nano /etc/X11/xorg.conf

```Type in the following set of commands then save and exit.

```
# /etc/X11/xorg.conf
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fbdev"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```This would tell X to use framebuffer instead of the actual drivers for your graphics card. After saving the file all you need to do is to run

```
sudo start gdm
```And you will get the LiveCD desktop and you can install from there. After it is finished you can restart your computer and either use the same xorg.conf file or install the official ATI drivers and let them take over. Whatever you do though don't just use the open source drivers because you won't be able to boot and have to do all the above steps again.

---

### Post by Sir Rodness on 2010-04-12
> **cariboo907 said:**
> There already is that option available. At the initial screen press any key and you should see the menu options (note: I haven't tried this myself) Press F6 and select nomodeset, then continue on with your installation.

Thanks, but that was a partial fix. The nomodeset works for checking out ubuntu, which looks pretty sweet I must say, however the actual installation appears to ignore that option and causes my video card to crash immediately after restarting for the first time. Unless there is another option that also works for the install like it works for the live CD.

---

### Post by Sir Rodness on 2010-04-26
> **Sir Rodness said:**
> Thanks, but that was a partial fix. The nomodeset works for checking out ubuntu, which looks pretty sweet I must say, however the actual installation appears to ignore that option and causes my video card to crash immediately after restarting for the first time. Unless there is another option that also works for the install like it works for the live CD.

As it turns out 'nomodeset' is the key to working without F4 safe mode. Only difference is that I had to use the option from F6 during install and then I had to manually add it to the my boot options when I restarted my computer after the install was completed. 

So after I finished my install I pressed shift to get to the grub selection screen and then pressed 'e' to edit my kernel boot options. Added 'nomodeset' to the boot options. Then used ctrl-x to continue boot. Now that I was safely able to enter the desktop and then able to do all my updates to my system, video driver, etc. 

Hope this helps anyone else that is unable to install like me without the use of safe mode.

Cheers! :)

---

