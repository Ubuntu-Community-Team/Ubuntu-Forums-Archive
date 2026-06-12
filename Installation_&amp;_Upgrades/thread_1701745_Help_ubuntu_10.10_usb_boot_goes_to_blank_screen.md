---
title: "Help: ubuntu 10.10 usb boot goes to blank screen"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by elucid_one on 2011-03-06
I put Ubuntu on a live usb stick and successfully boot to the menu where it give the option to install to a hard drive or boot from the usb.  I've tried both options and it starts booting with text info flying by.  Then it looks like it goes into a graphics mode my viewsonic LCD monitor does not support.  The screen goes blank saying no analog input.  I got the same error with the CD live boot/installation.

Any help would be greatly appreciated.

---

### Post by YesWeCan on 2011-03-06
Not sure if this will help but it is easy to try. When at the live CD menu there is a boot options function key. Selct nomodeset and then boot off the CD.

---

### Post by elucid_one on 2011-03-06
> **YesWeCan said:**
> Not sure if this will help but it is easy to try. When at the live CD menu there is a boot options function key. Selct nomodeset and then boot off the CD.

Something funny is going on.  I typed nomodeset at the boot menu and it said "kernel nomodeset not found".

Btw, I'm running Fedora currently.  Maybe, maybe there is a conflict?

---

### Post by YesWeCan on 2011-03-06
Weird.
Try it using a live CD or usb.

---

### Post by elucid_one on 2011-03-06
> **YesWeCan said:**
> Weird.
Try it using a live CD or usb.

I get the same problem with the liveCD and booting off the usb.

---

### Post by elucid_one on 2011-03-06
> **YesWeCan said:**
> Weird.
Try it using a live CD or usb.

I'm downloading 10.04 to see if that is better.

---

### Post by YesWeCan on 2011-03-06
Pardon? You boot from a Ubntu 10.10 CD and select the nomodeset option and it reports that the kernel doesn't support nomodeset?

---

### Post by elucid_one on 2011-03-06
> **YesWeCan said:**
> Pardon? You boot from a Ubntu 10.10 CD and select the nomodeset option and it reports that the kernel doesn't support nomodeset?

That was from the usb, from the CD I was seeing the same result with the blank screen.

---

### Post by elucid_one on 2011-03-06
> **YesWeCan said:**
> Pardon? You boot from a Ubntu 10.10 CD and select the nomodeset option and it reports that the kernel doesn't support nomodeset?

The mode of failure for the live CD is: lots of activity from the CD drive, eventually the screen goes blank.  The CD continues to spin for several minutes then stops.  All the while the screen is blank.

---

### Post by elucid_one on 2011-03-07
Same problem with 10.04.  Going to try usb on diff hardware...

---

### Post by elucid_one on 2011-03-07
USB is fine.  I tested it on another machine and it boots just fine.  Any way to change the boot options by editing a file since the command line mode is not working?

Edit: I can also change the boot options on the other machine, but it gives an error when I do the same thing on my desktop machine.

---

### Post by erbey on 2011-06-30
Hi,
I have exactally the same problem, also running fedora (15) after. it boots into USB, ubuntu screen sometimes flashs then goes to a blanks screen, i tried an arch install cd and it said that after the cd booted it couldnt find sr0 anymore, so im not sure but it seems that after the usb or cd is booted into, something unmounts it after that, its never happened on this computer before so the only thing i think it could be is fedora (this is the first time i have used fedora) or it could even be gnome 3 im not sure...

---

### Post by erbey on 2011-06-30
Hmmm, a fedora 15 live USB seems to work fine, using the same usb and computer, ill try ubuntu again and if it stil doesnt work ill try downloading another ISO, even though this iso works on my other computers...

---

### Post by erbey on 2011-06-30
when alpha 2 of oneric comes out later tonight, ill download that and see if it works, kleep you updated

---

### Post by erbey on 2011-06-30
ok, using the same usb. computer etc...i created a liveusb with 11.10 daily and it booted and installed fine, but now when booting into fedora, i get an error message 3 times before fedora boots, this could be causing the problem...error mesage is "*failed to set xfermode* (err-mast=0x4)"

---

