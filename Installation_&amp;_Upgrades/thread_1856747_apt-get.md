---
title: "apt-get"
date: 2011-10-08
forum: Installation &amp; Upgrades
---

### Post by nahua on 2011-10-08
Hi, I am quite new with linux and when I try to install packages with the apt-get install command, the terminal does nothing at all, just returns to a new line.

if I type: 
apt-get install python-tk
response:
bash: /usr/bin/apt-get: input/output error

if I type:
sudo apt-get install python-tk

I get no response at all and lets me write a new command.

The only thing I can think about is that I am running Ubuntu form a USB stick without installing it into the hard drive. Can this be the issue?

thank you.

---

### Post by dFlyer on 2011-10-08
Try this:

sudo apt-get update

sudo apt-cache search python-tk

sudo apt-get install python-tk

I can't answer the usb question, as i've always use a hd install.

---

### Post by Hakunka-Matata on 2011-10-08
> **nahua said:**
> Hi, I am quite new with linux and when I try to install packages with the apt-get install command, the terminal does nothing at all, just returns to a new line.

if I type: 
apt-get install python-tk
response:
bash: /usr/bin/apt-get: input/output error

if I type:
sudo apt-get install python-tk

I get no response at all and lets me write a new command.

The only thing I can think about is that I am [COLOR=Red]running Ubuntu form a USB stick[/COLOR] without installing it into the hard drive. Can this be the issue?

thank you.

The red bit, you cannot install programs whilst running from a live cd/usb.  Is that what you're doing?  
The changes cannot be saved to the CD.
Nothing you do whilst running in live CD lives beyond the reboot, it all goes away on reboot.

---

### Post by Nutria on 2011-10-09
> **Hakunka-Matata said:**
> The red bit, you cannot install programs whilst running from a live cd/usb. 

Sure you can.  I've done it more than a few times.  The updates get stored to your in-memory file system.

> The changes cannot be saved to the CD.
Nothing you do whilst running in live CD lives beyond the reboot, it all goes away on reboot.

That's a different issue.

---

### Post by Nutria on 2011-10-09
> **nahua said:**
> Hi, I am quite new with linux and when I try to install packages with the apt-get install command, the terminal does nothing at all, just returns to a new line.

if I type: 
apt-get install python-tk
response:
bash: /usr/bin/apt-get: [COLOR="Red"]input/output error[/COLOR]

That smells of h/w corruption.

> if I type:
sudo apt-get install python-tk

I get no response at all and lets me write a new command.

The only thing I can think about is that I am running Ubuntu form a USB stick without installing it into the hard drive. Can this be the issue?

What you did is *supposed* to work.  I'd try a different stick, or -- if possible, a CD/DVD.

---

### Post by nahua on 2011-10-09
Finally I installed it in the hdrive, everything is working fine now. Hope all these possible solutions can help anyone some time!

thanks a lot for the fast replies!

---

### Post by Hakunka-Matata on 2011-10-09
what did you do differently to make it work?

---

