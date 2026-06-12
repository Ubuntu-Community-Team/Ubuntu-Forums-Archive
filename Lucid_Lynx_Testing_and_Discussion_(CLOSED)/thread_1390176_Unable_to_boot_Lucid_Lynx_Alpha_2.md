---
title: "Unable to boot Lucid Lynx Alpha 2"
date: 2010-01-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by _SteveM on 2010-01-25
Hi All, looking for a bit of advice.

I've just downloaded a fresh copy of Lucid Lynx Alpha 2 32Bit (Server Edition), but can't get it to boot at all.

I've tried installing it several times and got the exact same result, it goes through the installation OK and everything installs.

When it comes to booting up, GRUB runs, tries to boot into Ubuntu and stops on:

[B]fsck from util-linux-ng 2.16
/dev/sda1/: clean, 50989/9592832 files, 863332/863332/38367228 blocks.[/B]

No other text on the screen, before or after the above.

Nothing else happens after this. It is a full install on a formatted (and freshly partitioned) Samsung IDE 160GB HDD.

Karmic was working fine until I formatted everything to try a fresh install of Lucid Lynx, but can't get it working!

**Things I have already tried;**
- Various installation setup options, guided partitioning and manual (with and without LVM)
- Verified the burned DVD (to make sure there are no corrupt files, and burned it again)
- Ran the tests on the Ubuntu DVD menu (seemed to pass OK)

**System Specs (It's not that new, but still runs Karmic quite fast):**
Samsung IDE 160GB HDD 7200RPM
AMD Athlon 64 2.4Ghz
ASROCK Motherboard
Netgear PCI NIC Adapter
128MB NVidia Card
1GB Kingstom DDR Memory (2x 512MB)
ASUS DVD-ROM

I don't really know what else to do, I can't even get to the command line to do anything after it's installed.

Any help would be great, I have tried to cover as much as possible but please let me know if you need any additional information.

PS. This is the first time I've EVER had any problems with Ubuntu, any versions - they have all ran on this hardware until now :(

Regards,
Steve

---

### Post by emarkay on 2010-01-25
Doesn't look like the hardware is the issue, unless there's some coincidental fault in a component.  Maybe there is an issue with the Server Alpha (I do not know about that) but to confirm, maybe try installing a Live CD iso and see if it goes OK.

May want to edit title to note "Server Edition".

---

### Post by _SteveM on 2010-01-25
Hi

I've just tried to install the Alpha 2 Desktop and stops before proceeding to the install with;

[B]init: ureadahead-other main process (1230) terminated with status 4
init: ureadahead-other main process (1231) terminated with status 4[/B]

I then rebooted and installed 9.10, which still installs and boots normally, I am still looking to get this Lucid Lynx working though :(

I did "Try Ubuntu with no changes to my computer" off that CD and got the exact same error as above. Does anyone know what "status 4" is?

Regards,
Steve

---

### Post by VMC on 2010-01-25
If you try using the recovery mode does it boot up then?
Also, if you can, edit grub, and add "nomodeset" at the end of the "linux" line, and re-boot.

---

### Post by Puck7 on 2010-01-25
There have been recent issues with the Daily CD's, so with the Alpha 2 CD also. You can search on some bugs on launchpad, but i'd just wait a couple of days, and the fixes will come, and then you can download the iso's again for testing purposes. You can find the daily images over at [http://cdimage.ubuntu.com](http://cdimage.ubuntu.com), if you wish you can report problems on IRC in channel #ubuntu-testing, the guys are great (:

---

### Post by jerrylamos on 2010-01-26
KMS is usually a PRIME suspect.

When the Grub2 boot screen comes up, 
e
on the linux line and add
nomodeset
just after quiet splash. 
Then CtrlX to continue.

If this works, then 
sudo gedit /etc/default/grub
and add 
nomodeset
just after quiet splash
save
do 
sudo update-grub

Another suspect could be splash.  Try removing that.

Ever since Ubuntu developers have been experimenting with Compiz and KMS with "new" tricks, there've been problems with video graphics ati, nvidia, intel, ...

I've had xorg problems with Alpha, Beta, Release code Intrepid, Jaunty, Karmic, Lucid, ....

I don't have any such problems with SUSE, Fedora, DebianLXDE, SliTaz, Slax, Knoppix, ....

I'm still primarily a Ubuntu user/tester because I like the community.

Good luck, 

Jerry

---

