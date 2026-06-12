---
title: "Freeze on Gnome login after install"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by Antithesis on 2005-04-13
Hi,

Installed Ubuntu for the first time yesterday after not having *nix on my home system for over a year (new computer, so I figured time for new OS)

Anyway, I installed the amd64 srelease from the iso installer.
(Some of these problems may not be related, but I am listing everything, just in case...)

1) During install, no network adapter could be configured. I got a message saying if I want to proceed or go back, but when I go back, it scans for a sec, and gives me the error again before asking anything. I proceed
2) when asked if my hardware clock is GMT or local time, I notice that the current system time is 0 (actually, you don't even see zero, only a dot.)
Finished copying of files to local hard drive. After restart, I selected generic Default (2.6 kernel - first option). Again, it gives me the error that it could not detect hardware clock. I proceed.
All packages are installed, and I reach login screen
3) Upon logging in, I recieve the error - "could not connect to host (my local host name) - please edit /etc/hosts or try again". This isn't a real suprise, since I already know it didn't recognize any network adapter. Now the fun part - after I hear the login music, 
4) My computer freezes. Mouse doesn't responce. NumLock isn't responding. Can't switch to any terminal. I restart, and try again - same problem. 
Restart again, go into terminal, and try to edit /etc/hosts... but I don't know what the roor password is (installer didn't mention, I couldn't guess), so thats a no go.
I try failsafe install - as soon as I click my mouse on the radio button for failsafe gnome (or any other button in the menu, actually) - my computer freezes again.
I restart and go into recovery mode - works fine, but I don't know what to do that can fix this problem.

I read that there were some problems with ACPI - I disable it in BIOS, and reinstall ubuntu from scratch (with pci=noacpi flag, as well) - same problem as before.

Previously had 1 primary partition (sda1) with winXP install and its bootloader, along with 2 other extended partitions (sda2 & 3) for XP x64 and data storgae). USed the Ubuntu automatic partitioner.

Any help will be appreciated - Hell, thanks for actually reading this far!

System:
Asus A8V-E mobo  - includes VIA K8T890 southbridge and VIA 8237R controller. Also includes 2 Network adapters (marvell gigabyte and wirless g)
AMD 64 3200+ winchester core
Maxtor 160Gb
1 Gb Corsair ram
Everything is at pretty much stock settings.

---

### Post by Antithesis on 2005-04-15
Update:

Sorry for the silly question regarding root... read tfm and realized the errors of my ways... 
edited /etc/hosts... but that wasn't the problem, still hang when I try to login to GNOME.

Read somewhere that disabling sound solved the problem with another VIA board... tried that, didnt help either..

I can login to shell, but can't think of anything to do, since I don't have a network...

(e.g., apt-get KDE or something..)

Any help will be appreciated,

Thanks!

---

### Post by Antithesis on 2005-04-22
[QUOTE=Antithesis]Hi,

Installed Ubuntu for the first time yesterday after not having *nix on my home system for over a year (new computer, so I figured time for new OS)

Anyway, I installed the amd64 srelease from the iso installer.
(Some of these problems may not be related, but I am listing everything, just in case...)

1) During install, no network adapter could be configured. I got a message saying if I want to proceed or go back, but when I go back, it scans for a sec, and gives me the error again before asking anything. I proceed
2) when asked if my hardware clock is GMT or local time, I notice that the current system time is 0 (actually, you don't even see zero, only a dot.)
Finished copying of files to local hard drive. After restart, I selected generic Default (2.6 kernel - first option). Again, it gives me the error that it could not detect hardware clock. I proceed.
All packages are installed, and I reach login screen
3) Upon logging in, I recieve the error - "could not connect to host (my local host name) - please edit /etc/hosts or try again". This isn't a real suprise, since I already know it didn't recognize any network adapter. Now the fun part - after I hear the login music, 
4) My computer freezes. Mouse doesn't responce. NumLock isn't responding. Can't switch to any terminal. I restart, and try again - same problem. 
Restart again, go into terminal, and try to edit /etc/hosts... but I don't know what the roor password is (installer didn't mention, I couldn't guess), so thats a no go.
I try failsafe install - as soon as I click my mouse on the radio button for failsafe gnome (or any other button in the menu, actually) - my computer freezes again.
I restart and go into recovery mode - works fine, but I don't know what to do that can fix this problem.

I read that there were some problems with ACPI - I disable it in BIOS, and reinstall ubuntu from scratch (with pci=noacpi flag, as well) - same problem as before.

Previously had 1 primary partition (sda1) with winXP install and its bootloader, along with 2 other extended partitions (sda2 & 3) for XP x64 and data storgae). USed the Ubuntu automatic partitioner.

Any help will be appreciated - Hell, thanks for actually reading this far!

System:
Asus A8V-E mobo  - includes VIA K8T890 southbridge and VIA 8237R controller. Also includes 2 Network adapters (marvell gigabyte and wirless g)
AMD 64 3200+ winchester core
Maxtor 160Gb
1 Gb Corsair ram
Everything is at pretty much stock settings.[/QUOTE]
 Help!

I'm getting desperate....

Please, anyone?

---

### Post by Alexander Kirillov on 2005-04-22
[QUOTE=Antithesis]Help!

I'm getting desperate....

Please, anyone?[/QUOTE]
 login in failsafe mode and loot at the logs: /var/log/{messages, Xorg*} and also file 
.Xerror (or something like this - do not remeber  precisely) in user home directory
and post relevant pieces gere. It may give a clue.

---

### Post by pharina on 2005-04-22
I certainly can't provide you with a direct answer, but can offer you a suggestion.....which of course requires more work:

Get Knoppix 3.7, burn it onto a CD, and then see if it comes up on your system.    This MAY provide you with some necessary clues about why your ubuntu install won't come up.     Knoppix is a live cd, and doesn't require a Hard-disk install to come up.

Who knows, you might figure out something!!

Good luck!!

JR

---

### Post by Antithesis on 2005-06-26
Hi,

I gave up on trying to solve this, but now I have some time again, and would really like to get gentoo installed on my machine.

Following suggestions above, I found the following:
1) No combination of no acpi during boot or in bios setting solved this problem
2) Using the ubuntu live CD, I still get a freeze on login, suggesting this is a fundamental problem, not something I can fix by using sudo and reinstalling gnome (though I tried that too)
3) Looking through logs, I couldnt find anything significant, but I don't really know what I'm looking for, so I might be missing (Seeing as I can't login other than shell login and that the installer doesnt recognize my ethernet card, any suggestion on how to get log out so I can post it here, if you really think it would help?)

Anyone managed to successfully install this version for this motherboard (Asus A8V-E ?)

Any help would be appreciated,

Thx.

---

