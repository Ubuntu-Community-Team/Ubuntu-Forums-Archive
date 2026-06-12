---
title: "mounting my ntfs drive, and its not working."
date: 2005-02-25
forum: Installation &amp; Upgrades
---

### Post by graigsmith on 2005-02-25
ok. i installed. linux on one hard drive i have. then, i plugged in a winxp ntfs hard drive  to get some files off it.

my win xp volume is in just temporarily.

i tried making an ntfs folder on the desktop.

and typing this in a terminal window.

sudo mount /dev/hdb1 /home/graig/Desktop/ntfs -r -o uid=1000

i typed that, and my drive popped up in the ntfs folder, but when i start copying things, it gives an error. and stops copying. and it wont let me unmount the drive either.  i think i have both drives set for cable select.  ](*,)  the drive works fine when im in windows.

any ideas on what im doing wrong?

---

### Post by graigsmith on 2005-02-25
does anyone know why?  is the ntfs driver just not good enough to read the partition? or have i configured it wrong?

---

### Post by alastair on 2005-02-25
What error?

What is in your /etc/fstab file (relevant to /dev/hdb1)?

Any errors or information in the logs - about the mount or errors?

/var/log/syslog

---

### Post by wallijonn on 2005-02-26
> sudo mount /dev/hdb1 /home/graig/Desktop/ntfs -r -o uid=1000

So you created a folder called ntfs on your desktop or in your home directory? If you created the folder, did you give full permission to it?

---

### Post by graigsmith on 2005-02-26
this was in the log file, /var/log/syslog.   diddn't list any errors.
Feb 26 02:44:03 localhost kernel: NTFS driver 2.1.15 [Flags: R/O MODULE].
Feb 26 02:44:03 localhost kernel: NTFS volume version 3.1.


before i mounted it, i set the folder to have all permissions.

now that i look again. it has less permissions, dr-x------  is what is listed.

now i try to drag files to the desktop, and gnome gives me an error window.

Error "I/O error" while copying "/home/graig.../AtiCim.bin".

---

### Post by graigsmith on 2005-02-26
i tried copying stuff using the cp command and it seemed to continue copying.
these are the errors it gave.  i haven't been having any problems with my ntfs drive, besides getting linux to read it.  perhaps the ntfs linux driver doesn't like my computer.

graig@smith:~/Desktop/ntfs $ cp -a /home/graig/Desktop/ntfs/DOS/ /home/graig/Desktop/dos/
cp: reading `/home/graig/Desktop/ntfs/DOS/ARENA/Docs/Arena106 Setup.doc': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/ARENA/FOG.TXT': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/DAGGER/ARENA2/CHLD00I0.RCI': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/DAGGER/ARENA2/DARKEN.LGT': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/DAGGER/ARENA2/DARKENA.LGT': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/DAGGER/ARENA2/FACES.CIF': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/DAGGER/ARENA2/HAZE.000': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/DAGGER/ARENA2/HAZE.001': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/DAGGER/ARENA2/ICON00I0.IMG': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/DAGGER/ARENA2/LIGHT.DAT': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/DAGGER/ARENA2/SHADE.000': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/DAGGER/ARENA2/SHADE.001': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/LOL/DATA/ENG/BLEND.TAB': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/LOL/DATA/ENG/BLEND2.TAB': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/SSHOCK/DATA/IPAL.DAT': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/SSHOCK/DATA/BWTABL.DAT': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/SSHOCK/DATA/SHADTABL.DAT': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/u4/CHARSET.EGA': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/u4/SHAPES.CGA': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/u4/SHAPES.EGA': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/u4/WORLD.MAP': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/u8/STATIC/TYPEFLAG.DAT': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/UW/DATA/LIGHT.DAT': Input/output errorcp: reading `/home/graig/Desktop/ntfs/DOS/UW/DATA/MONO.DAT': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/UW2/CRIT/CR.AN': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/UW2/DATA/LIGHT.DAT': Input/output error
cp: reading `/home/graig/Desktop/ntfs/DOS/UW2/DATA/MONO.DAT': Input/output errorgraig@smith:~/Desktop/ntfs $

---

### Post by graigsmith on 2005-02-26
tried putting the other hdd on another controller, apart from the hdd with linux on it. 

and i also ran a chkdisk on the windows drive. 

and its still doing it.

do my permissions on my windows drive matter at all?

if i try sudo umount /dev/hdb1 
i get a device is busy message.

---

### Post by alastair on 2005-02-26
Check in a shell :

ls -l /home/graig/Desktop/ntfs/DOS/ARENA/FOG.TXT

Permissions?

Perhaps try a :

sudo cp /home/graig/Desktop/ntfs/DOS/ARENA/FOG.TXT /tmp

But - "Input/output error" looks like a disk or mount issue.

What mounted, what does "mount" say i.e. type

mount

---

### Post by graigsmith on 2005-02-26
i did an ls with the -l on that file, and it said i had read only permissions.

i typed mount and it listed this.

devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=graig)
/dev/hdb1 on /home/graig/Desktop

when i try copying that file, it gives an IO error.

---

### Post by graigsmith on 2005-02-26
huh, i upgraded to warty, and its copying.  must be a newer version of something.

hey, also my wacom tablet sorta works :)


edit, the copy went thru with out any fails.  perhaps it diddnt like my nvidia chipset.

now the only problems i am having are, 

no sound in dosbox, and my tablet is not working correctly.

---

