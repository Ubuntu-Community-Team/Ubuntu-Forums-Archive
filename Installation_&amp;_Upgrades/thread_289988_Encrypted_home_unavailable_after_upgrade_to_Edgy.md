---
title: "Encrypted /home unavailable after upgrade to Edgy"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by mludd on 2006-10-31
Well, today was the day I decided to upgrade from 6.06 to 6.10. I was suspecting I might have some problems with my encrypted home partition but I was hoping I wouldn't.

Anyway, after upgrading my system rebooted and I faced what you can see in the picture below, except that it wasn't /dev/mapper/hda7, it was /dev/mapper/home but since that was also removed I tried changing it (there was no /dev/mapper/hda7 for me in Dapper).

I used the instructions on [this]("http://wiki.linuxportalen.se/index.php/Kryptera_filsystem_utan_dataf%C3%B6rlust") page to encrypt the partition and now I'm wondering if running
```
cryptsetyp -y -c aes -s 256 create home /dev/hda7
```
would fix the problem or make matters worse? I know I should use 'man' to look this up but my system is pretty hosed at the moment and I'm trying to get it fixed so I can get working on fixing everything else that surely broke when I upgraded.

Oh, I've got a photo of what it looks like when I try to boot, I would've tried to figure out a better way of doing it than a jpeg but I'm doing this from my windows box, seems ndiswrapper got killed as well.

[http://pantburk.info/edgyerror.jpg](http://pantburk.info/edgyerror.jpg)

/mludd

---

### Post by mludd on 2006-10-31
Well, running cryptsetup when I get dropped to the console during boot works for getting /dev/mapper/home up again so that it becomes mountable, unfortunately I haven't been able to get it to just prompt me for my passphrase, but at least I can salvage the data now (and reinstall, yeah I'm lazy :P ).

/mludd

---

### Post by QCompson on 2006-11-01
Those of us with encrypted home directories currently seem out of luck with Edgy Eft.

The bug is listed here:
[https://launchpad.net/distros/ubuntu/+source/cryptsetup/+bug/62751](https://launchpad.net/distros/ubuntu/+source/cryptsetup/+bug/62751)

I have been surprised at how little attention the cryptsetup bug in Edgy has gotten in these forums.  Apparently there aren't a lot of Ubuntu users who encrypt parts of their system (or at least very few who have upgraded to Edgy).  I hope this gets worked out soon, but according to the bug report the matter has "Low Urgency".  :(

---

