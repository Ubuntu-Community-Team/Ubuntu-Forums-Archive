---
title: "Network just &quot;dies&quot; after a while"
date: 2005-05-13
forum: Installation &amp; Upgrades
---

### Post by andersno on 2005-05-13
I am still trying to install an Apache2 server on a dedicated computer and am doing the configuration in console mode only.

After some fiddling, my wireless card is now working using the ACX100 utility, but after some time online the computer can no longer be seen from the network and pings do not go out or in. However, ifconfig and iwconfig still reports the card with an IP.

Enclose the outputs of "tail /var/log/syslog" and "tail /var/log/messages":

"tail /var/logsyslog:
May 13 17:09:01 localhost /USR/SBIN/CRON[5686]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)
May 13 17:17:01 localhost /USR/SBIN/CRON[5695]: (root) CMD (   run-parts --report /etc/cron.hourly)
May 13 17:29:41 localhost -- MARK --
May 13 17:39:01 localhost /USR/SBIN/CRON[5697]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)
May 13 17:43:25 localhost kernel: Starting radio scan
May 13 17:43:28 localhost kernel: Got Info IRQ: status 0x0001, type 0xc500: (unknown)
May 13 17:49:30 localhost kernel: FIXME: most likely needs refinement, first implementation version only...
May 13 17:49:30 localhost kernel: get_mask 0x00000000, set_mask 0x00000040
May 13 17:49:30 localhost kernel: setting RXconfig to 2010:0fdd
May 13 17:49:30 localhost kernel: get_mask 0x00000000, set_mask 0x00000000 - after update"

"tail /var/log/messages:
May 13 16:29:41 localhost -- MARK --
May 13 16:49:41 localhost -- MARK --
May 13 17:09:41 localhost -- MARK --
May 13 17:29:41 localhost -- MARK --
May 13 17:43:25 localhost kernel: Starting radio scan
May 13 17:43:28 localhost kernel: Got Info IRQ: status 0x0001, type 0xc500: (unknown)
May 13 17:49:30 localhost kernel: FIXME: most likely needs refinement, first implementation version only...
May 13 17:49:30 localhost kernel: get_mask 0x00000000, set_mask 0x00000040
May 13 17:49:30 localhost kernel: setting RXconfig to 2010:0fdd
May 13 17:49:30 localhost kernel: get_mask 0x00000000, set_mask 0x00000000 - after update"

Can anybody please explain what is happening here. I have not started any cron jobs.

In order to get the wireless card working I had to install "acx100-0.2.0pre8_plus _fixes_56" and I fear that I haven't completely gotten rid of the original acx100 which was installed when I first installed Ubuntu. Would also appreciate any advice on where to install the final configurations for acx100. Haven't used any Debian-style distro before.

---

