---
title: "Edgy Upgrade Interrupted"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by Freddie.Ruddick on 2006-10-20
Short Version: Edgy upgrade from Dapper interrupted,. PC won't boot.

Longer Version: My PC has a hardware problem, wherby every so often (about once a week), it will totally hang, no mouse movement, no response to CTRL-ALT-BACKSPACE. Sometimes it will freeze with a black screen. I have not yet traced the cause of this, but I know that it is not related to Ubuntu, as it also happened once when left in BIOS setup for a while.

Normally, this is not a problem. I save my work regularly, and have a sessionsaver on firefox, so I pull the power (only way, not even power button works), leave it 30mins, then repower.

However, last night I got an email from the Ubuntu-Announce list, that the RC was out and apparently stable. So I fired up the Update Manager, started the Edgy upgrade, closed all other apps and went to bed.

When I awoke, I find that it has hung on a black screen. After a hasty hard reboot, I get the (dapper) splash screen. It pauses for a few seconds on the second item (Mounting root filesystem), gives it an OK, waits a few more seconds, then drops to a black screen with just a flashing underscore. I assume this means that the PC crashed at just the wrong point during the upgrade.

I have tried a Knoppix LiveCD, and can access all of my data.

Is there an easy way of returning my HDD to a bootable state, or should I back up my /home, and reinstall?

Thanks,

Freddie

---

### Post by taurus on 2006-10-20
If you are able to, better back up your personal stuff in /home (and other directories) and do a fresh install.  Might save you a lot of hairs and headaches later.

---

### Post by Karma_Police on 2006-10-20
I can't guarantee this will work, and although I think it will, you better wait for someone to comment on it.

Get a Linux live cd (the Ubuntu should work) and boot it. now you need to mount all partitions. You can do it wherever you want, but you probably want to mount them under the /mnt/ folder. Create a folder there, and then mount your disk. If you have separated home or boot partitions, mount them in the correct place.

So you should have something like:
```
/mnt/oldinstall/
```
and if you have a separated home, mount it under
```
/mnt/oldinstall/home/
```

Now that you have that, you can chroot into your old system:

```

 # chroot /mnt/oldinstall /bin/bash
 # source /etc/profile

```

Now, you should be in your old broken system. You can now restart the update:
```
apt-get update
```
and it should resume the update, and update whatever config files it didn't have the chance to do before. You don't need sudo, because you're now running as root.

If it doesn't work... Well, you can still copy your files, and reinstall.

As I said before, wait for a while to see if anyone corrects me... and good luck.

---

### Post by benjaminzsj on 2006-10-21
If you can get to your system in recovery mode(grub choice), boot up and you're already root, then do things like apt-get dist-upgrade, just the apt-get way to update to Edgy and try to figure out what packages you're missing. You may need to install some of the packages through apt-get install -f, when all done reboot and start over normally, wish you good luck.

Small tip: when I went through this, apt-get didn't even install xserver-xorg for me, which might be your very problem, check it for yourself.

---

### Post by Freddie.Ruddick on 2006-10-22
Thanks for your help guys.

I'm posting this from my (now fully working) edgy box! :D I tried what you suggested, Karma_Police, and it didn't work (I can't remember the error message, but it was something to do with the xserver not being configured correctly. So I just backed up /home and installed from the CD. It was really easy, I just told the installer which partition to mount as /home, recreated my user account, and there was my wallpaper, panels, and menus, just as they were on Dapper :)

Thanks Again

---

