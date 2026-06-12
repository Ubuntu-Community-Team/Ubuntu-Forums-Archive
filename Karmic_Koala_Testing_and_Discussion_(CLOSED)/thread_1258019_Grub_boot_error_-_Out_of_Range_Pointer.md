---
title: "Grub boot error - Out of Range Pointer"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by twisted_steel on 2009-09-04
I booted up my laptop this afternoon without issue and rebooted after applying the updates.  After a reboot, I received the following error:

```
  Booting 'Ubuntu, Linux 2.6.31-9-generic'

out of range pointer 0x400040
Aborted. Press any key to exit.
```I am running 32 bit Karmic.  How do you get into the grub menu these days?

---

### Post by taavikko on 2009-09-04
> **twisted_steel said:**
> How do you get into the grub menu these days?

By pressing Shift a short period of time

---

### Post by twisted_steel on 2009-09-04
> **taavikko said:**
> By pressing Shift a short period of time

Ah, thanks.  I would never have guessed that one.

It looks like the problem is in Grub somewhere because this error appears with all kernels.  I filed a bug for now: _[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/424503](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/424503)_.

---

### Post by berthiggins on 2009-09-04
My machine just failed to boot grub.cfg was pointed at /dev/sdd1 instead of /dev/sdb1.
I booted with a live cd and edited to fix.

---

### Post by setherd on 2009-09-04
I get the same error but I think it is bug 
544155
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=544155](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=544155)
Apparently when gfxterm is enabled it causes the error.

I'll try the tip form this thread.
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=544639](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=544639)

basically: 
Uncomment the `GRUB_TERMINAL=console' in /etc/default/grub and run update-grub.I have a T43 with an ATI x300 video card.

---

### Post by seeker5528 on 2009-09-04
Here is an Ubuntu bug report for this issue:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/424503](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/424503)

The information I posted there related to my video card was obtained by doing:

sudo lspci -vnn

: in a terminal window. Don't know if they need that much information, but I figure it can't hurt.

Later, Seeker

---

### Post by setherd on 2009-09-04
OK I went into grub.cfg (I know I'm not supposed to) but it was easier than getting a shell.
I commented out the following

```

#if loadfont /usr/share/grub/unicode.pf2 ; then
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
  #  terminal gfxterm

  #fi
```

and rebooted.:KS

---

### Post by twisted_steel on 2009-09-04
> **setherd said:**
> OK I went into grub.cfg (I know I'm not supposed to) but it was easier than getting a shell.
I commented out the following

...

and rebooted.:KS

Perfect; that fixed it (I also commented out the last 'fi' in the block).  I updated the grub defaults file (uncomment the GRUB_TERMINAL=console in /etc/default/grub) and ran update-grub once I got back in to a working system.

---

### Post by mshroom on 2009-09-05
Had the same problem with my acer aspire2000 with mobility radeon 9200. 

uncommenting GRUB_TERMINAL=console in /etc/default/grub

and run update-grub worked perfectly. 

Thanx for the help

cheers 

mushroom

---

### Post by feltan on 2009-09-05
I got this problem aswell.
Tried booting with the latest LiveCD and edited boot.cfg but i didn't got it to work. :-(

How do i run update-grub when the system doesn't boot? Or can i do that from the LiveCD?

I appreciate some help.

---

### Post by seeker5528 on 2009-09-05
> **feltan said:**
> I got this problem aswell.
How do i run update-grub when the system doesn't boot? Or can i do that from the LiveCD?

I normally use systemrescuecd for these types of things:

[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

:which would need the following steps. Using sda7 in my examples since that is the root partition of my Ubuntu installation.

```

mkdir /mnt/ubuntu
mount /dev/sda7 /mnt/ubuntu
mount -o bind /dev /mnt/ubuntu/dev
mount -o bind /proc /mnt/ubuntu/proc
chroot /mnt/ubuntu bash
```

Bash being the shell you want to run, probably not necessary to specify when chrooting the ubuntu partition from the ubuntu live cd, but when doing it from System Rescue CD it defaults to a different shell resulting in an error if that shell is not available in the chrooted environment.

Use vim, nano, pico, etc... to make your changes if you have not done so already.

```

nano /etc/default/grub
```
then update grub, exit, unmount everything and reboot...

```

update-grub
exit
umount /mnt/ubuntu/proc
umount /mnt/ubuntu/dev
umount /mnt/ubuntu
reboot
```

If you get messages about things being busy and not being able to be unmounted, it should be fine to go ahead with the reboot, but the preference is to unmount the stuff first if you can.

Should be pretty similar from the ubuntu live cd, just a question of whether the stuff is mounted automagically in /media somewhere or you have to mount it yourself. If you prefer you can do your editing before you chroot your root partition.

RIP is another good live CD for troubleshooting situations:

[http://rip.7bf.de/current/](http://rip.7bf.de/current/)

: which provides an X session with menu items to take you through the mounting/unmounting of your partitions and configuration of wired/wireless network, if you need to download stuff while in the chrooted session. 

Later, Seeker

---

### Post by lprofil on 2009-09-06
Hello,

yesterday i tried to update my mothers pc via ssh but during the process the machine suddenly died. 
After reboot it hangs with exactely this error message:

```
Booting 'Ubuntu, Linux 2.6.31-9-generic'

