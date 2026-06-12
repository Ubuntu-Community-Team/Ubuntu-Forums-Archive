---
title: "How to change Grub menu display order (not boot order)"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by asarkar on 2011-07-16
Hi,
I am running Ubuntu 11.04 64-bit. I also have Windows 7 Home Premium installed.
I would like Win 7 to display first in the startup menu. Using Grub Customizer, I have been able to set Windows as the default entry but I am unable to set it as the first entry in the list. Even though I change the order and save it, the next restart sets everything back to square one. Grub Customizer screenshot is attached.
Appreciate any help.

---

### Post by oldfred on 2011-07-16
You are into manual editing the scripts or creating a copy of 40_custom as 06_custom with the windows entry.

The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

If you renumber 30_os-prober to 09_os-prober it will put the windows entries first but if grub ever updates it will create a new 30_os-prober and you get duplicate entries.

You can turn off os-prober and put you windows entry in 06_custom.

Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 06_custom and edit at will. Be sure to copy 40_custom to 06_custom to get the couple of lines at the top of the script.

sudo cp /etc/grub.d/40_custom /etc/grub.d/06_custom
Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit only titles:
gksudo gedit /etc/grub.d/06_custom
Then do:
sudo update-grub

---

### Post by asarkar on 2011-07-16
> **oldfred said:**
> 
You can turn off os-prober and put you windows entry in 06_custom.

Does this have any side effect? Will I have to do any cleanup if Grub or Kernel is updated? Not that I don't want to but I should know.

> **oldfred said:**
> 
One way to fix the descriptions is to move the windows entries to 06_custom and edit at will. 

This is after I turn off os-prober. Correct?

---

### Post by oldfred on 2011-07-16
No issues that I know of. You do want to keep backups just in case. If you add new systems or want to know a new boot stanza you can just turn the os-prober back on and copy the new entries. 

I use 40_custom a lot. I did have a typo in my 40_custom for the last several versions and it still worked. I was missing an old entry and did not realize it. Then with Natty I got errors. It does more checking to make sure entries are valid.

If you add entries to a custom file without turning off os-prober you get duplicate entries. You may want to do that the first time just to make sure the new entry works before turning off the auto generated entries.

---

### Post by MAFoElffen on 2011-07-16
> **asarkar said:**
> Does this have any side effect? Will I have to do any cleanup if Grub or Kernel is updated? Not that I don't want to but I should know.

This is after I turn off os-prober. Correct?
-- The only thing I can think of of is that you are going to have to pay attention to normal updates.  When it goes through normal updates, there is times when it's going to update the kernel and / or run update grub...  

If it updates the kernel version, you're going to have to manually add the new kernel version menuitem to your personal 06_custom to be able to use it...  If it were me, that would be just a formality.

--If you change the executtion bit of 30_osprober file, that will turn that script on and off, when update-grub is run:
```
[FONT=monospace]
[/FONT]sudo chmod -x /etc/grub.d/30_osprober

```with -x will turn it off and +x will turn it back on...

---

### Post by asarkar on 2011-07-16
I am not sure if I want to manually add entries to 06_custom (potentially) with every major upgrade. I may try it out for learning but it's unlikely that I will make the changes permanent. One would think that there'd be some option to achieve this simple task (seemingly) with an advanced Grub2. With Grub1, this would've been a piece of cake. I guess everything comes with it's pros and cons.

---

### Post by oldfred on 2011-07-16
Unless you also turn off the rest of the scripts you will still get your current Ubuntu install just not any additional installs that the os-prober finds. 

There are some standard boot stanza's you can add to boot a partition since Ubuntu puts a link to the most current kernel in root. Then it is easy to boot additional Ubuntu installs.

---

