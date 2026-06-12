---
title: "Error installing Maya"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by mella2000 on 2008-08-02
I'm following these instructions

[http://ubuntuforums.org/showthread.php?t=561417&highlight=Maya+2008](http://ubuntuforums.org/showthread.php?t=561417&highlight=Maya+2008)

I 've just mount Maya here:
/media/cdrom0/Maya

Here  /media/cdrom0/Maya/linux I have rpm files
AWCommon-server-10.80-13.i686.rpm
Maya2008_0-2008.0-116.i686.rpm
AWCommon-10.80-13.i686.rpm

I 've wrotten on terminal
sudo alien -i /media/cdrom0/Maya/linux/Maya2008_0-2008.0-116.i686.rpm

but

 Warning: Skipping conversion of scripts in package Maya2008_0:
postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.
mkdir: cannot create directory `Maya2008_0-2008.0': File exists
unable to mkdir Maya2008_0-2008.0:  at /usr/share/perl5/Alien/
Package.pm line 25

Please, I don't understand what's happened.

---

