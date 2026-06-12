---
title: "upgrade just one package"
date: 2005-06-23
forum: Installation &amp; Upgrades
---

### Post by edemark on 2005-06-23
Hi all

I was trying to install splashy to have boot splash. I have downloaded the packages lib++dfb-0.9-22-1_i386.deb
libdirectfb-0.9-22_0.9.22-1_i386.deb
splashy_0.1-5_i386.deb

To be able to install splashy first i would need to install the 2 lib files as splashy is based on them. Now I have an install based on the download iso and on the unofficial download extra cd. This secon installed mplayer (working :) based on an earlier version of libdirectfb and when i try to uninstall this libderectfb to ba able to use the new version it indicates in synaptics that it will remove mplayer mplayer-fonts and mozilla-mplayer plugin. 
Thus my question is if it is possible Upgrade (not uninstall the old version and reinstall the new one) just the libdirectfb package?

Please help
thanks 


pd at work I have uninstaled mplayer packages (as there i supposed to work) and installed splashy. Now splashy works (nice) but i am not able to reinstall mplayer OK at work it does not matter but at home

---

### Post by Xian on 2005-06-23
[QUOTE=edemark]This secon installed mplayer (working :) based on an earlier version of libdirectfb and when i try to uninstall this libderectfb to ba able to use the new version it indicates in synaptics that it will remove mplayer mplayer-fonts and mozilla-mplayer plugin. 
Thus my question is if it is possible Upgrade (not uninstall the old version and reinstall the new one) just the libdirectfb package?[/QUOTE]
The dpkg function is "upgrade smart" in that when you tell it to install a package it automagically knows if this means it will involve an upgrade. So, really all you need to do is place these packages in your /home directory and then issue the dpkg install command. The upgrade will proceed unless there are other library version issues.

Let's try one. Move the libdirectfb-0.9-22_0.9.22-1_i386.deb package to your /home folder. Now open a terminal (Applications > System Tools > Terminal) and issue the command below. Does it install the package?
```
$ sudo dpkg -i libdirectfb-0.9-22_0.9.22-1_i386.deb
```

---

### Post by edemark on 2005-06-23
Hi Xian 

I have tried what you suggested. Though I am not certain that dpkg is "update-smart" as you state. I am saying that just because i now hav two libdirectfb packages installed on the system. However both of them works. I mean mplayer still works and now splashy  also works. So eveythings just fine, nice splash screen almost perfect. It is olny almost as I have an error in setting up general console fonts that puts me back to text mode. 

So suming it up 
Thank you wery much for the help it worked out

pd if someone knows how to get rid of this:
*setting up general console font ...
*t_kernel_font: Invalid argument                           (fail) 

please help again

---

### Post by Xian on 2005-06-23
I'm glad that you got splashy running, but as for the font issue you might want to start another thread and address this problem as a new topic. The forum is very busy and it is generally best to keep threads to a specific subject.

---

### Post by edemark on 2005-06-23
I just find on an other post that someone had this font config problem so i will try suggestions of that post 

So just thanks

---

