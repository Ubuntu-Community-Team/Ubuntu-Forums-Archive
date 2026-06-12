---
title: "Using fstab to mount usb floppy drive"
date: 2012-06-24
forum: Installation &amp; Upgrades
---

### Post by F W Adams on 2012-06-24
I'm having getting this to work. I wanted to use a UUID and also to mount it at a user level.

Here is my current fstab:
# /etc/fstab: static file system information.
#
# Use 'sudo blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>                           <mount point>        <type>  <options>                  <dump>  <pass>
proc                                      /proc                proc    nodev,noexec,nosuid        0       0
/dev/mapper/LVM.1-system                  /                    ext4    errors=remount-ro          0       1
# /boot was on /dev/sda1 during installation
UUID=b2114f59-8176-4077-b2dd-e1713e3e3af5 /boot                ext4    defaults                   0       2
/dev/mapper/LVM.1-home                    /home                ext4    defaults                   0       2
# /home/felix/fast.ne was on /dev/sda2 during installation
UUID=8a14e4fb-7dc9-456c-b27d-cc179ca19504 /home/felix/fast.ne  ext4    defaults                   0       2
/dev/mapper/LVM.1-swap                    none                 swap    sw                         0       0
#UUID=2A87-6CE1                            /home/felix/floppy   vfat    user,noauto,noatime,flush  0       0		

You will see that fstab is not being used for the usb floppy at the start of this experiment. Here is my terminal output, you can see that without using fstab everything is working fine but the when I altered the fstab, I just took out the last "#" in the file at the start of the last line, it no longer worked when it had actually to access fstab.

```
alex@ubuntu6:~$ sudo blkid
/dev/sda1: UUID="b2114f59-8176-4077-b2dd-e1713e3e3af5" TYPE="ext4" 
/dev/sda2: UUID="8a14e4fb-7dc9-456c-b27d-cc179ca19504" TYPE="ext4" 
/dev/sda3: UUID="348f966a-fe61-4905-b9d7-e8ed8ff6d04e" TYPE="crypto_LUKS" 
/dev/mapper/sda3_crypt: UUID="HqoYLs-lW0x-hdBD-XGdw-wDL1-lHar-1nDuGz" TYPE="LVM2_member" 
/dev/sdb: UUID="8c95d6e8-66ca-4bef-8fb8-97a9c0ac73b3" TYPE="crypto_LUKS" 
/dev/mapper/LVM.1-swap: UUID="a157f461-3748-4f88-93ec-24d37cbe3f93" TYPE="swap" 
/dev/mapper/LVM.1-system: UUID="53a99feb-b6ff-4b99-a1ca-8a78e678ad14" TYPE="ext4" 
/dev/mapper/LVM.1-home: UUID="3276f94b-d27b-4d45-bb4a-d82652eb88ea" TYPE="ext4" 
/dev/sdc: SEC_TYPE="msdos" UUID="2A87-6CE1" TYPE="vfat" 
alex@ubuntu6:~$ ls floppy
alex@ubuntu6:~$ mount /dev/sdc floppy
mount: only root can do that
alex@ubuntu6:~$ sudo mount /dev/sdc floppy
alex@ubuntu6:~$ ls floppy
AUTOEXEC.BAT  DISPLAY.SYS  EGA.CPI   KEYBOARD.SYS  KEYBRD4.SYS  TIMETEST.EXE
COMMAND.COM   EGA2.CPI     IO.SYS    KEYBRD2.SYS   MODE.COM
CONFIG.SYS    EGA3.CPI     KEYB.COM  KEYBRD3.SYS   MSDOS.SYS
alex@ubuntu6:~$ sudo umount floppy
alex@ubuntu6:~$ ls floppy
alex@ubuntu6:~$ sudo mount /dev/sdc floppy
alex@ubuntu6:~$ ls floppy
AUTOEXEC.BAT  DISPLAY.SYS  EGA.CPI   KEYBOARD.SYS  KEYBRD4.SYS  TIMETEST.EXE
COMMAND.COM   EGA2.CPI     IO.SYS    KEYBRD2.SYS   MODE.COM
CONFIG.SYS    EGA3.CPI     KEYB.COM  KEYBRD3.SYS   MSDOS.SYS
alex@ubuntu6:~$ sudo umount floppy
alex@ubuntu6:~$ sudo gedit /etc/fstab
alex@ubuntu6:~$ sudo mount /dev/sdc floppy
alex@ubuntu6:~$ ls floppy
AUTOEXEC.BAT  DISPLAY.SYS  EGA.CPI   KEYBOARD.SYS  KEYBRD4.SYS  TIMETEST.EXE
COMMAND.COM   EGA2.CPI     IO.SYS    KEYBRD2.SYS   MODE.COM
CONFIG.SYS    EGA3.CPI     KEYB.COM  KEYBRD3.SYS   MSDOS.SYS
alex@ubuntu6:~$ sudo umount floppy
alex@ubuntu6:~$ ls floppy
alex@ubuntu6:~$ sudo mount floppy
alex@ubuntu6:~$ ls floppy
alex@ubuntu6:~$ sudo umount floppy
umount: floppy: not mounted

```

The idea is to eventually use "mount" with fstab rather than "mount" but I continued to use "sudo mount" for the sake of clarity.

---

