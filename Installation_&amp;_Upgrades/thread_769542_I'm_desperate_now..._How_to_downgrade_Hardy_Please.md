---
title: "I'm desperate now... How to downgrade Hardy?? Please?"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by mpetrovic on 2008-04-26
Two days ago I've decided to upgrade a "perfectly" stable 7.10 to "stable" Hardy.
Oh, what a mistake... I'm still not able to use my machine normally.

So, can anyone point me to a procedure for downgrading Hardy to previous version? I did this on a business laptop (where I used Ubuntu exclusively for the previous 6 months and was convincing my colleagues to do the same) and cannot let myself without computer on Monday.

Or... I can explain my troubles and someone might know what should be done.

Basically, I have these problems:

**1. The system won't shutdown/restart**:
- the X turns off normally and after that right when the actual restart/shutdown should occur, the screen just becomes filled with some thin vertical lines in different colors (after some time the screen turns to white and then to black).
I've edited the /etc/modules and added the
```
apm power_off=1
```
It worked the first time I rebooted the machine, but after that I had to reload the graphics driver at least two times and now it's not working again (/etc/modules still has the line above).

**2. Graphics**:
I'm using an Acer laptop with Nvidia 8400M GS (256MB) graphics card. On Gutsy, I was using "NVIDIA-Linux-x86-169.12" driver and had no problems with it.
After the upgrade to Hardy, I couldn't have resolution higher than 640x480 (not even 800x600, lol), and the native resolution for my monitor is 1440x900. After hours of trials and errors, I was able to download newer, beta, version of Nvidia drivers (long live Lynx!): "NVIDIA-Linux-x86-173.08". Now I'm able to set the correct screen resolution, but that's about it...
The system was very very slow... even changing the focus between two opened windows was taking 5 or more seconds. Very frustrating, believe me... I was able to speed it up a bit last night after installing the "xserver-xgl" with synaptic, but still Gutsy was much faster in using.

**3. Compiz-fusion**:
I know this is not crucial for a business laptop, but I've been using compiz for the past 6 months and it was the main reason my bosses allowed me to use non-windows OS (lol :)). Anyway, I also got used to it and now it's like I'm using "naked" machine... Something's missing all the time (apart from the speed ;)).
My problem with Compiz is, when it starts without whitening the whole screen, I don't have windows borders. After hours and hours of doing everything I could read of on the internet (gconf edit "patch", completely removing compiz, emerald and everything with it and then reinstalling either through synaptic or by compiling the latest git version) I found out that the main problem is that window decorators won't run. 
When I do the
```
compiz --replace
emerald --replace
```

and after that I do the
```
ps ax | egrep -i '(compiz|decorator|emerald)'
```
I cannot find emerald anywhere... And whatever I do, it remains unstarted.
Sometimes, when I try to start compiz through shell I get the:
```
compiz (core) - Warn: Unable to parse XML metadata from file "core.xml"
```
which remains mysterious and unsolved until now (in the meantime I've installed all the "python & xml" packages I could find, recompiled compiz, but no luck).

So, that's it.

Can somebody **please** help me either with turning back to Gutsy (I have previous kernel in my grub list, but at this point I'm afraid my computer is going to explode if I try it, so please advise) or with what should I do to solve the problems above. It is crucial to me to have any version fully operational by tomorrow night (I cannot do a clean install). Thanks a lot guys! :)

---

### Post by Tatty on 2008-04-26
Downgrading is not really supported as it is likely to break your system.  However there is a page on the wiki giving suggestions on how to do it - **use at your own risk**! [https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)

The best option however is simply to do a clean install, it will leave you with a much neater system.

---

### Post by mpetrovic on 2008-04-26
Saw that, but wouldn't like to be the first one to try :)

Can I do a partially clean install? I mean, to install with a CD/DVD, but to have all my data unchaged (evolution emails, etc...)? 

Thanks...

---

### Post by H4rm0ny on 2008-04-26
> **mpetrovic said:**
> Saw that, but wouldn't like to be the first one to try :)

Can I do a partially clean install? I mean, to install with a CD/DVD, but to have all my data unchaged (evolution emails, etc...)? 

Thanks...

If you've put your /home directory on a separate partition, which is always good practice, then you can just be careful not to format that partition when you do the reinstall. It's one of the options under custom partitioning during the install. Just assign the same partition as /home this time around and everything should be fine. Of course, it's important to back up your data first!

If you haven't put /home on a separate partition (and how would you have known?), then it's not the end of the world. If you have an external hard disk or some such, copy off the entire contents of the /home directory (or relevant parts of it) and copy it back on again afterwards. You might potentially need to reset some file permissions, but you should find that most of the programs just pick up where they left off. All they do is just read those directories in your home folder when they start up. They wont know that they went anywhere while they weren't running. Just be certain to copy all the hidden directories and files as well as the visible ones (there'll be an option in whatever you're using as your file manager).

---

