---
title: "What in hell am I supposed to do with this script?"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by Lism on 2011-03-27
What the hell do I do with this?

[http://uk.download.nvidia.com/XFree86/Linux-x86_64/270.26/NVIDIA-Linux-x86_64-270.26.run](http://uk.download.nvidia.com/XFree86/Linux-x86_64/270.26/NVIDIA-Linux-x86_64-270.26.run)

---

### Post by uRock on 2011-03-27
Please copy and paste your script in the browser using code tags.

Thank you,
uRock

---

### Post by mikewhatever on 2011-03-27
You run it, like so:
```
sudo ./NVIDIA-Linux-x86_64-270.26.run
```

...oh, by the way, that isn't a script.

---

### Post by Lism on 2011-03-28
> **mikewhatever said:**
> You run it, like so:
```
sudo ./NVIDIA-Linux-x86_64-270.26.run
```...oh, by the way, that isn't a script.

Oh right, I don't even know why i said it. 

I did that but when the install thing displays, all I get is:

ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

:confused:

---

### Post by Sean Moran on 2011-03-28
> **Lism said:**
> Oh right, I don't even know why i said it. 

I did that but when the install thing displays, all I get is:

ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com]("http://www.nvidia.com").

:confused:

I guess the README at the link above should fix it, and nVidia drivers that I use (185) usually need me to open a terminal (within the GUI) and run 'sudo nvidia-xconfig' and then reboot, and up she comes in 1366x768 on the next session.

---

### Post by realzippy on 2011-03-28
> **Lism said:**
> What the hell do I do with this?

[http://uk.download.nvidia.com/XFree86/Linux-x86_64/270.26/NVIDIA-Linux-x86_64-270.26.run](http://uk.download.nvidia.com/XFree86/Linux-x86_64/270.26/NVIDIA-Linux-x86_64-270.26.run)

..yep,there should be a reason to install a nvidia-driver manually.
Which is yours?

..you should prefer the driver in System-Administration-Hardware Drivers.

---

### Post by Lism on 2011-03-28
> **Sean Moran said:**
> I guess the README at the link above should fix it, and nVidia drivers that I use (185) usually need me to open a terminal (within the GUI) and run 'sudo nvidia-xconfig' and then reboot, and up she comes in 1366x768 on the next session.

No, I looked at the README before posting, theres nothing in there about how to fix whats wrong with it. My GPU is relatively new and the linux drivers are in beta so i think i'll wait for the release version.

---

### Post by realzippy on 2011-03-28
[readme]("http://de.download.nvidia.com/XFree86/Linux-x86/270.26/README/installdriver.html")

all you need,chapter 4,installing...

---

