---
title: "Results of failed upgrade"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2008-02-11
The upgrade from fiesty to gutsy was unsuccessful. Unfortunately there was no guidance to those various  request to approve new settings for programs that take place during the upgrade. I said yes to all requests substituting the latest settings for settings that differed. At the end it failed and reverted to fiesty. 

Most of the on screen failures during the upgrade had nvidia-glx in the string.

Fiesty does not work as well as it did. Not big differences but here are  the problems so far:

1. I use Vmplayer with Win2k. I can no longer cut and paste from Wiindows to Ubuntu. It appears to copy but does not paste to the destination.

2. All my messages in Thunderbird now show as bold so I can not tell which are unread.

3. I can not send a file from an application to Thunderbird as an attachment. I have to attach it manually from within Thunderbird.


As I  do not have a crippled machine, I would like to avoid a complete reinstall. It has taken me a long time to get Ubuntu working and I do not want to start again. The need for a complete reinstallation when Windows crashed was one of the things  I hated with Windows. 


Any ideas?

Robin

---

### Post by Robbyx on 2008-02-11
Does anyone recognise the problem I outlined above.

---

### Post by Robbyx on 2008-02-11
O dear, I now have another problem. I can not turn the machine off by software. The close down buttons do not work. What should I do?

---

### Post by zvacet on 2008-02-12
```
sudo shutdown -h now
```

Look in /etc/apt and see if you have two differnent sources list(one with Gutsy and other with Feisty).If you do delete one with Gutsy and then 

```
sudo apt-get update && sudo apt-get upgrade
```

That should beck you to up-to-date Feisty.

---

### Post by Robbyx on 2008-02-12
I looked in the current version of sources and found references to both fiesty and gutsy. I found the back up of the fiesty sources file and replaced the existing with that version. I then followed your terminal command which went through ok and updated the sources. No packages seem to have been replaced after that was finished.  I  tried the update manager and it found nothing to replace. I would have thought that if some of my programs are for gutsy they would need replacing back to the fiesty version. That did not happen.

The close down buttons still do not work.

---

### Post by Robbyx on 2008-02-12
I looked in the synaptic preferences and wonder if I should change any of the distribution preferences? Currently it is set to always prefer the highest version of a package when upgrading.

---

### Post by zvacet on 2008-02-12
```
uname -a
```

Just to see wich kernel you are runing.Did update manager give you message that newer version is available for download?

---

### Post by Robbyx on 2008-02-12
> **zvacet said:**
> ```
uname -a
```

Just to see wich kernel you are runing.Did update manager give you message that newer version is available for download?

Linux robin-desktop 2.6.20-16-386

The update manager is not showing there is a new version available.


The upgrade was a mess. Eventually I will have to upgrade to new versions. Would you advise I do a fresh install now? If so is there some advice as to what I can back up and restore from my current setup so that the new install does not involve reinstalling everything. 

Robin

---

### Post by chavanak on 2008-02-12
I seriously adivice you to do a fresh install. Even I faced the same problem and lost important data :(. What you need to backup is your home directory and any special configs you have done to your system. If your home directory is in separate partition, you can retain it and install gusty to your root partition.

---

### Post by Robbyx on 2008-02-12
> **chavanak said:**
> I seriously adivice you to do a fresh install. Even I faced the same problem and lost important data :(. What you need to backup is your home directory and any special configs you have done to your system. If your home directory is in separate partition, you can retain it and install gusty to your root partition.


Please indulge me with a few more comments.

How do I put the home directory on a new partition and have it recognised by ubuntu? Obviously I can copy the home directory to a new directory, but what do  I change so that Ubuntu knows the location of the home directory. 

Included in the home directory are a number of hidden directories starting with dot. They are all relate to programs that I have installed. If I move the home directory to a new location and then install a fresh copy of Gutsy, will all those programs work? I fear not because many of the settings are in bin which  I will not be copying. So why am I copying over the Home. What is the benefit?

Your refer to special configs. Where would these be found?

Robin

---

