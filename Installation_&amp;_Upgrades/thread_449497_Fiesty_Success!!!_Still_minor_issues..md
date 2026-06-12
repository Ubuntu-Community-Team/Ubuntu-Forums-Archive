---
title: "Fiesty Success!!! Still minor issues."
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by jholsenback on 2007-05-20
Hello,

Well I finally was able to get the Fiesty LiveCD to run. Thanks to user jerrylamos and information from this thread: [http://ubuntuforums.org/showthread.php?t=424225](http://ubuntuforums.org/showthread.php?t=424225)

I was having "can't access tty" errors ..... from the initial LiveCD menu I pressed F6 and added break=top to the boot options. Once the error shelled out I entered "modprobe piix". After a short delay I got the command line again and entered "exit" The Live CD started up just fine. BTW before I did this I completely removed my "Windoze" XP disc from the system and added a new WD200GB drive which I was able to then install 7.04 without a hitch. I shutdown my system (Dell 8250) and reinstalled my XP drive as IDE Master and 7.04 as slave. Now I'm back in Windoze with these issues yet to be resolved.

1) Dual boot two drives with XP as default boot (I'm not the only user on this system)
2) Nvidia GeForce4 Ti 4200 drivers
3) Modem setup (sorry no high speed way out here in the boonies)

I'm going to do some digging and try to begin resolving these issues. I'd appreciate any pointers that anyone might have to get me going in the right direction.

Jim

---

### Post by starcraft.man on 2007-05-20
1) You can edit GRUB (I don't know whether its installed to your second drive or first) to default XP to the top of the list, and thus it will boot to that when it times out. I also don't see why it couldn't handle both OS on both drives. If you want something maybe a bit easier, perhaps you would be interested in [GAG,]("http://gag.sourceforge.net/") though I use it more for recovery purposes, GRUB is better IMO for daily use. You should probably read up on [GRUB]("http://users.bigpond.net.au/hermanzone/") here, and try to get that working for you. Keep grub nearby if you make a large error your having trouble correcting.

2) Drivers for Nvidia cards can be gotten with [Envy,]("http://www.albertomilone.com/nvidia_scripts1.html") download and run by double click. Then go Applications > System tools >envy and select automatically install nvidia drivers. Then answer yes to everything and reboot at the end.

3) I haven't used dial up in ages, can't help, I certainly don't know how to use it on Linux, I should prolly find out.

---

### Post by jholsenback on 2007-05-20
Hey thanks for the links ..... I found a dual boot option that's working just fine although I get two splash screens from Dell .... something about service number or hardware tag. It just says press any key to continue, so I do and it does ..... continue that is! Has anyone else seen this and know what it's trying to tell me. Maybe it thinks I've pirated something. I'm legit so it's no worries for me. Just a minor inconvience.

I checked out the "Envy" link and downloaded the package and will give it a go .... Thanks!!!

I'm still trying to make heads -er- tails of scanModem output from linmodems.org .... well I'm making progress.

Again thanks for the reply.

Jim

---

