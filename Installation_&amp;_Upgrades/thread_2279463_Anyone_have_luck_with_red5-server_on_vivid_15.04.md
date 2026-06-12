---
title: "Anyone have luck with red5-server on vivid 15.04?"
date: 2015-05-23
forum: Installation &amp; Upgrades
---

### Post by rkleemann on 2015-05-23
I just installed 15.04 on Google Compute Engine and installed red5-server package.

However red5 fails upon attempting to start.

This is the only info I can get from it:

$ sudo service red5-server start
Job for red5-server.service failed. See "systemctl status red5-server.service" and "journalctl -xe" for details.
rmkleemann_gmail_com@instance-1:~$ sudo journalctl -xe
May 23 18:57:11 instance-1 systemd[1]: Starting LSB: Red5...
-- Subject: Unit red5-server.service has begun start-up
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
--
-- Unit red5-server.service has begun starting up.
May 23 18:57:12 instance-1 red5-server[8903]: * Starting Flash streaming server
May 23 18:57:17 instance-1 red5-server[8903]: ...fail!
May 23 18:57:17 instance-1 systemd[1]: red5-server.service: control process exit
May 23 18:57:17 instance-1 systemd[1]: Failed to start LSB: Red5.
-- Subject: Unit red5-server.service has failed
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
--
-- Unit red5-server.service has failed.
--
-- The result is failed.
May 23 18:57:17 instance-1 systemd[1]: Unit red5-server.service entered failed s
May 23 18:57:17 instance-1 systemd[1]: red5-server.service failed.
May 23 18:57:17 instance-1 polkitd(authority=local)[23398]: Unregistered Authent
May 23 18:57:17 instance-1 sudo[8877]: pam_unix(sudo:session): session closed fo
May 23 18:57:25 instance-1 sudo[8949]: rmkleemann_gmail_com : TTY=pts/1 ; PWD=/h
May 23 18:57:25 instance-1 sudo[8949]: pam_unix(sudo:session): session opened fo

---

### Post by Vladlenin5000 on 2015-05-23
There's already a reported [bug]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=781750") concerning *systemd*.
Try booting with *upstart* (Grub > Advanced), See if it makes a difference.

---

