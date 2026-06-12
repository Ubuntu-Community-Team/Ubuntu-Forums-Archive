---
title: "grub-install error"
date: 2015-09-01
forum: Installation &amp; Upgrades
---

### Post by devanalias on 2015-09-01
Hello, I have done a apt-get dist-upgrade and raised an error:

Configurando shim-signed (1.9+0.8-0ubuntu2) ...
Instalando para plataforma x86_64-efi.
error: no se puede leer «/dev/sdb»: Error de entrada/salida.
error: no se puede leer «/dev/sdb»: Error de entrada/salida.
error: no se puede leer «/dev/sdb»: Error de entrada/salida.
error: no se puede leer «/dev/sdb»: Error de entrada/salida.
error: no se puede leer «/dev/sdb»: Error de entrada/salida.
grub-install: error: no se puede encontrar una unidad GRUB para /dev/sdb1. Revise su device.map.
dpkg: error al procesar el paquete shim-signed (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 1
Se encontraron errores al procesar:
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)


And now it is raised every time I install something. I am afraid to rebooting because I don't know if this problem will preven linux from booting again.

Can you help me?

Thanks


Some system info:

javier@dell-xub:~$ uname -a
Linux dell-xub 3.13.0-62-generic #102-Ubuntu SMP Tue Aug 11 14:29:36 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


javier@dell-xub:~$ df
S.ficheros     blocks de 1K    Usados Disponibles Uso% Montado en
/dev/sda4          28705788  20532200     6692372  76% /
none                      4         0           4   0% /sys/fs/cgroup
udev                8156688         8     8156680   1% /dev
tmpfs               1633496      1540     1631956   1% /run
none                   5120         0        5120   0% /run/lock
none                8167476     15724     8151752   1% /run/shm
none                 102400        60      102340   1% /run/user
/dev/sdb1            507904     29660      478244   6% /boot/efi
/dev/sda6          51775076  27410628    21711316  56% /home
/dev/sda2         386718716 315961700    70757016  82% /media/javier/DATA


javier@dell-xub:~$ mount
/dev/sda4 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sdb1 on /boot/efi type vfat (rw)
/dev/sda6 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
vmware-vmblock on /run/vmblock-fuse type fuse.vmware-vmblock (rw,nosuid,nodev,default_permissions,allow_other)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=javier)
lxcfs on /var/lib/lxcfs type fuse.lxcfs (rw,nosuid,nodev,allow_other)
/dev/sda2 on /media/javier/DATA type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

---

### Post by dino99 on 2015-09-01
you get : error: no se puede leer «/dev/sdb»: Error de entrada/salida.
and it refer to:  /dev/sdb1 on /boot/efi type vfat (rw)

so the problem is with that vfat partition
hopes someone with efi experience will help you as i've no clue about efi.

maybe you can check that partition for possible error on it, with gparted, but without doing change, only to glance at.

---

### Post by oldfred on 2015-09-01
Does this Dell have an sdb drive, or is that just the flash drive you used to install?

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

    
I have never been able to get grub to install to an ESP - efi system partition on sdb.
What model computer?
If real new, you may need the newer verisons of Ubuntu or 14.04.3 or 15.10.

---

### Post by devanalias on 2015-09-03
First of all, the problem solved ¿magically?

This computer has 2 SS disks, sdb is the first one where Windows and MBR are installed. sda is a backup disk where I installed xubuntu. This is a Dell Precision M3800 1yr old, I have installed Xubuntu 14.04, I'll try to install newer version. Here is the BootInfo summary report you asked for: [http://paste.ubuntu.com/12262905/](http://paste.ubuntu.com/12262905/)
I opened GParted and it thrown an I/O error when trying to load sdb...then I began to cry :P
I decided to reboot with Super Grub2 Disk in a USB, it failed booting from USB stick so I entered BIOS. Only the usb appeared in the bootable devices list...screams of agony...

 I disabled Secure Boot to try USB Boot again...failed. I put off the USB, then Windows booted (before that it would have showed grub menu asking for a SO choice)
Then I entered BIOS and all bootable devices where there...I choose ubuntu the first and now grub asks where to go (as before).

Ubuntu booted, upgrade worked and gparted didn't show errors looking on sdb...

Secure Boot keeps Off by now.

Windows now seems to be broken and does not remember my configuration, programs or desktop. Something have dead... but I don't mind if I have *buntu ;) .


Thank you all

---

### Post by oldfred on 2015-09-03
Part of issues may be drive order or which drive is sda. That is usually determined by UEFI/BIOS and order plugged into SATA ports.
I know Windows likes to be first drive.
And Ubuntu's grub always installs to an ESP on sda. But you only have an ESP - efi system partition on sdb.

---

