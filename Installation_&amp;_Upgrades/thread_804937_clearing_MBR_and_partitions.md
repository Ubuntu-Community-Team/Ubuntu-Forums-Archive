---
title: "clearing MBR and partitions?"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by Serpreme on 2008-05-23
I would like to clear my mbr and all of my partition infromation.
I was wondering what the best way to zero out the mbr is?
I've fiddled with ```
dd if=/dev/sda of=/dev/zero bs=512 count=0
```but i think i am doing it wrong. 
Thanks for reading this =)

---

### Post by Serpreme on 2008-05-23
# dd if=/dev/zero of=/dev/hda bs=512 count=1
Solved.

---

### Post by Herman on 2008-05-23
:confused: First, what is it you are hoping to accomplish by zeroing your entire MBR?

You can take a look at a hexadecimal representation of your MBR with the following dd command,
```
sudo dd if=/dev/sda count=1 | hexdump -C 
```[What does an IPL really look like?]("http://users.bigpond.net.au/hermanzone/p6.htm#What_does_an_IPL_really_look_like")
The MBR contains an area reserved for the stage1 code for a boot loader, including a 'Disk Signature', (or ID number for your hard disk), which most boot loaders are careful not to touch. [MBR Disk Signature]("http://www.multibooters.co.uk/mbr.html") - Multibooters.co.UK.

Most people don't bother to zero the bootloader section of the MBR, when we want to change the boot loader, it is easier to just use a command to overwrite the old bootloader code with the staqe1 code for a new boot loader. For example, you might use FIXMBR, or grub-install or some other command. 
You can zero that part if you want, but I can't imagine why you would need to, and, if you have Windows Vista, you will lose your 'Disk Signature', which Microsoft has decided to anchor their operating system to. You will lose the boot of Vista that way unless you can restore your MBR from a backup, or at least the 'Disk Signature'.

[MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd")
You can back up the boot loader area of your MBR with,
```
sudo dd if=/dev/sda of=/home/ubuntu/OLDMBR.img bs=446 count=1
```You can restore up the boot loader area of your MBR from a backup with,
```
sudo dd if=/home/ubuntu/OLDMBR.img of=/dev/sda bs=446 count=1
```After that there is the partition table.
If you zero your partition table you will lose track of all your partitions and file systems and therefore you will lose normal access to all the information in your hard disk.
Are you sure you really want to do that?
It can be repaired by restoring the entire MBR from a backup.
You can back up the your entire MBR including the partition table with,
```
sudo dd if=/dev/sda of=/home/ubuntu/OLDMBR.img bs=512 count=1
```You can restore your entire  MBR from a backup with,
```
sudo dd if=/home/ubuntu/OLDMBR.img of=/dev/sda bs=512 count=1
```Lastly, there is also the 55aa bootable disk signature, in the last two bytes of your MBR.
When your BIOS is set to look for a bootable floppy disk, CD/DVD or a bootable hard disk or some other bootable device in your '[BIOS' 'boot order]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_boot_sequence_in_CMOS")', it looks for the 55aa bootable disk signature. WIthout that your BIOS will skip your hard disk and go to the next bootable device, if it doesn't find one, it will probably return something like: '[DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER]("http://users.bigpond.net.au/hermanzone/p15.htm#DISK_BOOT_FAILURE_INSERT_SYSTEM_DISK")'


But, if you really want to nuke your MBR, there is no harm in doing so as long as you have a Live CD and a backup copy of your MBR on some other media that you can use to restore your MBR with again, or you don't care about losing access to all the information in your hard disk.

Here is a link to a web page all about dd commands, [**Learn The DD Command Revised**]("http://www.linuxquestions.org/questions/showthread.php?t=362506"),  (by awesome machine)

If you are sure you really want to zero your MBR, maybe try,
```
dd if=/dev/zero of=/dev/sda bs=512 count=1
```I think that should work, but I don't want to try it right now myself. :)

While I was typing this long post, the question has already been answered quite succinctly by Serpreme. I agree with the above poster.

Regards, Herman :)

---

