---
title: "Ubuntu 9.10 on an external hdd - boot problems"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by Zonitas on 2010-02-28
Hi!

Normally, I use windows (games, you know), but I found out that its about time I try Linux. Thought it would be smart to install ubuntu 9.10 on an external hdd, so I could boot from that, install programs in ubuntu on it (instead of using a cd, where all changes are lost), and move it around so I could have the same ubuntu w/ all programs on different computers etc.
Booted ubuntu 9.10 from a cd, then installed it on the external hdd using the shortcut on the desktop (install Ubuntu 9.10). I set around 40 gb of the disc to be used, and it installed, everything seemed fine. Took a reboot, so I could boot from the external HDD and grub started. Here the problems start. In the GRUB boot menu I get 5 choices (where one of them is windows on my internal drive). Problem is that my (usb)keyboard won\t be able to do anything in this menu... pressing enter, nothing happens. Up/down, nothing. No light in the ketboard either (using a logitech g15), so it seems like it doesn't get any power. In other words, I cant boot anything.
Thought "well, thats sucky, Ill have to boot xp then". Unplugged the external HDD and thought everything would be fine, but I get "grub loading" even without the external disc connected, and it goes to a "no such file exist" errorthingy.
Only way I can boot **anything** now, is to use the ubuntu cd, and boot from that (f11 on startup, boot from cd). Won\t even boot from the windows cd, as grub starts and asks me to press a button to continue. And the keybboard can only be used on the "press del for menu/f11 for boot menu" place of startup and after a system has started.
Does anyone know how to fix this? First of all i just want to get the internal HDD to work again, booting xp and all. Don't want to format it. 

Hope you understand the problem, and if anyone can help, then thnx in advance :)

---

### Post by darkod on 2010-02-28
For the keyboard problem: Go into BIOS and look for USB Legacy option and enable it to support usb keyboard. Also in newer BIOSes there might be separate options for USB Keyboard and USB Mouse. Enable them if they exist.
I can't remember right now where these option would be, maybe in Integrated Peripherals, or similar.

For booting XP without the ext connected: Use the XP install cd and repair the boot process as per the instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you don't have XP disc, boot the ubuntu cd into the live desktop and run first:
sudo fdisk -l

to double check the name of the disk with your XP partition. For example it will be /dev/sda. Then run:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

That will install generic mbr on your internal hdd. You should be able to boot directly XP after that.

Note that this might make the ubuntu on the ext hdd unbootable, because grub2 went to the int hdd, not the ext one. Boot again the live desktop with the ext hdd also connected, run fdisk again and post the results here and we can give you exact commands to reinstall grub2 to the mbr of the ext hdd.

PS. If you sort out the keyboard problem and you can boot into ubuntu, it's better first to reinstall grub2 to the mbr of the ext hdd, and only then install the generic mbr on /dev/sda as described above.

---

### Post by Zonitas on 2010-02-28
Thnx a lot, I'll try that right away :)
[I]
Zon[/I]

---

### Post by Zonitas on 2010-02-28
Mr.(?) darkod, thnx a lot! XP will now boot again (auto when comp. starts)
I could not find any legacy/keyboard option in my bios (phoenix awardBIOS), so the keyboard in GRUB part wouldn't be fixed. Because of this, I couldn't boot from XP-cd either (since I had to press a button after saying "boot from cd", which is where my keyboard dies.)
I then did what you said, by using ubuntu cd - live desktop. Worked, as far as I can see till now, brilliantly! I'll put my results from the "fdisk -l" in a code box under (it's from after the fixing). 

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcd0bd50c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       38913   312560640    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbb40a6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14240   114382768+   b  W95 FAT32
/dev/sdb2           14241       19457    41905552+   5  Extended
/dev/sdb5           14241       19237    40138371   83  Linux
/dev/sdb6           19238       19457     1767118+  82  Linux swap / Solaris

```I haven't dared trying to boot from the ext hdd, so my next project will be fixing that. I hope to delete the current vers. of ubuntu and get an reinstall. I hope to get a ubuntu working on it, so I can use the same os with same settings, programs installed etc on different computers. Would be practical to just bring an ext hdd to school, work, public computers etc and be able to get the same software up and going in seconds! Do you know any way to help me with this as well? ")

And again, thank you a million times, darkod!

*-Zon*

---

### Post by darkod on 2010-02-28
I don't think you will be able to boot at all from the ext disk. It doesn't have any bootloader on it, definitely not grub2 that you need for ubuntu. It went on the int disk and that's why it didn't want to boot without the ext.

If you can boot the ubuntu cd with Try Ubuntu option, you can add grub2 to the ext with:

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Restart.

---

### Post by Zonitas on 2010-02-28
So, just to be sure that I don't **** anything up again:

What I need to do is start ubuntu from the cd, to get live desktopthingy. Don't do anything to the ext hdd, since ubuntu was installed earlier. Use the terminalthingy with those two codes. Will I then be able to boot from ext hdd, without doing anything to my internal disk?

Thnx in advance,

*-Zon*

---

### Post by darkod on 2010-02-28
> **Zonitas said:**
> So, just to be sure that I don't **** anything up again:

What I need to do is start ubuntu from the cd, to get live desktopthingy. Don't do anything to the ext hdd, since ubuntu was installed earlier. Use the terminalthingy with those two codes. Will I then be able to boot from ext hdd, without doing anything to my internal disk?

Thnx in advance,

*-Zon*

Yes, that's the idea. Exactly as you said. Load live desktop, install just grub2 to /dev/sdb because ubuntu is already there.

Then you can boot from internal directly to XP, or from external which will show grub2 boot menu where you can select ubuntu or XP.

---

### Post by Zonitas on 2010-03-01
Thnx, it worked=)
Can now get the  grub-menu from booting the ext hdd=)
Only problem noe, is the damn usb-keyboard-power... Guess I'll have to search some other forums for that.

Again, thnx a lot drakod!

---

