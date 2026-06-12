---
title: "need help installing 3d drivers and such"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by yowshi on 2007-11-05
ok so i managed to fix my basic display now i am needing help to get 3d acceleration enabled without messing up my xorg.xconf. i just spent an entire evening booting rebooting and restating X because i tried to install the restricted drivers (from ubuntu's restricted driver menu for nvidia drivers) and instead of helping it fragged my xorg.conf. from what i remember it was one hell of a hassle to get this working in fiesty but i dont remember the steps i was told to take to make it work

---

### Post by carlinuxlearner on 2007-11-05
Try this, (I made it)  (assuming you have a Nvidia graphics card)

HOW TO: install your Nvidia driver in Ubuntu 7.10

(Please MAKE SURE with ANY commands (or path names) that you capitalized what I capitalize!!!! This is VERY important!)

I will start by giving you two options. Both options require that you have a internet connection of some kind. (preferably high-speed)

Option #1. Install your Nvidia driver with "Envy"
(usually MUCH easier then installing the driver the manual way)

OR

Option #2. Install your Nvidia driver manually. (use this if Envy won't work)


If you choose Option #1 "Install your Nvidia driver with "Envy"" Then please proceed from here on.

1.1
Go to your (System>>Administration>>Software Sources) make sure you have all your repositories enabled. (Check mark them all)

Download "Envy" to your Desktop (to make thing easy) [http://albertomilone.com/ubuntu/nvid...untu10_all.deb](http://albertomilone.com/ubuntu/nvid...untu10_all.deb)
(if this link does not work, just visit this web site and download the latest version [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) )

1.2
Double click on the file you just downloaded and tell it to install

1.3
If all those steps went well then Envy should be installed and you should be able to find it in (Applications>>System tools), just run it and you should be able to install your driver all by your self very easily.


Option #2.

2.1
Open up a terminal window (Applications>>Accessories>>Terminal) type this in "sudo apt-get install build-essential"


2.2
In a terminal window type "lspci | grep VGA" find the part that has these around it "[ ]", write down what it says then go here
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)
If the name of your graphics card is in the list (such as "Geforce 6800") then download this driver to your Desktop
[http://us.download.nvidia.com/XFree8...14.19-pkg1.run](http://us.download.nvidia.com/XFree8...14.19-pkg1.run)
(if that link is old go to this page to get driver)
[http://www.nvidia.com/object/linux_d...100.14.19.html](http://www.nvidia.com/object/linux_d...100.14.19.html)
(if that link is old, go here and select the driver that starts with "100")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html).


(EXAMPLE

"carl@carlubuntu1:~$ lspci | grep VGA
01:0b.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
carl@carlubuntu1:~$"

The "GeForce4 MX 420" is the name you are looking for. So "GeForce4 MX 420" is what I would look for on the list here.
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

end of example)

2.3
IF YOUR GRAPHICS CARD NAME IS NOT ON THAT LIST look and see if it's on this one
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

If it was in the "The 1.0-96xx driver supports the following set of GPU" section, then download this driver to your Desktop
[http://us.download.nvidia.com/XFree8...43.01-pkg1.run](http://us.download.nvidia.com/XFree8...43.01-pkg1.run)
(If that link is old then go here)
[http://www.nvidia.com/object/linux_d..._96.43.01.html](http://www.nvidia.com/object/linux_d..._96.43.01.html)
(If that link is old go here and select the driver that starts with "96")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

If you graphics card name was in the "The 1.0-71xx driver supports the following set of GPUs" section,
then download this driver to your Desktop.
[http://us.download.nvidia.com/XFree8...86.01-pkg1.run](http://us.download.nvidia.com/XFree8...86.01-pkg1.run)
(If that link is old go here)
[http://www.nvidia.com/object/linux_d..._71.86.01.html](http://www.nvidia.com/object/linux_d..._71.86.01.html)
(If that link is old go here and select the driver that starts with "71")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)


2.4
Print out this page!

2.5
Restart your computer! At the Grub boot menu (if it doesn't pop up click ESC before it's to late) and select the "recovery mode" kernel, and hit enter!

2.6
Once booted, type in "sh /home/yourusername/Desktop/NVIDIA" but DON'T HIT ENTER!!
(replace "yourusername" with your user name)
click the TAB button on your key board twice, and it should fill out the rest of the name for you,
THEN hit enter.

2.7
The installer will ask you some question (don't worry if it says your in "runlevel 1" it doesn't matter) just make sure you answer all the questions so that it will continue the installation process.

2.8
Once the installer is done restart your computer by pressing CTRL+ALT+DELETE, boot up normally. And your Nvidia driver should be installed!

TROUBLE SHOOTING

If you have problems installing "Envy" ether ask about it on the forums, or just do Option #2.

If (in Option #2) when you reboot you get a black screen don't worry it can be fixed!
Just press these keys ALT+F2 and then type this in at the command prompt "sudo nano -w /etc/X11/xorg.conf"
Find the part of the file that says "Device", find "Driver "nvidia"" change "nvidia" to "nv".
Press ALT+X and save the file.
Restart your computer, try installing it again, or ask about it on the forums. (When asking on the forums, error messages are VERY helpfull please write down, or copy any you get)

C@RL

Any one is welcome to correct me on any thing!

---

### Post by yowshi on 2007-11-06
envy definitely solved my problem. thanks

---

