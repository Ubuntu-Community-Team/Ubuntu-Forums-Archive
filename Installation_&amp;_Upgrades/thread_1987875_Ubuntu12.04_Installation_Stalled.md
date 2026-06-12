---
title: "Ubuntu12.04 Installation Stalled"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by Randy Schilling on 2012-05-26
Hello-
 
I booted into Ubuntu for the first time in several months
and was greeted with a message saying that the upgrade to 12.04 
was available.  Liking to keep up with what's new, I clicked ok and the upgrade started.  The progress report looked like this:
 
         (check) Preparing to upgrade
         (check) Setting new software channels.
         (check) Getting new packages.
         >  Installing the Upgrade
          Cleaning up
          Restarting the Computer
     Installed libc-bin
   
It appeared that the system was stalled but I watched it for well over an hour.
The system did not respond to any mouse clicks; I could not, for instance, open a web browser or text editor or even a bash shell.  I gave up trying and forced a reboot.  I tried to boot into Ubuntu but that failed, stalling at my Grub2 splash screen.
 
Is there anyway to recover from all this without loosing all the work I invested in  my previous version of Ubuntu?  I was quite happy with my Ubuntu 11.04 and I'm really sorry I didn't just stay with it.  Anyway, please be as specifiec as you can with your instructions as I'm still a beginner.
 
Thanks so much -Randy

---

### Post by mörgæs on 2012-05-27
Yes, in a live boot you can rescue all your files.

---

### Post by Sef on 2012-05-27
>  I was quite happy with my Ubuntu 11.04 

Did you upgrade from 11.04 to 12.04 directly?

---

### Post by Randy Schilling on 2012-05-28
Morgaes: By a live boot, do you mean I should boot from my 
Ubuntu 11.04 installation disk?  Please, explain what I can
expect.  I would like to just get back to my original ubuntu 11.04 setup
and not do the upgrade to 12.04, but you're told during the upgrade
that once you click yes to begin the upgrade there is no turning back
(or something to that effect).  So please explain how I can get 11.04 running again without loosing my files and customizations.  Thanks  randy

---

### Post by Randy Schilling on 2012-05-28
Sef:  I just responded yes to a window that appeared on my system asking if I want to upgrade and the process took off from there.  I did not use a disk or visit a website looking to upgrade.   

I'm having a problem with my internet service which is not yet corrected.
Internet problem began during the upgrade.
Don't know if the upgrade caused the problem or if the problem interrupted the upgrade.  But I think upgrade problem and internet problem are somehow related to each other.  Any suggestions?  Thanks Randy

---

### Post by mörgæs on 2012-05-28
> **Randy Schilling said:**
> Morgaes: By a live boot, do you mean I should boot from my 
Ubuntu 11.04 installation disk?  Please, explain what I can
expect.  I would like to just get back to my original ubuntu 11.04 setup
and not do the upgrade to 12.04, but you're told during the upgrade
that once you click yes to begin the upgrade there is no turning back
(or something to that effect).  So please explain how I can get 11.04 running again without loosing my files and customizations.  Thanks  randy

In a live boot ('Try Ubuntu' from the installation CD/USB stick) you will see an icon called 'file system'. It will give read access to all files on the hard drive. 

Now you can copy the files you want into a USB stick. 

After that I would not recommend installing 11.04 again, since it has less than half a year support from now. Go for a fresh install of 12.04.

It's not worth the hassle to try to rescue the present installation.

---

### Post by Randy Schilling on 2012-05-29
Thanks very much Morgaes.  I appreciated the straight shhotin. Regards

---

