---
title: "live usbs not working after 11.10 installation"
date: 2011-12-26
forum: Installation &amp; Upgrades
---

### Post by quill3033 on 2011-12-26
Hi, I have installed edubuntu 11.10 and since I have done this I am unable to boot from live cd or live usb even though my bios is set to boot from these devices *before* booting from hdd. Have tried different distros like lucid lynx (I had wanted to downgrade as I'm not happy with oneiric), and bodhi. I dual boot Windows XP and Edubunt 11.10. Thanks in advance. :-)
:D

---

### Post by West201 on 2011-12-26
What application are you using to burn the ISO ? Are you using start-up creator ? The disk/usb must contain a bootable file that bios recognizes.

---

### Post by cappybob on 2011-12-26
I have used Unetbootin-Windows, this program changes the bios to allow it to usb boot, Give it a try, my older Acer laptop did not have this option in bios but does now.  The program gives different distros for casper but seems to work on any release. Just let it know you want a live CD, X64, or HDD.

---

### Post by quill3033 on 2011-12-27
Thank you for your replies. I made the usb with StartuUp Dik Creator on Ubuntu, but I think it may be that the usb is corrupted. I will buy a new one and see. The Bios (eeepc 2102) is set to boot from cd and removable device before the hdd so I don't think that is the problem. 
I disabled boot from hdd and got a screen saying to insert a bootable device so clearly the bios is responding to changes so... 

I did wonder it the problem had to do with trying to boot into an older version of Ubuntu, but I've used same usb and made bootable versions of linux mint and bodhi and still the pc did not boot into them so that' s not it either. 
Will buy new usb and try again and post. Thanks again.

---

### Post by quill3033 on 2011-12-28
SOLVED!!! I think. Posting this from Bodhi live usb :-) 

OK - the thing with the bios is that EACH TIME you want to boot either from cd (external drive) or usb, you have to press F2 (with the usb or cd drive with live cd connected)to take you to the bios and on the bios, in the Boot settings you have to pick the **actual** device eg. scancruzer or verbatime usb or whatever that you would like to boot first. That is the only way it works. There was nothing wrong with the usb dirve, it worked perfectly and so did the cd drive - booted into linux mint and now bodhi. Will check out jolicloud next. Thank you everybody.Will look at how to mark this thread SOLVED and how to give thanks tomorrow. 

Very happy me.: :guitar::popcorn::KS:KS:KS

---

### Post by West201 on 2011-12-28
I'm glad your up & running now :cool:

---

