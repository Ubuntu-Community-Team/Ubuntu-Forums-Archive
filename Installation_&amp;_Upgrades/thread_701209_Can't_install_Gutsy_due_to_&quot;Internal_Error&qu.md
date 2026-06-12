---
title: "Can't install Gutsy due to &quot;Internal Error&quot;"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by doug124 on 2008-02-19
Hello,

I am trying to install the 64 bit edition of Gutsy (7.10) on my desktop but an unable to do so.  I tried the alternate install CD which went very slowly, and then when it got to installing the "base system" froze at around 80%.  I'm then tried the standard desktop install CD which also took a long time to start, and after finally getting in to GNOME displays the error

```
Internal Error
Failed to initialize HAL!
```

I have seen lots of posts regarding problems with this error, however most the solutions require modifying configuration files and restarting. That is not an option for me since I have no OS installed at the moment.  The system also runs very slowly so even simple tasks are quite time consuming.

I have tried running

```
sudo /etc/init.d/dbus start
```

which prints out messages saying it is starting hald, but does not give the "OK" and does not speed things up.  I also tried replacing "start" with "restart" but there was no difference (well, other than everything being stopped before being started again).

Note: Other things are also started (dbus, Network Manager, NetworkManagerDispatcher, console-kit-daemon, avahi-daemon, dhcdbd, ...) and "system-tools-backends" fails to start if that is relevant.

I also tried restarting the X server, which gives an error 

```

There was an error starting the GNOME Setting Daemon
...
Failed to connect to socket /tmp/dbus-6MhXBH2jG2:
Connection Refused
...

```

and then removes the visual effects (making things slightly faster) but still unreasonably slow.  And I still can't get the installation to complete.

In /etc/init.d/rc "CONCURRENCY=none" was already the setting, so that is not likely the problem as was suggested for some problems.

If anyone has any ideas as to how I might get this install to work it would be appreciated, thanks

     -Doug

---

### Post by Pumalite on 2008-02-19
Make sure you do an md5sum on the iso, burn at 4x or less in good quality media as image, clean the lens in your burner; and if all checks out OK., try the CD's in a different computer.

---

### Post by doug124 on 2008-02-19
Hi Pumalite,

I did do a md5sum and it matched, this is also the second time I had downloaded the iso (in case it somewhow passed the md5sum while being incorrect).  The CD was burned at 4x and didn't look scratched or anything.... not sure what makes it good quality, it's made by "TDK".

I have access to only one 64bit computer (mine) though the CD seems to read fine on this one (a Pentium 4).  I would not expect it to work properly if I tried to boot from it, so am wondering how else I could check it.  Thanks for your quick reply,

     -Doug

---

### Post by Pumalite on 2008-02-19
The thing here is to find out if your burner is at fault. Check it in the 64 bit.

---

### Post by doug124 on 2008-02-22
So I'm not sure what you mean by "check it", here is what I have done:

After burning the CD I verified the data using the burning software (Nero) and it passed (no errors).

I also verified the CD from the CD itself (on the 64 bit computer) which also said it was ok.

If that's wrong let me know...

     -Doug

---

### Post by xeth_delta on 2008-02-22
Hope not to be intruding, but may I also sugest performing a check of the actual image, before you burn it to the CD? Also, you should burn the image at 4x or less. More information here: [https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28#head-6788e413b69a8947c263c08d435f3e7fa8a3237d](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28#head-6788e413b69a8947c263c08d435f3e7fa8a3237d)

---

### Post by Pumalite on 2008-02-22
> **doug124 said:**
> So I'm not sure what you mean by "check it", here is what I have done:

After burning the CD I verified the data using the burning software (Nero) and it passed (no errors).

I also verified the CD from the CD itself (on the 64 bit computer) which also said it was ok.

If that's wrong let me know...

     -Doug
If that's a new burnt CD you are talking (after doing md5sum on iso, burning at 4x or less, etc), go ahead and try it on your other computer.

---

### Post by doug124 on 2008-02-25
I tried checking it in my other computer but got the message:

```
Your CPU does not support long mode.  Use a 32 bit distribution
```

In response to other comments the MD5 sum matched that on the website, so it appears to have downloaded fine.  Also, it appears to have burned fine since it passed the "check" on the computer that burned it.

---

### Post by Pumalite on 2008-02-25
I downloaded the 64 bit iso and installed it in a Core 2 Duo. All went fine. So, you have some kind of hardware incompatibility. You might want to try some boot parameters. Here is a guide and a collection of them to be tried alone and in different combinations:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off

---

