---
title: "Upgrade to Ubuntu 18.04 LTS Fail"
date: 2018-05-12
forum: Installation &amp; Upgrades
---

### Post by lawrence-joy on 2018-05-12
I have been running 17.10 and the automatic msg said 18.04 LTS was available for download. So I clicked on yes. It took over 2 h to download and install. At the end the msg said there was a problem and the installation was not complete. I rebooted my system and now the Ubuntu (18.04 I think) GUI screen comes up with a window that wants my password. Under 17.10 I would get xubuntu on which screen I would choose "terminal emulator" and away I would go. Now, after entering my password the password entry window closes and goes to the main GUI screen (with the icons along the left edge of the screen). After about 3 s the password entry window opens up again. Again, I enter my password, the password entry window closes, and I see the GUI screen. This is an endless loop! What do I need to do, and how do I accomplish, getting a clean 18.04 LTS install?

---

### Post by dino99 on 2018-05-12
could be related to either 'gdm3' or 'graphic' driver
was lightdm used previously or else ?  18.04 use gdm3 (can be reconfigured: 'sudo dpkg-reconfigure gdm3'

but first, from a tty console, run 'startx' and then clean the system to purge old non needed packages/settings: using 'gtkorphan' and 'bleachbit' (as root, carefully select options) and reboot.

please post the output of 'journalctl -b' to glance at warnings/errors

---

### Post by lawrence-joy on 2018-05-14
I don't know what "gdm3" is or means. The video card is an NVIDEO system for dual monitors and I don't know anything about the sofware for it. What is "lightdm"? What do you mean "from a tty console"? As stated I can not get to a terminal emulator, so the terminal commands you suggest to use are useless. How do I get out of the endless loop that my system is in so I can get to the terminal emulator? As stated I can not get to the terminal emulator and so I can not do the command "journalctl -b". Any other suggestions?

---

### Post by dino99 on 2018-05-14
tty console via 'ctrl+alt+F2'
Think to test booting via 'system recovery' (grub advance option menu)

---

### Post by tinylagarto on 2018-05-14
It sounds like the upgrade to 18.10 was interrupted.

When you are finally in tty. Login with your username and password. You could then try the upgrade again manually:

```
sudo apt update
```

will update your system.

```
sudo apt dist-upgrade
```

will try to upgrade all packages.

And probably

```
sudo apt install -f
```

should resolve some problems.

---

### Post by missmoondog on 2018-05-14
personally, i'd find a way to download the iso and burn it and do a clean install from scratch. never really have liked those in place upgrades myself.

if you're system is already messed up even before getting it installed, it's likely to never be completely right.

---

### Post by lawrence-joy on 2018-05-15
Yes, I was able to get to the console (or terminal) by entering 'ctrl+alt+F2'. Thanks for that info.
I ran 'sudo apt update', then 'sudo apt dist-upgrade'.
I get "23 packages can be upgraded. Run 'apt list --upgradable' to see them".
"You might want to run 'apt --fix-broken install' to correct these".
"E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution)".
"E: Could not open lock file /var/lib/dpkg/lock - open (13:Permission denied)".
"E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"
Ran 'sudo apt install -f'. The following packages were automatically installed and are no longer required. [This produced a long list.]
"Use 'sudo apt autoremove' to remove them. [additional packages will be installed. NEW packages will be installed]
Ran 'sudo apt autoremove' and then ran 'journalctl -b'. This gave me 3298 lines of info, 5 were in red.
After all this I rebooted and the Ubuntu GUI shows up and after about 5 s it goes into the aforementioned loop of asking for password.
I run 'ctrl+alt+F2' getting to the terminal at which point I run 'firefox' and it comes back with "Error: no DISPLAY environment variable specified". [huh?]
At this point I still need help to fix this or do a clean install from scratch, for which I would need all the commands that I would need to run. Like, how do I remove what is there now for the OS without disturbing the programs and files for other things?
Thanks for all the help so far.

---

### Post by tinylagarto on 2018-05-15
You have to run this 'apt --fix-broken install' as root:

```
 sudo apt --fix-broken install
```

Did you execute any of these commands till the end?

---

### Post by lawrence-joy on 2018-05-19
Sorry this is taking so long and so much time, it looks like I need further help/instruction.
I enter "Ctrl+alt+F2" to get to the terminal
I run 'sudo apt --fix-broken install'
Comes back with:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
At the command line:~$ I run 'firefox' and it comes back with
"Error: no DISPLAY environment variable specified" as it did before.
Yes, I have executed all these commands till the end!
Still need much help!

---

### Post by lawrence-joy on 2018-05-30
Thanks to all who suggested terminal commands. They did not work completely. I am going to do as missmoondog suggested and try to do a clean install. I am having problems with that but will open another thread.

---

### Post by gldneagl on 2019-03-26
The solution that worked for me was...

1. If you can get to the grub menu
2. Choose the last kernel before the upgrade
3. Once fully booted, remove lines in grub config file (or comment them out) for the offending kernel that was upgraded to
     a. Once upon a time, the file was at: /boot/grub/menu.lst
     b. The config lines in 18.x are now in: /boot/grub/grub.cfg

This happened to me the first time during a "simple" package upgrade a few weeks back
 Last night while performing a distribution upgrade from a fully updated and upgraded Ubuntu-Mate 16.4.x to Ubuntu-Mate 18.x
It happened again
The system begins to boot and rushes head-long into "kernel panic" and halts
I have managed to pull out of it twice now
This was kind of like rushing down a slippery sloop you didn't see in front of you

---

