---
title: "Install drops to terminal"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by inkadu on 2008-11-07
I'm installing the latest Xubuntu (8.10) onto an old P3 Hewlett Packard laptop from CD. The only internet access I have is through a wireless card. 

The install requests that I download a driver and then drops into terminal. I'm assuming it's running in ram. 

I have downloaded the driver onto flash and can access it. Now the question is:

1) How do I restart the install process?
2) Where do I put this driver so the process will find it? 

Again, please note that I have no internet access.

Thanks in advance! 

(incidentally, I am missing ucode5.fw, thanks to crazyguy123 for finding it outside of a tarball ([http://ubuntuforums.org/showthread.php?t=759100](http://ubuntuforums.org/showthread.php?t=759100)).

---

### Post by Peter09 on 2008-11-07
Are you installing from the LiveCD and are you in the LiveCD system

What is the name of the driver? Is it in synaptic?

---

### Post by inkadu on 2008-11-07
> **Peter09 said:**
> Are you installing from the LiveCD and are you in the LiveCD system

What is the name of the driver? Is it in synaptic?

Installing from LiveCD, but not in LiveCD. The name of the driver is ucode5.fw from the b43 package available from [http://www.linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://www.linuxwireless.org/en/users/Drivers/b43#devicefirmware) 


I don't know if it's in synaptic. I just started installing from the hard drive, the splash screen comes up (how do I get rid of that to see behind the curtain?) and a few minutes later the driver warnings come up, it gives me about a minute, then it drops into terminal. 

My interpretation is that Intrepid Ibex is asking me to install something in terminal before proceeding with the installation, so I don't think anything's "wrong" per se. I'm just tryign to understand how the install process might work in this situation. 



Thanks.

---

### Post by Peter09 on 2008-11-07
at the command prompt try typing

```
sudo apt-get install b43-fwcutter
```

you may need to have an Internet connection active.

---

### Post by inkadu on 2008-11-07
> **Peter09 said:**
> at the command prompt try typing

```
sudo apt-get install b43-fwcutter
```

you may need to have an Internet connection active.

And after I do that, what happens? How would I restart the install process without losing what's in the RAM? 

If I can figure out where to put the driver -- which is all it's specifically asking for -- it might save me a lot of steps, too.

---

### Post by Peter09 on 2008-11-07
try doing it at the LiveCD stage, Not sure but that might then include the driver in the install. Other than that I would use the alternate CD (text only install) and install afterwards

---

### Post by inkadu on 2008-11-07
Xubuntu is installed via the alternate CD. Unfortunately, the install program did not pick up the PCMIA WLAN card at all, so I will have to futz with it further, but things should easier starting from an installed system. Thanks!

---

