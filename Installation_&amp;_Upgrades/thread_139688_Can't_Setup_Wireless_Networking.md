---
title: "Can't Setup Wireless Networking"
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by Maverick88 on 2006-03-04
I just installed Breezy Badger.  Since I use wireless encrypted networking, Breezy Badger was not able to properly setup my networking during installation.  

I have rebooted into the GNOME desktop.  I tried SYSTEM - ADMINISTRATION - NETWORKING, but the networking app just dies after I enter my password.  (It makes no difference if I enter my User password or my root password).  I see the whell turning and the "Starting Networking" in the taskbar, but then it just disappears.  Strange.  


I also tried setting up networking at the command prompt using iwconfig.  I can  select my access point and specify the key but I can't get DHCP to work.  There does not seem to be a dhcpcd command.  


Any ideas on what I must do to get networking working?
Do I need to reinstall Breezy Badger and somehow get networking working during installation?

Rob

---

### Post by Maverick88 on 2006-03-04
FYI - Wireless Networking works fine with the LiveCD of Breezy Badger.  I can use System - Administration - Networking to set up the encrypted wireless networking.  

But once I installed Breezy, I can't do the same thing.  The Networking app just dies.  

I am using a Toshiba Laptop with a Atheros AR5001X chip.

Any help would be greatly appreciated.

Rob

---

### Post by Maverick88 on 2006-03-04
I think I solved it.

Apparently, when you use the expert mode during installation, the sudoer file is not preperly created.  I had to add my regular user as follows:


harry  ALL=(ALL) ALL

Now I can set up networking using the GUI.  

Rob

---

