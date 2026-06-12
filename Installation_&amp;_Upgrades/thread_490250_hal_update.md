---
title: "hal update"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by spnoe on 2007-07-02
I recently updated my files using the update manager. The update was mostly Hal related. After I rebooted an error message appeared saying Hal failed. This has stopped the internet connection etc. I have tried to repair this but to no avail.

Could some one advise me 1) How will I know when it is safe to apply aHal update, 2) Is there a method of rolling back the update to the previous good one, without having to re-install.

I originally thought it was a problem with the type of install that I have i.e. WUBI but I have had others say that they have experienced the same problem and they installed in the normal manner.

Thanks for any help.

Steve

---

### Post by jzurawski99 on 2007-07-23
I posted this in another thread.  This worked for me.

Below is something I posted in another hal issue thread. It might apply here also.


Re: the infamous Failed to initialize hal error 

--------------------------------------------------------------------------------

I also suffered from this problem. After much searching, it seems that these hal issues might be the result of a recent hal update (just speculating).

Now, with me being a newbie at Ubuntu, take everything I say with a grain of salt. But, these are the steps I followed (gathered from a few other posts) that got me up and running again.

In short, you need to roll back the hal update. Below are the steps I followed to accomplish this.

First, when this error occured I lost all USB, DVD drives and also my network connectivety (wireless and wired).

The line below allowed me to restart dbus and hal (I needed to get my connectivity back for the roll back).

sudo /etc/init.d/dbus restart

Whatever the above line did, it allowed me to manually reconfigure my wired connection (even though it didn't look like it was working, I was able to connect to the internet).

I then followed the instrucitions below to force the hal rollback.

The info below was pasted from a thread titled "Recent HAL update caused frequently failure for "suspend when lid closes"

************************************************** *********************************

Re: Recent HAL update caused frequently failure for "suspend when lid closes" 

--------------------------------------------------------------------------------

I think i found a temp workaround for this: rollback to older versions of those hal packages.

This can be done pretty easily with Synaptic package manager in Ubuntu:

1. Open Synaptic

2. Menu: file -> history, find the history of the day you installed the hal update. For me it is under "5/11":

Code:
Commit Log for Fri May 11 15:08:47 2007

Upgraded the following packages:
hal (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
hal-device-manager (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal-storage1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1

Installed the following packages:
hal-info (20070402-1ubuntu1~feisty1)3. Now, search for each of the first 4 packages in Synaptic, then use "force version" in Package menu to force the latest version for each of them to be 0.5.8.1-4ubuntu12. When doing this for the first package, Synaptic automatically prompts to remove hal-info, which is what we want.

4. Now click on the "Apply" button. These packages will be downgraded to the good version.

5. After that, you'll immediately see the update manager pops up again to tell you there are new hal updates, this is the sign that the downgrading was successful. Of course this time you want to ignore the hal update...

************************************************** *************************************

Again, I have no idea what any of this effects. All I know is that after following the above I regained all hardware functionality. I hope this helps some of you.

JZ

---

