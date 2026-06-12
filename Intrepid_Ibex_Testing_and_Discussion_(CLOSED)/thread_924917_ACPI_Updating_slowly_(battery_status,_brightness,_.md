---
title: "ACPI? Updating slowly (battery status, brightness, power)"
date: 2008-09-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by chorca on 2008-09-20
I have a Dell Latitude D510 that I loaded up the latest alpha (6) of Intrepid on, and got the latest updates..

I'm having a bit of an issue, the problem is that the battery status, along with brightness OSD and power plug in and out are coming up very slowy at times.

What happens is this: Upon starting the computer, and moving the mouse over the battery applet in the panel, it shows no tooltips. Double-clicking on the battery applet does nothing. It will act this way for upwards of 30 seconds, after which time suddenly the battery properties will open. This also can happen with brightness. If the battery status is locked up as previousy described, and the brightness is changed, the hardware will changen the brightness level, however, there will be a box, either visible or not, where the OSD should be for the brightness indicator on the screen. This does not get updated until the approx. 30 secs have passed and the battery levels have update.

This seems to be some sort of ACPI? problem? I'm not sure what controls the buttons here, but it seems that it's locking up while trying to poll the battery status at certain times. I'm wondering if anyone else is experiencing this issue.

---

### Post by chorca on 2008-09-24
Been doin' updates, still having this issue. Does anyone know that Ubuntu uses ACPI to read in the battery status, brightness, and whatnot? I'm wondering under what package to file this bug.

---

### Post by nanog on 2008-09-25
I was having this problem intermittently but the new 2.6.27-4 version seems to have fixed it.

---

### Post by Nullack on 2008-09-25
Try synching to main if your using a mirror

---

### Post by chorca on 2008-09-25
I spent some more time researching the problem, and found that ACPI/HAL seem to be working properly, it's GPM that's having issues. Upon AC power state change (plugged/unplugged) GPM locks for anywhere from 40 seconds to a minute and a half. I filed a bug report on the issue, as the brightness control is also affected. Better description and screenshot are available on the launchpad bug page.
[https://bugs.launchpad.net/bugs/274197](https://bugs.launchpad.net/bugs/274197)

Software repos are on default settings, not using mirrors. Just updated about 10 minutes ago, still having the issue.

---

### Post by sroland81 on 2008-09-27
Hello, i updated to ubuntu intrepid amd64, think it is alpha 6... the latest to the date, on my compaq presario F700. I hardy i was able to fix many things and other many worked fine by default. I fonud this issues.

1) Battery status on the system tray shows a discharging battery... even the percentage of remainig battery decreases and the icon is only the battery, this is with the laptop plugged on AC power... in fact when positioning the mouse over it says "Laptop is running on AC power. Laptop Battery dischargingm XX% remaining... bla bla"... this is a contradiction.... i also removed the battery with the laptop running and the icon of discharging battery remained unchanged and the percetage also decreased. This is quite disturbing because you loose vital info if you are running on battery. I checked that the cable was allright and after a restarting of laptop... the power manager icon appears to be allright... but some times not.

2) The LCD brightness applet shows the red circle indicating that cannot reach the brightness control... but if click on it... the brightness dial appears and i change brightness normally... but the icon says it cannot do it.

3) In the shutdown dialog, Suspend icon is missing in the Tango Blue materia icon theme.

4) Some of hot keys are doing strange things... the sleep (Fn+crescent moon) restarts the machine.

5) skype installed by forcing architecture to i386 is no longer working too, but i can live with it.

6) One thing i fixed in hardy was the clicking noise of my hard drive associated with the disableing of Load Cycles. I did this installing tha laptop-tools package, and running "sudo laptop_mode start" in my rc.local script and editing the laptop.conf file to start the laptop mode on AC or battery power.... but i think this is no longer working because i hear the clicks again... but i need to study this more deeply.

Best regards,

---

### Post by mc4100 on 2008-09-27
I'm seeing the exact same issues.
Also, I had a pretty weird bug (I'll post a screenshot) with battery life, that, fortunately, was fixed simply by reinstalling Gnome Power Manager:

Edit:  sroland81, I also have the HD issue, which if it is what I think it is, was meant to be fixed ages ago; when it annoys me:
```
sudo hdparm -B 255 /dev/sda
```
This isn't a permanent fix.

---

### Post by zoomy942 on 2008-09-28
i posted something similiar here

[http://ubuntuforums.org/showthread.php?t=931431]("http://ubuntuforums.org/showthread.php?t=931431")

---

### Post by jfernyhough on 2008-09-29
I'm getting the same thing for my gnome-power-manager icon - it doesn't update correctly.

I think it started with an update to gnome-power-manager. There are a few bug reports that look similar, though nothing yet has mentioned the symptoms I'm experiencing.

---

### Post by chorca on 2008-09-29
Well the main problem that *I'm* having is that the icon locks up. Mousing over the icon after unplugging/replugging the AC power does not give a tooltip, double-clicking the icon does nothing, and if I change screen brightness while the icon is locked up, the screen brightness OSD does not come up. After approximately a minute, the icon unfreezes itself, the window shows up and the OSD for the brightness comes up, displaying the info from the previous brightness change.

There's something causing GPM to hang while it's trying to react to the AC plug/unplug.

---

