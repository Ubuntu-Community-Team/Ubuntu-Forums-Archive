---
title: "Can not login to Desktop after upgrade to 23.10"
date: 2023-11-07
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2023-11-07
Sorry, the information here is going to be basic as I am on my Windows OS as the xUBUNTU will not open since my upgrade.

I upgraded yesterday, following the usual instructions.  Was straightforward and only two ineteruptions to ask me if I wanted to keep the same IME config and the same GRUB config.  I ket the later and went with the new former.  After a reboot the laptop gets the GRUB menu and I chose the new image and started to boot as normal.  The logo appeared, and then it went in to a command line for me to enter my username and password.

I can not fix things.  I've tried a CD, but that won't load.  I've tried looking at the logs but there is so much there it is meaningless to me and I can't paste here...
I tried using the recovery and tried to fix broken packages.  I noted a lot of NVIDIA drivers with dependecies unmet, along with many other things.

I checked within the Windows 11 OS and the two hard drives appear, and all the partitions.  Two are NTFS and can be opened by Windows and work.  The others can not but state HEALTHY.  However in the Ubuntu terminal when I type sudo umount -a I get errors.  UUID not found as an example.  Not sure how to mod fstab in a terminal

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293024&stc=1[/IMG]

MSI GF63 Thin 9RCX 15.6" FHD Laptop Computer Intel Core i7 9750H 256GB SSD GTX 1050 Ti

As I can not get in to report I can not send command responses.  I have to photo them and paste here.  See link.


