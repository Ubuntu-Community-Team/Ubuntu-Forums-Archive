---
title: "Is there a way to stop MTP devices automounting ?"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nigelmouse on 2009-04-08
I'm running jaunty and whenever I connect my Creative Zen Vision:M it gets automounted. 

Is there a way to stop this as most of the time I only want to charge my mp3 player and would like to listen to it while it's charging (which can be done when it's not mounted).

Also, I use Amarok for managing my MP3 player and it can't access it until I unmount it and then connect from within Amarok. Disabling automounting MTP devices would solve my problems.

Cheers

---

### Post by Idefix82 on 2009-04-08
You can add a corresponding line for your mp3 player to fstab and use the noauto option.

---

### Post by gnomeuser on 2009-04-08
Perhaps we could also teach the system how to recharge the device while it's mounted. I have the same issue with my Sansa Fuze btw. it seems like a design flaw to me if the device cannot do it and if the device is capable then it is a bug if we do not do it right.

---

### Post by nigelmouse on 2009-04-08
> **gnomeuser said:**
> Perhaps we could also teach the system how to recharge the device while it's mounted. I have the same issue with my Sansa Fuze btw. it seems like a design flaw to me if the device cannot do it and if the device is capable then it is a bug if we do not do it right.

It will recharge while it's mounted, that's not the problem. The problem is that the device goes into 'Sync mode' while it's mounted ready to have files sent to it. In this mode the device cannot be controlled from it's keypad, and therefore tunes cannot be played. 

Once it's unmounted it continues to recharge but comes out of it's "sync mode". This allows both full playback controls of the device to be used while it gets a bit of juice.

---

### Post by andrewabc on 2009-04-08
> **gnomeuser said:**
> Perhaps we could also teach the system how to recharge the device while it's mounted. I have the same issue with my Sansa Fuze btw. it seems like a design flaw to me if the device cannot do it and if the device is capable then it is a bug if we do not do it right.

I only charge my sansa view on winxp because on ubuntu it would get all messed up attempting to charge and eventually view would shutdown. And when I would mount it it would make all the music files disappear and stuff. So I've stayed far away from ubuntu with my sansa view. Maybe the support works better on Jaunty?

---

### Post by nigelmouse on 2009-04-08
> **nigelmouse said:**
> I'm running jaunty and whenever I connect my Creative Zen Vision:M it gets automounted. 

Is there a way to stop this as most of the time I only want to charge my mp3 player and would like to listen to it while it's charging (which can be done when it's not mounted).

Also, I use Amarok for managing my MP3 player and it can't access it until I unmount it and then connect from within Amarok. Disabling automounting MTP devices would solve my problems.

Cheers

mount claims the device is mounted as

[INDENT][FONT="Courier New"]binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)[/FONT][/INDENT]

so I added the following line to my /etc/fstab

[INDENT][FONT="Courier New"]binfmt_misc   /proc/sys/fs/binfmt_misc     binfmt_misc     noauto    0   0[/FONT][/INDENT]

but it still gets automounted.

Any ideas what I got wrong or if there's another way to stop this device automounting ?

---

### Post by Idefix82 on 2009-04-08
You are reading the wrong line in the mount command. This is, what you are referring to: [http://en.wikipedia.org/wiki/Binfmt_misc]("http://en.wikipedia.org/wiki/Binfmt_misc")

My guess is that your mp3 player should be mounted somewhere under /media

---

### Post by nigelmouse on 2009-04-08
> **Idefix82 said:**
> You are reading the wrong line in the mount command. This is, what you are referring to: [http://en.wikipedia.org/wiki/Binfmt_misc]("http://en.wikipedia.org/wiki/Binfmt_misc")

My guess is that your mp3 player should be mounted somewhere under /media

You're incorrectly assuming my media player appears as a mass storage device. It does not. 

It's an MTP device (Microsoft's [Media Transfer Protocol]("http://en.wikipedia.org/wiki/Media_Transfer_Protocol")). This is now being interpreted through the binfmt_misc driver so Gnome can now browse it.

---

### Post by danwood76 on 2009-04-08
binfmt_misc loads more than one type of device/file and the kernel module is mounted to that file.

Your MP3 player is more likely loaded into a /media directory.
Can you view it in the places pane of gnome?
If so I would say its mounted to /media/xxx, and this is what you should be looking for in the moun command.

-- edit --

You can disable the binfmt_misc driver by adding it to the modprobe blacklist but I'm not sure if that will break anything.

---

### Post by nigelmouse on 2009-04-08
> **danwood76 said:**
> binfmt_misc loads more than one type of device/file and the kernel module is mounted to that file.

Your MP3 player is more likely loaded into a /media directory.
Can you view it in the places pane of gnome?
If so I would say its mounted to /media/xxx, and this is what you should be looking for in the moun command.

-- edit --

You can disable the binfmt_misc driver by adding it to the modprobe blacklist but I'm not sure if that will break anything.

When the mp3 player is connected there is nothing mounted under /media, the output of the mount command is:

[INDENT][FONT="Courier New"]nige@nige-eee:~$ mount
/dev/sdb1 on / type ext2 (rw,noatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
tmpfs on /var/log type tmpfs (rw,noatime)
tmpfs on /tmp type tmpfs (rw,noatime)
tmpfs on /var/tmp type tmpfs (rw,noatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nige/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nige)
nige@nige-eee:~$ 
[/FONT][/INDENT]

and yes, it in the Places menu in Gnome.

I could blacklist the binfmt_misc driver as I'm unlikely to use other devices that require it, however it does seem a bit of a cludgy solution.

---

