---
title: "Problems setting up a dual boot Ubuntu+Windows system"
date: 2016-12-01
forum: Installation &amp; Upgrades
---

### Post by orthoducks on 2016-12-01
I want to set up a dual-boot system by installing Ubuntu first, then Windows. I'm following instructions that I found at [http://lifehacker.com/5403100/dual-boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual-boot-windows-7-and-ubuntu-in-perfect-harmony). The concept is to boot Ubuntu from the distribution disk, then use GParted to create the required partitions, then install Ubuntu in one and Windows in another.

I burned a DVD from the Ubuntu 16.04.1 distribution, and I can boot it. Things go south when it's time to start GParted. The instructions say to "head to the System menu in the upper left when you get to a desktop, then choose the Administration menu and GParted under it." But there is no System menu. The menu bar displays the name of the active window on the left, followed by that window's menu, but no *System* menu, ever. There's a *System Settings* icon in the left sidebar, but it's just what it claims -- settings -- with no GParted in evidence.

The instructions are several years old. Probably Ubuntu has changed, and they don't reflect the way it works now.

How should I handle this? Is there a way to run GParted or the equivalent from a current distro, or should I do something else to get where I want to go?

---

### Post by Mark Phelps on 2016-12-01
There are different Ubuntu desktops and the one that has the menus is the Mate version.  As I like menus, and do not like big buttons (i.e., smartphone desktop), I use Mate instead of the Unity desktop.

You need to make installation media of the Mate version, if you want a desktop with menus.

---

### Post by oldfred on 2016-12-01
Is your hardware UEFI or BIOS?
How you partition if partitioning in advance makes a difference.
Windows only boots from MBR with BIOS.
Windows only boots from gpt with UEFI.
And how you boot install media is then how it installs, which may auto convert from MBR to gpt or vice versa erasing system.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

And in UEFI mode with gpt Windows has requirements for extra partitions, ESP, reserved, install, recovery and maybe others.

You can start gparted from Ubuntu live installer if Ubuntu, some flavors may not have gparted as a standard application, but then have other partition tools or gparted can be installed into any Ubuntu flavor.

---

