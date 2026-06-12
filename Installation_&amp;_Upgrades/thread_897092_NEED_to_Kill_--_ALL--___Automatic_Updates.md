---
title: "NEED to Kill -- ALL--   Automatic Updates"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by dgoddard1 on 2008-08-21
I need to kill all automatic update features.  I am new to Ubuntu and fairly new to Linux.

My rural location has _**only**_ slow dial up connection and I need to prevent  the operating system and all software from attempting any automatic updates.  

If I need any updates they will usually be so large that I will need to wait until I go to the library in town where I can use wireless.

I am buying a Dell laptop with Ubuntu and I presume that they will believe that they are doing me a favor by making sure that every form of automatic update is turned on. :(  

I will need to know how to find and assess the status and turn off any automatic update features in
A.
The Ubuntu operating system
B.  
The usual open source software that comes with most distributions

---

### Post by robert shearer on 2008-08-21
System=>Administration=>Software Sources

Open the Updates tab and uncheck the "check for updates" under Automatic updates.

---

### Post by Cheesehead on 2008-08-21
_Step 1_ - Today.

Yes, you can turn off Automatic Updates.

Another option is to go into System-->Administration-->Synaptic and remove (uncheck) the following packages:
update-notifier
update-notifier-common

This removes the update daemon that you're not using anyway. It does a couple things - it controls the little update notification icon in your system tray, it downloads updates in the background (but only installs security fixes automatically), and it reminds you to run Update Manager (step 2) for the rest of the updates.

So you can see that having it is quite optional, and removing it is an easy, reversible process that will not harm your system. You can always reinstall the packages at any time by checking the boxes again.

[U]
Step 2[/U] - When you're in town and online.

Do System-->Administration-->Update Manager to keep your system up to date. You needn't do it often, but you'll keep the updates much shorter if you run it monthly or more often. 
A few big updates might take up to 20-30 minutes to download (depending on your network connection, of course) and install...*and you should not interrupt it while it's working*. You can, of course, minimize or move the window, and you can let it work in the background while you surf or e-mail or continue to work on your system.

---

