---
title: "How to re enable hibernation and make it actually work on ubuntu 14.04?"
date: 2014-06-09
forum: Installation &amp; Upgrades
---

### Post by serouj2 on 2014-06-09
[COLOR=#000000]my hibernate doesnt work -_- and the terminal command sudo hibernate-pm [/COLOR][SIZE=2][COLOR=#333333][FONT=Monaco]doesnt work either and just makes my monitor turn off and turn on and then gets back to where it was ....my hibernate doesnt work and its the most important thing for me[/FONT][/COLOR][/SIZE][IMG]http://ubuntuforums.org/images/icons/icon8.png[/IMG]

---

### Post by grahammechanical on 2014-06-09
> [COLOR=#333333][FONT=Ubuntu]Unfortunately, hibernate [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][doesn't work]("https://help.ubuntu.com/14.04/ubuntu-help/power-suspendfail.html")[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] in many cases, which can cause you to lose data if you expect your documents and applications to re-open when you switch your computer back on. Therefore, hibernate is disabled by default.[/FONT][/COLOR]

[https://help.ubuntu.com/14.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/14.04/ubuntu-help/power-hibernate.html)

[https://help.ubuntu.com/14.04/ubuntu-help/power-suspendfail.html](https://help.ubuntu.com/14.04/ubuntu-help/power-suspendfail.html)

[https://help.ubuntu.com/community/PowerManagement/Hibernate](https://help.ubuntu.com/community/PowerManagement/Hibernate)

---

### Post by serouj2 on 2014-06-10
i may not even have a swap partition ...how do i add one?

---

### Post by grahammechanical on 2014-06-10
> **serouj2 said:**
> i may not even have a swap partition ...how do i add one?

That is unlikely. The installer automatically creates a swap partition unless we specifically instruct it not to. Open the Disks utility. That will show you the partitions, including swap, and their sizes. It is most likely that the swap partition is too small for hibernation to work.

Yesterday, being a curious person, I decided to test if hibernation worked on my motherboard. I ran pm-hibernate. The first time the machine shutdown and then immediately reloaded to the desktop with the applications open. But it took along time to get to the resumed state. The second time the machine switched off and when I rebooted it did not resume but came to the login screen and a desktop with no applications opened. Since then upon rebooting I get an error message about a failure to resume.

I am using the 14.10 development branch and crash reporting is enabled by default. Which is not the case with 14.04. So, you may not get error reports but it does show that Linux does have problems with hibernation due to the complexities of hardware and BIOS/UEFI boot systems.

By the way, we can use Gparted from a live session to resize partitions but we have to tick swap off in order to change the size of the swap partition. That is after we have created unallocated space for it to expand into.

Regards.

---

### Post by mastablasta on 2014-06-10
on the bright side suspend often Works.

also boot is much faster or as fast as in windows8 + you can save the session. e.g. KDE by default saves the session so let's say you just turn it off with various porgrams loaded when you boot backup it will load the programs and internet sites that were running in previous session.

---

### Post by serouj2 on 2014-06-10
this is how much my swap area is ...is it enough? and are you sure its because of the swap file that the hibernation doesnt work? seriously ..hibernation is the most important thing for me and suspend doesnt shut the computer completely off so i dont even need suspend at all :mad:..[ATTACH=CONFIG]253879[/ATTACH]

---

### Post by QIII on 2014-06-10
Unless you have 189MB or less of RAM, that is not enough.  Ubuntu checks that, sees that you don't have enough swap to preserve the RAM state and can't hibernate.  Linux does not dynamically adjust the space allotted on the disk as Windows does.  It is fixed at the time you create your partitions.

Yes.  You need swap to hibernate.  It used to be called "Suspend to disk".  You need enough swap to entirely preserve your RAM state -- all of it.

Theoretically, a swap exactly the same size as your RAM is sufficient.  All the old "twice your RAM" wisdom is outdated now.  In fact, I don't use any swap on my desktops because they all have 16GB+ of RAM and I don't hibernate them.

To hibernate, however, you do need that swap and it needs to be able to preserve your RAM state.  110 - 115% of RAM should do it on the safe side.  But if you have high swappiness and there is stuff already in swap, you need RAM size PLUS whatever is there already.  So maybe 125% or 150%.

How much RAM do you have?

---

### Post by serouj2 on 2014-06-10
dude my ram is 2GB

---

### Post by serouj2 on 2014-06-10
so what do i need to do? my hard disk is 500GB LOL ...i can resize if thats what is needed

---

### Post by QIII on 2014-06-11
My recommendation is that you will need to increase your swap partition to at least 2.2GB (that's the 10% extra) plus whatever you find is the typical swap use during normal operation (if any).

With your somewhat odd partition table, you may find that you mess up your UUIDs.  If that is the case, you may have to manually edit your fstab to make sure everything matches.

---

### Post by serouj2 on 2014-06-11
i resized the swap partition to 1.something GB ...i reinstalled ubuntu to resize it -_- still hibernation doesnt work

---

### Post by serouj2 on 2014-06-11
WAHOOOOOOOOOOOOOOOOOOOO it worked :D finally my hibernation works ^.^ the resize partition did it ...1 GB did it lol ...XDDDDDDD

---

### Post by mastablasta on 2014-06-11
you said you have 2 GB ram so your /swap should be equal or slightly more than 2 GB. 

you set it to 1. something GB - prepare to suffer now. :P or rather when you actually have a bit more programs running when you hibernate...

---

### Post by serouj2 on 2014-06-11
so i have to resize it to 2GB?

---

### Post by serouj2 on 2014-06-11
i made it 3.05 GB will it work now?

---

### Post by Vladlenin5000 on 2014-06-11
> **serouj2 said:**
> i made it 3.05 GB will it work now?

It should.

---

