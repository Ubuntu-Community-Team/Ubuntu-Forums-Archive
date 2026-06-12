---
title: "Serious Upgrade Bug: /root folder"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by strange_cathect on 2010-05-02
I have two hard drives. One contains separate partitions for /, /home, and /swap. I have a separate hard drive where I routinely back up my /home folder in case of data loss.

Upon installing 10.04 from 9.10 using the upgrade option, the installer installed / on my back up drive, where I keep my backup of /home. I would expect that the installer would instead choose my current root folder for this. I did not notice this for 2 days until I went to make my first backup of my /home partition since the upgrade. 

Unfortunately, due to the confusion over what had happened, I have experienced a serious data loss. This is a serious bug.

---

### Post by davidmohammed on 2010-05-02
sounds serious - but I dont remember seeing this issue through the late alpha-beta stages of testing.

Worth filing a bug on launchpad.

---

### Post by strange_cathect on 2010-05-02
I just did. I think my /home folder is ok. I'm burning a disk of 10.04 with the hope that I can go back and reinstall just the /root folder and fix this. Fingers crossed. If anyone has any ideas, please let me know.

---

### Post by strange_cathect on 2010-05-02
For some reason, it has really messed things up. I've now burned a virtual disk and am trying to use it to re-install my /root folder. However, I'm experiencing a "serious error" and then it tries to boot from the hard drive. Of course, this fails and my computer just hangs forever. 

I'm stuck! Is my machine bricked because of this?

---

### Post by strange_cathect on 2010-05-02
I will now try to downgrade to 9.10 using the installer disk that I have. I was able to load up the virtual disk and fire up gparted. I can see that somehow all of my mount points have been erased. However, my partitions remain. 

Currently installing / again while preserving my /home partition...

---

### Post by AlexandreP on 2010-05-02
.

---

### Post by strange_cathect on 2010-05-02
Ok, I was able to use my 9.10 disk to reinstall the OS in / while preserving /home. Then I was able to get my computer to accept the new 10.10 disk. 

I am currently involved in installing the OS back into / and preserving /home.

I noticed something interesting, that may be the cause of this. For some reason, the installer switched my hard drives. I had sda and sdb. The installer switched the labels, so that the disks are now labeled the reverse from my previous installations. 

Since my difficulty was that / was installed on the wrong hard drive, perhaps this is the cause?

---

### Post by strange_cathect on 2010-05-02
Ok, re-installed 10.04. 

Unbelievable. After reboot I receive the following message:

GRUB loading.
error: the symbol 'grub_puts_' not found
grub rescue>

Will not start up. Period.

---

### Post by strange_cathect on 2010-05-02
If anyone can help me, I'd be very, very, very grateful.:confused:

---

### Post by oldfred on 2010-05-02
Several grub puts have been solved by reinstalling grub especially those with 2 drives. It does sound like it is getting confused on which drive is which. Check /boot/grub/device.map.

I have not tried it yet with Lucid but with Karmic and external drives we had to run this to make sure grub stored the correct entry in some file on where to reinstall grub. Somewhere someone said it was fixed in Lucid.

Important for external removeable drives: Fixed 2010-02-04 for Lucid
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435)
reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/debconf/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep stage1 install in sync.

---

### Post by strange_cathect on 2010-05-05
I had reinstalled grub and everything was finally fixed. Then this mornings updates came in. I updated, and accepted the reboot. When my machine booted, it gave me the grub recover prompt. I am fuming mad.

What is causing this? How can I get grub to work properly?

---

