---
title: "Cant access BIOS when trying to change settings to load Ubunto through USB."
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by Starlon on 2010-06-07
Im trying to test out Ubuntu while running Windows currently, once i got the ISO image installed into my USB device by following the steps on the Ubunto site, i rebooted my PC and tried to get into BIOS to change the setting to boot through the USB device. 

but i was unable to open BIOS.

this is all i saw in the bottom right side of my screen as far as commands to open some thing before my PC would boot through my Cdrive and load Windows.


L> BIOS Setup/Q-flash

---

### Post by dino99 on 2010-06-07
do you want to flash your bios ?

depend on your system , you might enter bios with del key or F2 or following your hardware manual

---

### Post by Starlon on 2010-06-07
> **dino99 said:**
> do you want to flash your bios ?

depend on your system , you might enter bios with del key or F2 or following your hardware manual


Well when i fist installed windows, i had to enter BIOS to change the setting to read the CD from the CD/DVD driver. that was F11. but that Command is no longer there. im the only person that uses this computer, and i haven't used BIOS since installing Windows Home Edition.

Now all i see on the start up screen where the comand for BIOS is, is...    L>BIOS Setup/Q-flash  Instead of   <F11>BIOS Setup/Q-flash

---

### Post by dino99 on 2010-06-07
[http://forums.tweaktown.com/f69/bios-flashing-how-qflash-guide-27576/](http://forums.tweaktown.com/f69/bios-flashing-how-qflash-guide-27576/)

so you have asked to flash the bios, or a virus is inside the bios. 

workaround: unplug the power cord, wait a few minutes, remove the bios battery, wait again a few minutes then plug back the battery, plug the power cord and reboot and config the bios again.

---

### Post by sanderj on 2010-06-07
Googling for "BIOS Setup/Q-flash", the first Google hits suggest you have a Gigabyte mobo with Q-Flash. If that sounds familiar, those same first Google hits suggest you should use the DEL-key to enter the BIOS. So: startup your computer and start repeatedly hitting your DEL-key.

---

### Post by Starlon on 2010-06-07
> **dino99 said:**
> [http://forums.tweaktown.com/f69/bios-flashing-how-qflash-guide-27576/](http://forums.tweaktown.com/f69/bios-flashing-how-qflash-guide-27576/)

so you have asked to flash the bios, or a virus is inside the bios. 

workaround: unplug the power cord, wait a few minutes, remove the bios battery, wait again a few minutes then plug back the battery, plug the power cord and reboot and config the bios again.


the link you gave is kinda confusing to me, the images posted there are not what im seeing. 

also where is the BIOS battery?

---

### Post by Starlon on 2010-06-07
> **sanderj said:**
> Googling for "BIOS Setup/Q-flash", the first Google hits suggest you have a Gigabyte mobo with Q-Flash. If that sounds familiar, those same first Google hits suggest you should use the DEL-key to enter the BIOS. So: startup your computer and start repeatedly hitting your DEL-key.

Awesome, that worked. but now when i select the USBHDD option i get to the boot screen, and it says some thing like it cant load the data. i followed the instructions on [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) 

i have the options set for USB and Windows.

i used the Universal USB Installer like the instructions say.

when i got to the step where i select the Version of the OS that i have installed as an ISO, i dont have the option to brows for the ISO, it says the ISO has already been found and selected.

i followed every thing it says but it still wont let me boot it through the USB device.

---

### Post by sanderj on 2010-06-07
Two things you can do:

1) Use a live-CD in the target system (after setting CDROM before the harddisk in the BIOS boot order). Reason: apparantly you have a live-CD that works. It takes out the USB-stick a possible cause of non-booting

OR 

2) Use the live-USB-stick in another system to check you have correctly created a live-USB-stick.

---

### Post by Starlon on 2010-06-07
> **sanderj said:**
> Two things you can do:

1) Use a live-CD in the target system (after setting CDROM before the harddisk in the BIOS boot order). Reason: apparantly you have a live-CD that works. It takes out the USB-stick a possible cause of non-booting

OR 

2) Use the live-USB-stick in another system to check you have correctly created a live-USB-stick.


I wanted to use a blank disc to turn into a Live-CD but the closest Store is a mile away, and the next one is 20. that even carry blank discs. the store i went to was selling blank CD's and DVD's 5 for Around 20$ if i converted it right. and thats a bit much for me. i have a Flashdrive, so i want to try and get it with that.

what can i do if there isnt another system available to me? is there another processes i could try?

---

### Post by sanderj on 2010-06-07
Ah, you created a USB-stick from Windows, and you haven't got a live-Ubuntu-CD.

I see. Advice: use software + instructions from [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) If that doesn't work, open a new thread as this thread is about your BIOS (which now works).

---

### Post by Sylslay on 2010-06-07
Now, when You get to bios, what are Yours boot prioryty options;

Should be :
1st Usb or usb-hdd
2nd cd-rom
3rd hdd

But if yours mobo is to old or bios have errors you can't boot form usb-key.

PS Some time it help to connet usb-hub (kind of spliter and you can boot to kernel,,, it don/t stop during boot up.
But if You eaven see menu of Ubuntu , that sound like mobo is not great/

---

### Post by Starlon on 2010-06-07
> **sanderj said:**
> Ah, you created a USB-stick from Windows, and you haven't got a live-Ubuntu-CD.

I see. Advice: use software + instructions from [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) If that doesn't work, open a new thread as this thread is about your BIOS (which now works).


Alright, thank you for helping me with the BIOS problem. im going to try what you suggested.

---

### Post by Sylslay on 2010-06-07
Found what date and version of bios is in Yours mobo and check what version of bios for Yours mobo are on web, 
But sometimes is easyer get those Cd, sometime instead tweaking with all mobo......

---

