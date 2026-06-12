---
title: "Need help with nvidia 8800 GTS drivers"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by kreeten9996 on 2008-11-04
Hi everybody, Im new to this linux thing. I have been trying to get compiz and dual screens to work on my computer, but none of that can happen till I install the drivers for my graphics/video card. I have installed envy but when it tries to install my drivers a message comes up saying,

"There was an error in the installation process. You can see the log file /var/log/envy-installer.log"

When i type in the log file, it says that there is no such file in the directory. CAN SOMEONE PLEASE HELP

Computer specs.

intel core 2 duo extreme 3.0 GHz
asus nvidia 8800 GTS 512 Mg
EVGA 780i motherboard

---

### Post by Pumalite on 2008-11-04
Have you tried 'Hardware Drivers'?

---

### Post by Pumalite on 2008-11-04
You need:
sudo apt-get install build-essential
Add this for good mesure:
sudo apt-get install linux-headers-`uname -r`

---

### Post by Pumalite on 2008-11-04
And this:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by kreeten9996 on 2008-11-04
ya i did, it just freezes at o percent when i try to download the driver

---

### Post by Pumalite on 2008-11-04
Check your Internet connection

---

### Post by kreeten9996 on 2008-11-04
hey thanks for all the help, but i went on the nvidia site and found out that they also dont make a driver that works with the 8800 gts, guess i just need to get a different card

---

### Post by Partyboi2 on 2008-11-04
It looks like there is a problem with the nvidia site when trying to downlod drivers.
[[COLOR=Blue]This[/COLOR]]("http://www.nvidia.com/content/DriverDownload/download_confirmation.asp?url=http://us.download.nvidia.com/XFree86/Linux-x86/177.80/NVIDIA-Linux-x86-177.80-pkg1.run") should be the correct one for you to download

---

### Post by kreeten9996 on 2008-11-05
hey thanks, i downloaded the driver but when i click on the icon on my desktop it says

"Could not open the file /home/paolo/Desktop/NVID&#8230;Linux-x86-177.80-pkg1.run using the Western (ISO-8859-15) character coding. Please check that you are not trying to open a binary file.
Select a different character coding from the menu and try again."

is not supposed to happen or am i supposed to open the file a different way?

---

### Post by Partyboi2 on 2008-11-05
To manually install the driver, Open a shell (Ctrl_Alt+F2) and login then install what Pumalite has posted in his post, then  stop gdm
```
sudo /etc/init.d/gdm stop
```
then start the installer
```
sudo sh /home/paolo/Desktop/NVIDIA-Linux-x86-177.80-pkg1.run
```
Once it has finished installing you can start gdm again by
```
sudo /etc/init.d/gdm start
```

---

### Post by kreeten9996 on 2008-11-06
Hey, I did what you said. After putting the install code it said it could not open the file. did it multiple times and came up with the same thing. if you have any other ideas that would be great if not, thanks for all the help.

---

### Post by Pumalite on 2008-11-06
Be careful with your path. Where do you have your driver? Also be careful with the spelling of the driver.

---

