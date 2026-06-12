---
title: "Proprietary Drivers Failed To Install"
date: 2018-07-29
forum: Installation &amp; Upgrades
---

### Post by h3nry2 on 2018-07-29
Hi guys today i get my first notebook with specs:i5 8th gen, 8 gb ram, 2 gb geforce MX 150 graphic card
And i go through the installation procedure of ubuntu 18.04 lts which goes smooth without any hiccups
But when i first boot it and tried to play some games then i noticed gameplay was not so smooth and i suspect it may be the drivers
So i jump to the additional drivers section and i noticed that ubuntu is using open source nouveau drivers 
Then i click the proprietary and tested nvidia drivers displaying there to install them and the installation process takes place for nearly 2 minutes but suddenly stopped and drivers can't be installed 
I think it might be a crash so i reboot it and again tried to make the changes but i can't
Need solution to deal with this issue

---

### Post by JKyleOKC on 2018-07-29
You might be encountering this: "There's a major problem with Nvidia's driver in the most recent updates; it's on launchpad as bug #1737750." Basically, it's about an error upstream that has made it impossible for recent versions of the proprietary drivers to build. The long thread on Launchpad describes ways to deal with it, but they are more than slightly complicated. I found that rolling back to an older system installation was the easiest solution -- but not being a gamer I wasn't concerned about game playing.

---

### Post by SeijiSensei on 2018-07-29
Try installing from the command prompt with

```
sudo apt install nvidia-current
```

What errors do you see?

I had problems with the NVIDIA driver in 18.04 during the beta phase, but the problem appeared resolved now.  This machine I'm typing on uses driver 390. 48 with kernel  4.15.0-24-generic.

The driver must be compiled when it is installed.  Check to make sure you have the required compilation tools by first running

```
sudo apt install build-essential dkms
```

---

### Post by h3nry2 on 2018-07-30
By running
 ```
sudo apt install build-essential dkms
```
i get
```
dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem
```
then i run 
```
sudo dpkg --configure -a
```
and get this 
```
Configuring Secure Boot &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                                                                                                 &#9474; 
 &#9474; Your system has UEFI Secure Boot enabled.                                                                                                       &#9474; 
 &#9474;                                                                                                                                                 &#9474; 
 &#9474; UEFI Secure Boot requires additional configuration to work with third-party drivers.                                                            &#9474; 
 &#9474;                                                                                                                                                 &#9474; 
 &#9474; The system will assist you in configuring UEFI Secure Boot. To permit the use of third-party drivers, a new Machine-Owner Key (MOK) has been    &#9474; 
 &#9474; generated. This key now needs to be enrolled in your system's firmware.                                                                         &#9474; 
 &#9474;                                                                                                                                                 &#9474; 
 &#9474; To ensure that this change is being made by you as an authorized user, and not by an attacker, you must choose a password now and then confirm  &#9474; 
 &#9474; the change after reboot using the same password, in both the "Enroll MOK" and "Change Secure Boot state" menus that will be presented to you    &#9474; 
 &#9474; when this system reboots.                                                                                                                       &#9474; 
 &#9474;                                                                                                                                                 &#9474; 
 &#9474; If you proceed but do not confirm the password upon reboot, Ubuntu will still be able to boot on your system but any hardware that requires     &#9474; 
 &#9474; third-party drivers to work correctly may not be usable.                                                                                        &#9474; 
 &#9474;                                                                                                                                                 &#9474; 
 &#9474;                                                                     <Ok>
```

i thought i have done something with my UEFI and close the terminal cuz i don't know what to do with it :-k

---

### Post by QIII on 2018-07-30
Hello!

Would you please edit your post and replace the tabular thing you have going on there with the actual output from the terminal and place it between code tags?

What you have there is liable to be confusing.

---

