---
title: "No internet Connectivity"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-09-15
Has anyone else experienced that they cannot access the internet with the latest set of updates? Im running a live cd to type. My networking is disabled although I changed nothing in that setup. Any ideas?

---

### Post by tekstr1der on 2009-09-15
Network Manager is not starting. To start / restart it manually:

```
sudo NetworkManager restart
```

---

### Post by sports fan Matt on 2009-09-15
Did anyone else experience this with the updates or am I an isolated case?

---

### Post by philinux on 2009-09-15
Never mind Internet mine wont boot at all now.

---

### Post by LinuxLars on 2009-09-15
I have the same issue. NetworkManager is not restarting for me.

Checking /var/log/syslog, I see a series of commands then:

<WARN> nm_dbus_manager_start_service(): Could not acquire the NetworkManager service as it has already been taken.
<WARN> main(): Failed to start the dbus service

I've tried:
sudo NetworkManager restart
sudo NetworkManager stop
sudo NetworkManager start

Any ideas?

---

### Post by sports fan Matt on 2009-09-15
Mine will boot, just not get online..that command was fetched " command not found" after sudo NetworkManager restart..Sorry to hear that phil.

---

### Post by sports fan Matt on 2009-09-15
I saw the xorg and all those updates..since those are misbehaving would it be better if I hold off on those?  

And network manager is installed..the latest is 0.8.

---

### Post by philinux on 2009-09-15
I'm using chroot from jaunty. Just upgrade karmic and a new network-manager was downloaded.

---

### Post by sports fan Matt on 2009-09-15
Will symanptic work even though I have no internet connectivity?

---

### Post by fut21 on 2009-09-15
> **sox fan Matt said:**
> Will symanptic work even though I have no internet connectivity?


No

---

### Post by Wise Ferret on 2009-09-15
I also suffer from the same problem: no internet connectivity on 32-bit karmic. Network manager seems disabled, and there is no clear alternative to it. Maybe I should try downloading wicd packages from my windows machine and install them as an alternative to NetworkManager...

---

### Post by sports fan Matt on 2009-09-15
So I wait I guess..I cant seem to update even if I wanted to. Oddly enough this is the only major issue I have had in 4 early upgrades of Ubuntu going back to Gutsy.  

Sudo etc/init.d/networkmanager restart said "command not found" as well. Latest network manager is 0.8

---

### Post by simondlandau on 2009-09-15
Hi, I'm running Ubuntu Jaunty Jackalope and can connect to various routers and then the internet, but not from my new home router, I can see my router with good strength, however, entering the correct password does not work. I am currently posting this via Windows. As I have no gaming or Quicken issues I would like to be rid of Windows. I have little knowledge of Terminal commands, SODU help, please.
Simon.

---

### Post by Wise Ferret on 2009-09-15
You will have to do more than waiting. If you have no internet connectivity, it means you have no way to download a fix for the problem.
I hope the WICD method will work...

---

### Post by sports fan Matt on 2009-09-15
Ok, Ive never used WICD...Not sure how it works.

---

### Post by Wise Ferret on 2009-09-15
ok, problem solved for me - all it took was typing in terminal:
sudo NetworkManager
and that's it. I hope it works for you too, sox

---

### Post by Vanishing on 2009-09-15
> **Wise Ferret said:**
> ok, problem solved for me - all it took was typing in terminal:
sudo NetworkManager
and that's it. I hope it works for you too, sox

o.o
are you sure?:lolflag:

---

### Post by jeroenvrp on 2009-09-15
Same for me, after the updates an hour ago. No network after reboot. sudo NetworkManager restart solves it.

---

### Post by sports fan Matt on 2009-09-15
Odd I tried that, it wouldnt work

---

### Post by LinuxLars on 2009-09-15
"wouldn't work" - can you be more specific? For me, the issue was also internet connectivity.

Can you ping an outside address?

---

### Post by cykotiktek on 2009-09-15
yah restarting the networkmanager did not work for me either.  I have a new copy downloading right now i am not worried the hunt is half the fun with alpha

---

### Post by Leighman on 2009-09-15
I did a reinstall in synaptic and that did it.  Although it's now prompting me to restart which I assume is where the problem arises =D

---

### Post by fut21 on 2009-09-15
> **LinuxLars said:**
> "wouldn't work" - can you be more specific? For me, the issue was also internet connectivity.

Can you ping an outside address?


Copy this "sudo NetworkManager" put it in a terminal

---

### Post by lnxguit on 2009-09-15
I also thought "sudo NetworkManager restart" was too easy.
But it works! :)

---

### Post by cykotiktek on 2009-09-15
personally I can't ping an outside address even after restarting the network manager.

---

### Post by DougieFresh4U on 2009-09-15
> **sox fan Matt said:**
> Did anyone else experience this with the updates or am I an isolated case?
Yes I had that 'drama' early this morning after updating my 32 bit install. I was trying wireless and wired. Kept re-editing  my addresses in 'Edit Connections' and got back online.

---

### Post by nchase on 2009-09-15
I had to type 'sudo dhclient eth0' to get back online.

---

### Post by eris23 on 2009-09-15
The modules for my wireless (rt61pci, rt2x00pci, rt2x00lib) stopped loading.

---

### Post by kaitwospirit on 2009-09-15
I killed NetworkManager, removed everything in the nm-applet, restarted NetworkManager, and made a new ethernet connection. Through this process I have been able to connect over ethernet (though not over wireless yet).

---

### Post by PhilippeK on 2009-09-15
For me that worked:

1. Edited the Connections, and retyped manually the Auto eth0.
2. sudo dhclient eth0
3. sudo NetworkManager restart : RECONNECTED

Hoping it helps

---

### Post by drfox on 2009-09-15
> **lnxguit said:**
> I also thought "sudo NetworkManager restart" was too easy.
But it works! :)

Make sure you capitalize the N and the M in sudo NetworkManager restart. Otherwise the command networkmanager restart will fail.

HTH

Larry

---

### Post by eris23 on 2009-09-15
No connection with wireless after today's upgrades.  I tried to restart NetworkManager (0.8~a~git.20090911t130220.4c77fa0-0ubuntu3), still no connection.  I downgraded to 0.8~a~git.20090911t130220.4c77fa0-0ubuntu2, connection would drop after a few seconds.  Installed wicd, it works perfectly.

---

### Post by Saneless on 2009-09-15
The restart command worked for me. Thanks, I was worried there

---

### Post by Eestlane on 2009-09-15
God, I tried everything, also sudo network-manager. Then I found this thread and saw that I should have used sudo NetworkManager instead. This worked. Thanks!

---

### Post by Nullack on 2009-09-15
The fix to this regression has been released by the devs

---

### Post by hgergo on 2009-09-16
I ca not conect wihout use pon-dslprovider

---

### Post by jeroenvrp on 2009-09-16
I can't even boot anymore :(

---

### Post by madmetal on 2009-09-16
sudo NetworkManager restart 
worked for me :)

---

### Post by eris23 on 2009-09-16
To get network-manager working again I had to delete my wireless profile in nm-applet, and then recreate it.

---

