---
title: "No OS choice in GRUB menu after updating Ubuntu 10.04"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by supriyo on 2010-05-19
A typical problem I faced:(
 I installed Lucid Lynx in my p4:2.66 hz machine with XP sp3  pre-installed and the system booted just fine with dual boot option.  Then I updated my Lucid. All updates were downloaded. But during update  installation a power failure caused PC reboot. Again I started update  manager and it gave me option for "Partial Upgrade". I did the same and  it instructed me to reboot. The the real damn thing happens now when I  rebooted, In the GRUB menu it showed only Memorytest options. I see no  OS choice there, I tried to reinstall GRUB from live CD with mount  options. And it showed no errors during the procedure. I rebooted but  the same problem exists.
:confused:Please help  me out to get back my distro.:(
 Thanx.

---

### Post by darkod on 2010-05-19
Follow these instructions to run the boot info script and post the content of your results file as instructed:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

It sounds like your kernel(s) are missing, maybe because of the power failure. If there are no kermels, no boot options. XP should still be there, have no idea why it doesn't show. Lets see the results first.

---

### Post by Matti L on 2010-05-19
[Using CLI to Boot]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot")

---

### Post by supriyo on 2010-05-20
> **darkod said:**
> Follow these instructions to run the boot info script and post the content of your results file as instructed:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

It sounds like your kernel(s) are missing, maybe because of the power failure. If there are no kermels, no boot options. XP should still be there, have no idea why it doesn't show. Lets see the results first.
Yes Xp is still there....and I managed to get XP back by trying FIXMBR command in XP repair mode. Now what to do?????coz i can remount the GRUB menu.should I DO that?
or just lboot from live cd????and do as u instructed???:confused:
Ok here is my boot log results after I tried FIXMBR command in XP and  booted in XP but did no harm to linux partition ..I will also post the  original state I faced after I tried to remount the OS.
below is the link
[http://ubuntuforums.org/attachment.php?attachmentid=157681&d=1274374982](http://ubuntuforums.org/attachment.php?attachmentid=157681&d=1274374982)

---

### Post by oldfred on 2010-05-20
You have a couple of choices. reinstall grub and manually edit the menu item to boot. Or chroot into your system and update from there. You do show kernel but if the install did not complete correctly you may need the chroot to repair it.

Kansasnoob has chroot instructions & he puts everything on one line to make it easy to copy & paste:
kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

When in your chroot:
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages update must be run first
#would upgrade you to the latest kernel in the repositories
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# then to get grub to install and update:
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

sudo dpkg-reconfigure grub-pc

---

### Post by supriyo on 2010-05-20
> **oldfred said:**
> You have a couple of choices. reinstall grub and manually edit the menu item to boot. Or chroot into your system and update from there. You do show kernel but if the install did not complete correctly you may need the chroot to repair it.

Kansasnoob has chroot instructions & he puts everything on one line to make it easy to copy & paste:
kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

When in your chroot:
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages update must be run first
#would upgrade you to the latest kernel in the repositories
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# then to get grub to install and update:
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

sudo dpkg-reconfigure grub-pc
And here is the original boot condition after update of Ubuntu 10.04

---

### Post by drs305 on 2010-05-20
Your grub.cfg file shows no entries for any of the normal /etc/grub.d/ folder scripts (00_header, 05_debian_theme, 10_linux, etc).

These files must be executable (and of course must exist). You can do this by running a file browser as root if sda8 is already mounted. From the command line, you can run this if the files exist and you are on your system (via chroot):
```
sudo chmod +x /etc/grub.d/*_*
```

If you are on a LiveCD, mount /dev/sda8, then run:
```

sudo mount /dev/sda8 /mnt
sudo chmod +x /mnt/etc/grub.d/*_*
*when you are done looking at the files:*
sudo umount /dev/sda8

```

You will need to update-grub from within the chroot environment if this is how you have been installing/reinstalling grub2.

---

