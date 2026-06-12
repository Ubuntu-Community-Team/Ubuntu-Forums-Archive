---
title: "Problem when updating from 12lts to 14.04lts"
date: 2014-09-26
forum: Installation &amp; Upgrades
---

### Post by killid on 2014-09-26
Hi

I hope someone can help?

After updating from 12lts to 14.04lts I have 2 problems when starting my laptop.

The first is I keep getting the following message on startup:  System program problem detected
The second is my laptop sometimes refuses to start correctly - after initially starting and only a few seconds later I have a blank screen.  I close the laptop and usually on the second try it starts ok with the above message - System program problem detected.

Some guidance would be much appreciated by this ubuntu novice.  
Thanks
David

ps would never go back to MS Windows.

---

### Post by Bashing-om on 2014-09-26
killid; Hello and Welcome to the forum .

Maybe no big deal. Let's check and make sure the package manager is in a happy state:
Terminakl commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

``` If and when these run clean, we take a look at the graphics situation ( as we now have a firm foundation from which to work from ).
IF there are errors reported, then post the command and it's output back to the thread - BETWEEN Code Tags, please .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Maybe also to be highly considered is 3rd party software installed in 12.04 that has no support in 14.04 (??) ..

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by killid on 2014-09-26
Hi Bashing-om

I ran the 3 commands in terminal and couldn't see any errors.  I didn't understand the result of the 3rd:
```

 killid@killid-HP-ProBook-4510s:~$ sudo apt-get dist-upgrade
[sudo] password for killid: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
killid@killid-HP-ProBook-4510s:~$

```
After running the 3 commands I closed my laptop and then restarted it.  I again got the following  - System program problem detected, however my computer did start first time.

May I say how much I appreciate your help with my problem

Best wishes
David

---

### Post by slickymaster on 2014-09-26
Hey killid, be very welcome to the forums.

I've just edited your last post because what's intended to be placed within the code tags it's the outputted code itself, not your observations/requests.

---

### Post by Bashing-om on 2014-09-26
killid; Well, well ...
That indicates that overall the system is stable.

As to:
> 
I didn't understand the result of the 3rd:
 killid@killid-HP-ProBook-4510s:~$ sudo apt-get dist-upgrade

Using apt-get's smart mode; dist-upgrade is also able to remove existing packages if required/and install held back packages. A dist-upgrade will install new dependencies for packages already installed and may remove packages if they are no longer needed. This will not bring you to a new release of ubuntu.
The 0 0 0 0 0 output is nothing to do .. all is as up-to-date as Scott snuff - which is a great thing in this case -.

So that was not real productive. let us do look at the graphics, see if there is a problem there;
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

``` and take a look at the log file, see if the system is reporting a problem:
```

grep EE /var/log/Xorg.0.log
grep --ignore-case err /var/log/dmesg

``` where 'EE' denotes an error condition.

[INDENT][INDENT]I am becoming comfortable with
[INDENT][INDENT][INDENT][INDENT]the notion, not a big deal
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by killid on 2014-09-29
Hi Bashing-om

These are the result I got :-

```

 killid@killid-HP-ProBook-4510s:~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:3072]
    Kernel driver in use: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
killid@killid-HP-ProBook-4510s:~$ sudo lshw -C display
[sudo] password for killid: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:70f0(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d0400000-d04fffff
killid@killid-HP-ProBook-4510s:~$ grep EE /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.443] Initializing built-in extension MIT-SCREEN-SAVER
killid@killid-HP-ProBook-4510s:~$ grep --ignore-case err /var/log/dmesg


```

I must admit I don't understand them and your guidance is very much appreciated.

Many thanks
David

---

### Post by Bashing-om on 2014-09-29
killidl Humm;

Everything looks good. All we are looking at here is what chip set you have for graphics, and IF the proper driver is being utilized. Then looking to see if the system is reporting any graphical errors.
You have " Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller " for the chip set, and the driver is "i915".

As I say all looks good, and as I have no means to test the Intel hardware I do not know what else I can to at this time to aid you.

[INDENT][INDENT]regrets
[INDENT][INDENT][INDENT]I am halted at Intel
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by killid on 2014-09-30
Hi Bashing-om

Many thanks for all your help, it is very much appreciated.  It looks like I will just have to cancel and ignore the 'system program problem detected' message.

Like myself my laptop is now getting on in age and will soon need to be replaced with a more up to date model.  I will be dumping any MS Windows packages installed and replacing with Ubuntu.  I just love Ubuntu, I just wish I was more technically minded.  With people like yourself helping and giving advice will hopefuly encourage many more older users on board.  

Best wishes
David

---

### Post by Bashing-om on 2014-09-30
killid; Thanks ->

For your kind words. However, my attitude is not uncommon in this community.

Something to consider, as this is 'older hardware' -> (L)ubuntu !
(L)ubuntu is designed to run on older hardware, and I have been impressed with how well it runs on "difficult" hardware.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Knowledge and experience only comes with time and effort.

[INDENT][INDENT]only get out, what you put in
[/INDENT][/INDENT]

---

