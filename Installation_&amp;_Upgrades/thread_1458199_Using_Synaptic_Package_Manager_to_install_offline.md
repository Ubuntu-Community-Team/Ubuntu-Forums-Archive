---
title: "Using Synaptic Package Manager to install offline"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by mwade on 2010-04-19
Hello,

I am trying to update application on a ubuntu system that is offline (and must stay offline).  I would like to use the Synaptic Package Manager to do the application installs.  Can I just download the application and place it in a certain directory and have the Synaptic Package manager do the install?  If so, what directory do I place the new application in, and do I need to configure anything in the Software Sources?

Thanks,

---

### Post by 2hot6ft2 on 2010-04-19
Go to Synaptic on the one needing the packages and mark all the packages you want to install then click on File > Generate package download script
Then move or save the script to a usb flash drive which you can take to any linux box that is online and double click on it and selecting "Run" or "Run in Terminal if you want to be able to see when it finishes" it will download the packages to the same location as where the script is.

Then you take the usb to the machine that created the script and open Synaptic and click on File > Add downloaded packages and point it to where the script and packages are to install them.

The machine that creates the script is the architecture it will download them for. Not for the one you run the script on to download them.

I think keryx works the same way and updates your sources as well.
[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by mwade on 2010-04-20
Thank you for your assistance.  What if a package that you want is NOT currently on the Synaptic Package Manager list?

Thanks

---

### Post by RyuzakiTenseiga on 2010-07-04
can this be done from a windows 7 system or is that just crazy talk?

---

### Post by EXCiD3 on 2010-07-05
You can use Keryx on Windows 7, as well as adding repositories easily in case the package is not in the Synaptic list.

The problem with using Synaptic's script is that offline, you cannot download the list of available packages. Keryx lets you do that on any computer.

---

### Post by RyuzakiTenseiga on 2010-07-07
so how do i get Keryx to work in windows 7 because I don't get it.

---

### Post by EXCiD3 on 2010-07-07
> **RyuzakiTenseiga said:**
> so how do i get Keryx to work in windows 7 because I don't get it.

First you create a project on your offline machine using Keryx on a flash drive, then you take the flash drive to your windows computer, and run Keryx.exe and open the project, download your packages, go back to your offline machine and use Keryx again to install them.

---

### Post by RyuzakiTenseiga on 2010-07-08
oh duh thanks.

---

### Post by EXCiD3 on 2010-07-08
> **RyuzakiTenseiga said:**
> oh duh thanks.

No problem, if you run into any problems or have some ideas for improvement let me know. :D

---

