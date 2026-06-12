---
title: "ibex freezes after login :fresh install"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by megazerg on 2008-11-04
so i installed the ibex with a flash frove (no cdrom ) , 
Im using an ibm x30
now after the setup is complete . i log in , 
ibex freezes and i can move the mouse, i have a nice creamy brown screen with nothing on it
, 
Ive tried to reboot it does the same, also i have checked the packages on the safe mode option

game over , what can i do , 

thanks for your reply in advance, :)

---

### Post by theuion on 2008-11-05
I have the same problem with a CDROM on my x30.  Was running heron fine.  Will post if I find a fix.

---

### Post by abn91c on 2008-11-05
from a root console you may need to remove compiz or metacity then log in and turn off desktop effects. reboot to safe mode to do that. sudo apt-get remove compiz(metacity) if that is what you had then reinstall. accept all the defaults then do compiz --replace or metacity --replace whatever your case may be then log in. you should be able to get to the normal desktop then turn off desktop effects

---

### Post by vtom80 on 2008-11-06
I have the exact same problem on an ACER TravelMate 4001WLMi. After logging in I'm still able to move the mouse, but that's all. Now even with the live CD I get the same behavior, which I didn't have at the time I installed ubuntu 8.10. Weird...

I tried the suggestion of removing compiz. At the login screen I open a terminal by CTRL-ALT-F5 and log in. Next:

```

sudo -s
sudo apt-get remove compiz
sudo apt-get remove compiz-core

```

After this, I was able to log in back to GNOME (pres CTRL+ALT+F7, and log in)
But trying to shut down the system again freezes the system as before: you can still move around the mouse, but you cannot do anything else (not even CTRL+ALT+BACKSPACE to log off). After a manual reboot I checked the system log files and nothing special is found, actually the kernel is still alive, but I believe X has frozen. 

I really would like to get this problem solved, and I believe it was a big mistake to include 3D effects by default in the Ubuntu 8.10 distribution. Is there someone that can tell me how I can disable them fully, because I do not believe in the necessity to have all those fancy 3D effects, especially not at the cost of crashing the system all the time. A system that runs all the newest applications without hanging would be appreciated much more than a system that is fancy but unreliable, just like all windows systems...

---

### Post by vtom80 on 2008-11-07
Update:

I have been investigating several possibilities to solve this problem. One of the most interesting ones is the acpi story. However, I messed up my ATI driver while trying another possibility and finally I decided to go back to Hardy. My surprize was big when I found out Hardy had the same problems (even with the live CD).

But for Hardy I was able to fix it. First, to solve the problems of the freeze during the installation of 8.04.1 (but possibly also of 8.10) at boot time, instead of direclty lauching the live CD, press F6 to edit the boot options. Add

```

acpi=off

```

at the end of the line. It should look like:

```

file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash acpi=off

```

Press enter and the system will boot. Here you have the chance to investigate the stability of your system, e.g. if similar situations happen such as a freeze but when you are still able to move the mouse pointer. (be aware of the fact that everything is a little bit slower since it is on a live CD).

If everything remains stable, you might consider installation. After the installation you need to modify as well the boot options to get the acpi=off included.

This goes in two steps:

At the first time booting, GRUB comes up with a menu to select the OS to load. Press 'e' to edit the current line (default kernel). Move the focus down by one (press arrow down) to edit the kernel settings. Press 'e' again and append the line with

```

acpi=off

```

Press ESC, followed by 'b' to boot this kernel.

Now we need to make this acpi=off default at load time (step 2). For this we need to edit the grub menu list. Open a terminal and type:

> 
sudo gedit /boot/grub/menu.lst


enter your password

Now for each entry of the kernel in this file you need to append the acpi=off option 

for instance:

> 
kernel           /boot/blablabla root=blabla ro quiet splash


should become

> 
kernel           /boot/blablabla root=blabla ro quiet splash cpi=off


Save this file and you're done. Now each time you boot the acpi=off will be present. Remember well to append this option each time a newer version of the kernel gets installed.

The acpi is the Advanced Configuration and Power Interface and is some kind of standard for the communication and monitoring with hardware. Setting it off will not allow you to see the battery charge status for instance. You could sen debug reports in order to solve this problem, see [DebuggingACPI]("https://wiki.ubuntu.com/DebuggingACPI").

This helped me at least in Hardy, for Ibex it didn't so well, but this could have been due to other reasons (I messed up some things during my search to solve the problem). Maybe it helps someone. Posts and replies if this does (not) work are most welcome.

---

### Post by vtom80 on 2008-12-13
Update:

Disabling acpi has some consequences: the wireless card is not activated at start-up, available battery power is not shown (giving no warnings when few energy is left, causing the system to turn off abruptly...), no automatic switch off of the computer, requiring still a press on the shut-down button after ubuntu has been closed down, all other systems, such as the cooling fan do not work properly, ... It gave me a headache. Finally I found a solution for all this pain. After all, I figured out that for my system the problem could not have been acpi, as it was working for previous versions of ubuntu. There must have been something else that was changed in the kernel since then, that was not supported on my system. Finally I tried what was suggested in [this]("http://ubuntuforums.org/search.php?searchid=53067270") thread and it worked! Basically, use the same guide as described before, but change the "acpi=off" by "nohz=off" and all problems and frustrations are gone!

I hope this helps other people in the same situation!

---