out of range pointer 0x400040
Aborted. Press any key to exit.
```

Is there any easier way to fix this issue through the grub-edit menue?
Actually i do not want to let her have to chroot into the system through a live-cd.

Thanks in advance.

/lprofil

---

### Post by feltan on 2009-09-06
> **seeker5528 said:**
> I normally use systemrescuecd for these types of things:

[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

:which would need the following steps. Using sda7 in my examples since that is the root partition of my Ubuntu installation.

```

mkdir /mnt/ubuntu
mount /dev/sda7 /mnt/ubuntu
mount -o bind /dev /mnt/ubuntu/dev
mount -o bind /proc /mnt/ubuntu/proc
chroot /mnt/ubuntu bash
```

Bash being the shell you want to run, probably not necessary to specify when chrooting the ubuntu partition from the ubuntu live cd, but when doing it from System Rescue CD it defaults to a different shell resulting in an error if that shell is not available in the chrooted environment.

Use vim, nano, pico, etc... to make your changes if you have not done so already.

```

nano /etc/default/grub
```
then update grub, exit, unmount everything and reboot...

```

update-grub
exit
umount /mnt/ubuntu/proc
umount /mnt/ubuntu/dev
umount /mnt/ubuntu
reboot
```

If you get messages about things being busy and not being able to be unmounted, it should be fine to go ahead with the reboot, but the preference is to unmount the stuff first if you can.

Should be pretty similar from the ubuntu live cd, just a question of whether the stuff is mounted automagically in /media somewhere or you have to mount it yourself. If you prefer you can do your editing before you chroot your root partition.

RIP is another good live CD for troubleshooting situations:

[http://rip.7bf.de/current/](http://rip.7bf.de/current/)

: which provides an X session with menu items to take you through the mounting/unmounting of your partitions and configuration of wired/wireless network, if you need to download stuff while in the chrooted session. 

Later, Seeker

Everything works great until i enter 'update-grub'. 
It says, "grub-probe: error: cannot find a device for /." 
What does that mean?

Thanks for your help! :)

---

### Post by hgergo on 2009-09-06
Hmm same problem can sombody say a good restor commands from Alpa 3~4 disk i dont know wich i hawe

---

### Post by Balle-Larsen on 2009-09-06
seeker5528,

Good guide on how to repair the grub.cfg.
Worked fine for me. Since I have a separate fs for /boot I needed to mount that fs on /boot after the chroot (and before update-grub).
Otherwise you will not get your kernels put into the grub.cfg file by update-grub.

---

### Post by hgergo on 2009-09-06
The guid is not working for me other solutions?

---

### Post by feltan on 2009-09-06
seeker5528, 

Thanks for the instruction. I didn't follow it correctly the first time but when i finally did as you wrote it finally worked. 

Thanks! :D

---

### Post by hgergo on 2009-09-06
Ehh finaly done too

---

### Post by Cuba71 on 2009-09-06
> **feltan said:**
> Everything works great until i enter 'update-grub'. 
It says, "grub-probe: error: cannot find a device for /." 
What does that mean?

Thanks for your help! :)

I'm at this point, all I have is the Live CD and can't find a way to run update-grub

---

### Post by feltan on 2009-09-06
> **Cuba71 said:**
> I'm at this point, all I have is the Live CD and can't find a way to run update-grub

I used the latest Live CD and got it to work. Just follow seeker5528's instructions accurately and you should be up in no time. :)

---

### Post by robin0800 on 2009-09-06
You can also use an alpha 5 alternate cd

Boot CD

select Rescue System

Make sure you set the correct root ......./dev/sda in my case

Follow prompts untill you reach Rescue Menu

choose first option Console Window Note this is root no need for sudo

Type nano /etc/default/grub Uncomment the GRUB_TERMINAL=console line
Save file

Type update-grub

Type exit

Choose reboot from Rescue Menu

---

### Post by Cuba71 on 2009-09-06
Thank you all for the good tips.

---

### Post by Brandel Valico on 2009-09-07
seeker5528 thanks for the walk through got my system back up and running by following it exactly.

---

### Post by helmut0 on 2009-09-07
Not for nothing but I did a fresh install and didn't update yet.When do you think this issue will be fixed?

---

### Post by hgergo on 2009-09-07
With the latest grub update 1.97~beta2-2ubuntu1 the problem still there!!

---

### Post by helmut0 on 2009-09-07
Well I'll wait.No updates and no problems yet on beta 5.....

---

### Post by hgergo on 2009-09-12
With the latest grub update the problem persists

Som new solutions?

---

### Post by twisted_steel on 2009-09-12
> **hgergo said:**
> With the latest grub update the problem persists

Som new solutions?

Not yet.  I've only seen that they are making progress on finding a solution.  You can read more from the Remote Bug Watches linked from [the bug on launchpad]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/424503").

---

### Post by twisted_steel on 2009-09-17
Everything should be fixed with the updates from a few days ago (version 1.97~beta3-1ubuntu1).

---

