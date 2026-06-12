---
title: "Grub issue - Linux dual os - system fails to boot"
date: 2014-01-01
forum: Installation &amp; Upgrades
---

### Post by muruga86 on 2014-01-01
Hi All,

I have a x86_64 machine with 500GB diskspace.
First, i have successfully installed ubuntu-12.04.3-desktop-amd64 OS.  The disk has been partioned into 2 x 200GB ext2 sections, 2 X 25GB ext2  sections, 1 X 30GB ext4 section and 10GB swap space. The / is mounted on  one 25GB section and /home mounted on one 200GB section.

Now, i tried to Fedora19 Fedora-Live-Desktop-x86_64-19-1 on the  remaining 25GB partition. During installation, the system hanged and i  aborted the process.

Now, when i start the system from existing installation (ubuntu os) grub  window is shown, but on selecting the ubuntu version (Ubuntu with Linux  3.8.0.29-generic and recovery mode), a kernel panic is being thrown as  "kernel panic: out of memory and no killable processes". Now, i inserted  my ubuntu image disk but sill i get the same issue with out grub  window.

//My grub settings
setparams 'Ubuntu with Linux 3.8.0.29-generic'

recordfail
gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
insmode ext2
set root='(hd0,msdosa)'
search --no-floppy --fs-uuid --set=root xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
linux /boot/vmlinuz-3.8.0.29-generic root=/dev/sda1 ro quiet splash $vt_handoff
initrd /boot/initrd.img-3.8.0-29-generic



My system never boots up with either installed image nor with ubuntu/fedora boot disk for fresh install. 
I could only access to grub cmdline grub>,.

On further analysis of this issue, [kdump "kernel panic: out of memory  and no killable processes..." url] mentioned to set crashkernel=768M in  grub.cfg file. Now i could not update this cmd in grub>  /boot/grub/grub.cfg file in grub cmd line using vi or emacs. And manual  edit using e cmd and ctrl+x leads to same issue.


Please let me know how to recover this from this issue.

Thanks in advance
Murugan

---

### Post by carl4926 on 2014-01-01
Just to be clear
Are you saying you can't even boot up with the Live Image?

---

### Post by grahammechanical on 2014-01-01
The Grub command line uses Grub specific commands and not the BASH commands that we use in a terminal. These Grub commands relate to setting the Grub boot parameters. The best I can do is direct you to where we can download the Grub manual. I have tried studying and using these commands as a form of education but I fail to get to grips with them.

[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

Regards.

---

### Post by oldfred on 2014-01-01
You can try a manual boot from grub command line. If install is in sda1.

       set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux (hd0,1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,1)/initrd.img
boot

      
 See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)

Generally better not to use ext2, ext4 has much better recovery capabilities since it has a journal. 

If you can boot Ubuntu live Installer.
      
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by muruga86 on 2014-01-03
Yes, your are correct.
Both by ubuntu/fedora live CDs does not work.
Kernel panic is being thrown.
When i try to boot installed ubuntu, i get grub window and then followed by kernel panic.

---

### Post by muruga86 on 2014-01-03
Hi,

> **oldfred said:**
> You can try a manual boot from grub command line. If install is in sda1.

       set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux (hd0,1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,1)/initrd.img
boot

*>>I will try this method in my grub cmd prompt and let you know the results.*
      
 See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)

Generally better not to use ext2, ext4 has much better recovery capabilities since it has a journal. 
[I]>>I am planning to reformat my disk and give a fresh install after recovering from this issue.
I will use ext4 instead of ext2.
[/I]

If you can boot Ubuntu live Installer.
      *>>No, i am unable to do so.*

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by muruga86 on 2014-01-08
Hi All,

I tried all the above methods but all failed.
Finally, i have used ultimatebootdisk from my CD drive to wipe out my boot sector.
Then, ubuntu installation was successful.
Thanks for all your support.

Murugan

---

