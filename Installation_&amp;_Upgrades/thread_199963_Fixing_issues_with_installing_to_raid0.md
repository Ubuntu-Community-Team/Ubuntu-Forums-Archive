---
title: "Fixing issues with installing to raid0"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by jewishj on 2006-06-19
I have recently installed Dapper to my SATA RAID0 using the onboard motherboard fakeraid controller.  I ran across a few issues using the [http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto) and [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) how-tos.  I figured I would relate my experiences to help anyone else who is having similar issues.  I already tried to update the wiki pages mentioned, but was not able to.

so here are the steps I took to get everything successfully working:

1) Follow [http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto) steps until you get to the part where you chroot into the target system (sudo chroot /target).  Note: during the format part, run the commands from terminal rather than trying to use gparted.

2) Run the following commands:

```

export LC_CTYPE=C
export LC_MESSAGES=C
export LC_ALL=C
apt-get install language-pack-en-base
tzconfig
dpkg-reconfigure locales

```

3) Continue to follow the steps in [http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto) (use [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) for more info on setting up grub correctly)

4) Ignore the part that says enter base-config to configure the base system (command is deprecated) and finish the steps outlined in the howto.

5) When you reboot, go to the recovery mode instead of normal install and get to the root command line.  Run the following commands:

```

passwd (sets root password)
adduser <username>
addgroup <groupname>
adduser <username> <groupname>
visudo (add user info for user you just added to resulting file)
reboot

```

6) Go to normal desktop and you should be set.  If the System->Administration menu is missing alot of options, open a terminal, use the adduser command to add a new user, logout and login as them.  They should have all the menu items.  Go to users and groups in the System->Administration menu, choose the original user, click on properties, go to the privilege tab, and check everything.  (I dont know how to do this from the terminal).

Anyways, that's how I got it working for me, so I hope this can help someone else.

Regards

---

### Post by etheberge on 2006-08-11
Thanks man, that last part starting from step 4 really helped me out.

---

