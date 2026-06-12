---
title: "Install 12.X On Non-Responsive 10.04 Without Losing Data"
date: 2014-06-18
forum: Installation &amp; Upgrades
---

### Post by OrionXIII on 2014-06-18
Is there a way to install Ubuntu 12.X on top of a non-responsive 10.04 LTS desktop that was broken due to an update that was released?

It'll boot, it just stops responding to the mouse clicks and keyboard...I will happily upgrade the OS if there's a way to do it without losing my files and a way to make it happen before it locks up! :D

Thank you for the guidance to date! This gives me hope!

Orion

---

### Post by yancek on 2014-06-18
Ubuntu 10.04 and 12.04 are both LTS and you should be able to upgrade but that is always risky.  I would back up any important data before trying.  You mightbe better off to install 12.04 to another partition if you have room for it then copy what you want from 10.04.  In either case, I would suggest a backup before beginning.  The link below has instructions

 [https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

---

### Post by OrionXIII on 2014-06-18
I'd love to back up my files first. Any idea how to do that when I cannot use the keyboard or mouse?
As I said, once it boots, and I log in, the keyboard no longer functions. I can move the mouse, but mouse clicks have no effect. I can watch the clock tick, but that's it.

I'm okay taking the risk if there's a way to upgrade the system without logging in - which would leave me unable to upgrade since I cannot use the keyboard or click with the mouse. Is there a way to do that?

Thanks for the help!

Orion

---

### Post by Bucky Ball on 2014-06-19
Boot from a LiveDVD/USB and backup files. DO NOT go for the in system upgrade to 14.04 LTS, even if you can. You have a broken system and upgrading with the Update Manager will just give you a more recent broken system and will be problematic.

We don't support EOL (end-of-life) releases here anymore, so stick to 'how to install 12.04 LTS' rather than asking for help with 10.04 LTS (not that you were about to). ;)

A clean install on another partition is a good choice, as suggested, if you have the room. Once you are backed up though, I would personally do a clean install of 12.04 LTS (or 14.04 LTS) to the existing 10.04 '/' partition. Just install straight over it. 

To do this, when you get to the partitioning section of the install choose 'Something Else' and partition manually. You only need to worry about the partition marked with '/' as its mountpoint. Leave the rest alone and make sure they are marked 'Do not use' and not ticked to format. Only tick the / partition to format and make sure it has / as its mountpoint. 

The install will recognise this and take care of the rest. Good luck. ;)

---

### Post by kansasnoob on 2014-06-19
Step #1 is deciding which Ubuntu to install. This involves a few considerations.

Which desktop environment do you want to use? Have you tried Unity? Or GNOME Shell? The reason for asking is that I can't help but wonder why you were still using 10.04 when it reached EOL over one year ago :confused:

What hardware are you using? Some older hardware that would run Ubuntu 10.04 with the GNOME 2 DE is not capable of running Unity or GNOME Shell :( If you still have the old 10.04 live CD (or other live media) you could use that to gather hardware info before proceeding.

So please take time to research this a little bit (feel free to ask as many questions as you wish - perhaps even starting new threads as needed), then you can obtain the proper live media, back up your data using the live media, and then provide some details about the existing installation.

The good news is that all flavors of 14.04 (Trusty) are LTS:

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes)

> Ubuntu 14.04 LTS will be supported for 5 years for Ubuntu Desktop, Ubuntu Server, Ubuntu Core, Kubuntu, Edubuntu, and Ubuntu Kylin. All other flavours will be supported for 3 years. 

---

### Post by sudodus on 2014-06-19
I support kansasnoob's suggestion to spend some time and effort to decide what to install. Try several versions (12.04 LTS and 14.04 LTS), and several flavours (desktop environments with light, medium or heavy footprints and different styles). See also this link
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by Niets on 2014-06-21
> **OrionXIII said:**
> Is there a way to install Ubuntu 12.X on top of a non-responsive 10.04 LTS desktop that was broken due to an update that was released?

