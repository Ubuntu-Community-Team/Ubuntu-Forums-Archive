---
title: "Many issues after upgrading to 16.04"
date: 2016-06-24
forum: Installation &amp; Upgrades
---

### Post by lance317 on 2016-06-24
Hello, I have a VPS running Ubuntu that hosts my personal WordPress testing site (which is mostly just a sandbox of sorts to play around in and test mock-ups and such)

The other day I updated the VPS to 16.04 LTS, and now Apache and MySQL won't start....I can't seem to reinstall or configure either.

Here are the errors from journalctl:

```
[SIZE=2][COLOR=#000000][FONT=Monaco]Jun 22 10:21:38 oasis apache2[4717]:  * Starting Apache httpd web server apache2[/FONT][/COLOR]
Jun 22 10:21:39 apache2[4717]:  *
Jun 22 10:21:39 apache2[4717]:  * The apache2 configtest failed.
Jun 22 10:21:39 apache2[4717]: Output of config test was:
Jun 22 10:21:39 apache2[4717]: apache2: Syntax error on line 204 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/apache2/modules/libphp
Jun 22 10:21:39 apache2[4717]: Action 'configtest' failed.
Jun 22 10:21:39 apache2[4717]: The Apache error log may have more information.
Jun 22 10:21:39 systemd[1]: apache2.service: Control process exited, code=exited status=1
Jun 22 10:21:39 systemd[1]: Failed to start LSB: Apache2 web server.
-- Subject: Unit apache2.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
--
-- Unit apache2.service has failed.
--
-- The result is failed.
Jun 22 10:21:39 systemd[1]: apache2.service: Unit entered failed state.
Jun 22 10:21:39 systemd[1]: apache2.service: Failed with result 'exit-code'.
Jun 22 10:21:45 systemd[1]: Failed to start MySQL Community Server.
-- Subject: Unit mysql.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
--
-- Unit mysql.service has failed.
--
-- The result is failed.
Jun 22 10:21:45 systemd[1]: mysql.service: Unit entered failed state.
Jun 22 10:21:45 systemd[1]: mysql.service: Failed with result 'exit-code'.
Jun 22 10:21:45 systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Jun 22 10:21:45 systemd[1]: Stopped MySQL Community Server.
[COLOR=#000000][FONT=Monaco]-- Subject: Unit mysql.service has finished shutting down[/FONT][/COLOR][/SIZE]
```

Can anyone shed some light on what I can do to troubleshoot? It seems as though the upgrade changed or removed files....Many thanks for any help!

---

