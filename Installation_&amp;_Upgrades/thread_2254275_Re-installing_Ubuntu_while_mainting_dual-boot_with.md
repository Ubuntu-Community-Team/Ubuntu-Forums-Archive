---
title: "Re-installing Ubuntu while mainting dual-boot with Windows?"
date: 2014-11-26
forum: Installation &amp; Upgrades
---

### Post by Cl0ner on 2014-11-26
[SIZE=2][FONT=tahoma][COLOR=#333333]I am kinda new to ubuntu and the whole linux field, and have some concerns.
[/COLOR]
[COLOR=#333333]First, I currently have Linux Mint 17 dual booting with Win8.1 via grub 2, my question is how to remove linux mint and install ubuntu instead while keeping the windows untouched.
[/COLOR]
[COLOR=#333333]I can go ahead and give it a shot by formatting the mint's partition but i already had enough failures this week installing mint (14 freaking hrs) so i want to do it right this time, if format the the mint and swap partitions and recreate them with bigger sizes will grub identify the change and remove the mint's entry and recognize windows?
[/COLOR]
[COLOR=#333333]Im installing in 1 TB HD and 300 gb left, and giving 100 gb for ubuntu divided between (/, /home, /swap) how much space to give each? considering i have 8 gb physical ram.
[/COLOR]the scheme i have in mind at the moment is
[/FONT][/SIZE]```
/        30 gb
swap        10 gb
/home        60 gb

```

[SIZE=2][FONT=tahoma][COLOR=#333333]when making a separated home partition and happens that i want to reinstall/upgrade/change dist, will the new system recognize that /home partition from previous installation or will i have to recreate or point to it manually?[/COLOR]

[COLOR=#333333]What i want is a stable dual booting machine that i dont have to reconfigure in the long run.[/COLOR]
[COLOR=#333333]
Please advice.[/COLOR][/FONT][/SIZE]

---

### Post by sudodus on 2014-11-26
0. You should ***backup everything valuable***, your  personal data as well as Windows, so that you can restore it, if you  have bad luck, because editing partitions and installing operating  systems is risky.


1. Decide how to do it. It is possible to install like you describe. If you want to hibernate, 10 GB is fine for swap, otherwise I think 2 GB would be enough unless you intend to run some application, which really needs a lot of memory.

You might be able to keep the home partition (without wiping it), it  would save your personal settings but may create some problem because  you switch from one distro to another. I would save the personal files  and let the installer format the root partition and also format the home  partition.


2. You can do the partitioning/formatting with ***gparted*** (when booted from the Ubuntu install drive). I like gparted, it has a good graphical user interface.


3. Then start the installer. Please select ***Something else ***at the partitioning page. It will give you the best control of what is happening.

---

### Post by oldfred on 2014-11-26
Backups & only use Something Else. 

 Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but mulitiple drive installs must use Something Else. And fix is not in current versions as ISO install version is not changed.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

If you understand partitions a bit and are willing to edit fstab to add a data partition, that can work better than a separate /home when changing distributions. All your data is still in a different partition and only the user settings are in /home. Then a separate /home is not required as it is so tiny.
Otherwise a separate /home is easier to set up, but you must use Something Else. And with every re-install you have to also mount it, but DO NOT tick format box, otherwise data is erased.

      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[URL="http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html"]http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html
[/URL]
 [http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

Also backup the efi partition.
You will have to manually remove Mint folder in efi partition and then remove mint entry in UEFI's NVRAM with efibootmgr. 

More info in links in my signature.




[URL="http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html"]
[/URL]

---

### Post by Cl0ner on 2014-11-27
Thanks for the help.

I ended up shrinking an ntfs partition from windows, deleting the old swap and /root partition, and recreating them with bigger spaces (10gb swap, 90gb /root no seperated home) and everything working as intended.

feels better being on ubuntu, shes a beauty.

---

### Post by Bucky Ball on 2014-11-27
Sounds good, but the /swap is excessive. 2Gb generally suffices, unless you hibernate a lot, then the size of your installed RAM or larger is best. Good luck and enjoy! ;)

---

