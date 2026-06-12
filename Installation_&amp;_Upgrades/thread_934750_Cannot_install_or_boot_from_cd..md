---
title: "Cannot install or boot from cd."
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by importune on 2008-09-30
I've never installed any version of linux on any of my machines, but I figured I'd give it a shot. I used partition manager and gave myself 10 gig off to the side to do this with, and downloaded the latest version of ubuntu. I put the disc in, booted from it, and clicked the first option, the one that says install or boot from cd. I let the whole thing run through its boot up process but nearing (what i believe is) the end it fails. Comes up with an error -> "Unable to start the x server (your graphic interface)." Or something along those lines. Sorry, its been a couple days since i've tried.


Running a dell inspiron 9400, windows xp, 2 gig ram, intel core duo 1.8 ghz.


Ideas? :confused:

---

### Post by overdrank on 2008-09-30
> **importune said:**
> I've never installed any version of linux on any of my machines, but I figured I'd give it a shot. I used partition manager and gave myself 10 gig off to the side to do this with, and downloaded the latest version of ubuntu. I put the disc in, booted from it, and clicked the first option, the one that says install or boot from cd. I let the whole thing run through its boot up process but nearing (what i believe is) the end it fails. Comes up with an error -> "Unable to start the x server (your graphic interface)." Or something along those lines. Sorry, its been a couple days since i've tried.


Running a dell inspiron 9400, windows xp, 2 gig ram, intel core duo 1.8 ghz.


Ideas? :confused:

Hi and welcome, what graphics card? Have you tried the options under F4 from the start install screen?

---

### Post by cariboo on 2008-09-30
You should be able to start in safe graphics mode by pressing F4 and selecting it. The problem is your video card isn't detected properly so X can't start. I had the same problem about 3 releases back, but during the installation the card was detected properly.

Jim

---

### Post by importune on 2008-10-01
Wow, fast responces. I'll give it a run now and post after i'm done playing with my new os.

---

### Post by importune on 2008-10-01
Unfortunately I've had no luck. I tried grahics in safe mode 3 times, each with different F4 settings. First I tried VGA, second 640x480x16, third 800x600x32. Every time I tried I got the same error screen as before. 

The error screen looks like this ->
[http://img134.imageshack.us/img134/8596/3800yq1.jpg](http://img134.imageshack.us/img134/8596/3800yq1.jpg)

I've also noticed that if I let the screen sit for a bit, a different error keeps poping up on my screen. That error is in black and looks like it doesn't fit at all, but this is what it says ->

```
bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
```


I am really interested in getting this to work, any help would be appreciated.



EDIT: Btw, I'm using a ATI Mobility Radeon X1400.

---

### Post by overdrank on 2008-10-01
Ok I would say check the cd for errors and if you burned the cd then also check the iso for errors
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
You may also try and install with the alternate cd as it is a text based installer and then get the graphics issue then.

---

### Post by importune on 2008-10-01
> **overdrank said:**
> Ok I would say check the cd for errors and if you burned the cd then also check the iso for errors
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
You may also try and install with the alternate cd as it is a text based installer and then get the graphics issue then.

I figured this was coming. 

I'm sure this isn't the problem. I've downloaded 4 different copies of the iso, from different mirrors, and burnt 5. I've also downloaded one custom version of ubuntu and tried that as well. All were burnt at 4x. I'm going to try to check them all, but I really don't think the cd's the problem.


I'm trying an auto-installer windows executable, to avoid having to burn the cd and live boot linux. It'll take awhile to download as my internet connection sucks ATM, but I'll post back with an update.

---

### Post by importune on 2008-10-01
Ok, this is getting really frustrating.

I've got ubuntu completely installed on a partition via the auto-installer, i reboot my computer, choose to boot into ubuntu, it starts booting and has the same errors as before. My assumption is that it has to be something to do with my hardware. Any ideas?

---

### Post by overdrank on 2008-10-01
You can try and boot into recovery mode and use the xfix option. Recovery mode is usually the second choice from the grub. After the xfix option then try and proceed with the normal boot and hopefully this will correct the issue.

---

### Post by importune on 2008-10-01
> **overdrank said:**
> You can try and boot into recovery mode and use the xfix option. Recovery mode is usually the second choice from the grub. After the xfix option then try and proceed with the normal boot and hopefully this will correct the issue.

I'm a little more noob than that, what exactly is the grub? I'm assuming the menu from the bootable cd? I didn't see a recovery mode...?

---

### Post by vluhd on 2008-10-01
grub is the boot menu.
if ubuntu is the only thing you have installed (im assuming it's not, you mentioned xp) it will say something like press esc for menu in 3..2..1
but! since you have xp grub should be the menu from which you select what OS you want to boot into.
it should show up as
Ubuntu blahblahblahblah
Ubuntu blahblahblahblah(safe mode)
Recovery mode       (<-you want this one!!)
Windows XP

it will then bring up the command line, then do your thing.

---

### Post by cariboo on 2008-10-01
When you first start your computer you should see a grub menu where you can select what os you want to boot. The 2nd selection from the top is recovery mode, choose that,you will see a lot of messages scroll by. Eventually you will come to a menu, select **xfix**, you will be asked questions about your mouse and keyboard as well as your video card and monitor. I'ts been a while since I've had to use it, but i believe it will autodetect your video card and display. If not, your computer has an Nvidia Go 7900gs video card.

I have a question, how are you installing Ubuntu, as I've never seen a error message like that come up before. Are you installing inside of windows or are installing a complete new installation by having to setup partitions?

Jim

---

### Post by overdrank on 2008-10-01
> **importune said:**
> Ok, this is getting really frustrating.

I've got ubuntu completely installed on a partition via the auto-installer, i reboot my computer, choose to boot into ubuntu, it starts booting and has the same errors as before. My assumption is that it has to be something to do with my hardware. Any ideas?

Ok when you state auto-installer I believe you mean Wubi from withing windows?
As the others have stated if you have installed ubuntu on it own partition you should be able to see the grub while booting the system.

---

### Post by importune on 2008-10-02
Uh, aparently ubuntu doesn't support my graphics card yet. I finnally got it working with this ->
 [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853)


Unfortunately, despite me getting the live cd to actually boot, I cannot install it because when I use dpkg-reconfigure to select the settings, no matter what I choose, I seem to get a resolution of 320x240...which just isn't enough screen to see the options for installing.

---

### Post by cariboo on 2008-10-02
Grub comes up when you first boot your computer and allows you te choose which os you want to use. It has nothing to do with the livecd. See my previous post.

Jim

---

