---
title: "boot is not ready yet or not present"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by addisor on 2011-05-29
Hi guys,

My work laptop running XP is a Dell and IT have put Anywhere+ on it that stops all the sites I want to use, i.e FB Hotmail blah blah.

Solution- run Ubuntu 11.04 off a USB hard drive (500GB)

To get there, I set up a usb stick drive with 11.04 and installed it on another usb hard drive using my own laptop (Samsung) as the hardware. I dont wont any dual boot on my work laptop or any evidence of tinkering.

My problem is, as in the title. If i boot up my Dell, the HD is skipped and not recognised. If I boot up my samsung, it is also skipped, unless I reboot from XP and then it shows up, I boot 11.04 and reach /boot is not ready etc. 

I press 'S' to skip this and everything is fine. The problem is, I only want to boot my Dell into Nawty, so think I need to tweak my etc/fstab somehow.

Any help?

---

### Post by addisor on 2011-05-29
Further update, 

I've run the usb stick and tried to mount the usb hdd and it wont mount. I took a screen shot and attached it. still battling on.

---

### Post by addisor on 2011-05-31
I've now run boot info script looking for any defects. But I'm not overly confident on what im reading.

Can someone have a look and see if why my USB HDD is not booting?

---

### Post by oldfred on 2011-05-31
What I can see of your configuration looks ok, but script is having trouble mounting several partitions. If script cannot mount them I would expect you to have trouble booting as then they do not mount.

Both sda2 & sdc6 seem to have issues. I might try running chkdsk from a windows disk on sda2 and e2fsck on sdc6 to see if that fixes things.

From liveCD so everything is unmounted,swap off if necessary, change sdc6 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdc6
if errors:
sudo e2fsck -f -y -v /dev/sdc6

To repair windows with mounting issues from your Windows XP CD - Do not run fixMBR unless you want windows boot loader in the MBR.
fixboot C:
XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by addisor on 2011-06-01
cheers, I'll give that a go.

---

