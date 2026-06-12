---
title: "Hmm, something is wrong.."
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by Frugoo Scape on 2007-08-17
I downloaded the intell 32bit base and also the 64. Only the 32 would work, but i have an amd processor. I installed the server edition with no problem with  LAMP on it. When i go to start the system up. All it does it say loading then it goes to restart once again. Over and over this happens. Does anyone know what could be causing this?

---

### Post by dabl on 2007-08-17
Doesn't sound right to me.  I would think the AMD-64 version is the one you should use, unless your CPU is not a 64-bit processor.  Did you check the md5 sum on your downloaded ISO file?  Did you burn the CD at no more than 4X speed?

---

### Post by Frugoo Scape on 2007-08-17
> **dabl said:**
> Doesn't sound right to me.  I would think the AMD-64 version is the one you should use, unless your CPU is not a 64-bit processor.  Did you check the md5 sum on your downloaded ISO file?  Did you burn the CD at no more than 4X speed?

I did 28x or something. Also it is a AMD, but it is old. The 64 bit installer told me to do a 32 bit install.

---

### Post by Frugoo Scape on 2007-08-17
I tested the cd. It came out fine.

---

### Post by dabl on 2007-08-17
> **Frugoo Scape said:**
> I did 28x or something. Also it is a AMD, but it is old. The 64 bit installer told me to do a 32 bit install.

Hmmmm.  Well, the recommendation is to burn your installation CD at 4X, and not faster.

However, it sounds like 32-bit is right for your hardware.  You said it goes "blank" or something when loading -- could it be just an issue with the video display?  What happens if you Ctrl-Alt-F1, after you see no more hdd activity?

---

### Post by Frugoo Scape on 2007-08-17
> **dabl said:**
> Hmmmm.  Well, the recommendation is to burn your installation CD at 4X, and not faster.

However, it sounds like 32-bit is right for your hardware.  You said it goes "blank" or something when loading -- could it be just an issue with the video display?  What happens if you Ctrl-Alt-F1, after you see no more hdd activity?

It says loading grub then it says starting up. Then the computer restarts. Pressing those keys during this process had no effect.

---

### Post by dabl on 2007-08-17
> **Frugoo Scape said:**
>  Then the computer restarts. Pressing those keys during this process had no effect.

Ahhhh -- so it is "endlessly rebooting"?

Well, then something is indeed wrong, either with the kernel boot instruction in /boot/grub/menu.lst, or else with the filesystem table in /etc/fstab.  If your system won't start, you obviously cannot copy and post those files ...  hmmmmmmmmmmmm.

Well, you say you "installed the server edition with no problem", but I'm beginning to wonder about that.  How did you partition your hard drive -- how much space for "/" and for swap?

---

### Post by Frugoo Scape on 2007-08-17
> **dabl said:**
> Ahhhh -- so it is "endlessly rebooting"?

Well, then something is indeed wrong, either with the kernel boot instruction in /boot/grub/menu.lst, or else with the filesystem table in /etc/fstab.  If your system won't start, you obviously cannot copy and post those files ...  hmmmmmmmmmmmm.

Well, you say you "installed the server edition with no problem", but I'm beginning to wonder about that.  How did you partition your hard drive -- how much space for "/" and for swap?

I did the whole disk one.

---

### Post by Frugoo Scape on 2007-08-17
When i started the installation up it says bios age is 1998 fails cutoff 2000 force Enabling apci. How would i go about upgrading my bios, it is a IBM computer or am i taking the wrong solution?

---

### Post by dabl on 2007-08-17
Interesting. Well, some problematical setting in the BIOS could indeed be the source of your problem.  Is there a calendar/clock setting in there?  Sounds like Ubuntu doesn't like the year, maybe.  I'd get into BIOS and review the settings.  Also, go to the IBM support site for that model of computer, and see if there is an updated BIOS that you can flash it with.   Good luck!  :)

---

### Post by dabl on 2007-08-17
Also, there's probably a little ni-cad battery on that motherboard, and it may be dead, which would cause it to lose the time & date whenever the computer is shut down.  If you can pull that battery out, and put in a new one, and then reset the date in BIOS, maybe it will be OK in the future.  :)

---

### Post by insane_alien on 2007-08-17
if the 64-bit installer told you to do a 32-bit install it probably means you have a 32-bit processor. 32-bit processors do not handle 64-bit instructions.

not sure about the endlessly rebooting thing though.

---

### Post by Frugoo Scape on 2007-08-17
> **insane_alien said:**
> if the 64-bit installer told you to do a 32-bit install it probably means you have a 32-bit processor. 32-bit processors do not handle 64-bit instructions.

not sure about the endlessly rebooting thing though.
Yeah, no duh on the processors bit.

---

### Post by Frugoo Scape on 2007-08-17
Nope, on bios the time and date is accurate.

---

