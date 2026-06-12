---
title: "How many nerds does it take to switch on a LAMP?"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by unco on 2006-10-02
Now I've got you interested, and you think your a nerd, please help by imparting your expert knowledge.  Oh and I don't need any of those 'it just works' replies as clearly it doesn't for me!

Problem:

Trying to install ubuntu server (i386) and after installation completes, the machine won't boot.  It just gets into an infinite loop of starting to boot, then in between the 'boot' line and the 'Uncompress Linux... Ok. booting the kernel.' line, the screen goes black and the machine resets itself with a beep.  I can tell you I have been beeping a bit too.

To see a screenshot of where in the boot I am talking about visit [Ubuntu LAMP Server With Torrentflux In VMware]("http://www.howtoforge.com/ubuntu_lamp_torrentflux_vmware_p2") and check out the top image.  In my case however I never see the uncompress linux line.

I have tried the following:
1. FAILED.  Fix mentioned on the page above e.g. sudo apt-get install linux-686.  Should I be getting 686 or 386?
2. FAILED.  Installing LAMP with own partition setup.  
3. FAILED.  Installing LAMP with erase disk for partition selection.
4. FAILED.  Installing to HD (non-LAMP) with erase disk for partition selection.
5. SUCEEDED.  Installing Ubuntu desktop on the machine erase disk for partition selection (but it was extremely slow installation, close to 2hrs).  And I want a server not a desktop.

6. Also I have been able to use the recovery option on the server CD to open a shell in the root.

I am using 6.06.1 LTS server CD downloaded 2 days ago.  And comparing to 6.06 (not sure if .1) desktop CD as download a month or so ago. 

Only other notable setting in setup process is that I answer yes to UTC time.

My hardware is:

CPU: AMD K6
MOTHERBOARD: same age (can get ID if needed) has onboard AGP video, and I have switched off the onboard USB and sound/legacy sound in the BIOS.
RAM: 286MB (8MB shared with video)
HD: 15GB HD (either seagate or western digital)
CDROM: SONY
NIC: NETGEAR 311.

I have removed of disconnected all other hardware to see if I can get the server version to install.

Another question if someone can answer it quickly:
What is the difference between xfs and ext3 partition formats? A HOWTO I looked at indicated to use xfs but didn't mention why.

---

### Post by unco on 2006-10-02
found [this]("http://ubuntuforums.org/showthread.php?t=256144") thread that might solve it.

But [this]("http://paradigma.pt/ja/slog/index.php/2006/08/ubuntu-server-606-lts-doesnt-boot-if-cpu-686.html") is more likely, maybe.

Will try tonight.

---

### Post by unco on 2006-10-03
And the answer is 2!

Me and Joel (from second link above).

It appears there were two things wrong with what I was doing.

1. Don't use xfs (a mate says x stands for eXperimental) in a LVM partition configuration ... reason: every time I tried this just didn't work, wouldn't get past the boot.  So instead just go with the erase entire disk option and stick with ext3.  Didn't investigate but their was a point where it said or recommended to use lilo instead of grub when playing with xfs.

2. Need to do the following after installation completes.

```
sudo apt-get install linux-386
sudo apt-get remove linux-server
```

(thanks Joel for that one) appears that some older hardware configuration can't handle linux-686 and linux-server.

At this point machine is happy to boots into console. Sweet as!

---

