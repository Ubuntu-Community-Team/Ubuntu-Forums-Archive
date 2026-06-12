---
title: "Basic ATI question"
date: 2012-11-04
forum: Installation &amp; Upgrades
---

### Post by Moofy on 2012-11-04
So I got a **ATI Radeon HD 5670 graphics card**, i hear a lot about it being non-supported. Well, i run like 27 FPS in basic games like Minecraft, i really like Linux but i couldn't resist going back to Windows just for this, i atleast wan't to pay Minecraft at 60-70 FPS, on Windows i get like 120 FPS.

What is possibly wrong?

---

### Post by Mark Phelps on 2012-11-04
We're not mind readers here!  

How about at least telling us the following:

1) Which version of Ubuntu are you running?

2) Are you running the open-source Radeon drivers, or the Restricted AMD drivers?

---

### Post by Moofy on 2012-11-04
Oh yea sorry, I'm running Ubuntu 12.10 64bit desktop, and I am not quite sure about the second question. All I've tried was to go to software sources and change to a propriety driver, both. Still no good FPS. I am no computer expert unfortunately.

---

### Post by Mark Phelps on 2012-11-05
The GOOD news is that your AMD chipset is SUPPOSED to work under 12.10 with the new AMD drivers.

Tha BAD news is that everyone is having driver problems with those in 12.10.

I've read that the 12.11 Beta drivers are SUPPOSED to be OK, but as I have one of the NOW unsupported AMD chipsets (4290), I can not test them.

I think the driver version in the Software Center is 12.8 or something like that  You should see if you can get the 12.11 beta drivers.

Also, would be a good idea to check over in the Phoronix forums -- as they do a lot of testing with AMD drivers -- to see what is the most current version.

---

### Post by marin123 on 2012-11-05
I have Radeon 5650 and I was using AMD proprietary drivers from their website.

I recommend installing the driver from here:
[http://support.amd.com/US/GPUDOWNLOAD/Pages/index.aspx](http://support.amd.com/US/GPUDOWNLOAD/Pages/index.aspx)

Choose your settings, download the driver.

After downloading, open terminal, go to directory where your file is downloaded, ie.
```
cd Downloads
```

Then run

```
./ati_driver_filename.sh
```

obviously, with the name of the file. TIP: type ./ati and press TAB to autocomplete filename.

Then wait a bit for installer to load and follow the installer.

IMPORTANT: Uninstall proprietary driver before doing this or you might run into trouble.
ALSO IMPORTANT: I don't know how is this now, since I am using open-source drivers, but when I was using prop. drivers, Xorg update caused trouble.
Before updating Xorg, you should run uninstall script for the driver and repeat this procedure.

---

### Post by Moofy on 2012-11-05
> **marin123 said:**
> I have Radeon 5650 and I was using AMD proprietary drivers from their website.

I recommend installing the driver from here:
[http://support.amd.com/US/GPUDOWNLOAD/Pages/index.aspx](http://support.amd.com/US/GPUDOWNLOAD/Pages/index.aspx)

Choose your settings, download the driver.

After downloading, open terminal, go to directory where your file is downloaded, ie.
```
cd Downloads
```

Then run

```
./ati_driver_filename.sh
```

obviously, with the name of the file. TIP: type ./ati and press TAB to autocomplete filename.

Then wait a bit for installer to load and follow the installer.

IMPORTANT: Uninstall proprietary driver before doing this or you might run into trouble.
ALSO IMPORTANT: I don't know how is this now, since I am using open-source drivers, but when I was using prop. drivers, Xorg update caused trouble.
Before updating Xorg, you should run uninstall script for the driver and repeat this procedure.

So how would I go about uninstalling so I can do what you told me on the installing procedure?

---

### Post by marin123 on 2012-11-06
Go to Additional drivers and "Deactivate" ATI driver (if any).

If you didn't have the driver activated, run 
```
sudo apt-get remove fglrx
```
just to be sure.

Then do the procedure to install the driver.

Note: to uninstall ATI driver (you downloaded) run 
```
sudo sh /usr/share/fglrx/fglrx-uninstall.sh
```

You should do that before installing new driver, and before Xorg update, just to be sure.

---

### Post by Moofy on 2012-11-06
> **marin123 said:**
> Go to Additional drivers and "Deactivate" ATI driver (if any).

If you didn't have the driver activated, run 
```
sudo apt-get remove fglrx
```
just to be sure.

Then do the procedure to install the driver.

Note: to uninstall ATI driver (you downloaded) run 
```
sudo sh /usr/share/fglrx/fglrx-uninstall.sh
```

You should do that before installing new driver, and before Xorg update, just to be sure.

Why would i uninstall the driver I just installed with that .sh terminal command? That makes no sense to me.

Also will this be the same procedure in Xubuntu, and if i change my DE my settings would remain the same right? (if i shhift to MATE or something)

---

### Post by marin123 on 2012-11-06
You only need to uninstall before you install new driver (with sh command). I wrote it in case you need to uninstall.

Installer is Linux related, not DE related. Works everywhere :)

---

### Post by Moofy on 2012-11-11
Okay so what I've done is install Ubuntu 12.04 LTS, wen't to additiopnal drivers and selected the FGLRX not post release updates and everything was fine.

Now I'm sitting on Xubuntu because i wanted XFCE without installing a DE on top of anything. I did the exact same thing and i only strike around 43 FPS in Minecraft, i got my AMD control center but i didn't touch anything.

:(

---

