---
title: "Upgraded from 9.10 to 10.04 and my dual monitor setup doesn't work anymore"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by jmisasa on 2010-05-01
It used to work perfectly on Ubuntu 9.10 but I get "input not supported" in the secondary monitor.

chema@chema-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: **ATI Technologies Inc RV280 [Radeon 9200 PRO]** (rev 01)

What could it be?

Thank you.

---

### Post by notte on 2010-05-01
Similar problem here. 

(Ati Radeon 9250 - Ubuntu 10.4) 
[i]{lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)}[/i]

My dual screen configuration was working fine with 9.10, until I was forced to a fresh install yesterday.

The screen looks like it has been correctly drawn (3200x1200) in the *desktop chooser applet* and the windows can be placed outside the right limit of the screen. But in both the monitors is drawn the same screen (the *monitor preferences* window identifies each screen with a coloured rectangle on the upper left corner: it reports the same name).
I tried to do the usual:
```
xrandr --output VGA-0 --mode 1600x1200
xrandr --output DVI-0 --mode 1600x1200
xrandr --output VGA-0 --left-of DVI-0
```
but nothing happens. 
I already put the *virtual*  parameter in the correct xorg.conf section.
No graphical tool could help.

Hope someone find a solution, I find really uncomfortable with only one monitor...

---

### Post by jmisasa on 2010-05-01
What I did was an upgrade from update manager, not a fresh installation but we have the same problem.

I am even thinking about doing a downgrade, at least until the issue gets solved. I am totally lame with only one monitor.

---

### Post by robvas on 2010-05-01
When you boot the computer up, before Ubuntu loads are your monitors both displaying the same thing?

Also, does the LiveCD display both monitors properly?

Dual 19 or larger monitors? (> 1280x1024)

---

### Post by notte on 2010-05-02
> **robvas said:**
> When you boot the computer up, before Ubuntu loads are your monitors both displaying the same thing?

Also, does the LiveCD display both monitors properly?

Dual 19 or larger monitors? (> 1280x1024)

I use 2x19" monitors 1600x1200 (3200 1200) and yes, monitors are always both displaying the same thing, even now. Once logged in, with xrandr commands, the desktop really extends to 3200x1200, but what I see is the first 1600x1200 on both screens.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=155106&stc=1&d=1272790519[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=155107&stc=1&d=1272790519[/IMG]


PS
Livecd usually show cloned screens, but I haven't got one now to test.

---

### Post by wcorey on 2010-05-02
I believe one of the features of 10.4 was a new open source video driver such that you weren't subject to using a restricted driver. Try System->Administration->Hardware drivers. You may need to reinstall the restricted driver. Although I recently upgraded to 10.4 from 9.10 and it is still using the restricted driver for my nvidia. However, at work I put on some maintenance and lost my second monitor, which is to say it just mirrored the first. In my case I used the Nvidia X Server settings application and that reset the config such that I had, after reboot, my second monitor working properly.

---

### Post by hidden.nld on 2010-05-06
I had the Similar problem.

Notice The monitor identification in the upper left corners have the same color!

I fixxed this issue by disconnect the monitor an boot the system and login.
After logging in reconnect the monitor and go to System->Preference-> Monitors
Now your monitor starts to work as a second monitor again :)

---

### Post by dino99 on 2010-05-06
aticonfig --help

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by notte on 2010-05-06
Thanks for all the replies!

I usually run the opensource driver, I prefer not to install the proprietary one. 
On the other hand, If this was the only way... The adapter I use is not supported any more by ATI, so I should find an old package which probably won't work with lucid. 

I'll try the trick to disconnect the secondary monitor... I feel like this is a lucky suggestion. I'll update the topic.

---

### Post by notte on 2010-05-06
> **hidden.nld said:**
> I had the Similar problem.

Notice The monitor identification in the upper left corners have the same color!

I fixxed this issue by disconnect the monitor an boot the system and login.
After logging in reconnect the monitor and go to System->Preference-> Monitors
Now your monitor starts to work as a second monitor again :)


BINGO!
You were right! That was the right solution... Don't ask me why, but it is working now!

Steps:
Turn on the computer with the secondary monitor (for me the one attached to the dvi connector) unplugged. Login and THEN plug in the DVI connector. Run your system's tool to correctly position your screen and monitors, or simply type in your preferred terminal:

```
xrandr --output VGA-0 --left-of DVI-0
```
or
```
xrandr --output VGA-0 --right-of DVI-0
```

Don't know where to suggest this "bug" for a real fix...

---

### Post by jmisasa on 2010-05-07
It's working again! Thank you @[hidden.nld]("http://ubuntuforums.org/member.php?u=1068580") @[notte]("http://ubuntuforums.org/member.php?u=214305")

---

### Post by notte on 2010-05-07
:(

*Randomly* it turns to show only one screen... It is not very comfortable to always unplug one monitor before turning on the machine...

Actually... randomly is not really correct. If I want to use both the screens with an extended desktop, I have tu turn on the computer with one connector unplugged.

:(

---

### Post by notte on 2010-05-09
Filed bug report here: 

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/577959](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/577959)

---

### Post by dibuntux on 2010-06-30
I followed your advise after messing around with amdcccle (Ati control center: sudo amdcccle) and not getting the right resolution for my main monitor. I was always getting the 1440x900 res of my secondary on both, instead of 1680x1050 and 1440x900.

So I unplugged the second (1440x900) and using amdcccle I was able to set the maximum res on the main, 1680x1050.
Then I plugged the second and let amdcccle discover the new monitor.
After that I selected multi-display setup and restart.
Now everything is back at normal.

Upgrade 9.10->10.04 on AMD64 with ATI HD2400pro

---

### Post by Qazzian on 2010-08-18
This worked for me to, but I also had 'unify Outputs' selected in the KRandRTray settings. Un-checking that before rebooting helped.

---

