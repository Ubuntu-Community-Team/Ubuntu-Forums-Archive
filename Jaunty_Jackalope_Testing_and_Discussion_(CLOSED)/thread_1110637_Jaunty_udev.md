---
title: "Jaunty udev"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by djuniah on 2009-03-30
I seem to be having a couple small udev related issues with jaunty...
First, When i plug in my LG cellphone to use bitpim, the app can no longer see the phone.  It lists the following in regards to the USB connector:
```

active  - True  -  Your operating system shows this driver and port is correctly configured and a device attached 
available  -  False  -  It was not possible to open this port 

```
This is apparently due to a udev rule issue.  Although, all the correct files in rules.d seem to exist.  Any suggestions?

Also, since upgrading, the OS no longer sees the fat32 portion of my rockbox'd media player when i plug it in.  It should just appear as though it is an external hard drive, but i'm not even seeing it in /dev anywhere.  Any thoughts?  (note: it works FINE in other computers, linux/osx/windows)

---

