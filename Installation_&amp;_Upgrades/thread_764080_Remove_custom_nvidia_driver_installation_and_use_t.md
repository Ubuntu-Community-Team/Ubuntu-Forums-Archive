---
title: "Remove custom nvidia driver installation and use the &quot;right&quot; way"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by zooounds on 2008-04-23
When I used Gutsy I had to remove the nvidia drivers installaed with apt and instead install the ones found on nvidias site. This because I needed the latest version for my GeForce 8800 GT.

Now with Hardy, I can use the apt drivers but I can't get it to work.

I have tried installing manually:

nvidia-glx-new

I have tried Envy.

Nothing works besides using the script from Nvidias site.

How do I reset everyting so it's the way it was menat to be in Hardy?

---

### Post by Lantesh on 2008-04-23
Did you try the newest version of Envy called EnvyNG?  The old version doesn't work with Hardy from what I understand.

---

### Post by martrn on 2008-04-23
> **zooounds said:**
> When I used Gutsy I had to remove the nvidia drivers installaed with apt and instead install the ones found on nvidias site. This because I needed the latest version for my GeForce 8800 GT.

Now with Hardy, I can use the apt drivers but I can't get it to work.
I have tried installing manually: nvidia-glx-new I have tried Envy. Nothing works besides using the script from Nvidias site. How do I reset everyting so it's the way it was menat to be in Hardy?

There is a nvida manual for ubuntu and how to do this.
[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

First ensure you donwnload the latest driver from nvidia.
Open a console and type :
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo apt-get uninstall --purge nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings
sudo apt-get remove --purge nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings
```
To backup your xorg config file, and remove the restriced drivers (necessary).

Then open a console and type :-
(one of the following to download the kernel headers)
```
sudo apt-get install linux-headers-386 
sudo apt-get install linux-headers-server
sudo apt-get install linux-headers-generic
```

depending on which kernel you are using type [COLOR="SeaGreen"]**uname -r**[/COLOR] to find out which kernel you are using.

Then open a console and type :-
```
sudo /etc/init.d/kdm stop
sudo sh NVIDIA*
// Answer the most likely answers
sudo /etc/init.d/gdm start
```
to run the shell script from nvidia and re-start gdm, change this to kdm if you are using kdm and the desktop manager.

This is all from memory try [https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")
for a more authoratitive report.

---

### Post by tyblu on 2008-04-23
The new version wasn't so hot, either, though it did get updated this morning...

[http://www.albertomilone.com/envyfaq.html#A](http://www.albertomilone.com/envyfaq.html#A)

---

### Post by zooounds on 2008-04-24
> **Lantesh said:**
> Did you try the newest version of Envy called EnvyNG?  The old version doesn't work with Hardy from what I understand.

I did

---

### Post by zooounds on 2008-04-24
> **martrn said:**
> There is a nvida manual for ubuntu and how to do this.
[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

First ensure you donwnload the latest driver from nvidia.
Open a console and type :
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo apt-get uninstall --purge nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings
sudo apt-get remove --purge nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings
```
To backup your xorg config file, and remove the restriced drivers (necessary).

Then open a console and type :-
(one of the following to download the kernel headers)
```
sudo apt-get install linux-headers-386 
sudo apt-get install linux-headers-server
sudo apt-get install linux-headers-generic
```

depending on which kernel you are using type [COLOR="SeaGreen"]**uname -r**[/COLOR] to find out which kernel you are using.

Then open a console and type :-
```
sudo /etc/init.d/kdm stop
sudo sh NVIDIA*
// Answer the most likely answers
sudo /etc/init.d/gdm start
```
to run the shell script from nvidia and re-start gdm, change this to kdm if you are using kdm and the desktop manager.

This is all from memory try [https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")
for a more authoratitive report.

Here you answere the opposit of my question.

I WANT to use the ubuntu package and not any file downloaded from the nvidia site.

---

### Post by zooounds on 2008-04-24
The hing is that I think the nvidia install script has left some files in my filetree that make it impossible to use the package nvidia-glx-new.

---

### Post by kpkeerthi on 2008-04-24
1. Change your driver to "nv" in xorg.conf
2. Install envy and run it. There is an option in its main menu to uninstall nvidia driver.
3. Reboot.
4. Now install the driver from System -> Admin -> Hardware Drivers
or 
```
sudo aptitude install nvidia-glx-new nvidia-settings
```

If you install from command line, be sure to enable it in xorg.conf

---

### Post by zooounds on 2008-04-24
> **kpkeerthi said:**
> 1. Change your driver to "nv" in xorg.conf
2. Install envy and run it. There is an option in its main menu to uninstall nvidia driver.
3. Reboot.
4. Now install the driver from System -> Admin -> Hardware Drivers
or 
```
sudo aptitude install nvidia-glx-new nvidia-settings
```

If you install from command line, be sure to enable it in xorg.conf

None of these ways work. Hardware drivers show no Nvidia at all.
I'm wirting that above. I'm searching for a way to remove any trace from nvidia drivers installed with apt and/or the nvidia installer.

When I think your suggestionwill work.

X says there is no valid nvidia driver.

---

