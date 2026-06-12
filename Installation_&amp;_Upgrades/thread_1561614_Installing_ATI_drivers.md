---
title: "Installing ATI drivers"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by sugam on 2010-08-26
I installed Ubuntu yesterday to try it out, but encountered some freezing/locking issues. Seems to be related to the video card. I'm running Ubuntu in low graphics mode, but wanted to install the proper ATI drivers.

I went to the ATI website for my X1950 (sucks, I know). Downloaded them just fine but when I run them nothing happens. I'm used to Windows so I'm probably doing something wrong.

Any help would be great.  =]

---

### Post by sikander3786 on 2010-08-26
You can install the package from menufacturer website but that is not recommended.

Did you see this page? Most certainly it will help if you go through some reading.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by sugam on 2010-08-26
> **sikander3786 said:**
> You can install the package from menufacturer website but that is not recommended.

Did you see this page? Most certainly it will help if you go through some reading.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I did see that page. I'm just a little weary on whether or not I want to attempt to install those.

I've tried a couple different things, but the graphics drivers that Ubuntu installs as default causes my pc to freeze/lockup. Running in low graphics mode / nomodeset alleviates the issues. I know my card is working just fine because I have no problems running it under windows.

So does installing the proprietary drivers seem like the best thing for me to do?

---

### Post by sikander3786 on 2010-08-27
Download .deb package of EnvyNG and install it as mentioned on this page

[http://albertomilone.com/envyfaq.html#A](http://albertomilone.com/envyfaq.html#A)

Then check for unmet dependencies (if any)

```

sudo apt-get install -f

```

It will appear in Application >>> System Tools >>> EnvyNG.

EnvyNG is very easy to use and installing drivers without breaking anything is what it is intended for.

---

### Post by sugam on 2010-08-27
> **sikander3786 said:**
> Download .deb package of EnvyNG and install it as mentioned on this page

[http://albertomilone.com/envyfaq.html#A](http://albertomilone.com/envyfaq.html#A)

Then check for unmet dependencies (if any)

```

sudo apt-get install -f

```

It will appear in Application >>> System Tools >>> EnvyNG.

EnvyNG is very easy to use and installing drivers without breaking anything is what it is intended for.

It appears that EnvyNG is no longer supported as of Ubuntu 10.04. So I can't download from the repositories. On the Envy site it says to use Jockey if using 10.04. Well, the Hardware Drivers don't list any drivers for me. Maybe because I'm in recovery/low graphics mode. Not sure. 

Is there anything I can do to solve these freezing problems? The ATI website drivers don't support version 10.04 either.  :(

---

### Post by rawlins02 on 2010-08-27
I have the ATI Radeon 4670 card on a system running Lucid.  I installed ATI's fglrx driver from Synaptic Package Manager. Significantly improved my 3D acceleration which allowed me to use a flight simulator.  Otherwise, no other noticeable change in system performance.

---

### Post by sugam on 2010-08-27
> **rawlins02 said:**
> I have the ATI Radeon 4670 card on a system running Lucid.  I installed ATI's fglrx driver from Synaptic Package Manager. Significantly improved my 3D acceleration which allowed me to use a flight simulator.  Otherwise, no other noticeable change in system performance.

Yeah, but my ATI X1950 isn't supported.  :(

---

### Post by rawlins02 on 2010-08-27
> 
Yeah, but my ATI X1950 isn't supported.


Err, sorry about that. Perhaps I can learn something from your experiences, as I have a second machine with the (unsupported) ATI Radeon Mobility X1400.

---

### Post by sugam on 2010-08-27
Disabling KMS fixed my problems. I did the following:

```
gksu gedit /etc/modprobe.d/radeon-kms.conf
```
Copy the following and save
```
options radeon modeset=0
```

---

### Post by avengerxp on 2010-10-06
what did you mean by "it worked by disabling KMS" is that i could use my ati x 1950 pro card in ubuntu 10.04 with drivers??

---

