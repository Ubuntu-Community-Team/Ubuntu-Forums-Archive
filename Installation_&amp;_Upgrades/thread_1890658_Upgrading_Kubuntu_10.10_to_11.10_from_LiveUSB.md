---
title: "Upgrading Kubuntu 10.10 to 11.10 from LiveUSB"
date: 2011-12-04
forum: Installation &amp; Upgrades
---

### Post by SolaceFile on 2011-12-04
Hello Members,

I am in need of help! I have dual boot my Windows 7 Home Premium PC with Kubuntu 10.10. 

I have also downloaded Kubuntu 11.10 and prepared a Live USB using the LiveUSB software. But when I am booting from the USB there is no option to upgrade the current Kubuntu version.

What shall I do? It would be great if anyone can guide me step by step since I am a newbie in this field. 

Regards

---

### Post by Max4344 on 2011-12-04
Is it in the boot menu or the install screen?
Form my experience with Ubuntu In the install screen there is a option to upgrade.

---

### Post by SolaceFile on 2011-12-04
I have read somewhere that we can upgrade Kubuntu after downloading the ISO file and creating the Live CD or USB. But now I am not getting the upgrade option. 

I have created a LiveUSB of the latest Kubuntu 11.10. What shall I do next?

---

### Post by SolaceFile on 2011-12-04
Can anyone help? I am stuck in this.. :(

---

### Post by internetprofiles1 on 2011-12-04
I believe like ubuntu kubuntu CANNOT upgrade from 10.10 to 11.10 you have to go from 10.10 to version 11.04 upgrade first then to version 11.10 this can be done via update manger instead of a burnt iso after you get 11.04 then you will be able to upgrade to 11.10

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

first go to software sources and on the update tab make sure its set for Normal Releases,then to find update manager...make sure to hit the check first install those updates then do the upgrade. after that do the upgrade. This can all be done via the internet you dont need the usb except that it will save you some time.

[http://www.ubuntu.com/download/ubuntu/upgrade](http://www.ubuntu.com/download/ubuntu/upgrade)

---

### Post by kio_http on 2011-12-04
> **SolaceFile said:**
> Can anyone help? I am stuck in this.. :(

You cannot upgrade like that from 10.10 to 11.10

If you want to upgrade via network do so with the package manager. (update to 11.104 then to 11.10)

Or you can use the alternate cd, you will need 11.04 and 11.10 alternate disks or DVD.  See the respective release notes for 11.04 and 11.10. 

To upgrade with the alternate disk (change iso path and name)
```
sudo mount -o loop ~/Desktop/ubuntu-10.04-alternate-i386.iso /media/cdrom0
```
```
kdesudo "sh /cdrom/cdromupgrade"
```

---

### Post by SolaceFile on 2011-12-04
Thanks guys! I got the Kubuntu Installed. I am now running Kubuntu 11.10. 

I formatted the previous installation and installed this inside window. I have found another problem!! :( 

I think kubuntu is not installed properly. The teminal shows files locked, permission denied error whenever I do something. 

When I wrote :apt-get update
It gave me: ```
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

When I tried to install firefox it is showing: ```
The package "firefox-kde-support" has not been found among your software sources. Therefore, it cannot be installed. 
```

Please help me out in this.

---

### Post by Elfy on 2011-12-04
> E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?This :)

Use sudo - ```
sudo apt-get update
```

---

### Post by SolaceFile on 2011-12-04
Okay, I did it. It is showing the below quoted text from last 10 mins:
> 0% [Connecting to us.archive.ubuntu.com (91.189.92.184)] [Connecting to security.ubuntu.com (91.189.92.167)]

What is the problem with firefox? When I clicked on Mozilla firfox browser Installer, it shows:
> The package "firefox-kde-support" has not been found among your software sources. Therefore, it cannot be installed.

---

### Post by kio_http on 2011-12-05
> **SolaceFile said:**
> Okay, I did it. It is showing the below quoted text from last 10 mins:


What is the problem with firefox? When I clicked on Mozilla firfox browser Installer, it shows:

Try pressing ALT + F2 then type
```
kdesudo software-properties-kde
```
In the dialog that shows up select the mirror with best speed or chose a different one close to your home. 

Since your on Kubuntu 11.10 you might like [this thread of mine ]("http://ubuntuforums.org/showthread.php?t=1889034")on performance.

---

