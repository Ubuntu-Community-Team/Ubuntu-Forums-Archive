---
title: "Desperate for help getting ANY NVIDIA drivers to work"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by darkprime on 2011-05-13
I'm new to Ubuntu (I'm an openSuse guy), but a workstation I need to use at school needs to run with Ubuntu (it's what my advisor chose).  

We had version 10.04 installed, but couldn't get any version of the NVIDIA drivers to work.  Our Xorg.0.log file would show that they are loaded, but running any openGL applications would or tools (such as glxinfo, glxgears, etc.) would how that direct rendering was not enabled and NV-GLX was not loaded, even though our logs said otherwise.  GLXINFO will show that the CLIENT side is running nvidia glx, but the server side is always running SGI.  

Anyways, I couldn't find any solutions that worked, so I upgraded to 10.10, but nothing improved.  Yesterday I upgraded to 11.04, but still nothing has improved.  I've purged and reinstalled drivers over and over.  I've rebooted over and over.  I've installed nvidia-current, a bunch of nvidia versions from ubuntu, and built them from the NVIDIA installer from nvidia directly.  

I have wiped out my xorg.conf file many times and let nvidia set it up, but that doesn't seem to help.  When I run gnome-session and go into system tools -> administration -> additional drivers, it shows that the nvidia driver is active but not in use.  

The only thing that I still wonder about is if modules from xserver or mesa are getting loaded that shouldn't.  For example, I have the following lines in my log file:

[    11.549] (II) "dri" will be loaded by default.              
[    11.549] (II) "dri2" will be loaded by default.  

If I disable them in xorg.conf, the message will change to say they were disabled but they are getting reenabled anyways.  

Thoughts/comments/suggestions?

I need help badly.  We have NEVER gotten nvidia's drivers to be working right on this machine.  The card in question an a 480 GTX.

---

### Post by quixote on 2011-05-14
It's been a while since I fought with nvidia drivers, so even this suggestion is probably no use (but will at least bump your question back up :D).  Have you already tried the open source driver? (xserver-xorg-video-nouveau in synaptic)  I used it under Lucid and it worked much better for me than nvidia's own drivers.

---

### Post by darkprime on 2011-05-14
No I have not tried that one.  I haven't tried it because I need to use some applications that are using the GPU for both computations (CUDA) and OpenGL, and the calls in the codes require NV-GLX apparently.  I don't think I will get that with the open source drivers.  Regardless, it's worth a shot to make sure.

---

### Post by SeijiSensei on 2011-05-14
Have you tried installing by running the Additional Drivers application and letting it find and install the drivers for you?

How about "sudo nvidia-xconfig"?  Sounds like you tried that already.

Try opening a terminal after start up and run "lsmod | grep nvidia".  Is the "nvidia" driver loaded?  It's pretty large; on my machine it's about 10MB in size.

Next take a look in /etc/modprobe.d/ and see if any drivers are blacklisted.  It's possible that the nvidia driver has been accidentally blacklisted, so your efforts to install it are being thwarted.  If you don't see the driver using lsmod, a blacklisted driver may be the answer.

I have a 9500 GT, which is pretty similar to your adapter.  My driver is currently 270.41.06-0ubuntu1, according to "dpkg -s nvidia-current".

---

