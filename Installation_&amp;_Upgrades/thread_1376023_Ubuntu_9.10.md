---
title: "Ubuntu 9.10"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by hantechbl on 2010-01-08
I had ubuntu 9.04 which worked ok  but now i installed 9.10 and that installed tons of kernels that don't work just as new kernels never have.  When i use my old kernel it boots but takes 5 minutes.  The desktop is extremely slow even with 1 program running (google Chrome)  X window system also crashes.  I need a way to get back to older versions of windows I would like 9.04 but earlier would be better.  I have important files and I would like them to be preserved. If apps were preserved that would be great.  Does anyone know how to do this?

---

### Post by stlsaint on 2010-01-08
so you did an upgrade from jaunty to karmic and now your system doesnt work? what do you mean by earlier versions of windows...and i backup will save all files and you may want to use [aptoncd]("https://help.ubuntu.com/community/APTonCD") for programs or try going through Synaptic Package Manager and selec File>Save markings to use later when wanting to reinstall them. Please explain your issues and what the endstate that you would like more clearly.

---

### Post by hantechbl on 2010-01-08
> **stlsaint said:**
> so you did an upgrade from jaunty to karmic and now your system doesnt work? what do you mean by earlier versions of windows...and i backup will save all files and you may want to use [aptoncd]("https://help.ubuntu.com/community/APTonCD") for programs or try going through Synaptic Package Manager and selec File>Save markings to use later when wanting to reinstall them. Please explain your issues and what the endstate that you would like more clearly.

I managed to get my system up but it is very unstable. What i mean is that the X window manager crashes and I get brought back to the login screen.  I would like to know If I could go uninstall Karmic Koala packages and use the ones that the older versions of ubuntu uses.  I would also like to know how to get rid of the new kernel at least from the bootloader.

---

### Post by presence1960 on 2010-01-08
I guess you didn't see all the threads about dist-upgrade problems. I would back up your data and do a clean install of either 9.10 or 9.04. There are ways to get your currently installed packages on the new installation provided they are in the repositories and not compiled from source or downloaded from third parties. One is the Synaptic method stlsaint mentioned. Here is a [link]("http://ubuntuforums.org/showpost.php?p=7157175&postcount=5") for the method I have used successfully many times for myself and others' machines I have worked on. Just make sure you add all software sources prior to restoring the packages.

This is just my opinion and does not reflect reality for all who do dist-upgrades. For some it works and for others there are major problems, I don't want to roll those dice- do a clean install with the methods described above. IMHO the dist-upgrade is a lazy way to try to avoid **_perceived work_**. But in a lot of cases it leads to even more work because there are a lot of documented problems because of the in place dist-upgrade. Do yourself a favor and don't roll those dice next time. Do a clean install and restore your packages. Very little work compared to what you are going to go through now.

---

