---
title: "NOTHING fixes my volume control problem since i upgraded from 7.10 to 8.04"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by ayeshap on 2008-06-26
i upgraded from 7.10 to 8.04 a few days ago and since then i have been trying EVERYTHING to fix my 'no volume control gstreamer plugins and/or devices found.' problem.

i have tried this [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade)

i have tried this [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

i have tried this [http://ubuntuforums.org/showthread.php?t=543793&page=2](http://ubuntuforums.org/showthread.php?t=543793&page=2)
after i did step 3 of this solution in the terminal , this came up
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libncurses5-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  libenca0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

am i supposed to do something else from here? i know absolutely NOTHING about computers btw.

i do know that when i put uname -r into the terminal, this kernel comes up
2.6.24-18-generic
also i am using a dell inspiron 1525.

one last thing, i know that to check to see if ubuntu is still seeing your sound card u can skim through the device manager which u get to System --> Administration --> Device Manager.

however, i go to System --> Administration and then there is nothing called Device Manager and i dont know how to find it.

---

### Post by eryksun on 2008-06-26
> **ayeshap said:**
> i do know that when i put uname -r into the terminal, this kernel comes up
2.6.24-18-generic
also i am using a dell inspiron 1525.

Do you have no audio at all? Have you not had any audio since upgrading? My version of Hardy shipped with kernel version 2.6.24-16-generic. Did you get a kernel upgrade and somehow not get the associated kernel modules? Try the following command:

```
ls -la /dev/snd 
```

If it doesn't list some sound devices, you may not have the kernel modules installed to properly access your sound system. Try the following command:

```
dpkg -l linux-ubuntu-modules-`uname -r`
```

This checks to see that you have the modules package installed for your currently running kernel. If it says "No packages found", install the modules package with the following command:

```
sudo apt-get install linux-ubuntu-modules-`uname -r`
```

Reboot.

---

### Post by eryksun on 2008-06-26
If the above doesn't work you should make sure your user account has access to the audio devices, which are in the 'audio' group. Just enter the command 'groups' at the command line. It will come back with a list of groups your account belongs to. If 'audio' isn't in the list, add yourself to that group with the following command:

```
sudo usermod -g $USERNAME -a -G audio $USERNAME
```

$USERNAME is a shell variable that simply equals [gets replaced with] your actual user name. Make sure to paste this command exactly as above. For example, if the -a (append) option is missing, you'll be removed from every group except for your default $USERNAME group and 'audio', which would be bad.

Reboot.

---

### Post by ayeshap on 2008-06-26
ok so i just realised, after much days of stress, that when i boot with kernel version 
2.6.24-18-generic i have absolutely no sound but when i boot with 2.6.24-16 sound works.
however this requires me to boot in 2.6.24-16 EVERYTIME i start my laptop...
is there anyway to fix this to make it so i stay in 2.6.24-16?

---

### Post by eryksun on 2008-06-26
> **ayeshap said:**
> ok so i just realised, after much days of stress, that when i boot with kernel version 
2.6.24-18-generic i have absolutely no sound but when i boot with 2.6.24-16 sound works.
however this requires me to boot in 2.6.24-16 EVERYTIME i start my laptop...
is there anyway to fix this to make it so i stay in 2.6.24-16?

Sure, just run the startup manager, available from the menus at System->Administration->Startup-Manager. The first tab, Boot options, lets you choose the default kernel to load. 

Hopefully your module situation will be straightened out with 2.6.24-19.

---

### Post by ayeshap on 2008-06-26
[QUOTE=eryksun;5267796]Sure, just run the startup manager, available from the menus at System->Administration->Startup-Manager. The first tab, Boot options, lets you choose the default kernel to load. 


when i go to System->Administration i actually dont have an option called Startup-Manager.
i have Authorizations,Hardware Drivers,Hardware Testing, Language Support,Login Window, Network, Network Tools,Printing, Services, Software Sources, Synaptic,System Log, System Monitor,Time and Date, Update Manager, Users and Group.

would i be able to change it from any of those?

---

### Post by eryksun on 2008-06-27
> **ayeshap said:**
> when i go to System->Administration i actually dont have an option called Startup-Manager.
i have Authorizations,Hardware Drivers,Hardware Testing, Language Support,Login Window, Network, Network Tools,Printing, Services, Software Sources, Synaptic,System Log, System Monitor,Time and Date, Update Manager, Users and Group.

would i be able to change it from any of those?

Try the following command to load the startup manager:

```
gksu /usr/sbin/startupmanager
```

---

### Post by ayeshap on 2008-06-27
that didnt work either...i still cant find it but thanks for all your help..i guess i just gotta go to that grub thing everytime i start my laptop.

---

### Post by eryksun on 2008-06-27
> **ayeshap said:**
> that didnt work either...i still cant find it but thanks for all your help..i guess i just gotta go to that grub thing everytime i start my laptop.

It's just not installed. I should have checked first to see if it's a default program. Anyway, you can install it with

```
sudo apt-get install startupmanager
```

The other alternative is manually editing /boot/grub/menu.lst, but it's better to stick with GUI tools if you're not experienced.

---

### Post by ayeshap on 2008-06-28
YAY!! that worked...thanks so much! lol i have no idea what GUI tools are btw...i feel way too inexperienced to be using this system...

---

### Post by eryksun on 2008-06-29
> **ayeshap said:**
> YAY!! that worked...thanks so much! lol i have no idea what GUI tools are btw...i feel way too inexperienced to be using this system...

You're welcome. GUI stands for Graphical User Interface. In other words, with a GUI you control the computer using a mouse with icons, buttons, drop-down boxes, etc, as opposed to a CLI, Command Line Interface, where the computer is controlled with text commands you type in a terminal (or terminal window). A GUI is more intuitive, but limited. A CLI requires the user to read a lot and memorize commands, but it offers a finer level of control. Linux commonly uses both, even for end users, while Windows tries to do almost everything in the GUI. 

Ubuntu is a great system to learn to use Linux. It's much better than back when I first started on Slackware Linux in 1996, for which almost everything had to be compiled from source code and manually set up in text configuration files. Some of that is still with us, but it's like night and day in comparison.

---

