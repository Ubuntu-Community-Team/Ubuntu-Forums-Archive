---
title: "NVIDIA graphics card"
date: 2012-12-07
forum: Installation &amp; Upgrades
---

### Post by davejm73 on 2012-12-07
Hi

I would just like to find out of I should install NVIDIA. Im running 10.04.4 LTS. Ive had it on my system before upgrading and would like to find out if I should install it again?

If so..please can someone instruct me how to install and configure it.

Many Thanks
D

---

### Post by bogan on 2012-12-07
Hi!, **davejm73**,

If you had nvidia-current installed before you updated, it should have also been reinstalled automatically. If you had an Nvidia downloaded driver installed it would not have been, and your graphics would probably be a mess, or not available.

If the graphics are OK - including Videos - you probably do not need to install anything extra with 10.04 - 11.04 would be more demanding.

If graphics are not OK then run 'Additional Drivers' [ It may be called 'Additional Hardware' in 10.04], there may be an Icon in the top left toolbar, or look in 'System Settings'. It should offer Nvidia drivers and tell you if one is installed, if not, choose the 'updates' version, and click on 'Activate' if it is not in use.

From a Terminal: Please Post:```
 uname -ar
echo $DESKTOP_SESSION
lspci -nnk | grep  -iA3 vga
apt-cache policy nvidia-current
```

Chao!, **bogan.**

---

### Post by davejm73 on 2012-12-07
Thank you for the quick reply

I managed to download Nvidia current through Synaptic, but when I click on the icon in system > admin, I get this message: 

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

Can you instruct me on how to do this?

Many Thanks
D

---

### Post by bogan on 2012-12-07
Hi!, **davejm73**,

Did you reboot after downloading **and installing **nvidia-current.

I am not running a copy of 10.04 at the moment, and things are different in 12,10, so this may not work the same for you.

From a terminal run: ```
sudo nvidia-xconfig
```For me, that just creates a new config file - & backs up the old one if it exists.

Reboot, then run```
gksudo nvidia-settings
```Select 'Xserver Display Configuration' and if the resolution is what you want, select the " Save to X Configuration file " option , 'Quit' and reboot.

You may need to download the nvidia-settings file from Synaptic or use: ```
sudo apt-get install nvidia-settings
```Chao!, **bogan**.

---

### Post by grahammechanical on 2012-12-07
Have you just upgraded to 10.04? I have a lot of difficultly remembering back that far. I am not sure of what directions to give you because Ubuntu is now very different.

I think that you need to look for something called the Control Centre. In there you should find a utility to give you control over Appearance. You then select Enhanced graphics. That should download the Nvidia driver and install/activate it. That will give you a Nvidia Xserver settings manager. I think that is how it was done in the old days.

This advice is based upon memory and not research. It most likely will be inaccurate.

Regards.

---

### Post by davejm73 on 2012-12-11
Hi

When I add this in terminal, I get this response: 

sudo: nvidia-config: command not found

Not sure what to do as I have Nvidia, but cannot seem to set it up

thanks

---

### Post by bogan on 2012-12-11
Hi!,** davejm73,**

Edit:  The nvidia config command should have been: > sudo nvidia-xconfigSorry for the Typo.

Did you try: 
```
gksudo nvidia-settings
```It runs on my set- up even though Synaptic says it is not installed.

In 10.04, from memory, both 'Synaptic Package Manager' and 'NVIDIA X Server Settings' should be available in the System>Administration menu.

If it runs, select XServer Display Configuration in the Left side; on the right side there should be some options starting with 'Apply' and ending with 'Reset', between those should be two more, of which the second may be: 'Basic'.

If so, Click on 'Basic' and it will change to 'Advanced', Select the other 'Detect Displays' option. Then use the Drop-down menu of 'Resolution' to set it to either 'AUTO' or the resolution you want, then select 'APPLY' and 'Save Configuration'.
Then reboot.

Chao!,** bogan**.

---

### Post by dannyboy79 on 2012-12-11
> **davejm73 said:**
> Hi

When I add this in terminal, I get this response: 

sudo: nvidia-config: command not found

Not sure what to do as I have Nvidia, but cannot seem to set it up

thanksbecause it's suppose to be 
```
sudo nvidia-xconfig
```
Also, 10.04.4 they introduced the nouveau driver, check your /var/log/Xorg.0.log file and see what's in it as far as errors. I am guessing that you need to blacklist nouveau so that the nvidia driver module can be loaded. Does your xorg.conf file call for the nvidia driver?

---

### Post by bogan on 2012-12-11
Hi!, **dannyboy79**, 

Thanks for correcting my typo, I just realised my error, but you beat me to it.

Chao!, **bogan**.

---

### Post by davejm73 on 2012-12-13
Hi Guys

Thanks for all the help, but no Joy - still getting an error message, but luckily not the end of the world

D

---

### Post by bogan on 2012-12-13
Hi!,** davejmj73,**

Re **grahammechanical's** Post #5

In10.04, System Menu> Preferences>Appearance>Visual Effects, select from: "None" / "Normal" / "Extra", then "Apply" and Close.

"Extra" Effects is the equivalent of what became "3D".

Chao!,** bogan**.

---

### Post by dannyboy79 on 2012-12-13
> **davejm73 said:**
> Hi Guys

Thanks for all the help, but no Joy - still getting an error message, but luckily not the end of the world

Dwhat error are you getting? we'll need to see your /var/log/Xorg.0.log file to diagnos. Paste the output from the log at pastebin and then paste link here so we can see it all. I am guessing it's a module conflict (nouveau as I mentioned)

---

