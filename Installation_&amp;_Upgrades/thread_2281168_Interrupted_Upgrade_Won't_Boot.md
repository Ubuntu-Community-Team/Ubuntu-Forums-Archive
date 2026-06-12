---
title: "Interrupted Upgrade Won't Boot"
date: 2015-06-04
forum: Installation &amp; Upgrades
---

### Post by johny why on 2015-06-04
Hello

While my Xubuntu updater was installing updates, i removed several packages in Ubuntu Software Center. Then, when the updater asked to restart, i clicked 'restart'. But, the Ubuntu Software Center still had a blue number displayed in the "Progress" spinner (which was still spinning). 

On restart, i see all the packages i had removed in Software Center were gone. But, i'm concerned the uninstalls were incomplete, since the Progress spinner still showed pending activity when i restarted. 

Were the uninstalls done properly and completely?

Next, i had my Xubuntu updater upgrading Xubuntu. During the "Installation" phase, i closed the lid of my computer. 

When i reopened the lid, there was an 'authorization required' dialog, asking for my password. Unfortunately, sometimes when i reopend the lid, some key was stuck in repeat mode, and the only way to cancel the key-repeat is to hit the Escape key. Unfortunately, this had the effect of cancelling the 'authorization required' dialog. I noticed the updater finished the upgrade, and asked me to restart the computer. 

Now i get a command-line on booting-- no desktop. 

What happened? Is my install hosed?

Thx!

---

### Post by grahammechanical on 2015-06-05
If you are concerned that removed packages have not been fully removed, then install them again and then uninstall then again. And allow the Software Centre the time to finish.

An upgrade that requires a restart always gives us the option to "restart now" or "restart later."

What does closing the lid do? Does it put the machine into hibernation? Is the OS set to require a password to unlock the OS when coming out of hibernation for screen lock?

The question of incomplete removal of packages is of lesser importance now because of a much bigger problem. Who can say what the problem is? It depends on what kind of command line you are getting. Is it a grub rescue prompt? Or is it a Linux command line where you can log in? Or is it just a flashing white cursor? At what point does the loading stop. If we knew that we might have an idea of how serious this problem is.

There is something that you can try and I give no promises.

1) Use the Advance options for Ubuntu to go into Recovery mode.
2) At the recovery menu select Network. That will set up an internet connection and put the file system in read/write mode.
3) When back at the recovery menu select Root. That will give you a root shell prompt and then use these commands to update/upgrade. See what errors you get
4) apt-get update
5) apt-get upgrade
6) When finished type this command to get back to the recovery menu
7) exit.
8) At the recovery menu select Resume and see what happens.

Regards

---

### Post by RobGoss on 2015-06-05
You need to allow your updates to completely update that's what there were intended for, interrupting updates will only cause other issues with other programs.

---

### Post by ajgreeny on 2015-06-05
How did  you manage to get both the update utility and Software centre both working at the same time? Any two "apt" applications running at the same moment allways show an error for the second one opened.

---

### Post by johny why on 2015-06-08
thx for all replies. Before i saw these replies, i went ahead and did a reinstall of the OS. That was the simplest solution. 

> **grahammechanical said:**
> If you are concerned that removed packages have not been fully removed, then install them again and then uninstall then again. And allow the Software Centre the time to finish. An upgrade that requires a restart always gives us the option to "restart now" or "restart later."
in other words, the software center and updater apt applications don't look out for each other. That might be a good idea! I believe i've seen that if software center is running when i do a command-line apt-get, i get an error saying you cannot do that because another apt application is already running. Seems like it would be helpful if the GUI apps did that too. 

> **grahammechanical said:**
> What does closing the lid do? Does it put the machine into hibernation? Is the OS set to require a password to unlock the OS when coming out of hibernation for screen lock?
Was set to screen-lock. Don't recall about the password, but i think so. 

> **grahammechanical said:**
> Use the Advance options for Ubuntu to go into Recovery mode.
Those are helpful steps, which i may use in the future. Thx for that. > **ajgreeny said:**
> How did  you manage to get both the update utility and Software centre both working at the same time?
Hm, i believe i opened one, and then opened the other. It's possible i waited to open the software center after the updater was already running. 

> **ajgreeny said:**
> Any two "apt" applications running at the same moment allways show an error for the second one opened.
i did not get any errors.

thx! but this issue is no more, as i've reinstalled the OS.

---

### Post by ajgreeny on 2015-06-09
I have always disabled the autostart of software-updater in my system as I think it is very annoying.  I use the notification system in the panel instead.

I am not sure, however, how or even if you can disable that easily in Ubuntu with unity as I use Xubuntu.

---

