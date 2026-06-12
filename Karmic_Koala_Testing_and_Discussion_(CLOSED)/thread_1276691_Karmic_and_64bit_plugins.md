---
title: "Karmic and 64bit plugins"
date: 2009-09-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by FrancoNero on 2009-09-27
Can someone tell me why, if I run 64bit karmic, there's a 32bit Flash plugin in the ndspluginwrapper installed (I hope I'm spelling this correctly)?
When I install a 64bit OS, I want just that. No wonder everyone's complaining about not working Flash or something, it works perfectly if you get the 64bit Flash from Adobe and kick that wrapped-stuff off your harddrive.
When will the 64bit OS truly be 64bit? I don't get this....

---

### Post by MilesRdz on 2009-09-27
> **FrancoNero said:**
> Can someone tell me why, if I run 64bit karmic, there's a 32bit Flash plugin in the ndspluginwrapper installed (I hope I'm spelling this correctly)?
When I install a 64bit OS, I want just that. No wonder everyone's complaining about not working Flash or something, it works perfectly if you get the 64bit Flash from Adobe and kick that wrapped-stuff off your harddrive.
When will the 64bit OS truly be 64bit? I don't get this....

Flash from the "64bit" repository not only crashes the system often, but it just doesn't work right. Shame, really...

---

### Post by FrancoNero on 2009-09-27
sais who? for me the 32bit-wrapped one never works right. the other one does

---

### Post by MilesRdz on 2009-09-27
> **FrancoNero said:**
> sais who? for me the 32bit-wrapped one never works right. the other one does

Yeah, sorry I was referring to the 32-bit-wrapped version which are in the repositories.

---

### Post by hanzomon4 on 2009-09-27
> **FrancoNero said:**
> Can someone tell me why, if I run 64bit karmic, there's a 32bit Flash plugin in the ndspluginwrapper installed (I hope I'm spelling this correctly)?
When I install a 64bit OS, I want just that. No wonder everyone's complaining about not working Flash or something, it works perfectly if you get the 64bit Flash from Adobe and kick that wrapped-stuff off your harddrive.
When will the 64bit OS truly be 64bit? I don't get this....

The plugin is still in alpha/beta

---

### Post by FrancoNero on 2009-09-27
the other one isn't working right, what qualifies that one for being non-alpha/beta?

---

### Post by philinux on 2009-09-27
Conspiracy theory:-

Adobe left the 64 bit linux flash plugin at alpha because they haven't done one for 64 bit MS and MAC yet.

---

### Post by shafin on 2009-09-27
> **FrancoNero said:**
> the other one isn't working right, what qualifies that one for being non-alpha/beta?
That one is non alpha for 32 bit firefox, on 64 bit FF, that one is not even supported by adobe.

---

### Post by sonicb00m on 2009-09-27
> **shafin said:**
> That one is non alpha for 32 bit firefox, on 64 bit FF, that one is not even supported by adobe.

I'm not sure why the 32bit wrapped one is in the repos and not the official 64 bit one. I read something to do with licensing but could be wrong.

For sure though the wrapped version sucks big time and never works right, if at all.

All i do is an "updatedb" and locate the libflashplayer.so or whatever it's called and replace it with the 64 bit version from the adobe site. I also remove the wrapped version. This time it has worked flawlessly and has been no trouble with pulse audio.

---

### Post by FrancoNero on 2009-09-27
> **sonicb00m said:**
> All i do is an "updatedb" and locate the libflashplayer.so or whatever it's called and replace it with the 64 bit version from the adobe site. I also remove the wrapped version. This time it has worked flawlessly and has been no trouble with pulse audio.

can you point me to a terminal command that'll do this in a quick step?

---

### Post by inportb on 2009-09-27
> **FrancoNero said:**
> sais who? for me the 32bit-wrapped one never works right. the other one does

Says I. The 64-bit version works much better than the 32-bit version on ia32libs, but still dies quite often in Firefox. (with Arora, on the other hand... it's quite good)

> **FrancoNero said:**
> [QUOTE=sonicb00m;8016529]All i do is an "updatedb" and locate the libflashplayer.so or whatever it's called and replace it with the 64 bit version from the adobe site. I also remove the wrapped version. This time it has worked flawlessly and has been no trouble with pulse audio.can you point me to a terminal command that'll do this in a quick step?[/QUOTE]

This should be reasonably quick on a half-decent system. If you could run Ubuntu on your computer, the locate/rm/untar should not be slow at all. updatedb might take a little bit of time.

---

