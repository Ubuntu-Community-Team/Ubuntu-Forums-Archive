---
title: "Upgrade from 11.04 to 11.10:Waiting for network config on boot"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by lujate on 2011-10-18
I was prompted to upgrade to 11.10, so I did so.  The upgrade process seemed to go all right and I restarted when the popup prompted me to do so.  It came up to a new login screen, I entered my credentials and my desktop came up.  The power looking button in the upper right was lit up, so i clicked on it and there was an option in the drop down menu to restart to complete updates.  I did so and have not seen my desktop since.  

I get my bootloader and the Ubuntu splash screen.  It appears to be working, then it displays "Waiting for network configuration...".  That message stays up for less than a minute and then it is replaced by "Waiting up to 60 more seconds for network configuration...".  That message is up for less than a minute and the screen goes black.

Any idea where I went wrong, and more importantly how it get back?

TIA

---

### Post by youngunix on 2011-10-18
1. are you using wired or wireless network?

2. if you can remember when the upgrade manager was working on your system, did it ask you if you wanted to **change** or **keep** your **network configuration**, did you keep it or changed it?

---

### Post by lujate on 2011-10-18
1. Wired
2. I do not remember it asking.

---

### Post by youngunix on 2011-10-18
have you tried booting up the system with ethernet cable unplugged?

in case you didn't, try it and if you can log in, plug it back in and run the magic commands.

---

### Post by lujate on 2011-10-18
I unplugged the NIC and booted the machine.  I still saw the two messages from before but they stayed up longer.  Then another message flashed by and I am back at the black screen.  The message went by really fast but said something like, "Booting the machine without full network configuration".

---

### Post by youngunix on 2011-10-18
just to be on the same page here, you removed the network card from the motherboard? 

don't remove the NIC from your PC, just unplug the cable!

---

### Post by lujate on 2011-10-19
Well that is going to be a problem.  It is integrated with the motherboard so I cannot just remove the NIC.

---

### Post by lujate on 2011-10-19
I have it booted to a shell through recovery mode.  Where is the best place to start looking to find the source of my problem?

---

### Post by tc7 on 2011-10-19
> **lujate said:**
> I was prompted to upgrade to 11.10, so I did so.  The upgrade process seemed to go all right and I restarted when the popup prompted me to do so.  It came up to a new login screen, I entered my credentials and my desktop came up.  The power looking button in the upper right was lit up, so i clicked on it and there was an option in the drop down menu to restart to complete updates.  I did so and have not seen my desktop since.  

I get my bootloader and the Ubuntu splash screen.  It appears to be working, then it displays "Waiting for network configuration...".  That message stays up for less than a minute and then it is replaced by "Waiting up to 60 more seconds for network configuration...".  That message is up for less than a minute and the screen goes black.

Any idea where I went wrong, and more importantly how it get back?

TIA

I had the same problem - eventually the desktop came up (kind of). 

I had to switch to a text tty (ALT-SHIFT-F1) and make the following change as described at each of the following:

1) [http://uksysadmin.wordpress.com/2011/10/14/upgrade-to-ubuntu-11-10-problem-waiting-for-network-configuration-then-black-screen-solution/](http://uksysadmin.wordpress.com/2011/10/14/upgrade-to-ubuntu-11-10-problem-waiting-for-network-configuration-then-black-screen-solution/)

2) [http://uksysadmin.wordpress.com/2011/10/14/upgrade-to-ubuntu-11-10-problem-waiting-for-network-configuration-then-black-screen-solution/?like=1](http://uksysadmin.wordpress.com/2011/10/14/upgrade-to-ubuntu-11-10-problem-waiting-for-network-configuration-then-black-screen-solution/?like=1)

3) [http://joshua14.homelinux.org/blog/?p=1029&wpmp_switcher=mobile](http://joshua14.homelinux.org/blog/?p=1029&wpmp_switcher=mobile)

Basically in 11.10 /var/run and /var/lock were moved to /run, and there needs to be symbolic links created to point the old to the new, eg:
cd /var
sudo rm -rf run lock
sudo ln -s /run run
sudo ln -s /run/lock lock
(reboot)
:o

---

### Post by ClarkWierda on 2011-10-19
Lucky for me, everything seems to be working, but for the delay.

Does anyone know what is waiting for what data?  I'd rather not lose the wired port, but having to wait several minutes for it to decide to continue is very frustrating.

At least removing everything involving Network Manager and replacing it with Wicd allows the system to connect without waiting for me to log in.

I'm running on a laptop and sometimes have a hard connection and sometimes have a wireless connection.  Many times, I don't have wireless available when a wired connection is offered.

I already had the end-state with the directories and the symlinks, I'm just trying to reduce the time from starting the boot and having a useful system.  As this is a dual-boot system, I could just use the Windows boot, but that is just wrong.

Thanks,
Clark

---

### Post by lujate on 2011-10-19
tc7, that did the trick.  I am up to my desktop and now I get to start trying to repair or replace all the apps that are broken or gone.

Thanks

---

### Post by ClarkWierda on 2011-10-19
The solution I found for this was to comment out all "iface <device>" lines in /etc/network/interfaces except for "iface lo" (loopback).

I left all the "auto" lines.

Now, there is no delay "Waiting for network configuration".

---

