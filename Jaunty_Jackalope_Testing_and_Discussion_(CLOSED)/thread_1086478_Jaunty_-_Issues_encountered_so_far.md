---
title: "Jaunty - Issues encountered so far"
date: 2009-03-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LordChaos73 on 2009-03-04
* Printing (HP Photosmart C4380) - every print preview looks fine on screen, but the print itself is not correctly vertically aligned on paper, seems like a margin issue. This is a system-wide problem, probably cups or hplip related.

* Pulseaudio distorted sound on logon, has been discussed by other threads already.
However, when playing music, the user.log & syslog get flooded by these type of messages:

Mar  3 22:38:22 vaiopro pulseaudio[4142]: module-alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write! Most lik ely this is a Linux bug. Please report this issue to the ALSA developers. We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail_update() returned 0.

* ufw - Logging is set to medium, yet I can't find any log entry. Also, it seems like service specific configuration options in /etc/ufw/applications.d are not inclucded.

Cheers,

Eric

---

### Post by Triggerhapp on 2009-03-04
* Runescape, ANY Browser(FF, Epiphany etc), ANY Java (icedtea, sun etc), Nvidia Binary drivers - been long standing issue with the game freezing during play, often not recoverable without crashing Firefox and starting again

---

### Post by Nullack on 2009-03-04
Please consider contributing to bugs, links in my sig

---

### Post by Triggerhapp on 2009-03-04
> **Nullack said:**
> Please consider contributing to bugs, links in my sig

In my case... Im a bit  lost as to what package is at fault... Still trying to work it out :)

---

### Post by Vinci71 on 2009-04-13
> **LordChaos73 said:**
> * Printing (HP Photosmart C4380) - every print preview looks fine on screen, but the print itself is not correctly vertically aligned on paper, seems like a margin issue. This is a system-wide problem, probably cups or hplip related.


I can confirm this, and also that I think it is system related, since it happens when the same printer is shared from a Windows machine, and I print using both hp and standard drivers.

The top of the page is systematically cut off

As for the other applications I usually use, there is just Amarok 2 that seems not to work properly when using files from the collection instead of single .mp3 files, but I still have to understand the real problem in it.

---

