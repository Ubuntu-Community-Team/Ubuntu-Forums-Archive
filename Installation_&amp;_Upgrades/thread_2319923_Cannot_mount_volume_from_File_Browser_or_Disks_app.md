---
title: "Cannot mount volume from File Browser or Disks application"
date: 2016-04-08
forum: Installation &amp; Upgrades
---

### Post by XEtedBear on 2016-04-08
I have a Dell Studio XPS 8100 with a 250 GB drive (which is, I think, the boot drive), formatted with NTFS, and a 750 GB drive. Windows 10 is on the 250 GB drive; Ubuntu/Mint 17.3 Rosa is on the 750 GB drive. When in the Linux file browser, or using the disks application, I can see the 250 GB drive; it's not mounted. If I try to mount it, by right clicking on the icon in file browser or clicking on the right facing triangle in the disks app, I get this error message:

"Unable to mount 249 GB Volume

Error mounting /dev/sda2 at /media/tony/48E0EE44E0EE3838: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda2" "/media/tony/48E0EE44E0EE3838"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option"

Windows 10 can be booted and run with no unexpected problems. It was closed by shutdown the last time I used it. The 250 GB drive has been taken from a different failed  system so it has a couple of 'hidden' partitions for system (Vista/Win 7) recovery and restoration of that failed system. These partitions are visible from the disks application but  don't have any idea of what state they are in

How do I correct this problem ?

---

### Post by deadflowr on 2016-04-08
> [COLOR=#000000]Windows is hibernated[/COLOR]
That's your problem and changing that is the answer.

Not a subject in my personal wheelhouse, so here:
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by XEtedBear on 2016-04-09
> **deadflowr said:**
> That's your problem and changing that is the answer.

Not a subject in my personal wheelhouse, so here:
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

&#65279;Hmm, don't understand your answer. How do you know Windows is hibernated? As I said in my o.p., last time I exited from Windows was via shutdown. However, since I know nothing, I tried booting to Windows and removing hibernation voa the command 'powercfg - h off'. There was no hiberfil.sys file on my system to start with (which I why I don't think the system was hibernated), but having shutdown Win 10 again and returned to Linux, the disk mounted immediately.

Thanks for your help.

---

### Post by deadflowr on 2016-04-09
> [COLOR=#000000]&#65279;Hmm, don't understand your answer. How do you know Windows is hibernated? [/COLOR]
Because it told you it was.

> [COLOR=#000000]Error mounting /dev/sda2 at /media/tony/48E0EE44E0EE3838: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dm ask=0077,fmask=0177" "/dev/sda2" "/media/tony/48E0EE44E0EE3838"' exited with non-zero exit status 14: **Windows is hibernated**, refused to mount.[/COLOR]
[COLOR=#000000]Failed to mount '/dev/sda2': Operation not permitted[/COLOR]
[COLOR=#000000]The NTFS partition is in an unsafe state. Please resume and shutdown[/COLOR]
[COLOR=#000000]Windows fully (no hibernation or fast restarting), or mount the volume[/COLOR]
[COLOR=#000000]read-only with the 'ro' mount option"[/COLOR]

---

### Post by XEtedBear on 2016-04-10
Yes, I was aware of what the message claimed. The difficulty with it was that I had shut down windows, not hibernated it and there never was any instance of hiberfil.sys on the system, including deleted copies. Indeed when I started Win 10 again, it went through a normal 'cold' start. All this tells me it was not hibernated.

---

### Post by deadflowr on 2016-04-10
Did you check hidden files?
hiberfil.sys is a hidden file.
Or did you mean you checked both deleted and hidden files?

---

