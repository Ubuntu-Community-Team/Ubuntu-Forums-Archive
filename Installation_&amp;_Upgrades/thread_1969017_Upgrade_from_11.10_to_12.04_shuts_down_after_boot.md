---
title: "Upgrade from 11.10 to 12.04 shuts down after boot"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by HectorG on 2012-04-29
So I upgraded last night and after the reboot, I tried logging in. A couple of seconds later computer shuts down. Tried rebooting various times to no avail. I am able to get in to recovery mode. I don't find anything useful in the logs. Any ideas? I have checked messages error dmsg log files but nothing...

I do get to log screen but even if I don't type anything It shuts down. I tried hitting alt F1 


Only weird thing is a message that says "acpid: exiting"

---

### Post by jadtech on 2012-04-29
> **HectorG said:**
> So I upgraded last night and after the reboot, I tried logging in. A couple of seconds later computer shuts down. Tried rebooting various times to no avail. I am able to get in to recovery mode. I don't find anything useful in the logs. Any ideas? I have checked messages error dmsg log files but nothing...

I do get to log screen but even if I don't type anything It shuts down. I tried hitting alt F1 


Only weird thing is a message that says "acpid: exiting"

the computer just shuts down ?? or  loads and reboots ?? 

is this a dual boot if so can you boot windows and run normally  , did 11.10 run well no issues ..

---

### Post by whiskers751 on 2012-04-29
Aha! I see your problem.
What I think you have is your computer thinking that you have pressed the OFF button.
Hold Shift at startup
Choose a kernel with a lower release number
You might need to look in Previous Linux Versions
Ta-dah
Or
Hold Shift etc
On your Ubuntu selection, press e
Go to the big long line containing stuff like vt.handoff=7
Add on the end: acpi=off
Ta-dah

Note neither of these are permanent!!

---

### Post by HectorG on 2012-04-29
My issue seems to have been with upsd sending a TERM signal. I have since uninstalled it with

sudo apt-get purge upsd 


That stopped the shutdowns. Now my X11 broke as well but that's a separate issue. Thanks for the help!

---

### Post by captinkid on 2012-05-03
I have a similar problem on a Gateway Viper TA7. It boots to the desktop in 12.04, and I have about three seconds to interact with unity before something issues the shutdown command and it shuts off.

With acpi=off it does not shutdown. (Strike that, it just crashed.)

:confused:

---

### Post by HectorG on 2012-05-04
The way I fixed it was by going into recovery mode when booting. You will need to hit the shift key and keep it pressed when computer gets past post bios check. You will get into grub and then click on recovery. Now enable networking which will give you read / write access. Then go to root shell and type "sudo apt-get purge upsd". That should do it if upsd is causing your issue. Reboot and cross your fingers.

---

