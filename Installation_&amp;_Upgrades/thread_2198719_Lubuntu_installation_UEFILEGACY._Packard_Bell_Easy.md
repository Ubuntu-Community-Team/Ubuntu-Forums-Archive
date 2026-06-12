---
title: "L/ubuntu installation UEFI/LEGACY. Packard Bell Easynote TE69KB"
date: 2014-01-10
forum: Installation &amp; Upgrades
---

### Post by Itiwid on 2014-01-10
Long saga of failed or unusable installations of ubuntu studio / ubuntu / lubuntu.

Latest attempt was Lubuntu.

Runnning a PB easynote TE69KB with amd dual E1-2500 & 6GB DDR3

latest problem...

created installation USB with UNETBOOTIN (no optical drive) with BIOS in legacy, receive message:

"Missing Operating System"

out of desperation, revert to UEFI boot (with un-disableable Secure Boot) and the stick loads. Lubuntu installs....

Now on boot lubuntu begins to load and then I get a message about unable to connect to plymouth and put into TT1 where it asks for my login and then leaves me stuck...

previously loaded USB from legacy boot without issue (although the distros installed were unusable for various reasons). Not sure what has changed to give "missing OS"...

any help greatly appreciated.

Thanks.

UPDATE.

Ran download and installation of 13.1 saucy from inside TT1...

Lubuntu now starts to load and then simply hangs halfway without even pretending to do anything until the power off button is pressed. giving this.

*Asking all remaining processes to terminate
*All processes ended within 1 seconds...
nm-dispatcher.action: Caught signal 15, shutting down...
*Deactivating swap
*Unmounting Local filesystems
*stopping remaining cryptodisks
*cryptswap1 (stopped)...
*stopping early crypto disks
*cryptswap1 (stopped)
mount: / is busy
*will now halt
( 278.599981) reboot Power down

and then hangs again...

NB.  a couple of times booting in UEFI it has loaded the GRUB2 interface but it has now ceased to do this.

LEGACY boot reads no bootable disk without USB and still reads "missing operating system" with...

beginning to suspect I have taken a computer and made a brick....

---

### Post by Itiwid on 2014-01-10
Update: finally managed to disable secureboot. trying fresh lubuntu 13.04 install with unetbootin drive on UEFI boot.

Further Update: Back to loading into TT1... displays KVM disabled by BIOS before doing so... not sure if it's possible to upgrade the BIOS as the download from PB site somes as a windows installer.

---

### Post by oldfred on 2014-01-10
Many of the budget PCs seem to have limited UEFI also. 

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

