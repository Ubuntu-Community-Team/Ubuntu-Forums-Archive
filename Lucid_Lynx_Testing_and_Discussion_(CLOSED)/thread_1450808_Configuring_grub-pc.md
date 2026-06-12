---
title: "Configuring grub-pc"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by drumorange on 2010-04-09
During the partial-upgrade of Lucid, this popped up... How do i figure out which one to click??

---

### Post by drumorange on 2010-04-09
I have Vista installed on my first internal HDD (plus a recovery partition created by HP) and Ubuntu on my second internal HDD.

---

### Post by note32 on 2010-04-09
i think its asking where you want to install grub

---

### Post by note32 on 2010-04-09
just select one of the options it gives you and deselect the rest

---

### Post by kansasnoob on 2010-04-09
You need to know which device you want to install grub on. I can see you have two drives - /dev/sda and /dev/sdb but I can't be sure which drive is the first to boot in BIOS.

I can tell you it's almost never a good idea to install grub to a partition, eg: /dev/sda1 so you'd want to choose either /dev/sda or /dev/sdb. It's impossible for me to know which, this is something that needs to be planned in advance of installing.

More to follow!

---

### Post by kansasnoob on 2010-04-09
> **note32 said:**
> just select one of the options it gives you and deselect the rest

Feeling reckless are we? Flip a coin? Draw straws?

---

### Post by kansasnoob on 2010-04-09
In this case choose to install grub to both /dev/sda and /dev/sdb BUT NOT ANY PARTITION!

If necessary to restore a Windows readable mbr to either drive that's a piece of cake!

DO NOT install to any device ending with a NUMBER! Only sda and sdb!

---

### Post by drumorange on 2010-04-09
So after seeing your responses (thanks!) I went back to finish updating and the program had frozen, so I just restarted it... but now the same thing comes up but in this form:

[IMG]http://img689.imageshack.us/img689/2088/screenshot1nnf.png[/IMG]

How do I unselect them?? If I highlight the one I want to deselect and press ENTER it just continues with them all selected. TAB makes it highlight OK, though. I'm confused... hmm.

---

### Post by kansasnoob on 2010-04-09
More specific info related to your machine, from what you've said (and some general info):

#1: Drive sda must be the Windows drive with sda1 being Vista and sda2 being recovery (my guess based on size of the partitions).

#2: Drive sdb must be Ubuntu with sdb1 being Ubuntu's root "/" partition, sdb2 being an extended partition, and sdb5 being a logical SWAP partition contained in the extended partition.

#3: No harm will be done by installing grub to the mbr (master boot record) of both drives. That's why the pop-up to the right of your sreenshot says, "If you're unsure .............. install to all of them".

But it's almost never a good idea to install grub to a partition rather than the mbr of a drive!

#4: If my guesses are right, and if you ever removed the Ubuntu drive you can restore the Vista mbr either by following these instructions:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Or using an Ubuntu Live CD and running:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sd**[COLOR="Red"]X[/COLOR]** mbr
```

Of course in your case **[COLOR="Red"]X[/COLOR]** would be "a", eg: **/dev/sda**

#5: To remove any guess work from the equation you can use this great tool:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

#6: Even if you really mess up you can recover from it. For instance:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

The bottom line is, "never panic"! Plan ahead and if something goes wrong be prepared!

#7: Because of differences between legacy grub and grub2 know how to tell the difference. I'll not go into great detail right now but there again the Boot Info Script provides enough info top tell if there's a problem.

---

### Post by kansasnoob on 2010-04-09
> **drumorange said:**
> So after seeing your responses (thanks!) I went back to finish updating and the program had frozen, so I just restarted it... but now the same thing comes up but in this form:

[IMG]http://img689.imageshack.us/img689/2088/screenshot1nnf.png[/IMG]

How do I unselect them?? If I highlight the one I want to deselect and press ENTER it just continues with them all selected. TAB makes it highlight OK, though. I'm confused... hmm.

Ouch! Partial upgrades are almost always bad news:

[http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)

---

### Post by kansasnoob on 2010-04-09
If you can still boot the Ubuntu OS try running:

```
sudo apt-get clean
```

which may clear the "package cache", then try:

```
sudo apt-get dist-upgrade
```

If you can't boot into Ubuntu boot any Ubuntu Live CD and post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kansasnoob on 2010-04-09
Duh moment on my part!

Try using the "tab" key and the "enter" key to change those selections!

Edit: maybe the up and down arrows will let you go from device to device, then maybe the Tab key will let you change the tic mark to no tic mark, then the Enter key might save that decision. I hope!

---

### Post by mdurham on 2010-04-09
> **kansasnoob said:**
> Duh moment on my part!

Try using the "tab" key and the "enter" key to change those selections!

Edit: maybe the up and down arrows will let you go from device to device, then maybe the Tab key will let you change the tic mark to no tic mark, then the Enter key might save that decision. I hope!

Doesn't the space-bar do that?

---

### Post by kansasnoob on 2010-04-09
> **mdurham said:**
> Doesn't the space-bar do that?

Do what?

We're talking about changing a "tick" to a 'tick-off" aren't we?

To be honest I've never seen what the OP is dealing with, but I have a lot of experience with grub and/or grub2 so I replied with the best of my knowledge.

This makes me think I should do some multi-drive distribution upgrading but I'm just about double-stacked on bug chasing!

---

### Post by ranch hand on 2010-04-09
Space bar should select.

If booting both drives from the same menu I would select both sda and sdb and make very sure that all others are not selected.

This will hurt nothing and should make sure that both drives boot.  This can be changed if needed.

---

### Post by drumorange on 2010-04-10
Fixed by entering the following into the terminal:

sudo apt-get install testdisk
sudo testdisk

and then following the following steps:

  First   screen:  Select "No Log" and press enter.
  Second  screen:  Select the hard drive containing  the Windows system partition and  choose "proceed".
  Third   screen:  "intel"
  Fourth  screen:  "advanced",
  Fifth   screen:  Select the Windows system partition  and choose "boot"
  Sixth   screen:  "BackupBS"
  Seventh screen:  type "Y" to confirm
 
Then press q a few times to exit out. Restart the computer in Vista.

Thank you everyone for your help.

---

