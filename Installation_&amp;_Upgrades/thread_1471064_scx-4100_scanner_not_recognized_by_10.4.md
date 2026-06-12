---
title: "scx-4100 scanner not recognized by 10.4"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by mimmo.marozzi on 2010-05-03
I have the  samsung scx-4100 multifunction printer that worked perfectly in 9.10 while now the scanner isn't detected anymore by 10.4 and it's also impossible to install samsung linux drivers due to dependencies lack. Any suggestion on how to solve this?

---

### Post by Jimmy McKellar on 2010-05-17
> **mimmo.marozzi said:**
> I have the  samsung scx-4100 multifunction printer that worked perfectly in 9.10 while now the scanner isn't detected anymore by 10.4 and it's also impossible to install samsung linux drivers due to dependencies lack. Any suggestion on how to solve this?

Hi

I have the same problem, neither simple scan nor xsane image scanner seem to recognise the scanner.  

I tried the obvious first and used a boot disk for the previous version of Ubuntu to boot a different box (computer) and tried to connect from that and strangely that too failed.

This clearly needs a bit of investigation - I will report back once I get somewhere or nowhere depending on the magnitude of the glitch.

Regards
Jimmy

---

### Post by timgood on 2010-05-17
Similar problem here - would be great if I could get it to work in Lucid.

---

### Post by yahs on 2010-05-17
Trying to be helpful I suggest you check out this post - 
HOWTO Install Samsung Unified Printer Driver by Tweedledee
it's long but it is the definitive guide to installation of all Samsung Printers and is a must for all samsung users.

I have been using Ubuntu since 2007 and my scx-4100 is still going strong.
This is how my latest upgrade went, I hope it's useful. 

I did a fresh install of Lucid Desktop on May 1st (Intel Pentium Dual core)
Unlike Jaunty, Lucid did not recognise my Samsung scx4100 mfp.
Using system, administration, printing, new - Lucid recognised the printer and offered scx4200 as the only available printer driver. I accepted this and printed a test page which printed okay. The device URI: was listed as usb://Samsung/SCX-4200%20Series using SpliX V.2.0.0
I have found the easiest way to install correctly is to download the unified driver from Samsung but you have to use scx-4600 as 4100 no longer appears on the web site.
My normal method of installation is as follows
Change to the directory cdroot/Linux and run sudo ./install.sh
In the terminal I get messages as follows

libstdc ++.so.5 not found, install ... done
libstdc ++.so.3 not found, install ... done

It seems Qt library is not installed or X display is not accessible
Custom Qt library will be configured for use with this package.

Samsung GUI installer then appears and runs, you are offered the option of adding users to the group lp and disabling parallel printing.

The printer is configured to use /dev/mfp4 and a test page can be printed using CUPS v 1.1.x.

The unified driver configurator appears on the desktop and Scanner comes up as flatbed scanner scx-4100 series on usb:0 and works perfectly. 

Note: After the reboot, in the unified driver configurator there are now 2 printers showing.

SCX-4200-Series on usb://Samsung/SCX-4200%20Series (using Splix)
scx4100(default) on mfp:/dev/mfp4

I am going to do a complete reinstall shortly as I did have a problem initially
A message about not being able to print as cups not started – however this disappeared before I had time to check it out.

---

### Post by krige on 2010-05-20
I had the Samsung SCX4100 printer and scanner working on 9.10. After upgrading to 10.04 the printer still worked but the scanner not.

I solved it by installing again the Samsung Unified Linux Drivers, version 3.00.65, I have downloaded from the following page:
[http://www-personal.umich.edu/~tjwatt/suldr/](http://www-personal.umich.edu/~tjwatt/suldr/)

---

### Post by gychang on 2011-04-23
> **krige said:**
> I had the Samsung SCX4100 printer and scanner working on 9.10. After upgrading to 10.04 the printer still worked but the scanner not.

I solved it by installing again the Samsung Unified Linux Drivers, version 3.00.65, I have downloaded from the following page:
[http://www-personal.umich.edu/~tjwatt/suldr/](http://www-personal.umich.edu/~tjwatt/suldr/)

that web site is not working.

I need to get the at least the printer going on my 10.10.  Can someone give a newbie hand on how to get this working on my ubuntu?

thanks,

gychang

---

### Post by yahs on 2011-04-25
I used to own a scx-4100 and it does work (both printing and scanning under all ubuntu versions)

The web site is as follows.

[http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)

Check out the thread "HOWTO install Samsung unified print driver" by Tweedledee

---

### Post by DanaNutter on 2011-05-14
I have 11.04 installed (upgraded from 10.10).   The printer was plug-n-play but I do not see the scanner at all.

---

### Post by 1script on 2012-08-03
> **yahs said:**
> I used to own a scx-4100 and it does work (both printing and scanning under all ubuntu versions)

The web site is as follows.

[http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)



Thank you very much for the link! I finally got the scanner part of the SCX-4100 working under Ubuntu 10.10. It would have been a real shame to throw this old workhorse of a printer out just because of Ubuntu upgrade (which was a couple of year ago by now :) ) and now I don't have to! 

Cheers!

---

