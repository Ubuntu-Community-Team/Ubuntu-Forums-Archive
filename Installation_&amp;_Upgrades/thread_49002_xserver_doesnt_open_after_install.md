---
title: "xserver doesnt open after install"
date: 2005-07-14
forum: Installation &amp; Upgrades
---

### Post by mastersam on 2005-07-14
hello ,, i have just completed the install for ubuntu 5.0 hoary ( amd64 ) .. and when booted up xserver wont open ... it says 
" i cant start xserver . it problably isnt set up right ..." and in the log it says " xserver error . no screens found "

HELP ME

here are my specs ...
amd 64 3200+ 
dfi lanparty ut-d 
1024gb geil ultra
saphire x800pro 256mb ...

---

### Post by badrinarayan on 2005-07-14
Can you do [FONT=Courier New]killall -9 -m gdm[/FONT] from a tty and then post the last error when you type [FONT=Courier New]startx[/FONT]?

Regards
Badri

---

### Post by mastersam on 2005-07-14
when i enter #killall -9 -m gdm ...   it spits out  "#gdm(21848):Operation not permitted gdm: no process killed "

when i enter #startx  the last error there is is "#(EE) No devises detected . Fatal error: no screens found . XIO: fatal IO error 104 ( connection reset by peer) on X server ":0.0" after 0 requests with 0 events remaining...

thanks for the quick reply .. but please keep them coming ...

---

### Post by badrinarayan on 2005-07-14
Ok, I must have prefixed sudo
Make it **sudo killall -9 -m gdm**
Then **startx**

Anyway, no screens found indicates that Ubuntu has not configured the xserver well. Could you post the contents of [FONT=Courier New]/etc/X11/xorg.conf[/FONT]

and also those lines marked with **(EE)** in [FONT=Courier New]/var/log/Xorg.0.log[/FONT]

Regards
Badri

---

### Post by RJARRRPCGP on 2005-07-14
Type **sudo killall -9 -m gdm**

---

### Post by mastersam on 2005-07-14
sudo killall -9 -m gdm wants a password ... i havnt configurd the root password yet and it wasnt part of the install .... and also how do i veiw the contents of a .conf file when in comandline ?

---

### Post by varunus on 2005-07-14
EDIT:  The password that sudo wants is your password, not the root password.

Your screens problem is probably due to your ATI video card.  Try the following:

Once your x server fails to start and it drops you to a console, do the following:

```
sudo /etc/init.d/gdm stop
``` 

Then type:

sudo nano /etc/X11/xorg.conf

Scroll down to the driver section and change the Driver line from

Driver   "ati" #might be radeon or something else here

to

Driver   "vesa"

Then try typing 

sudo /etc/init.d/gdm start

Does this let you get into a GUI?  If it does, install the proprietary ATI drivers, and everything should be good.  There's a howto in the "tips and tricks" section.

---

### Post by mastersam on 2005-07-14
i dont have a "driver" section ... I have a "screen" section with 

# Device  "ATI TECH. INC. Radeon X800Pro ( R423 UI )"

as well as a "Device" Section with 

# Identifier "ATI TECH. INC. Radeon X800Pro ( R423 UI )"

---

### Post by badrinarayan on 2005-07-14
He meant Device Section. Must be a typo. 

Regards
Badri

---

### Post by mastersam on 2005-07-14
OK i did that and i got a black screen when i started gdm ... i restarted and still got a black screen .. so now i cant even work in commandline

... keep the post coming tho

---

### Post by badrinarayan on 2005-07-14
Well, you can still use command-line by pressing Ctrl+Alt+F1
Also, could you paste lines with (EE) in /var/log/Xorg.0.log for debugging. Also, startx again to see whether the error is different this time...

Regards
Badri

---

### Post by mastersam on 2005-07-14
control alt f1 isnt working

---

### Post by badrinarayan on 2005-07-14
How about Ctrl+Alt+Backspace a few times?

---

### Post by mastersam on 2005-07-14
nope. ... h/o im going to change the "vesa" back to "ati"

---

### Post by mastersam on 2005-07-14
ok i changed the driver back to "ati"

the lines with (EE) just say " No Devices Detected "

---

### Post by badrinarayan on 2005-07-15
[QUOTE=mastersam]ok i changed the driver back to "ati"

the lines with (EE) just say " No Devices Detected "[/QUOTE]

That's unhelpful. Are there no more debug messages? Even when you type startx?

Anyway, you can try running xorgconfig and see if it fixes it.

Regards
Badri

**Edit: Do you have xorg-driver-fglrx package installed?**

---

### Post by badrinarayan on 2005-07-15
[http://ubuntuforums.org/showthread.php?t=24557&page=1](http://ubuntuforums.org/showthread.php?t=24557&page=1)
Why didn't I see that thread before?

Badri

---

