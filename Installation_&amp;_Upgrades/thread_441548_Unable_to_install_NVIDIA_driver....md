---
title: "Unable to install NVIDIA driver..."
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by synquest on 2007-05-12
I am stumped. NVIDIA says to type "sh NVIDIA-Linux-x86-1.0-9755-pkg1.run". This only tells me I have to be root. OK. So I type in a command window "sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run", and am told that I have an xterm running and must shut it down. 

Now for the stupid questions...
NVIDIA says type.... I ask where? Apparently not in a command window? How do I shut down xterm? 

I believe that all else is as it should be.

Operating system is Ubuntu Feisty Fawn....
Video card is GeForce 6800...

Your clear, consise answer for this Linux dummy would be appreciated. I have spent several hours on this and am unable to find an answer...

[http://smokethiscigar.com](http://smokethiscigar.com)

---

### Post by taurus on 2007-05-12
You must shutdown X first before you can install nVidia by hand.

<Ctrl><Alt>F2 and log in with your name and password.  Then at the prompt, do

```
sudo /etc/init.d/gdm stop
chmod 755 NVIDIA-Linux-x86-1.0-9755-pkg1.run
sudo ./NVIDIA-Linux-x86-1.0-9755-pkg1.run
```

Otherwise, use envy to install nVidia on your machine, without shutdown X first.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by synquest on 2007-05-12
Thanks for the quick reply! I used Envy... worked like a charm!

---

