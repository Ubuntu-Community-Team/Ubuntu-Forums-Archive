---
title: "madwifi or ath5k"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by maestrobwh1 on 2008-10-23
AR5001X+ chipset - said to work with ath5k but until now, although I could see my ath0 interface along with whatever virtual thing it created (master), I could not connect most of the time, and the times I could, I was good for a few minutes before it pooped out.  I went with madwifi-hal compiled from source and it works, although if I **suspend/hibernate, for some reason ath0 is brought up without its counterpart wifi0 and networkmanager won't connect. **Usually if I issue ifconfig wifi0 up and then use networkmanager and it then connects.  Is there I script that runs on resume where I can put this command? /etc/acpi/resume.d?  I read in a few posts in launchpad that since hardy, this is a deprecated location and nothing is run from there.

Since the kernel just updated again today, if I want to try the ath5k, 

1) can I use rmmod ath_pci and them modprobe ath5k to see if it works now, or
2) should I blacklist ath_pci and then add ath5k to /etc/moodule and reboot or
3) do I need to uninstall the madwifi driver completely

---

### Post by inportb on 2008-10-23
ath5k should be automatically loaded if you haven't changed anything. and it does not create athX devices.

---

### Post by maestrobwh1 on 2008-10-23
> **inportb said:**
> ath5k should be automatically loaded if you haven't changed anything. and it does not create athX devices.

**So, um now your post has me totally confused and you really didn't help me solve my issue/question with this and left me with more. :confused: **If I rmmod ath_pci, then modprobe ath5k, I get the following:

lo
eth0
ath0
**master0**

running under madwifi (ath_pci enabled)
I get the following

lo
eth0
ath0
**wifi0**

So what would my device look like running ath5k?  wlan0?

---

