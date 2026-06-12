---
title: "Which Ubuntu CD/USB image includes wireless for DLink WDA-2320 PCI ?"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by NamaeKana on 2010-09-23
I had a Ubuntu USB key that booted x64 and brought up the wireless network mgr with DLINK WDA-2320. But it was lost.

Now I am trying different distro images to get back to what I had. But none has the Network mgr with wireless in it.

I don't have any other Linux/UNIX machine here at home. Just Winbloze.

Do you know which Ubuntu CD/USB image comes with a network manager and wireless for DLink WDA-2320 PCI ?

---

### Post by mikewhatever on 2010-09-23
I am afraid none of the Ubuntu images have that driver, since it is a restricted/non-free or what not one. According to [this list]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCI") the chipset is that of Atheros, and the driver should be available through System->Admin->Hardware-Drivers.

---

### Post by NamaeKana on 2010-09-23
So there's no distro with the DLink WDA-2320 PCI on it already. That driver was on the USB key I had. I'm not a heavy Linux person and didn't install it there. There IS a distro image with it, but maybe from one of the USB Key Making downloads or something. I tried unetbootin's Ubuntu Live distros but none of them have it. Oh well, I know how to to dpkg to install mt-st, looks like I'll have to learn to install a driver on an Ubuntu system without the luxury of a live internet connection.

---

### Post by sikander3786 on 2010-09-23
USB key making software and Unetbootin download from the same source i.e, ubuntu.com and the same image that is burnt on CDs so I don't agree if it was present in one of them. There is a possibility that you were using some derivative of Ubuntu like Ultimate Edition (don't know if even that one includes the drivers) or a custom built distro that contained the driver.

Installation will not be that much easy without an internet connection. It will be better if you could connect it via cable and install the drivers.

---

### Post by NamaeKana on 2010-09-23
OH. I know what to do next.

On my recent Tosh Notebook, I'll load the latest Ubuntu live on the USBKey, boot it on same, install the DLink driver

Then put the USBKey on my Desktop/DLINK

That should work

---

