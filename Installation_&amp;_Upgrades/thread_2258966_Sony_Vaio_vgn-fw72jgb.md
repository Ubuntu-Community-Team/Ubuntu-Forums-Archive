---
title: "Sony Vaio vgn-fw72jgb"
date: 2014-12-31
forum: Installation &amp; Upgrades
---

### Post by MibunoOokami on 2014-12-31
Happy New year everyone!

I probably should have put this in my other 14.04 thread a while ago but didn't since it involves a different computer.

When I installed 14.04 on my main work horse laptop several months ago, I encountered a problem where I get to the login screen, enter my password and... That's it, it gets stuck at the splash screen I think it's called. I did try fixing the problem at the time by following a number of instructions in various threads but none the solutions of the solutions worked, so I simply swapped out the HDD and went back to 12.04 (or 12.10) thinking that maybe if I wait awhile perhaps I can update the software using tty1 and the problem might be solved.

Today I put the drive back in the laptop and used tty1 and did 
```
sudo apt-get update 
sudo apt-get upgrade
sudo apt-get autoclean
sudo apt-get autoremove

```
then I rebooted and nothing had changed. I searched for new threads to fix the problem, the most promising one (I can't find right now) said to install xauth, xorg and a bunch of others (these are off the top of my head at the moment and might not be the correct programs) everything is apparently the latest version except a program called fxlrg which terminal says there is no such file or directory (or couldn't locate).

I went in to tty1 again and suddenly have this message ```
[61.916026] Corrupted low memory at ffff88000000be38 (be38 phys) = b036000400000000 [61.916555] Memory corruption detected in low memory
```

My guess is the corrupted memory error is more serious than not being able to use the OS, but can anyone tell me how my memory suddenly became corrected and if there is a fix other than buying new RAM? And after that, where can I find and install fxlrg?


Thanks in advance for your help.

EDIT: I've just remembered, after I put the HDD back in and booted up, I think it was before the login screen there was a brief error message about resolution and something to do with having no $display X11. I googled how to install $display X11 and followed [this]("http://askubuntu.com/questions/213678/how-to-install-x11-xorg") thread. It is the 4[SUP]th[/SUP] post which says about installing fxlrg, xserver-xorg-core, xserver-xorg, xorg, xorg openbox and ubuntu-desktop. Everything is already installed and the latest version except fxlrg. 

 Incidentally, when I logged into tty1 for the second time just before getting the corrupted memory message, there was another message on screen saying there are 11 (security) updates available. Even though I had run the update and upgrade commands.

---

### Post by ubfan1 on 2015-01-01
Did you ever run the memory check from the installation live media?  Do you mean fglrx, the amd graphica driver? look for the "Additional Drivers" from the dash button, and see what's offered.

---

### Post by MibunoOokami on 2015-01-01
Hi ubfan1, I think I would have run memory check years ago at a different distro like 10.04/10.10 or less but nothing recently. The [thread]("http://askubuntu.com/questions/213678/how-to-install-x11-xorg") I linked has it as fxlrg could be a type and might explain why it can't be found. It is for amd graphics card. I don't have a dash button or any other unity related options, all I can see is my wallpaper after entering my password.

Thanks

---

### Post by MibunoOokami on 2015-01-01
Ubfan1, it was a typo in that thread and it was as you asked fglrx, but that is the newest version too.

---

### Post by ajgreeny on 2015-01-01
We really need to know what hardware you are using; do you have an AMD/ATI graphics card, and if so which one is it?

Lets see the output, from a command line if necessary, of the command **lspci**.

You can get to a command line by pressing **Ctrl+Alt+F1** at the point where you have only your wallpaper showing, then login with username and password (password will not show on screen).

---

