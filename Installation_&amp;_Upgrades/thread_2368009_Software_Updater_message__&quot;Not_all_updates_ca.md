---
title: "Software Updater message:  &quot;Not all updates can be installed&quot;"
date: 2017-08-05
forum: Installation &amp; Upgrades
---

### Post by n4lbl on 2017-08-05
Hello:

On a 16.04 LTS (dual boot w/ Win10) I get the message in the title.  If I select “Continue” maintenance runs normally and I get the “Your machine is up to date” message.  Everything is satisfactory.


If I select “Partial Upgrade”  I get an “Do you want to start the upgrade?” message?  I don’t want to leave 16.04 LTS until a new LTS is available.  It doesn’t say if it is an upgrade to 16.10, 17.04, etc. or what it is.  What in the world is it talking about.  I am afraid to try without knowing what the outcome will be.

thanks,,,

---

### Post by kostkon on 2017-08-06
A partial upgrade will not upgrade your system to a new release. You can see what will happen by giving
```
sudo apt-get dist-upgrade
```
in a terminal. It will ask you if you want to go ahead with it, if you are still unsure, press N and then the enter key. Paste that output here if you want to enquire about it.

---

### Post by Bucky Ball on 2017-08-06
> **kostkon said:**
> 
```
sudo apt-get dist-upgrade
```

Just a note. Software Updater would have done this for you, but generally, ALWAYS run the update command before running the command given above. So:

```
sudo apt update
sudo apt dist-upgrade
```

As mentioned, the last command will NOT upgrade your current release to a newer one.

After running those two commands, does it show a clean bill of health and take you back to a cursor in the terminal? If so, reboot and see how you go. If not, post any error messages it throws between code tags (see link in my signature for how).

---

### Post by n4lbl on 2017-08-06
Thanks.  I still don't understand what the result is supposed to be.  

Yesterday I started the updater, hit "continue", the updater ran, and it ended with the message "the software on this computer is up to date".
If I run the updater yet again I still get the options "continue" or "partial upgrade".  Choosing "continue" gets the "the software on this computer is up to date" right away now.

What I want to understand is what the "partial upgrade" will do if I let it run.  
[INDENT]Will it start the upgrade to 16.10?
Will it start the upgrade to 17.04?
Is it really an upgrade and not an update?[/INDENT]
I don't want to upgrade until the next LTS is available.  

Of the four reasons enumerated by the updater message:
[INDENT]1) "A previous upgrade that didn't complete"  The upgrade to 16.04 LTS was done years ago and I run updates somewhat regularly.  This would have been caught years ago.
2) "Problems with some of the installed software"  There is nothing apparent and no messages.  
3) "Unofficial software packages not provided by Ubuntu"  Nothing I can think of and definitely nothing new in the last year.
4)  "Normal changes of a pre-release version of Ubuntu"  That obviously doesn't apply to 16.04 LTS.[/INDENT]

Lots of people who come here for help have serious and immediate problems.  My problem is certainly a lower priority.  Nevertheless, the symptoms that I've described indicate to me that something is wrong and that it would be good to solve it before I do upgrade to the next LTS which I guess is a few months away.

Many thanks,,,

---

### Post by n4lbl on 2017-08-06
I'n sorry I didn't show the results.  

max@slug:~$ sudo apt-get dist-upgrade
[sudo] password for max: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.10.0-21 linux-headers-4.10.0-21-generic linux-headers-4.10.0-22 linux-headers-4.10.0-22-generic linux-headers-4.10.0-24
  linux-headers-4.10.0-24-generic linux-headers-4.10.0-26 linux-headers-4.10.0-26-generic linux-image-4.10.0-21-generic
  linux-image-4.10.0-22-generic linux-image-4.10.0-24-generic linux-image-4.10.0-26-generic linux-image-4.8.0-53-generic
  linux-image-extra-4.10.0-21-generic linux-image-extra-4.10.0-22-generic linux-image-extra-4.10.0-24-generic linux-image-extra-4.10.0-26-generic
  linux-image-extra-4.8.0-53-generic linux-signed-image-4.10.0-21-generic linux-signed-image-4.10.0-22-generic linux-signed-image-4.10.0-24-generic
  linux-signed-image-4.10.0-26-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  gnome-software gnome-software-common gnome-software-plugin-snap grub-common grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed grub2-common
  libqt5concurrent5 libqt5core5a libqt5dbus5 libqt5gui5 libqt5network5 libqt5opengl5 libqt5printsupport5 libqt5sql5 libqt5sql5-sqlite libqt5test5
  libqt5widgets5 libqt5xml5 libwhoopsie0 python3-distupgrade python3-update-manager qt5-gtk-platformtheme shim-signed sudo
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk ubuntu-software update-manager update-manager-core whoopsie
32 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.6 MB of archives.
After this operation, 41.0 kB of additional disk space will be used.
Do you want to continue? [Y/n] ^C
max@slug:~$ 

Again, no crisis but I'm still concerned as this is new and different.

thanks,,,

---

### Post by Bucky Ball on 2017-08-06
You type 'y' and update/upgrade the machine. That should stop the partial upgrade message.

I will repeat: this will NOT upgrade your currently installed release to a newer one. It will upgrade your currently installed software to the latest it can be from the official repositories for your currently installed release.

I will also repeat that you should always run these two commands together:

```
sudo apt update
sudo apt dist-upgrade
```

;)

(When posting terminal output, please put it between code tags. See the green link in the first line of my signature at the bottom of this post.)

PS: I just noticed you have a heap of old kernels also. You could run this command before the other two to clean up the system.

```
sudo apt autoremove
```

Then the two commands above.

---

### Post by n4lbl on 2017-08-06
Thanks very much.  I appreciate your efforts.

---

### Post by Bucky Ball on 2017-08-07
No problems. I notice you marked the thread as 'solved'. Could you please confirm in a post that your problem is fixed and you are no longer getting errors? Thanks. ;)

---