It'll boot, it just stops responding to the mouse clicks and keyboard...I will happily upgrade the OS if there's a way to do it without losing my files and a way to make it happen before it locks up! :D

Thank you for the guidance to date! This gives me hope!

Orion

Boot from a CD and edit your grub.cfg file on the hard drive so it stops during boot and allows you to move back a kernel revision.  Then purge the offending kernel (2.6.32-61).  Now you should have a working system to plan your upgrade.

See-
[http://ubuntuforums.org/showthread.php?t=2228645&page=3](http://ubuntuforums.org/showthread.php?t=2228645&page=3)

(I remember years ago when the Ubuntu community was more helpful.  Guess I have been away for too long.)

---

### Post by Bucky Ball on 2014-06-21
> **Niets said:**
> Boot from a CD and edit your grub.cfg file on the hard drive so it stops during boot and allows you to move back a kernel revision.  Then purge the offending kernel (2.6.32-61).  Now you should have a working system to plan your upgrade.

See-
[http://ubuntuforums.org/showthread.php?t=2228645&page=3](http://ubuntuforums.org/showthread.php?t=2228645&page=3)

(I remember years ago when the Ubuntu community was more helpful.  Guess I have been away for too long.)

You should not edit grub.cfg directly. You should edit /etc/default/grub and when you've finished, 'sudo update-grub'. This will write the changes to grub.cfg.

---

### Post by OrionXIII on 2014-06-22
Bless you!!!!

*happy dance!*

LOL It ate my entire post - Thank you!! That was exactly what was needed!! I was able to use the SHIFT key to get into the Grub Menu - never even THOUGHT of that! You guided me to just the right solution. Now I can back up my files.

I've tried the newer versions of Ubuntu - everything from 11 on up (haven't tried for a year) and cannot STAND the Unity desktop and have found them to be very unstable, especially in their 64-bit incarnations. Perhaps it's time to try again...I've got a laptop just dying for a new OS. :)

Niets, the next time you are in the Portland, OR area, drop me a line and I will buy you a glass of your favorite adult beverage. I am SOOO thankful right now. I yelled "YESS!!" so loud I scared my cats.

Orion

---

### Post by OrionXIII on 2014-06-22
Thank you for the advice! Once I back up my files, I will do that - Bless you all for your help!! 

I am one VERY happy camper right now!

Orion

---

### Post by Bucky Ball on 2014-06-22
There are a million and one choices of desktop environment other than Unity. That is one of the beauties of Linux/Ubuntu.

Try Xubuntu, Lubuntu, Kubuntu (first two light and fast, Kubuntu a bit bloaty and not as quick). Or just try a couple of lightweight desktop environments; xfce4 (used by Xubuntu) or lxde (Lubuntu) installed into a regular Ubuntu install (choose 'Sessions' at the login screen). You are definitely NOT restricted to Unity if you want to upgrade to a newer release (and eventually you will if you want to be using a supported release - we don't support EOL (end-of-life) releases here anymore). ;)

To install xfce4 in a Ubuntu install, simply:

```
sudo apt-get install xfce4
```

... log out, choose xfce4-session from 'Session' and login. 'lxde' for lxde. Same procedure. You can also install either from the Software Centre. Good luck and enjoy!

---

### Post by OrionXIII on 2014-06-22
Just a follow-up - Thank you to all of you for your help.

My files are backed up. My Grub working like a champ, and I've got 14.04LTS installed on my Laptop with Xubuntu's desktop purring along.

I've been running 10.04LTS (the antique) because it does everything I like the way I like it, and to date, none of the Ubuntu's I tried between 10.04 and 12++ worked very well, were very stable, nor did they perform how I liked. I'm testing out an upgrade from 10.04 to 14.04 now though as that seems fairly nice and fairly stable.

You all have my deep gratitude for your patience and expertise!

Orion

---

### Post by Bucky Ball on 2014-06-23
Great news! I love xfce4. Enjoy. ;)

---

