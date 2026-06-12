---
title: "nvidia restricted driver wont load after 10.04 upgrade"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by Phezz on 2010-05-28
The 10.04 upgrade caused a number of problems.  
This is the only remaining one.  
Every boot
- X pops up and tells me my video is all broken. 

 It offers me several options - the only ones that work are: 
- Low graphics mode 
- console  

After trying all permutations of the obvious things like:  
removing every synaptic package with nvidia in the name.  
Or: 
 reinstalling the ones that appear most likely to work, in a number of different combinations...

I ended up installing the correct kernel headers and compiling the NVIDIA...run driver manually. 
 This reported success and it seemed all good until the reboot brought me another screen of fail. 

The error message being slightly different I found the following sanity check: 
```
sudo modprobe nvidia 
``` which failed with: 
```
FATAL: Error inserting nvidia (/lib/modules/2.6.32-222-generic/kernel/drivers/video/nvidia.ko): No such device
```(I don't know what it means by device - but there's a 13M file there)  

Clearly I've spent far too long removing my brain through a console window. 

Any ideas?

---

