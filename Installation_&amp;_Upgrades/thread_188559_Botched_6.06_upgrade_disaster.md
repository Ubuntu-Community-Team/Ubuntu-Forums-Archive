---
title: "Botched 6.06 upgrade disaster"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by JLane on 2006-06-04
Apologizes in advance if this seems random and vague, but I am a Linux/Ubuntu newbie having some problems.

I started a Dapper upgrade from the GUI when the update notification came. The downloading all seemed to go fine, I left it go for a few hours and came back and saw that though it started installing packages, a terminal-like screen was in the update dialog. The install had stopped on a conflicted config file that had been apparently changed from the default. I will I could remember what file it was, but I cannot. I didn't recognize it. Regardless, it asked if I wanted to see a diff of the changes, and I hit yes. It showed the diffs, and then an <end> at the bottom, with no instructions. I tried hitting space or enter, or x to make it continue, and it didn't. So I hit CTRL-C. Big mistake! The install completely halted!!  ](*,) No dialog, no warning. A serious UI failure.

I then tried re-running Synaptic or the Updater and it wouldn't let me. It told me to run "dpkg --configure -a" from a terminal and refused to do anything else in the GUI. I tried to open a terminal from the menu, and nothing happened (uh oh). Not knowing what else to do, I rebooted.

After rebooting, logging to the desktop fails with an x-windows error. I've been able to login in failsafe terminal mode, however.

I've tried following [HOWTO fir dependency problems]("http://www.ubuntuforums.org/showthread.php?t=186672") a best as I could, with little luck. I was able to get some packages apparently installed, but the rest fail in dependency hell.

If I do "dpkg --configure -a", I get a large number of dependency errors and it halts with "too many errors".

If I do "apt-get -f remove", I get am error with trying to remove nautilus-share, like [in this thread]("http://www.ubuntuforums.org/showthread.php?t=136080"). I am not able to fix it by making a symlink as suggested, as the file libdbus-1.so.1 is *also* not on my system. I have not been able to figure out how to install it. Every time I try to install anything, I get this same error with nautilus-share.

I would have posted my logs, but I don't know how to get them off the system in its current state without typing them in by hand. Most unfortunate.  :confused: 

I figure my next option is re-install from CD, but I'm not sure I know how to do that without killing my configuration and data (which is mostly backed up, but not fully at this point). Any assistance or suggestions would be appreciated.

---

### Post by rcarring on 2006-06-04
Run your system in recovery mode -- when you boot, hit esc when you see the grub loader, and choose recovery mode. This should take you to prompt.

If your network is available then you should be able to ping your ISP, assuming you have broadband. If you can ping your isp, then the next step is to try to restart the upgrade. If you have no network and no ping, then my suggestion is that if you have the alternate (not the Live) cd, you may be able to edit your sources.list to point it at the cdrom and comment out the other network repos, and hopefully restart the upgrade again manually.

```

#
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


```

This is taken from my working sources.list

I don't know if you have a friend with a fast internet connection and a cd burner who could help.

My proposal would allow you to restart the upgrade from the cd assuming as I said that you can boot your system to a point.

+++

On a simple hack side of things, you may be able to manually install missing libs, after making changes as described above to sources.list

sudo apt-get install libdbus-1.so.1

***

To edit the sources.list you need to do

```

cd /
cd /etc/apt/
sudo cp sources.list sources.list.bak
sudo nano sources.list

```

Ctrl-O to save the edit
Ctrl-X to quit nano

If nano not installed, try use pico instead.

NB the diff process opens vi. To quit vi, type

```

:
q

```

---

### Post by ubuntu_demon on 2006-06-04
Since you are new then it's probably the easiest to make backups of your personal files and reinstall.

If you have trouble making backups let us know.

**If you want to try to solve it :**

please read these guides :
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

Please be elaborate about your problems. Post the errors you get. Post your /var/log/Xorg.0.log and ~/xsession-errors log files. Post the result of $lspci and post your /etc/apt/sources.list.

---

### Post by JLane on 2006-06-04
I was able to fix my problem on my own by using dselect to put nautilus-share on hold instead of install or removal. After doing that, running Install from deselect was able to continue and I could figure it out from there. Although I did not use your suggestions rcarring, thanks for the advice, I appreciate you taking the time to give it.

[QUOTE=rcarring]
On a simple hack side of things, you may be able to manually install missing libs, after making changes as described above to sources.list

sudo apt-get install libdbus-1.so.1[/code][/QUOTE]

I just wanted to mention for future use that this did not work for me. It says the package does not exist or has been removed. I copied and pasted my sources.list from the clean list in this forum and it is correct. I guess it's an older version that is no longer used in Dapper. I don't really understand why a dependency is needed to remove a package anyway. Oh well.

[QUOTE=rcarring]NB the diff process opens vi. To quit vi, type

[code]
:
q[/QUOTE]

Thanks for the info. I didn't even know I *was* running vi. I have to say that this prompt was very daunting for someone that doesn't do work with the CLI on a daily basis. It was pretty sucky that it didn't suggest what to do or give a confirmation dialog before aborting the install. When I reinstalled, I just let it pick the version from the distro and crossed my fingers.

---

### Post by ubuntu_demon on 2006-06-05
[QUOTE=JLane]I was able to fix my problem on my own by using dselect to put nautilus-share on hold instead of install or removal. After doing that, running Install from deselect was able to continue and I could figure it out from there. Although I did not use your suggestions rcarring, thanks for the advice, I appreciate you taking the time to give it.



I just wanted to mention for future use that this did not work for me. It says the package does not exist or has been removed. I copied and pasted my sources.list from the clean list in this forum and it is correct. I guess it's an older version that is no longer used in Dapper. I don't really understand why a dependency is needed to remove a package anyway. Oh well.



Thanks for the info. I didn't even know I *was* running vi. I have to say that this prompt was very daunting for someone that doesn't do work with the CLI on a daily basis. It was pretty sucky that it didn't suggest what to do or give a confirmation dialog before aborting the install. When I reinstalled, I just let it pick the version from the distro and crossed my fingers.[/QUOTE]
Try the command "pico" it's more easy. I'm an experienced Ubuntu user but I'm afraid of vi. I don't want to learn everything from the top of my head to be able to work faster and at the same time get RSI :-D.

to edit a file in the terminal :
$sudo pico /etc/filename

---

### Post by JLane on 2006-06-06
[QUOTE=ubuntu_demon]Try the command "pico" it's more easy. I'm an experienced Ubuntu user but I'm afraid of vi. I don't want to learn everything from the top of my head to be able to work faster and at the same time get RSI :-D.

to edit a file in the terminal :
$sudo pico /etc/filename[/QUOTE]

You misunderstand, it runs vi when there is a file modification conflict during the dapper install and you ask it do show you the differences (diff). You don't really have a choice. Otherwise, I absolutely stick to to pico (and gedit if I possibly can help it). A blatant ambush by whoever wrote the installer if you ask me! :wink:

---

### Post by ubuntu_demon on 2006-06-06
[QUOTE=JLane]You misunderstand, it runs vi when there is a file modification conflict during the dapper install and you ask it do show you the differences (diff). You don't really have a choice. Otherwise, I absolutely stick to to pico (and gedit if I possibly can help it). A blatant ambush by whoever wrote the installer if you ask me! :wink:[/QUOTE]

For some reason the system wide alternative isn't pointing to nano (I just like to type pico to start nano). By default it does. But to change it :
$sudo update-alternatives --config editor

and choose  nano.

---

