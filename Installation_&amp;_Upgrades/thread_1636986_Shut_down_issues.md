---
title: "Shut down issues?"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by tehchibipanda on 2010-12-03
I've searched on this one for a few weeks now, and I have come up missing a solution. Whenever I hit shutdown on my computer, it turns off, only to boot back up. Also, when hibernating, trying to come out of hibernation I get an error stating something to the effect of the device is not ready. Has anyone found a solution do the first problem, and maybe even the second one?

Edit: Figured out the device not ready bit, but still can't shut down the computer. :(

---

### Post by tehchibipanda on 2010-12-04
Not to sound annoying, just bumping up the thread. :)

---

### Post by ToFue on 2010-12-04
open System>Preferences>Power Managment

go through the tabs; on the third tab there's a box for "when power button is pressed" behaviour options.. look for anything that would suggest a restart.

Also, make sure that the BIOS isn't overiding ACPI policies that Linux would take care of (which is like everything) by turning off any kind of BIOS power management options..

if that doesn't do it, you'll want to snoop around in /etc/acpi to see if that can give you a clue - compare the contents of scripts, investigate installed kernel modules.. 

that's about as pointed as I can offer, hope it helps ya!

---

### Post by matt_symes on 2010-12-04
Hi

Open a terminal and type

sudo shutdown now

Enter your password. You will not see anything on the screen as you type it.

Does that shut it down?

Kind regards

---

### Post by tehchibipanda on 2010-12-04
Matt, I've tried that, along with sudo halt, and a lot of other commands trying to shut it off. It always seems to restart after a moment and turn back on. Not that it's a TOTAL problem, just slightly irritating...ToFue, I did check the bios settings as my computer was starting up, but I didn't see anything about power options. Less I was looking in the wrong spot, which is a possibility. I just got my computer back not long ago, so I'm a little bit rusty with things :P

---

### Post by wilee-nilee on 2010-12-04
> **tehchibipanda said:**
> Matt, I've tried that, along with sudo halt, and a lot of other commands trying to shut it off. It always seems to restart after a moment and turn back on. Not that it's a TOTAL problem, just slightly irritating...ToFue, I did check the bios settings as my computer was starting up, but I didn't see anything about power options. Less I was looking in the wrong spot, which is a possibility. I just got my computer back not long ago, so I'm a little bit rusty with things :P

Are you powering off with the power on button or the icon in the panel?

---

### Post by tehchibipanda on 2010-12-04
Well I tried the button first, and I figured it was set to restart. I then tried to use the panel, and the same thing. It just restarted.

---

### Post by matt_symes on 2010-12-04
Hi

You don't have wake on LAN set in the BIOS do you?

Kind regards

---

### Post by wilee-nilee on 2010-12-04
So lets try this I remove the stock icons from the panel myself for shutdown. If you right click on the panel then add to panel you can add this icon in the screenshot. It is called shutdown try that.
[ATTACH]177411[/ATTACH]

Could be other issues as others suggest remedies.

---

### Post by tehchibipanda on 2010-12-04
Matt: I do not. I just checked, it said disabled.

Wilee: I tried that, no such luck though.

---

### Post by matt_symes on 2010-12-04
Hi

What happens if you press and hold alt and sysrq, and with those two buttons pressed, hit 

r e i s u o

one after another

You should try using both alt keys (not at the same time) as only the right one works on my laptop.

Does that shut it down?

Kind regards

---

### Post by tehchibipanda on 2010-12-04
I got excited, it stayed off for two seconds! But alas, it turned back on.

---

### Post by tehchibipanda on 2010-12-05
Oh well, I give up. At least it's just a minor nuisance rather than something serious :D Just wondering, though, has anyone else had this problem? I know I've read similar reports, but never found a fix.

---

### Post by ToFue on 2011-01-04
> **tehchibipanda said:**
> I've searched on this one for a few weeks now, and I have come up missing a solution. Whenever I hit shutdown on my computer, it turns off, only to boot back up. Also, when hibernating, trying to come out of hibernation I get an error stating something to the effect of the device is not ready. Has anyone found a solution do the first problem, and maybe even the second one?

Edit: Figured out the device not ready bit, but still can't shut down the computer. :(

Just a shot in the dark:  Have you checked that the case's power switch cable isn't connected to 'reset' header pins instead of 'power' on the motherboard?

---

