---
title: "Installation does not start"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by siku on 2006-10-10
Hello,
I'm having a problem with installing ubuntu. I had installed ubuntu previously on other systems and it used to work great. This time I'm having a problem.
I downloaded the beta Edgy Eft, Desktop cd and used that as install media. The problem I think may be the hardware.  I have a Radeon x300 PCIExpress card. 
But when I'm installing ubuntu the only screen that greets me is the first splash screen (with install, check cd, F1, F2, F3, etc. options).  So I click install option and then it appears that something is happenning. I get the next splash screen as well, with the progress bar.  Then after that it tells me that there was a problem with X-server and because of that installation could not proceed. 
I did sudo dpkg-reconfigure xserver-xorg and went through all that process, selecting "ati" as my video card driver. But still nothing. I read that using "vesa" may solve the problem , but didn't. 
I then tried "sudo X-configure" and it tells me that my mouse has a problem.  I'm using a logintech usb optical mouse.
The thing that is getting on my nerves is that, most of the forums that I've been to tell of X problems after installing Linux. This time however I have not evern started to install anything. If I had installed everything else and only X was not working then I could download ati's drivers and install them. But everytime I have to launch the live cd. 
So if anyone knows why the install process will not start and could help me out, (with video card or mouse or both).  Or tell me of an alternative way to install would be great.

I found a linnk on installing ubuntu from windows, maybe looking into that. 

thanks all

---

### Post by mssever on 2006-10-10
If there's an Edgy alternate install CD, you can probably use that (I don't use edgy yet). Alternately, install Dapper (possibly using the Dapper alternate install CD), then upgrade to Edgy.

To upgrade to Edgy, open up /etc/sources.list and change every occurance of dapper to edgy. Make sure that you have ubuntu-desktop installed (or kubuntu-desktop, xubuntu-desktop, etc.). Then,
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