[https://www.amazon.co.uk/photos/share/jZln00pK7QzIJl9GKpoEvvZlXDq0fZto2zVkKoFoLK8](https://www.amazon.co.uk/photos/share/jZln00pK7QzIJl9GKpoEvvZlXDq0fZto2zVkKoFoLK8)

---

### Post by MAFoElffen on 2023-11-07
At the Grub2 menu > Select "Advance Options: > Select and option that includes "Recovery". > At the Recovery Menu, select "network", then "root" > At the root prompt
```

apt update
apt list nvidia-driver* --installed

```
Write down the driver it said is installed. it will be in this format: "nvidia-driver-XXX". Lets say it said nvivia-driver-470, for example.

Then you would do
```

apt remove --purge nvivia*
# just an example of the driver version, which you would substitute with the version you found above
apt install -y nvidia-driver-470  
reboot

```

---

### Post by Claus7 on 2023-11-07
Hello,

the error message: array out of bounds, that you are having happened to me as well. This didn't result in unsuccessful login to ubuntu though. You should look elsewhere I guess, in order to see where the problem lies and which seems to be your graphics drivers.

Regards!

---

### Post by Jonners59 on 2023-11-08
> **MAFoElffen said:**
> At the Grub2 menu > Select "Advance  Options: > Select and option that includes "Recovery". > At the  Recovery Menu, select "network", then "root" > At the root prompt
```

apt update
apt list nvidia-driver* --installed

```
Write down the driver it said is installed. it will be in this format:  "nvidia-driver-XXX". Lets say it said nvivia-driver-470, for example.

Then you would do
```

apt remove --purge nvivia*
# just an example of the driver version, which you would substitute with the version you found above
apt install -y nvidia-driver-470  
reboot

```


Thank you.
Tried that.  Gave no Nvidia cards in list.  I tried a driver number I remembered from another posting and installed that instead.  Rebooted and still didn't work

I noticed a lot of threads with other issues I have like no Bluetooth.  Directories and hardware not found.  As mentioned the fastab doesn't work fully as directories and missing hardware.  I know they are there and not faulty as they appear in windows, the two hard drives work, but I can't open some of the directories as windows doesn't like ext4

Any other solutions, please?  All welcome.
I now suspect the directories/fastab is probably the 1st thing to fix.

---

### Post by Jonners59 on 2023-11-08
> **Claus7 said:**
> Hello,

the error message: array out of bounds, that you are having happened to me as well. This didn't result in unsuccessful login to ubuntu though. You should look elsewhere I guess, in order to see where the problem lies and which seems to be your graphics drivers.

Regards!

Thank you.
Graphics card, and other devices are an issue.  Seems to be a common issue with the last couple of upgrades.  I have another PC that started playing up in June due to incomplete upgrades.  Died in July and has been with a PC workshop since trying to fix it.  I have another that needs upgrading, but I am loathed to start it due to all these issues.  Not had this since about 2013.  There is clearly an issue with the processes and quality in the upgrade programe.  There are many blogs of failed upgrades just like mine.

---

### Post by Jonners59 on 2023-11-09
No progress.  Any other help PLEASE?

Here are some photos of the screen showing the logs.  I can't copy n paste them for obvious reasons.

[URL="https://www.amazon.co.uk/photos/share/LSF1UCvypJh3tA1skfWZ89PIlQewv4uIn0JzioZ9J73"]https://www.amazon.co.uk/photos/share/LSF1UCvypJh3tA1skfWZ89PIlQewv4uIn0JzioZ9J73


[/URL]

---

### Post by Claus7 on 2023-11-09
Hello,

are you sure that the upgrade went fine? I mean, it just finished and then system restarted or it finished with errors. My speculation is that some things were not installed correctly. The upgrade took place from which version to 23.10?

One idea would be while booting to fall under command line and try to upgrade your system. That way it might either install the packages that have missing dependencies or complete an unfinished installation.

So you could issue the command to upgrade anew your system or try sudo apt update, sudo apt upgrade in that order and see what you will get.

Regards!

---

### Post by Jonners59 on 2023-11-09
> **Claus7 said:**
> Hello,

are you sure that the upgrade went fine? I mean, it just finished and then system restarted or it finished with errors. My speculation is that some things were not installed correctly. The upgrade took place from which version to 23.10?

One idea would be while booting to fall under command line and try to upgrade your system. That way it might either install the packages that have missing dependencies or complete an unfinished installation.

So you could issue the command to upgrade anew your system or try sudo apt update, sudo apt upgrade in that order and see what you will get.

Regards!

Hiya Claus7
Well, yes, clearly it didn't upgrade correctly, but it certainly completed normally and showed zero errors.  It completed, asked to remove unwanted resources.  Then cleaned up and then asked if I wanted to reboot now.  All very normal.  After the reboot, it didn't work.  I had an issue with my PC too, earlier in the year and that is also still not working.  Same thing.  Normal update, but wouldn't work with USBs and later Network.  Seems there was a bug in the upgrade and a key package didn't install.  Found the package and that couldn't install, so it is now woith a local PC shop who've had it for 2 months.  There is defo a failing in the quality checking of the recent upgrades.  Not had issues like this since 2012/2013...

I agree that in the upgrade, certain packages have been missed off.  The dependencies probably and or configs/settings deleted.  I have tried the usual sudo update, sudo clean, sudo autoclean, sudo upgrade.... but they don't work either.  I do not know what is not working or what is missing to even start to rectify.

---

### Post by Jonners59 on 2023-11-09
YES, YES, YES!!!!  Sorted.

I was randomly playing and I got a warning that the "Display Environment" was missing.  Double-checked what it meant and as soon as I noted xUbuntu and XFCE, I rebooted in to "recovery".  Control+D, Selected "Turn on Network", then "Root" and ```
sudo apt-get update
```, ```
sundo apt-get clean
```, ```
sudo apt-get autoclean
```, ```
sudo pat-get autoremove
```, ```
sudo apt-get install xfce4
``` and then ```
sudo apt-get install xubuntu-desktop
```.  That latter threw up a choose "Display Manager"; "gdm" or "LightDim"?  I chose GDM, but not sure of teh differences, but I do recall that a few years ago one gave issues.  So need to recall which and learn how to switch.  After completing the install, I then did, ```
sudo apt-get install gnome-software
```.  None of these threw up errors, other than xfce was already installed.

This must mean that during the upgrade the XUbuntu was removed and not replaced, or at least it was not configured to switch to an alternative.  The laptop was rebooted.  Took a while but soon I had my log-in again, with chooser.  Although a different appearance.  Logged in, a bit slow.  But after a couple of reboots it has sped up and all is right with the world.

Thank you to all those who looked in and especially [QUOTE=Claus7;14164694][\Quote] and [QUOTE=MAFoElffen;14164481][\Quote]

Hope this helps someone else.

---

