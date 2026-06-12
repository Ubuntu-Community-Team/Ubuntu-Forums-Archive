---
title: "alpha 5 cds fail"
date: 2009-03-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ELD on 2009-03-03
I have tried both ubuntu and kubuntu alpha 5 cd's, i burn, verify and then it still tells me it is an invalid cd?

---

### Post by obscur156 on 2009-03-03
Hi, first have you checked the MD5SUM if its ok?
You can try GTKHASH for that.

Second,what kind of fail you have?
Do you get error message and if yes,what is that message?
Regards.

---

### Post by nyarnon on 2009-03-03
Where did you get them, did you notice that there is a warning that you cannot burn them as they are to big for a cd due to a bug. You should use a DVD or a usb pen or something alike.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

states:

Warning: This image is oversized (which is a bug) and will not fit onto a standard 700MB CD. However, you may still test it using a DVD, a USB drive, or a virtual machine.

---

### Post by mkvnmtr on 2009-03-03
Ha I tried to burn a 702Mb disk a while back. Acted like it burned but no. Then I opened the ISO and tried to see if I could remove a couple of Mb. I guess I needed coasters.

---

### Post by ELD on 2009-03-04
They cd images are below 700mb, it was just windows xp saying it was invalid it booted as a livecd fine so it's just windows not liking it.

---

### Post by obscur156 on 2009-03-04
Hi ELD,i have always used this tutorial for dual-booting and always worked straight foward every time.

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty")

Maybe you can check this out if it looks the way you did it and maybe give it a try.

Good luck,best regards.

---

### Post by Nullack on 2009-03-04
Eld as youve figured out, you need to run the livecd in its own Linux kernel as a clean boot (this can be either a virtual machine or native), the Windows kernel wont recognise it.

---

### Post by ELD on 2009-03-04
@obscur156 i know how to dual boot i already do it but thanks :)

@Nullack it was just the cd menu that comes up with stable cd burns in windows that doesn't work (where you can install inside windows wubi) works fine as a livecd.

---

