---
title: "Loss of Ubuntu, forced to BusyBox"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by Kungfujon on 2008-05-12
Hi all,

Quick setup...I have a Toshiba Satellite notebook that I am attempting to migrate from WinXP to Ubuntu.  I received a distro of Ubuntu 7.10 and installed that (creating a second partition on my only drive).  Worked great.  I let it download and upgrade to 8.04 with no problems.  

Several times while working with files, I recieved a message that I did not have permission, but it did not ask me for a password.  Specifically when I was migrating my Outlook email settings from Mozilla Thunderbird (windows) to Thunderbird (Linux).  I fixed that problem by using "sudo nautilus" and changing the folder permissions (some website explained how to do that).

I ran in to the same file permission problems a few more times, until I made my first BIG Linux mistake.  Like a fool, I assumed I knew what I was doing and I selected all folders on my Linux partition (with sudo nautilus) and changed all permissions to read & write for everyone. I figured why not, I'm the only one using the comp and I'll never have to do this again.

Well, now when I boot up, I get to the dual boot screen and no matter if I pick Ubuntu 8.04 or Ubuntu 8.04 (safe mode) I see alot of text then:

-----------------------------
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in Shell (ash)

(initramfs)

-----------------------------

is there anyway to save me?  It has been suggested to me to wipe the partition and make a clean install of 8.04

I guess I can do that, but I'd like to preserve all of the settings, files, etc that I have set up.

I searched the forums and didn't find anything like this problem.  Most people seem to run into this prompt during an instalation if it fails to recognize the boot drive.

Thanks for any help you can offer,

Jon B. "learned my lesson and won't do it again"

---

### Post by Mr A Mouse on 2008-05-12
Hi, Jon,

I'm afraid I know of no way to repair the damage and save your settings, though you can save your files. It won't be easy, but it is possible.

1: Get some form of bootable CD that can set up a "live disk" system--something like Knoppix or OpenCD. 
2: Boot into the "live disk" system, and copy your files off of the Linux partition (or at least out of the home folder--I copied mine to /zzdocs, just by way of example).
3: OPTIONAL: Once you have the files copied, you can delete the old system files from the hard disk, if you choose. I didn't do this, but some people feel better about doing it cleanly.
4: Reboot with the Ubuntu install disk--when it loads the disk management, select "manual" instead of guided, and do not format the main Linux partition.

My problem happened when I upgraded my ProLiant from Gibbon to Heron--I would get to the login screen, it would accept my password, then the entire system stuck at the pale tan screen.

---

