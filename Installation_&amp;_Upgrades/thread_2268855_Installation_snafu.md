---
title: "Installation snafu"
date: 2015-03-12
forum: Installation &amp; Upgrades
---

### Post by frankindustries on 2015-03-12
So here is the deal. I was updated Ubuntu on my laptop and half way through the install process the battery died, after I plugged it in it now boots to a screen where I can choose the version of ubuntu  to boot from one of them being a recovery  mode and there are two memory test options as well.

But no matter what version I choose I get the meessage stating that 

" filesystem check or mount failed.
   maintenance shell will now be started.
  Control-D will terminate this shell and contine  booting after re-trying file systems.
 any further errors will be ignored
root@mr-G585 :~#  " 


and nothing else will happen on that screen, and hitting control D brings up.

"mountall start/starting. "
followed by the same message as seen above.

I have tried to boot from a usb drive, when I restart with a USB drive inserted it starts and gets past the Lenovo screen ( that is the laptop manufacturer) and then goes to a blank screen, and even though the boot sequence says optical drive the dvd does nothing.

What am I missing and/or doing wrong.  please keep in mind I am not overly computer/Ubuntu savvy

---

### Post by ian-weisser on 2015-03-12
There is no simple way to 'repair' a botched install due to power loss, unless you understand the install process and can tell us exactly where during that process you lost power. From there, its a fairly simple matter to resume.

However, it's unlikely that a beginner can do that. So the easiest and fastest solution is to insert your install media and do the entire install again....while plugged in.

---

### Post by frankindustries on 2015-03-12
I thought thats what I was doing by trying the bootable USB. but with the usb drive inserted I just get a blank screen. is that what you mean by "install Media " ?  or is there another option I can use ?    I am not worried about any data I just want to be able to have a working laptop again.

---

### Post by ian-weisser on 2015-03-13
The 'install media' is whatever you inserted into the machine to install Ubuntu in the first place.
Do that process again. Do the entire install again.

---

### Post by frankindustries on 2015-03-13
oh I see, I did the original install off a bootable USB. Is that the only option ?

---

### Post by DennisFolsom on 2015-03-13
I concur that a reinstall from the USB is the best way to go.  You may have to get into a boot menu in the BIOS to tell the PC to boot off the USB.  If your bootable LiveUSB is damaged, you may have to create another one (on another machine, of course).

---

### Post by ian-weisser on 2015-03-14
> **frankindustries said:**
> oh I see, I did the original install off a bootable USB. Is that the only option ?

There are many options, but the others require a bit a skill and experience.
The other options are not trivial insert-and-push-the-button instructions. They get deep and dirty, and take much longer.

---

