---
title: "Upgrading from an old (no longer supported) Ubuntu version - guidance?"
date: 2016-02-16
forum: Installation &amp; Upgrades
---

### Post by cmetzler on 2016-02-16
Hi.  I have a machine that has 10.10 (Maverick) installed.  I'd like to bring this machine up to a supported version of Ubuntu.

I assume that I have two options:

1.  Do this by successive upgrades, first to 11.04 (Natty), then to 12.04 LTS (Precise), which I believe is still supported.

2.  Do as a fresh install at whatever supported version I want.

The former obviously seems like more work, but it also seems like I could do it without needing to restore the userspace from backup (except if something goes horribly wrong).  I have backups of /home, I'm anal-retentive about it, so it's not like I can't do it; but if I can upgrade around the userspace as it is, that doesn't bug me as much.  I'm not sure why.  Maybe I shouldn't be bugged by the fresh install, I dunno.

Anyway, my main questions concern what options I have for the upgrading or the fresh install.  Everything seems available as an .iso file; but I don't have a CD burner on this machine currently.  I do, however, have three big USB drives which I use for backups.  Is putting the ISO there, and then telling my current grub to boot off an ISO file on the USB drive, and option?  If so, can someone point me to a HOWTO that would educate me on how to do that?  Is there a better option I should consider?

Thanks very much.

---

### Post by kurt18947 on 2016-02-16
I would certainly start fresh. Save any important data files first. You can download the .iso of choice, download USB creation software (I use Unetbootin but there are other great choices) and create a live USB. How powerful is your machine? Processor? Memory? 'Lighter' distros such as Lubuntu, Xubuntu and similar work better on older or less capable machines. A live USB might help you make that determination. If the last Ubuntu you used was 10.10,  Unity & gnome-shell are a LOT different. Ubuntu-MATE or Gnome Flashback might be closest in terms of look and feel and they're also somewhat less demanding of resources.

---

### Post by grahammechanical on 2016-02-16
Here is the difficulty.

1) Ubuntu 10.10 is end of life. So, you have to do an end of life upgrade to get to 11.04.
2) Ubuntu 11.04 is end of life. So, you would have to do an end of life upgrade to get to 11.10.
3) Ubuntu 11.10 is end of life but you might not need to do an end of life upgrade to get to 12.04.
4) Ubuntu 10.10 uses Gnome 2 desktop environment with the Gnome 2 panel user interface. But from 11.04 onwards Ubuntu started using the Gnome 3 DE & the Unity UI. So, there is a big, big jump in code between 10.10 & 11.04.
5) A lot of improvements were made to Unity between 11.04 & 12.04.
6) all these code jumps increase the risk of the upgrade breaking in some way.

The good news is that by the time you get to 12.04 you will be an expert on end of life upgrades and can advise others based upon experience. So, here you go.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Please keep something else in mind.

a) Ubuntu Unity requires a video adapter that can do hardware accelerated 3D rendering. Older video adapters do not have this capability.
b) Newer versions of Ubuntu come with newer Linux kernels & newer proprietary video drivers which may have dropped support for the video adapter.
c) Revert to using an open source video driver.
d) Revert the desktop to as default a condition as far as possible.
e) Expect the whole thing to break at some point.

I have a machine that first run Ubuntu 07.04 and is now running Ubuntu 16.04. But a few years ago I upgraded to video adapter does hardware accelerated 3D rendering and with 1GB of it own memory and that is making the difference.

Regards.

---

### Post by mastablasta on 2016-02-17
Do a fresh install. you do not need to format the drive if you do not want to. might still be good to clean up the /. and also make sure new version works well with your PC (in stock Ubuntu you now need descent GPU and enough RAM).

> **cmetzler said:**
> 
Anyway, my main questions concern what options I have for the upgrading or the fresh install.  Everything seems available as an .iso file; but I don't have a CD burner on this machine currently.  I do, however, have three big USB drives which I use for backups.  Is putting the ISO there, and then telling my current grub to boot off an ISO file on the USB drive, and option?  If so, can someone point me to a HOWTO that would educate me on how to do that?  Is there a better option I should consider?
.

oh dear... an 8 GB USB stick costs less than 4 EUR here. you can put a single linux on it (Unetbootin, pendrivelinux...) or multiple Linux distros on that stick (using YUMI). with multiboot you can later use the USB it as system rescue disk (holding your live install image), or for creating backup images (RedoBackup, Clonezilla), troubleshooting (hyren's boot disk, ultimate boot disk...), anonymous browsing (TAILS, liberte linux)... many uses on same USB and here it would cost less than 4 EUR to get the stick so I am not sure why would you want to complicate your life to save 3 or 4 EUR. maybe you can get a smaller one even cheaper, they just don't sell them where I live. 8 Gb is min.

---

### Post by cmetzler on 2016-02-17
> **mastablasta said:**
> 
oh dear... an 8 GB USB stick costs less than 4 EUR here.
Man, for some reason a USB stick never occurred to me.

Thanks folks!

On the machine in question, the CPU is pretty old (Athlon XP 3800+ 64-bit, from ~2005) but I do have more recent video (nVidia GTX 280).  That said, I dl'd xubuntu to minimize the impact of speed issues.

You indicated that I shouldn't need to re-format; that suggests I'll be able to identify the existing partitions and say "use this already-existing partition for /var, use this one for /home" etc.?

Thanks again.

---

