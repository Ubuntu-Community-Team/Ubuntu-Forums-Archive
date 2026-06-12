---
title: "WindowsBackend object has no attribute 'iso_path'"
date: 2012-03-29
forum: Installation &amp; Upgrades
---

### Post by unknown user on 2012-03-29
I am currently trying to install Ubuntu 11.10 (Wubi) on to a laptop that I have which is running windows 7 on currently.

The laptop is a Lenovo (Thinkpad) X61s. A nice small thing that has no disk drive on it. It is nice and small, good for the train trip to work.

The Ubuntu 11.10 is on a flash pen currently. When I click on the Wubi option to install inside windows, I receive an error message saying that there is no disk in the drive, but I can click continue past this. So when I get virtually to the end of the insterlation, I receive the following error message:

WindowsBackend object has no attribute 'iso_path'

Does anyone know how to get past this as I would really like Ubuntu on this machine?

---

### Post by bcbc on 2012-03-30
You can't install wubi from a USB drive... except in certain limited circumstances. Wubi does a size check and will fail if it exceeds ~850MB and if the usb partition is bigger it will copy the whole partition and fail it. You can confirm this in the log - check the %TEMP% directory to find it.

The iso_path problem is a bug that happens after the ISO is rejected due to an uninitialized variable reference.

My suggestion - place the desktop CD ISO in the same folder as wubi.exe and run it from there, not from the USB.

---

### Post by unknown user on 2012-03-30
Thanks for the reply.

After putting this post up I had a further look on the net and did find an article that confirmed what you said about putting the downloaded wubi iso on the desktop and then taking the wubi exe and placing it on the desktop too.

I did this and sure enough I was able to install Ubuntu 11.10 without any issues. Fantastic, I can work on something other than windows on this laptop.

---

