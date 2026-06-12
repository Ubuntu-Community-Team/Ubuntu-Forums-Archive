---
title: "Ubuntu 20.04 can't login with correct password - no .Xauthority folder"
date: 2020-07-09
forum: Installation &amp; Upgrades
---

### Post by smolla97 on 2020-07-09
Hello, this is my first time installing Ubuntu.
I installed it alongside Windows 10 (dual boot).
I got UEFI BIOS, and Nvidia GPU if that matters.

i7 7700k, 16GB ddr4 RAM and gtx 1080

[B][U]Here is my procedure:
[/U][/B]
[LIST=1]
[*]Downloaded Ubuntu 20.04 from official Ubuntu website
[*]Using rufus, I flashed the image to the USB drive of 8GB (FAT32 formated)
[*]Plugged USB in and rebooted my PC. At the boot menu I chose the USB drive and then the file checking process started.
[*]During that checking process 0 errors have been found.
[*]Then the setup wizard showed up. I chose Install Ubuntu and chose the option "Install alongside Windows".
[*]I made an username and password, and chose to option to "Log in automatically".
[*]I dedicated 70GB via the slider to the Ubuntu, and left 150GB to the Windows 10.
[*]The installation proces began, and completed after few minutes.
[*]I was asked to reboot my PC and then to eject the USB drive and press ENTER.
[*]Did that, and then I got automatically booted into Windows 10.
[*]Rebooted my PC again, and in the boot options chose "ubuntu". Booted into Ubuntu and got to the screen where I need to choose a User and then enter a password.
[*]Entered the correct password and then got simply return to the user selection screen. No message came up that the password is incorrect for example.
[*]Just for testing purposes, I entered the wrong password, and then the message came that the password is incorrect, and I stayed on the "enter password" screen.
[/LIST]

Online people have told to log in to shell via CTRL + ALT + F3. I did that and I was able to log in then.
During that shell, my screen glitched a bit. I was able to see Ubuntu desktop on some parts of my screen.
People online suggested to look for .Xauthority folder, and I did everything, but it always said "no such file or direcctory".

I have no idea what to do anymore. I even tried installing Ubuntu with custom partitions, and the outcome was the same. It installed without errors, but always unable to login.

---

### Post by cmcanulty on 2020-07-09
This bug gets me once in a while try these 2 sites

[https://www.youtube.com/watch?v=togIj3hfbDs]("https://www.youtube.com/watch?v=togIj3hfbDs")

[https://www.maketecheasier.com/fix-ubuntu-login-loop/]("https://www.maketecheasier.com/fix-ubuntu-login-loop/")

---

### Post by ActionParsnip on 2020-07-09
Did you MD5 test the ISO you downloaded?

---

### Post by ninadkul on 2020-07-09
Can you check Graphics mode in UEFI and let us know or change it to hybrid mode? 

When i installed Ubuntu 20.04 on my lenovo x1 extreme laptop then i keep graphics mode as "discrete" while installing but once installation is done then i have change it back to "hybrid" graphics mode.

---

### Post by tea for one on 2020-07-09
> **smolla97 said:**
> 
[*]I made an username and password, and chose to option to "Log in automatically".
.

I think that, at this stage, it would be better to re-install and **not** choose automatic log in.

---

### Post by ajgreeny on 2020-07-09
There is no .Xauthority file in Ubuntu 20.04 though I believe it is present in most if not all the other flavours of *ubuntu; certainly it's in my Xubuntu 20.04

---

### Post by pqwoerituytrueiwoq on 2020-07-09
.Xauthority is a file not a folder
in my experience i can fix it by logging in at a tty (Ctrl+Alt+F2) and deleting the file

---

### Post by ubfan1 on 2020-07-09
Login to the virtual terminal off F3 again, and take a look at the X errors file in /var/log/Xorg.0.log   There may be several of them with slightly different names, but the error will be in all of tem I'd guess.

---

### Post by smolla97 on 2020-07-09
> **tea for one said:**
> I think that, at this stage, it would be better to re-install and **not** choose automatic log in.
This has fixed it. thanks!!!

---

### Post by tea for one on 2020-07-10
> **smolla97 said:**
> This has fixed it. thanks!!!

Splendid - Please mark the thread as solved to help other searchers.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

