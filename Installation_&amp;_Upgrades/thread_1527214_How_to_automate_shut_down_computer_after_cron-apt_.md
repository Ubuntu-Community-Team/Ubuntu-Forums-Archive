---
title: "How to automate shut down computer after cron-apt job finished?"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by lhcpr on 2010-07-09
Hello all,

Hopefully a simple question but one I have had a hard time finding:

I am using cron-apt to automate updates as follows:

```
graham@graham-desktop:~$ sudo cat /etc/cron.d/cron-apt
#
# Regular cron jobs for the cron-apt package
#
# Every morning at 2 15 on the 10 and 28th of each month.
15 2	10,28 * *	root	test -x /usr/sbin/cron-apt && /usr/sbin/cron-apt

```

I wish to automatically shutdown my computer AFTER this cron-apt job is finished/completed. Can anyone provide assistance with how to achieve this??

Thanks

Graham
Lucid 10.04 user

---

### Post by lechien73 on 2010-07-09
As I understand it, cron-apt cycles through each file in its "action" directory (normally /etc/cron-apt/action.d) in numerical order.

So if you do the following from a terminal window:

```
cd /etc/cron-apt/action.d
ls -l

```
Check the file names - the default is just two files 0-update and 3-download. If this is the case for your installation, then create a new file as follows:

```
sudo nano 5-shutdown
```

And make the contents:

```
shutdown -P now
```

This should power off the machine after the cron-apt job has run. If you have more than two files in the /etc/cron-apt/action.d directory, then make sure that the shutdown command is the last thing that is run  by giving it a higher number (e.g: 99-shutdown).

---

### Post by lhcpr on 2010-07-09
Hey Matt,

Was not aware of the cron-apt action firing sequence :) Have created 5-shutdown and will give it a go tonight & confirm outcome.

Cheers Graham

---

### Post by lhcpr on 2010-07-09
Alright then,

So I had my cron-apt job scheduled for 2:15 am this morning. Was logged in as my user name and then left the computer to it's own devices as I slept :p

As per your suggestion (thanks Matt), I added the 5-shutdown (shutdown -P now) to the /etc/cron-apt/action.d folder.

I woke at 5:26am to check the computer and found that it was still running and the screen was locked. Thinking that 3hrs should have been enough to run the cron-apt job, I unlocked my session and shutdown the computer (sorry this is long winded).

Checking log messages this morning, it seems as though (as far as my understanding goes) the cron-apt job was started but then suspended/slept until I woke the computer up at 5:26am at which point the job resumed. See log messages below:

```
--------------------------------------------------------------------
**_Jul 10 02:15:01_** graham-desktop CRON[1790]: (root) CMD (test -x /usr/sbin/cron-apt && /usr/sbin/cron-apt)
Jul 10 02:17:01 graham-desktop CRON[1806]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 10 03:09:29 graham-desktop wpa_supplicant[988]: WPA: Group rekeying completed with 00:19:db:9c:9d:de [GTK=TKIP]
Jul 10 03:17:01 graham-desktop CRON[1913]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 10 04:17:01 graham-desktop CRON[1921]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 10 04:24:25 graham-desktop wpa_supplicant[988]: WPA: Group rekeying completed with 00:19:db:9c:9d:de [GTK=TKIP]
Jul 10 04:45:55 graham-desktop dhclient: DHCPREQUEST of 192.168.1.3 on wlan0 to 192.168.1.254 port 67
Jul 10 04:45:55 graham-desktop dhclient: DHCPACK of 192.168.1.3 from 192.168.1.254
Jul 10 04:45:55 graham-desktop dhclient: bound to 192.168.1.3 -- renewal in 19892 seconds.
Jul 10 05:03:22 graham-desktop dhclient: DHCPREQUEST of 192.168.1.3 on wlan0 to 192.168.1.254 port 67
Jul 10 05:03:22 graham-desktop dhclient: DHCPREQUEST of 192.168.1.3 on wlan0 to 192.168.1.254 port 67
Jul 10 05:03:22 graham-desktop dhclient: DHCPACK of 192.168.1.3 from 192.168.1.254
Jul 10 05:03:22 graham-desktop dhclient: DHCPACK of 192.168.1.3 from 192.168.1.254
Jul 10 05:03:22 graham-desktop dhclient: bound to 192.168.1.3 -- renewal in 19782 seconds.
Jul 10 05:03:22 graham-desktop dhclient: bound to 192.168.1.3 -- renewal in 19782 seconds.
Jul 10 05:17:01 graham-desktop CRON[1968]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
--------------------------------------------------------------------------

**_Jul 10 05:26:23_** graham-desktop cron-apt: CRON-APT RUN [/etc/cron-apt/config]: Sat Jul 10 **_02:15:01_** WST 2010
Jul 10 05:26:23 graham-desktop cron-apt: CRON-APT SLEEP: 2584, Sat Jul 10 02:58:05 WST 2010
Jul 10 **_05:26:23_** graham-desktop cron-apt: CRON-APT ACTION: 3-download
Jul 10 05:26:23 graham-desktop cron-apt: CRON-APT LINE: /usr/bin/apt-get dist-upgrade -d -y -o APT::Get::Show-Upgraded=true
Jul 10 05:26:23 graham-desktop cron-apt: Reading package lists...
Jul 10 05:26:23 graham-desktop cron-apt: Building dependency tree...
Jul 10 05:26:23 graham-desktop cron-apt: Reading state information...
Jul 10 05:26:23 graham-desktop cron-apt: The following NEW packages will be installed:
--------------------------------------------------------------------------

Jul 10 **_05:26:23_** graham-desktop cron-apt: CRON-APT RUN [/etc/cron-apt/config]: Sat Jul 10 0**_2:15:01_** WST 2010
Jul 10 05:26:23 graham-desktop cron-apt: CRON-APT SLEEP: 2584, Sat Jul 10 02:58:05 WST 2010
Jul 10 05:26:23 graham-desktop cron-apt: CRON-APT ACTION: 3-download
Jul 10 05:26:23 graham-desktop cron-apt: CRON-APT LINE: /usr/bin/apt-get dist-upgrade -d -y -o APT::Get::Show-Upgraded=true
Jul 10 05:26:23 graham-desktop cron-apt: 221 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Jul 10 05:26:23 graham-desktop cron-apt: Need to get 233MB/235MB of archives.
Jul 10 05:26:23 graham-desktop cron-apt: Fetched 92.8MB in 2h 28min 7s (10.4kB/s)
Jul 10 **_05:26:23_** graham-desktop cron-apt: E: Some files failed to download
--------------------------------------------------------------------------
``` - I am using a wireless USB adapter to connect with wireless router. Under power settings, I do not have sleep/hibernation activated

Ok - so the reason that the computer didn't shut down was because the cron-apt job; I get that.

Now, can anyone suggest a reason and solution as to why the cron-apt job won't just initiate and complete at the said time???

Thanks in advance - Graham
Ubuntu 10.04 Lucid Lynx user

---

