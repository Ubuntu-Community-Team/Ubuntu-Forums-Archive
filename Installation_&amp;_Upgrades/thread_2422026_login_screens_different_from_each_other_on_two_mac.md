---
title: "login screens different from each other on two machines"
date: 2019-07-01
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2019-07-01
I have two very similar machines, both recently upgraded to 18.04, one by updater, the other through terminal.  The log-in screens are totally different.  One has the outline of a beaver, the other is more like Windoze.  

Why are they different?

How do I make them the same, preferably more like Windoze.

---

### Post by Claus7 on 2019-07-01
Hello,

first you have to verify which display manager is running issuing the command:
cat /etc/X11/default-display-manager

then, either you have to change display manager (from lightdm to gdm3 or vice verca depending on your tastes) or change the background of the display manager. The former is done via:
sudo dpkg-reconfigure xxx, where under xx you place the output of the command above (the very last part of it).

If you wish to change background first you have to enable the display manager which fits your needs.

Regards!

---

### Post by RogerDavis on 2019-07-01
roger@roger-desktop:~$ cat /etc/X11/default-display-manager
/usr/sbin/lightdm
roger@roger-desktop:~$ 

The "beaver" machine is using lightdm.  I presume if I change this to gdm3 I'll have the "Wiindoze" type log-in, and nothing else will change.

When I try I get this...

roger@roger-desktop:~$ sudo dpkg-reconfigure gdm
[sudo] password for roger: 
/usr/sbin/dpkg-reconfigure: gdm is broken or not fully installed
roger@roger-desktop:~$ 
===
roger@roger-desktop:~$ sudo apt-get install gdm3
[sudo] password for roger: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gdm3 is already the newest version (3.28.3-0ubuntu18.04.4).
gdm3 set to manually installed.
The following packages were automatically installed and are no longer required:
  libapparmor1:i386 libargon2-0:i386 libcryptsetup12:i386
  libdevmapper1.02.1:i386 libgck-1-0:i386 libgcr-base-3-1:i386
  libgudev-1.0-0:i386 libip4tc0:i386 libjson-c3:i386 libseccomp2:i386
  libsecret-1-0:i386 libudisks2-0:i386
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
roger@roger-desktop:~$ 
===
roger@roger-desktop:~$ sudo dpkg-reconfigure gdm3
[sudo] password for roger: 
gdm.service is not active, cannot reload.
invoke-rc.d: initscript gdm3, action "reload" failed.
roger@roger-desktop:~$ 

Any ideas ?

---

### Post by again? on 2019-07-01
That's a normal message after selecting gdm3 as default display manager.
If you got a selection dialog, just reboot.

---

### Post by RogerDavis on 2019-07-01
I rebooted, and got big problems.  It begins to boot, gets to purple screen and then just rotates the dots.  Depending on what keys I beat on, I get Ubuntu with dots, stops at "created slice system -getty slice, started Gnome display manager, system log-in (but I don't know what it wants for that, just the password doesn't work, or logitech-hidpp device - (numbers) unable to retrieve ...(name?) of device.  I'm stuck with the old computer until I can get this done.

---

### Post by again? on 2019-07-02
```

```You can boot in recovery mode, login and switch back to lightdm.
```
sudo dpkg-reconfigure lightdm
```
then
```
reboot
```
Are you using nvidia drivers?
I recall a bug with gdm3 and nvidia drivers.

---

### Post by RogerDavis on 2019-07-02
I can't get to recovery mode - don't know how.  Is this the "roger-desktop login" that I can't find the right answer for?  This is followed by password - no problem  I can only get to this about one of 50 tries.  What's the specified method?  If I google it, I get lots of different answers.

---

### Post by RogerDavis on 2019-07-02
Also, what's the magic answer when it asks for "desktop-login:" ?

---

### Post by again? on 2019-07-02
At the grub menu you should see an "Advanced Recovery options" listing.
[ATTACH=CONFIG]283535[/ATTACH]
If you don't see grub, I think you need to hold down shift or escape during boot.

> **RogerDavis said:**
> Also, what's the magic answer when it asks for "desktop-login:" ?
Not sure what you are referring to
In the console you type your username, press Enter...then your password and press Enter.(password doesn't show as you type)

---

### Post by RogerDavis on 2019-07-02
I've tried Esc, I'll try shift now... will take a few minutes...

---

### Post by RogerDavis on 2019-07-02
I tried both Shift and Esc, and for good measure, both.  No luck.

I'm getting better at getting to where it asks me for user name, but I don't know it and don't know how to get it.

The hard drive I'm using now is the one that the update to 18.04 came from, it should be the same here?  but everything I try gives me answers that don't work.

---

### Post by again? on 2019-07-02
If you don't know your username I don't know how you are going to login.
You don't recall what the terminal showed or your /home/<user> directory in the install?
eg it shows username@hostname in the terminal command prompt when logged in.
mine is glen@Bionic
[ATTACH=CONFIG]283536[/ATTACH]

You could boot to a live cd/usb and look at the /home directory of your install.
eg I have 2 users ....me "glen" and a test account called "test".
[ATTACH=CONFIG]283538[/ATTACH]

---

### Post by CatKiller on 2019-07-02
> **RogerDavis said:**
> I tried both Shift and Esc, and for good measure, both.  No luck. 

IIRC, it's spamming the Esc key with UEFI, but holding the Shift key from just the right point with BIOS. I think "the right point" is just after the BIOS has said which keys it uses itself. You've said you have a purple screen: that suggests you're using BIOS rather than UEFI. 

> I'm getting better at getting to where it asks me for user name, but I don't know it and don't know how to get it. 

roger@roger-desktop

Your username is **roger**. Your computer's name is **roger-desktop**. 

> The hard drive I'm using now is the one that the update to 18.04 came from, it should be the same here?  but everything I try gives me answers that don't work.

If you still can't get into Grub, you can boot from a live USB and chroot into your computer to fix stuff, or SSH from another computer.

---

### Post by RogerDavis on 2019-07-02
SUCCESS - Apparently the fool's routine of doing the same thing over and over is a good one !!!

I got logged into a big terminal screen about the 50th time of entering what I was (SURE???) was my user name where it asked "roger-desktop login:", and my for sure password.  I entered " sudo dpkg-reconfigure lightdm, got a white screen to select lightdm, and waited through a LOOOONNNGGGG reboot, and all was well.  

Ctl+Alt+F2 got me to that log-in spot, which was one of MANY methods found by search.

Now to find out why gdm didn't work on this one, and works ok on the other machine 50 miles away...

Any further ideas / suggestions, please  ???

Thanks for the help !!!

---

### Post by Claus7 on 2019-07-02
Hello,

gdm caused many problems including log-in loops. If you do not like the background of lightdm then you can change it from here:
[https://ubuntuforums.org/showthread.php?t=2400921](https://ubuntuforums.org/showthread.php?t=2400921)

then you will be able to have any picture you wish during login screen.

Regards!

---

### Post by RogerDavis on 2019-07-05
Shift seems to only work if done while BIOS is in progress.  If you miss that, I think it was ALT+F2 to get to the login, which I also got to work finally .

SOLVED !

---

