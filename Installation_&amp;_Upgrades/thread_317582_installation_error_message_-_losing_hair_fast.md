---
title: "installation error message - losing hair fast"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by atarileaf on 2006-12-12
Ok, help please.

I've finally got the Live CD to work on my system as I was having the blank screen problem with my ATI card. So I followed a suggestion and used the following string of code (which BTW, means absolutely nothing to me as a newbie but I typed it anyway):

mv /root/etc/X11/xorg.conf /root/etc/X11/xorg.conf.disabled

OR, I tried this one too:

chroot /root rm /etc/X11/xorg.conf

Using either I got into the OS itself.
Now, here's my new problem. I try to install the thing. It asks me my language. Fine, asks my time zone, fine, then it asks my keyboard settings, I answer English then the thing crashes with an error message telling me to report the bug and with a whole of lot stuff I don't understand but the final line which caught my eye was this:

"no such file or directory: 'etc/X11/xorg.conf'

Which tells me this error is tied to the changes I HAD to make to get into Ubuntu in the first place. Is this a catch-22 thing? I'm using the 64 bit of 6.06 BTW. Any help really really appreciated cause my bald spot is growing by the minute with this new OS. ](*,) ](*,) ](*,)

---

### Post by taurus on 2006-12-12
If you want to install Dapper on your machine, why not use the alternate CD!!!  It would save you some hair in the meantime...

---

### Post by Sqwishy on 2006-12-12
> **atarileaf said:**
> Ok, help please.
I'm using the 64 bit of 6.06 BTW. Get 6.10 Edgy Eft

Also, you need xorg.conf lol. if you have problems with what you see you might need to change stuff or get drivers. but install ubuntu first before you install drivers.

---

### Post by wpshooter on 2006-12-12
Did you try running with safe video mode parameter ?

---

### Post by rlynch on 2006-12-12
actually, i bet the issue is that he is using the edgy eft live cd. and that because of the drivers it uses, it uses the wrong configs for it.

the most simple answer i can suggest is downloading a dapper livecd, you will see this works flawlessly.

---

### Post by atarileaf on 2006-12-12
Ok thanks guys. I have to ask what the heck is a dapper and an edgy?

And I tried the alternate CD. I just get a blue screen with a strip of grey at the bottom that I can type in but I'm completely new to this so I have no idea what I'm supposed to type.

---

### Post by atarileaf on 2006-12-12
Ok, Dapper and Edgy are different versions of Ubuntu. I've tried 6.10 and 6.06 and both give me the same problems.

In a nutshell, this is my problem:

I need to manipulate this /etc/X11/xorg.conf file as I mentioned in the OP or I cannot get into the LiveCD, no matter which version I use (6.06 or 6.10) and no matter if I use safe graphics mode or not.

However, if I do manipulate, delete, or whatever these commands are doing to this file, I then cannot install Ubuntu to my harddrive. 

So its a catch-22 for sure. If I don't change this xong.conf file I can't get into the LiveCd, if I do, I can't install it.

Please please help. Baldness approaches quickly now.

---

### Post by taurus on 2006-12-12
Please try the alternate CD version before all the hair's gone!!!

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by greylica on 2006-12-12
Can this be a misconfig of hardware too ?
PLZ post your configs of hardware so we can help better.
Some misconfigs can cause the same behavior.

---

### Post by wpshooter on 2006-12-12
atarileaf:

Please do the following:

Go to the Ubuntu website on another machine (not the one you are having all this trouble with) and then find and download the **ALTERNATE** CD version of Ubuntu 6.06.1.

Then burn that ISO image to a good brand named (preferably CD-RW) at 4X or less.

Then also on that same computer go to the KILLDISK website and download the killdisk program and use it to WIPE the computer you are having problems with completely clean (this means that if there is anything on it that needs to be kept, you need to make sure that you have it backed up somewhere).

[http://www.killdisk.com/](http://www.killdisk.com/)

After having WIPE the hard drive clean, then boot from the ALTERNATE CD and make sure you:
 
1) check the integrity of the Ubuntu CD by running the verification test function that is found on the initial Ubuntu boot screen menu.  Make sure the CD comes back with ZERO error found.

2) Boot to the ALTERNATE CD again and this time check your computer's memory by running the MEMTEST function that is found on the initial Ubuntu boot screen menu.

If the memory passes, then and only then, reboot the machine again to the ALTERNATE CD and this time attempt to install the O/S.

Hint:  Make sure that when the installation instructions are fed to you by the installation CD that you let your CD spin down completely between getting the installation prompts and answering them.

Good luck.

---

### Post by atarileaf on 2006-12-12
Thanks for your help guys. I finally figured out what I did wrong and was able to edit the xorg.conf file and switch the "ati" command to "vesa". 

I now have a new problem though but I started a new thread for it:

[http://www.ubuntuforums.org/showthread.php?t=317668](http://www.ubuntuforums.org/showthread.php?t=317668)

Thanks again for your help everyone. Very much appreciated.

---

### Post by SteveOSupremo on 2008-02-07
ok so what did you do to write the xorg.conf file?

I'm having a similar problem with 7.10


SteveO

---

