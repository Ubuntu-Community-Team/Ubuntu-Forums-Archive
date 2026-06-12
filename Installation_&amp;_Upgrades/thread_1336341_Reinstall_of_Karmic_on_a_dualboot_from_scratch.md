---
title: "Reinstall of Karmic on a dualboot from scratch"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by stesosaso on 2009-11-24
Let me explain what I would like to do:

I have a partition with XP on it and then another one with / and /home and /swap

Karmic is running on the linux partitions but issued from upgrades.
I would like to reinstall it from scratch.

My questions are:
- What scould I take care about in order to avoid a grub problem as I had in the past with the same machine [http://ubuntuforums.org/showthread.php?t=770088](http://ubuntuforums.org/showthread.php?t=770088)
- How can I reconect Evolution to the existing data on /home
- Are there any changes to take into acount regarding my xorg config? Could I just save my config and overwrite the new one?
- Any other advice is wellcomed

Many thanks in advance for your help and advice
Stéphane from France

PS: Please excuse my English as it is not my mother language

---

### Post by presence1960 on 2009-11-24
> **stesosaso said:**
> Let me explain what I would like to do:

I have a partition with XP on it and then another one with / and /home and /swap

Karmic is running on the linux partitions but issued from upgrades.
I would like to reinstall it from scratch.

My questions are:
- What scould I take care about in order to avoid a grub problem as I had in the past with the same machine [http://ubuntuforums.org/showthread.php?t=770088](http://ubuntuforums.org/showthread.php?t=770088)
- How can I reconect Evolution to the existing data on /home
- Are there any changes to take into acount regarding my xorg config? Could I just save my config and overwrite the new one?
- Any other advice is wellcomed

Many thanks in advance for your help and advice
Stéphane from France

PS: Please excuse my English as it is not my mother language

There is a way to save your current packages installed to a file then have them installed after a clean install. Your settings for those packages will remain the same as long as you specify your /home partition in the install. When you get to the partitioner screen specify root (/), but then also highlight the /home partition, click change and set the parameters in the window that appears. **_VERY IMPORTANT: do not tick the format box and specify mount point as /home._** Proceed with the installation.

here is the procedure for saving your installed packages to a file and then after the clean install using that file to have all the packages reinstalled for you. Please note any packages not installed through apt will not be restored. You will have to manually reinstall those.

To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```


This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```


It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository.

I strongly advise you back up your data prior. Although you have separate partitions never take the chance of doing partitioning/installation operations without your data being backed up. Anything can happen, although 99.9% of the time nothing happens don't be the one caught with your pants down.

---

### Post by stesosaso on 2009-11-24
Many thanks for your help **presence1960**.

But in my case I installed Ubuntu Tweak and I think that this could be the source of my problems.
So my next question is : does your command 
```
dpkg --get-selections > ~/my-packages 
```save this software ?
With this software, I have updated my firefox for example, but this update is not in the repositories etc... Will all that beeing saved with your command?

Thanks again for your help and advice

---

### Post by presence1960 on 2009-11-24
> **stesosaso said:**
> Many thanks for your help **presence1960**.

But in my case I installed Ubuntu Tweak and I think that this could be the source of my problems.
So my next question is : does your command 
```
dpkg --get-selections > ~/my-packages 
```save this software ?
With this software, I have updated my firefox for example, but this update is not in the repositories etc... Will all that beeing saved with your command?

Thanks again for your help and advice
Both will be saved to the file. But when you use the file to restore the packages only those packages in the repositories will be installed. Any other software that is not contained in the repositories will not be replicated and must be manually installed.

Note: make sure you update your sources list before running the command to install from that file.

---

### Post by stesosaso on 2009-11-25
Many thanks for your help **presence1960**

I will do so then.

How can I, or have I to mark this thread as solved ?

---

### Post by presence1960 on 2009-11-25
> **stesosaso said:**
> Many thanks for your help **presence1960**

I will do so then.

How can I, or have I to mark this thread as solved ?

Use the Thread Tools link top right of page to mark as solved.

---

### Post by stesosaso on 2009-11-26
> **presence1960 said:**
> Use the Thread Tools link top right of page to mark as solved.
Many thanks, I should have looked more in detail to the different menus. :-)

---