### Post by tokyobadger on 2015-01-01
Append the following to your boot parameters
```
memmap=64K$0 memory_corruption_check=0
```
[more info here](https://bbs.archlinux.org/viewtopic.php?pid=1473156)
Your RAM is most likely fine - to get further help you should do as ajgreeny advises

---

### Post by grahammechanical on 2015-01-01
There seems to be more than one problem. which makes for confusion.

As pointed out earlier, we can use the Ubuntu live session to do a memory check. At the first purple screen press Enter, then select the language. At the underlying screen we will see these options

> Try Ubuntu without installing
Install Ubuntu
Check disc for defects
Test memory
Boot from first hard disk


You may be having proprietary video driver problems. There are a couple of things you can try. After login in and at that screen that does not have the launcher, the dash or the top panel, Right click the desktop. You may get a menu with an option to Change Desktop Background. That will open System Settings at the Appearance utility. From there you can get the the Software and Updates utility and on its Additional Drivers tab you can change video drivers. You might want to try the open source video driver which is called "radeon" for AMD cards and Nouveau for Nvidia cards. There should also be about 4 different versions of the AMD/ATI proprietary video driver to experiment with.

Ubuntu also has a Recovery mode. We access it by choosing Advanced Options for Ubuntu at the Grub boot menu. The Recovery mode menu has an option called Resume. That should load to a desktop without using a proprietary video driver and so bypassing what may be causing this problem.

A third option is to open a terminal - Ctrl+Alt+T or Ctrl+Alt+F2 and run one or both of these commands as necessary

```
dconf reset -f /org/compiz/
setsid unity
```

The first command resets Compiz the window compositor. The second command restarts Unity. If you are not taken back to the desktop then press Ctrl+Alt+F7.

Regards.

---

### Post by MibunoOokami on 2015-01-01
> **ajgreeny said:**
> We really need to know what hardware you are using; do you have an AMD/ATI graphics card, and if so which one is it?

Lets see the output, from a command line if necessary, of the command **lspci**.

You can get to a command line by pressing **Ctrl+Alt+F1** at the point where you have only your wallpaper showing, then login with username and password (password will not show on screen).

The output is ```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV620/M82 [Mobility Radeon HD 3450/3470]
```

> **grahammechanical said:**
> 

A third option is to open a terminal - Ctrl+Alt+T or Ctrl+Alt+F2 and run one or both of these commands as necessary

```
dconf reset -f /org/compiz/
setsid unity
```


I'll follow the rest of your and Tokyobadger's suggestions later today, just wanted to add now, I've tried the dconf one before and got this message ```
error: Cannot autolaunch D-Bus without X11 $DISPLAY
```

---

### Post by tokyobadger on 2015-01-01
Can you give the details on the laptop model?
1) You may need to specify the Radeon over onboard (eg Intel) graphics in the BIOS
2) Knowing more about your laptop would help others provide suggestions - I'm not a Radeon user but I think your card might not be supported by fglrx in newer linux releases - have you tried the radeon driver?

---

### Post by ajgreeny on 2015-01-01
Indeed, your card is now too old for fglrx to support and you will have to use the open source radeon driver, so uninstall fglrx completely and try again, though you may have problems using unity with that card, and may find it easier to try using some other DE; as you can see from my signature, I use, and really like Xubuntu, which has a classic style desktop, but if you prefer can easily be set up with a left side panel to imitate the unity launchbar.

---

### Post by MibunoOokami on 2015-01-01
> **tokyobadger said:**
> Can you give the details on the laptop model?
1) You may need to specify the Radeon over onboard (eg Intel) graphics in the BIOS
2) Knowing more about your laptop would help others provide suggestions - I'm not a Radeon user but I think your card might not be supported by fglrx in newer linux releases - have you tried the radeon driver?

It's a Sony VAIO vgn-fw72jgb (Japanese model), off the top of my head it has a 2.4Ghz +/- processor 4gb RAM and 64b system. I haven't tried Radeon driver yet.

As for the memory I'm making a new usb startup disc to do a memtest, for some reason the laptop refused to boot from dvd even after changing startup order in bios. Fingers X'd the usb works. 
I'm reading that thread you linked for a second time now because I've missed the post on how exactly to append the boot parameters.

> **ajgreeny said:**
> Indeed, your card is now too old for fglrx to support and you will have to use the open source radeon driver, so uninstall fglrx completely and try again, though you may have problems using unity with that card, and may find it easier to try using some other DE; as you can see from my signature, I use, and really like Xubuntu, which has a classic style desktop, but if you prefer can easily be set up with a left side panel to imitate the unity launchbar.

I will attempt installing the radeon driver and if that doesn't work I will revert back to 12.04 or see if it's economical to get a new graphics card.

---

### Post by MibunoOokami on 2015-01-01
USB startup worked, memtest has been running for 2hrs now and has found 213 errors. How long does it take for the scan to complete and with all these errors is my memory basically stuffed?

I used the same 12.04 iso image to make the startup disc,  the iso worked fine when I was using 12.04 so I assume these results aren't due to a bad iso.

---

### Post by MibunoOokami on 2015-01-02
I read online that there is a bug in the memtest for 12.10 that causes false errors as does excess heat. I downloaded 14.04, made a USB startup disc and put a notebook cooler under the laptop and proceeded to run memtest again. Two passes later there were zero errors found so I must have been using 12.10 before. I'll assume the memory is fine.

After removing fglrx I can now see my startup programs but there is no unity (side left panel), dash/home and no top tool bar. It's an improvement from before so we are making progress.

---

### Post by ajgreeny on 2015-01-02
> **MibunoOokami said:**
> I read online that there is a bug in the memtest for 12.10 that causes false errors as does excess heat. I downloaded 14.04, made a USB startup disc and put a notebook cooler under the laptop and proceeded to run memtest again. Two passes later there were zero errors found so I must have been using 12.10 before. I'll assume the memory is fine.

After removing fglrx I can now see my startup programs but there is no unity (side left panel), dash/home and no top tool bar. It's an improvement from before so we are making progress.
In that case I suspect, as I said before, that you will not be able to run unity with that graphic card.  I am not sure if you can use the classic gnome desktop in 14.04 by adding gnome-panel to your system, as was possible in 12.04, but that is worth searching out, or using Xubuntu, Kubuntu or Lubuntu instead, all of which appear to use lower graphic resources.

---

### Post by MibunoOokami on 2015-01-02
> **ajgreeny said:**
> In that case I suspect, as I said before, that you will not be able to run unity with that graphic card.  I am not sure if you can use the classic gnome desktop in 14.04 by adding gnome-panel to your system, as was possible in 12.04, but that is worth searching out, or using Xubuntu, Kubuntu or Lubuntu instead, all of which appear to use lower graphic resources.

YES! Installed gnome-panel and that worked. I wasn't keen on unity when it first came out but I've got so used to it now that gnome seems weird to me again. It won't take long before I get the hang of gnome again.

I tried installing something called openbox before gnome-panel in hopes that would work for me but it's obviously as you say ajgreeny, my graphics card is now outdated. That's no big deal at the moment since I can now use my machine with 14.04 now.

Thank you to everyone for all your advice and suggestions. My apologies for the slight sidetrack about my RAM errors.

---

### Post by ajgreeny on 2015-01-03
If you do come across some inadequacies in the classic gnome desktop, because there are some compared with the "real" gnome-2, you might like Xubuntu more as it is now, in my opinion the best, most configurable classic panel-style DE available.

Can you mark this as **SOLVED** from **Thread tools** menu at the top please; it helps others looking for solutions to this same problem.

---

