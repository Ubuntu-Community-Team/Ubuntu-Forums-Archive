---
title: "shutdown issue"
date: 2010-01-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by woodnymph on 2010-01-07
shut down problem .. goes through what appears normal shutdown process, but then leaves me a a dark screen with only a cursor.  i can type here, but doesn't seem to have any command function.  
ctrl-alt-del finishes the shutdown after flashing briefly 
"init: alsa-mixer-save main process (xxxx) terminated with status 1"  
the 19xx has been variously 1911, 1921, 1926 ..  3229 ..
any ideas what this is or how to fix?  i am not a sound user really, normal setup. thx

---

### Post by VMC on 2010-01-07
> **woodnymph said:**
> shut down problem .. goes through what appears normal shutdown process, but then leaves me a a dark screen with only a cursor.  i can type here, but doesn't seem to have any command function.  
ctrl-alt-del finishes the shutdown after flashing briefly 
"init: alsa-mixer-save main process (19xx) terminated with status 1"  
the 19xx has been variously 1911, 1921, 1926 ..  
any ideas what this is or how to fix?  i am not a sound user really, normal setup. thx

alsa is for your sound functionality. Were you listening to music shutdown?

How long do you wait before ctrl-alt-del?

Did this just happen or has it been happening from day one?

You could try removing 'quiet' and 'splash' from the end the the linux line in your grub boot to see if thre is anything of errors on bootup and shutdown.

Also check out /var/log files or use System>Admin>Log File Viewer to check.

---

### Post by Vanishing on 2010-01-07
my thinkpad t500 have similar issue with shutdown and restart.

but instead of dark screen with cursor, mine just hangs with dark screen, cannot input, but alt+prtSc+ REISUB works.

running 
> sudo shutdown -h now
and 
> sudo rebootwill hang too,
but running the shutdown and restart scripts in /etc/rc*.d manually will work.

---

### Post by dino99 on 2010-01-08
i have these issues too for a long time now ( probably since i use grub2). I need to unplug most of the time: when i shutdown, ubuntu is closed but hardware does not stop ( no console available)

Don't found bug report about that and don't know what to report. (thinking of some services still running)

---

### Post by ranch hand on 2010-01-08
This is not a grub2 problem.

---

### Post by woodnymph on 2010-01-08
> **VMC said:**
> alsa is for your sound functionality. Were you listening to music shutdown?

How long do you wait before ctrl-alt-del?

Did this just happen or has it been happening from day one?

You could try removing 'quiet' and 'splash' from the end the the linux line in your grub boot to see if thre is anything of errors on bootup and shutdown.

Also check out /var/log files or use System>Admin>Log File Viewer to check.

the first couple times, i gave it about 10 minutes .. when i was convinced it was not doing anything i just quit.  i was not listening to music or anything, rarely use sound apps.  just started yesterday after a daily update .. 

daily update:  today the issue is a display one .. another update and last night at shutdawn, waiting to see if the alsa thing was still there, the monitor froze and very slowly went to all lines and eventually black.  again i waited about ten minutes, then just turned it off.  hmm ... 

anything particular i should look for in errors ??  ideas ??  running lucid alpha, maybe it'll all clear up with time ..

---

### Post by VMC on 2010-01-08
> **woodnymph said:**
> the first couple times, i gave it about 10 minutes .. when i was convinced it was not doing anything i just quit.  i was not listening to music or anything, rarely use sound apps.  just started yesterday after a daily update .. 

daily update:  today the issue is a display one .. another update and last night at shutdawn, waiting to see if the alsa thing was still there, the monitor froze and very slowly went to all lines and eventually black.  again i waited about ten minutes, then just turned it off.  hmm ... 

anything particular i should look for in errors ??  ideas ??  running lucid alpha, maybe it'll all clear up with time ..

Your home folder has two files ".xsession-errors.old" and ".xsession-errors". Anything there of interest.

Maybe type dmesg from a terminal and look through that.

---

### Post by woodnymph on 2010-01-09
seems now like maybe more of a video/ vga thing .. 

ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) 

kernel driver bad match .. today i could only boot into low graphics mode, after yesterday's update .. would be nice if i could go back two days and just leave it there ..

---

### Post by garvinrick4 on 2010-01-10
Did you upgrade a WUBI install?

Any which way you can get a quick shutdown by going to config editor  to APPS to indicator-session and check the value box and will shutdown without timer just like sudo shutdown -h now and restart will be just like sudo shutdown -r now

Just saves opening a Terminal. Always hated timer of 60 seconds in GUI extra enter was pain.

Do not know if that will shut you down without fault but only time I had your problem was with a WUBI install.

Any which way gets rid of timer in GUI shutdown and restart

---

### Post by myoungf1 on 2010-02-17
I am having the same problem.  When I either do the gui restart or manual terminal restart Kubuntu starts to shutdown kdm, I hear the shutdown music, then I get a system beep the screen goes black and then my computer freezes.  The only way I can restart the computer is by hitting ctrl+alt+delete and then the reboot continues as normal.  The only thing I have changed hardware wise is install a new bfg geforce 9800 gt graphics card.  I can confirm that this is not a problem in Windows Vista.  Any help would be great.

---

