---
title: "What do I do now that my computer is erased"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by kaminski825 on 2010-10-06
I finally got the ubuntu 10.04 live cd to work by pressing any key when the icons of the person and the keyboard pop up. I chose my language and scrolled down to install ubuntu. I went through the 7 steps and I chose to install Ubuntu completely. Then the install process started. It went up to copying files and stopped at 22%. Then an error message popped up saying that something was wrong with the disk or my hard drive. I then tried to reboot without the live cd and it turns out that the install deleted windows and started linux, but stopped so now I have no operating system. All I get is a black screen with a tiny white line. I cant even use system recovery! So now the only thing I can use is the live cd and I need some kind of authorization username and password to get into the try Ubuntu option. There has to be some way that I can get windows back or at least finish installing Ubuntu.

---

### Post by andrewthomas on 2010-10-06
Could you try installing again and take a screenshot where you get the error.  

Also, could you look at [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
and state what choices you made at the various steps (e.g. Install them side-by-side or Erase and use entire disk, etc.)

Is this screen where your error happened?

---

### Post by srs5694 on 2010-10-06
I recommend you check the SMART status of your drive. Boot the live CD, open a text-mode shell, and type "sudo apt-get install gsmartcontrol". You can then type "sudo gsmartcontrol" to launch the utility and check the status of your hard drive. If it turns up as bad, replace it and try installing Ubuntu again.

At this point, the only way to get either Windows or Ubuntu to boot from the hard disk is to re-install the OS; by installing over Windows, you've wiped the Windows installation, with essentially 0% probability of a complete recovery of Windows.

---

### Post by kaminski825 on 2010-10-06
I tried to install it several times. I clicked forward every time and clicked install ubuntu over windows. I got past the screenshot you showed me and  got about to the point where the slideshow shows F-spot at 22%

---

### Post by andrewthomas on 2010-10-06
> **srs5694 said:**
> I recommend you check the SMART status of your drive. Boot the live CD, open a text-mode shell, and type "sudo apt-get install gsmartcontrol". You can then type "sudo gsmartcontrol" to launch the utility and check the status of your hard drive. If it turns up as bad, replace it and try installing Ubuntu again.

At this point, the only way to get either Windows or Ubuntu to boot from the hard disk is to re-install the OS; by installing over Windows, you've wiped the Windows installation, with essentially 0% probability of a complete recovery of Windows.
Have you checked the status of your hard drive as suggested above?

---

### Post by PapaNerd on 2010-10-06
When you are booted from the LiveCD, please open a terminal window and issue this command:
```

sudo fdisk -l

```
and post the output to this thread.  This will show if the hard drive partitions are still in tact.

---

### Post by oldos2er on 2010-10-06
What are your system specs?

---

