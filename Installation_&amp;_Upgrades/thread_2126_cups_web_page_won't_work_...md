---
title: "cups web page won't work ..  ?"
date: 2004-10-26
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2004-10-26
I get the following message when attempting to use the CUPS web page to set up a printer.

Administrative commands are disabled in the web interface for security reasons. Please use the GNOME CUPS manager (Computer > System configuration > Printing).

Is there a way to enable admin commands again?

Thanks

Jim

---

### Post by jeremy on 2004-10-26
I would love to have an answer to this one too

---

### Post by jdong on 2004-10-26
Why would you need to?

---

### Post by jeremy on 2004-10-26
[QUOTE=jdong]Why would you need to?[/QUOTE]
 Because I have played around with the settings in the 'printing' (System configuration) box, and haven't been able to fix my problem (draft mode doesn't seem to work), and now would like to try  using the web dialogue.

---

### Post by Kopf on 2004-10-26
Edit the /etc/cups/cupsd.conf file.

In the file there will be a few lines for admin that begin with <Location /admin>.

Add a line that allows you to admin the box from your local network.  

I use the 192.168.1.x network so I added the following line under Allow From 127.0.0.1:

Allow From 192.168.1.0/24

Save the file, restart cups and you shoudl be good. Let me knwo if you run into problems.

Kopf

---

### Post by jeremy on 2004-10-26
Thanks for troubling to answer, Kopf, but I am afraid it didn't work.

---

### Post by jamaas on 2004-10-26
Hi Kopf et al.

Thanks but no cigar!  Now the broswer won't even let me see the web page.  Someone asked why I want to use the web interface???  Because I've tried to use the gnome-cups interface, or whatever the utility is that pops up from the menu, but can not get it to work.  I've been successfull before at getting the CUPS web interface to set it up  and it worked find, so the answer is just looking for a way to configure a wireless print server.  Any other contributers here?  Looks like I'm not the only one printerless....  :-)

Thanks a bunch

Jim



[QUOTE=Kopf]Edit the /etc/cups/cupsd.conf file.


Allow From 192.168.1.0/24

Save the file, restart cups and you shoudl be good. Let me knwo if you run into problems.

Kopf[/QUOTE]

---

### Post by jamaas on 2004-10-27
I finally cracked it for myself, about the milliionth permutation ...


forget cups

go to the printer setup
choose unix/lpd or whatever the other choice is, not cups
for host put in the host ip address, in my case 192.168.2.1
in queue put the printer port to capture, like LPT1 in my case
save, it works for me... good luck

Jim

---

### Post by jdong on 2004-10-27
I think ubuntu cups is patched to disable the admin page. Copying over a Debian /etc/cups folder doesn't help.

---

### Post by Kopf on 2004-10-27
I messed with it for quite a while today.  It looks like the package is built with the admin page disabled.  I guess you guys are out of luck.  I checked the cups logs and saw it accessing PAM for authentication so that may be another place to hunt.  I guess you guys have to use the Gnome tool. Best of luck.

Kopf

---

### Post by dninja on 2005-05-31
Has anyone got any further with this?

I can't follow the instructions given, the ones about using Gnome, as I don't have Gnome installed.

Is there any alternative other than installing CUPS from source not ubuntu?

---

### Post by SNo0py on 2005-06-08
[QUOTE=jdong]Why would you need to?[/QUOTE]
Because I don't have X installed at all because it's a server?

Personally I think the Ubuntu-Developers should re-enable this feature, otherwise Ubuntu is a bit unuseable for computers that don't run X and/or Gnome...

---

### Post by SNo0py on 2005-06-08
Oh, it works... don't ask me why, but it works:

[http://dramor.blogspot.com/2004/12/todays-stupid-trick-on-ubuntu.html](http://dramor.blogspot.com/2004/12/todays-stupid-trick-on-ubuntu.html)

--> it's really a stupid trick...

---

### Post by Joshua Swink on 2005-06-17
In summary, the answer is:

[INDENT]**adduser cupsys shadow** 
**/etc/init.d/cupsys restart**[/INDENT]

---

### Post by Mortal on 2005-06-27
But what if I want to use this on a regular basis? Is it safe to have cupsys in the shadow group? Why is this disabled as default? Is the web interface really that insecure?

---

### Post by jago25_98 on 2006-09-30
Seeing as I don't use gnome and the KDE printer admin page halts on initialising I can't use cups. I'll try upgrading everything, but I'm looking forward to it; something usually breaks.

---

