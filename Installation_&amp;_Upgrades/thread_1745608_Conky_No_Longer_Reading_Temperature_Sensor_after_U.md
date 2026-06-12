---
title: "Conky No Longer Reading Temperature Sensor after Upgrade to Natty"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2011-05-01
Hello,

I recently upgraded to Natty and now Conky is no longer reading the temperature sensor.  It permanently displays 0' Celcius.

The temperature was displaying correctly before the upgrade and the mobo is brand-new.


Any assistance appreciated.



Hannibal

---

### Post by coljohnhannibalsmith on 2011-05-01
Additional information:

I verified conky's operation with the previous -29 kernel, which is still installed.  Conky is able to read the temperature sensor correctly with -29.

Obviously it is the -8 kernel, which is preventing conky from reading the temperature sensor.


Should I submit this as a bug?  If so, how do I do it?




Thanks Hannibal

---

### Post by Quackers on 2011-05-01
Yes, acpitemp doesn't work in conky with Natty Narwhal. It has never worked, in fact with Natty.

---

### Post by coljohnhannibalsmith on 2011-05-01
> **Quackers said:**
> Yes, acpitemp doesn't work in conky with Natty Narwhal. It has never worked, in fact with Natty.

Thanks for the additional verification; however this begs the question...

WTH not!:confused:

Oh and BTW, I love ducks...  *One of my favorite songs is **"One White Duck"** by Jethro Tull.*

[COLOR=Blue]***And here's a couple of YouTube covers that I think are fabulous:***[/COLOR]

[http://www.youtube.com/watch?v=x01gY3GIMmE](http://www.youtube.com/watch?v=x01gY3GIMmE)

[http://www.youtube.com/watch?v=YgsKRM6EFhk](http://www.youtube.com/watch?v=YgsKRM6EFhk)





[COLOR=Blue]***Thanks, Hannibal***[/COLOR]

---

### Post by Quackers on 2011-05-01
Lol. The simple answer is I don't know.
I first noticed it when running a Natty testing system some months ago. I'm not even sure it's a Natty problem, as such. It could be something that conky can't handle. I just don't know.
I didn't launch a bug as I didn't need the temp display at the time, so deleted the line from the conky display.

---

### Post by coljohnhannibalsmith on 2011-05-02
Now logging stopped working...


Nutz...

---

### Post by coljohnhannibalsmith on 2011-05-15
Well,

I booted back into the 35-9 kernel, and logging has stopped working there too...

[COLOR=Blue]***How can this be...***[/COLOR]

---

### Post by m_duck on 2011-05-15
I saw another post similar to this a week or so ago. I think the solution involved using another command in conky (hwmon perhaps?) to read your temperatures - have a look on the [conky variables](http://conky.sourceforge.net/variables.html) page. Failing that, if you install ***lm_sensors***, you can grab the temperatures using an ***execi*** variable, the ***sensors*** command and some grepping, cutting and awking.

---

### Post by coljohnhannibalsmith on 2011-05-15
> **m_duck said:**
> I saw another post similar to this a week or so ago. I think the solution involved using another command in conky (hwmon perhaps?) to read your temperatures - have a look on the [conky variables]("http://conky.sourceforge.net/variables.html") page. Failing that, if you install ***lm_sensors***, you can grab the temperatures using an ***execi*** variable, the ***sensors*** command and some grepping, cutting and awking.

Thanks for the reply,

I checked-out the conky variables page as you suggested; and read the usage info; but I still can't seem to write this properly.  The info for this variable follows:

hwmon     (dev) type n (factor offset)

Hwmon sensor from sysfs (Linux 2.6). Parameter         dev may be omitted if you have only one hwmon device.         Parameter type is either 'in' or 'vol' meaning voltage;         'fan' meaning fan; 'temp' meaning temperature. Parameter n         is number of the sensor. See /sys/class/hwmon/ on your         local computer. The optional arguments 'factor' and         'offset' allow precalculation of the raw input, which is         being modified as follows: 'input = input * factor +         offset'. Note that they have to be given as decimal values         (i.e. contain at least one decimal place).          

In [COLOR=Blue]** /sys/class/hwmon/**[/COLOR] I have [COLOR=Blue]**hwmon0**[/COLOR] and [COLOR=Blue]**hwmon1**[/COLOR].

I tried writing this as:

[COLOR=Blue]**${hwmon (0) temp 0}**[/COLOR]

and had unsatifactory results.

Am I not writing this correctly???




**Thanks Hannibal**

---

### Post by coljohnhannibalsmith on 2011-05-15
Ok, I think I've got it:

I Google'd ***"conkyrc hwmon;"*** and found an example rc file that shows the correct way to write this variable:


[COLOR=Blue]**${hwmon 0 temp 1}**[/COLOR]

[FONT=Verdana]I was trying to write:[/FONT]

[COLOR=Blue]**${hwmon 0 temp 0}**[/COLOR]

[FONT=Verdana]
Conky wouldn't even lauch until I wrote the variable as in the first example.

Now my tempreature sensor is reading correctly[/FONT]. (see attachment)

[FONT=Verdana]BTW, I told the last poster that I love ducks...  That goes double now...


[COLOR=Blue][B][I]Yummy popcorn for all...
[/I][/B][/COLOR][/FONT]
[IMG]http://www.picturesof.net/_images_300/Girl_Feeding_Baby_Ducks_Royalty_Free_Clipart_Picture_090319-205425-832052.jpg[/IMG]


[FONT=Verdana]Also, any ideas about how I might be able to get ***logging*** back???




[COLOR=Blue]***Thanks Hannibal***[/COLOR]
[/FONT]

---

### Post by Quackers on 2011-05-16
Me too :-)
My temp is back as well.
Thanks brother m_duck :wink:

---

### Post by m_duck on 2011-05-16
Glad to help. With regards to logging, which logs were you reading, how were you reading them and in what way does it no longer work (no output, error message - I assume the former from your previous image)?

---

### Post by coljohnhannibalsmith on 2011-05-16
> **m_duck said:**
> Glad to help. With regards to logging, which logs were you reading, how were you reading them and in what way does it no longer work (no output, error message -*** I assume the former from your previous image***)?

Here's the code I'm using for logging.  It's from my ***.conkyrc*** file:

```
[COLOR=Blue][B]${color yellow}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}[/B][/COLOR]

```And, you're quite right...  **No output.**:(





[COLOR=Blue][B][I]Hannibal
[/I] [/B][/COLOR]

---

### Post by m_duck on 2011-05-16
Hmm. I can only think of two reasons for that off the top of my head - either /var/log/messages doesn't exist, or the permissions have changed and do not allow your user to read them anymore. In that vane, can you give the output of the following:

To see if we can actually tail the messages log file:
```
tail -n3 /var/log/messages
```
To see what log files are available, and if messages is one of them in addition to who owns it:
```
ls -l /var/log
```
Finally, since I don't have an Ubuntu box to hand, the respective outputs for:
```
groups user
```
where ***user*** is root, and then user is your username (2 commands).

---

### Post by coljohnhannibalsmith on 2011-05-16
> **m_duck said:**
> Hmm. I can only think of two reasons for that off the top of my head - either /var/log/messages doesn't exist, or the permissions have changed and do not allow your user to read them anymore. In that vane, can you give the output of the following:

To see if we can actually tail the messages log file:
```
tail -n3 /var/log/messages
```To see what log files are available, and if messages is one of them in addition to who owns it:
```
ls -l /var/log
```Finally, since I don't have an Ubuntu box to hand, the respective outputs for:
```
groups user
```where ***user*** is root, and then user is your username (2 commands).

Sounds like a plan:

[B]Here's the output from the first command:
[/B] 
```
[COLOR=Blue][B]sophie@sophie-laptop:~$ tail -n3 /var/log/messages
sophie@sophie-laptop:~$ [/B][/COLOR]
```Not very impressive.  This file is also empty.  But, I've noticed a file sitting right next to it named **/var/log/messages.1**; and it's populated, and appears to contain the normal system log messages.

**Here's a sample of its contents:**

```
[COLOR=Blue][B]Apr 30 07:59:21 sophie-laptop kernel: [58579.147338] type=1400 audit(1304164761.922:32): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=18630 comm="apparmor_parser"
Apr 30 07:59:21 sophie-laptop kernel: [58579.147466] type=1400 audit(1304164761.922:33): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=18630 comm="apparmor_parser"
Apr 30 08:00:42 sophie-laptop kernel: Kernel logging (proc) stopped.
Apr 30 08:00:42 sophie-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="938" x-info="http://www.rsyslog.com"] exiting on signal 15.[/B][/COLOR]

```[B]I can also tail its contents:

[/B]```
[B]
sophie@sophie-laptop:~$ tail -n3 /var/log/messages.1
Apr 30 07:59:21 sophie-laptop kernel: [58579.147466] type=1400 audit(1304164761.922:33): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=18630 comm="apparmor_parser"
Apr 30 08:00:42 sophie-laptop kernel: Kernel logging (proc) stopped.
Apr 30 08:00:42 sophie-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="938" x-info="http://www.rsyslog.com"] exiting on signal 15.
sophie@sophie-laptop:~$ 
[/B]
```
[B]
Here's the output from the second command:[/B]

```
[COLOR=Blue][B]sophie@sophie-laptop:~$ ls -l /var/log
total 44020
-rw-r--r-- 1 root              root        11030 2011-05-15 22:28 alternatives.log
-rw-r--r-- 1 root              root       109142 2011-05-01 10:31 alternatives.log.1
-rw-r--r-- 1 root              root         2735 2011-03-31 11:08 alternatives.log.2.gz
-rw-r--r-- 1 root              root         1552 2011-02-28 17:10 alternatives.log.3.gz
-rw-r--r-- 1 root              root         6043 2011-01-05 17:26 alternatives.log.4.gz
drwxr-x--- 2 root              adm          4096 2011-05-15 23:03 apache2
drwxr-xr-x 2 root              root         4096 2010-09-27 12:09 apparmor
drwxr-xr-x 2 root              root         4096 2011-05-02 07:41 apt
drwxr-xr-x 2 root              root         4096 2011-05-16 07:59 argus
-rw-r----- 1 syslog            adm        154971 2011-05-16 11:20 auth.log
-rw-r----- 1 syslog            adm        809562 2011-05-15 08:05 auth.log.1
-rw-r----- 1 syslog            adm         54629 2011-05-08 07:35 auth.log.2.gz
-rw-r----- 1 syslog            adm         68044 2011-05-02 07:40 auth.log.3.gz
-rw-r----- 1 syslog            adm         51382 2011-04-24 08:02 auth.log.4.gz
-rw-r----- 1 root              adm            31 2010-10-07 11:57 boot
-rw-r--r-- 1 root              root         2703 2011-05-15 23:00 boot.log
-rw-r--r-- 1 root              root        41377 2010-10-07 11:58 bootstrap.log
-rw-rw---- 1 root              utmp         1152 2011-05-13 23:32 btmp
-rw-rw---- 1 root              utmp          151 2011-05-01 18:23 btmp.1.gz
drwxr-xr-x 2 root              root         4096 2006-05-04 19:44 checkservice
drwxr-xr-x 2 clamav            clamav       4096 2011-05-15 08:08 clamav
drwxr-xr-x 2 root              root         4096 2011-05-02 07:42 ConsoleKit
drwxr-xr-x 2 root              root         4096 2011-05-14 08:01 cups
-rw-r----- 1 syslog            adm             0 2011-05-02 07:42 daemon.log
-rw-r----- 1 syslog            adm       1128965 2011-04-30 08:00 daemon.log.1
-rw-r----- 1 syslog            adm        165012 2011-04-24 08:00 daemon.log.2.gz
-rw-r----- 1 syslog            adm        359600 2011-04-18 07:16 daemon.log.3.gz
-rw-r----- 1 syslog            adm        778109 2011-04-10 07:00 daemon.log.4.gz
drwxr-xr-x 2 root              root         4096 2010-12-23 17:09 dbconfig-common
-rw-r----- 1 syslog            adm             0 2011-05-02 07:42 debug
-rw-r----- 1 syslog            adm        713218 2011-04-30 07:53 debug.1
-rw-r----- 1 syslog            adm         88691 2011-04-24 07:55 debug.2.gz
-rw-r----- 1 syslog            adm        139144 2011-04-18 07:19 debug.3.gz
-rw-r----- 1 syslog            adm        113580 2011-04-10 06:35 debug.4.gz
-rw-r----- 1 root              adm         36626 2011-05-15 23:00 denyhosts
-rw-r----- 1 root              adm        292609 2011-05-15 18:12 denyhosts.1
-rw-r----- 1 root              adm          5424 2011-04-23 16:13 denyhosts.4.gz
-rw-r----- 1 root              adm         10936 2011-04-18 07:15 denyhosts.5.gz
-rw-r----- 1 root              adm         10863 2011-04-09 17:38 denyhosts.6.gz
-rw-r----- 1 root              adm          3799 2011-04-02 15:32 denyhosts.7.gz
-rw-r--r-- 1 root              root         2184 2011-03-26 21:50 denyhosts.8.gz
drwxr-xr-x 2 root              root         4096 2011-04-30 09:23 dist-upgrade
-rw-r----- 1 root              adm         62542 2011-05-15 23:00 dmesg
-rw-r----- 1 root              adm         61555 2011-05-15 22:22 dmesg.0
-rw-r----- 1 root              adm         16289 2011-05-15 22:13 dmesg.1.gz
-rw-r----- 1 root              adm         15582 2011-05-15 18:27 dmesg.2.gz
-rw-r----- 1 root              adm         15810 2011-05-15 18:23 dmesg.3.gz
-rw-r----- 1 root              adm         15544 2011-05-15 18:19 dmesg.4.gz
-rw-r--r-- 1 root              root       898538 2011-05-16 10:09 dpkg.log
-rw-r--r-- 1 root              root      4205322 2011-05-01 15:00 dpkg.log.1
-rw-r--r-- 1 root              root        67085 2011-03-31 13:34 dpkg.log.2.gz
-rw-r--r-- 1 root              root        69686 2011-02-28 20:54 dpkg.log.3.gz
-rw-r--r-- 1 root              root       169941 2011-01-05 19:05 dpkg.log.4.gz
-rw-r--r-- 1 root              root        32032 2011-05-04 02:22 faillog
-rw-r--r-- 1 root              root         5273 2011-05-14 00:13 fontconfig.log
drwxr-x--- 2 freerad           freerad      4096 2011-05-15 08:08 freeradius
drwxr-xr-x 2 root              root         4096 2010-10-07 11:57 fsck
drwxrwx--T 2 root              gdm          4096 2011-05-15 23:00 gdm
drwxr-xr-x 2 gnugk             root         4096 2011-04-10 16:19 gnugk
drwxr-xr-x 2 gnunet            gnunet       4096 2011-05-16 00:02 gnunetd
-rw-r--r-- 1 root              root           92 2011-03-19 08:24 gufw_log_server.txt
-rw-r--r-- 1 root              root          292 2011-03-19 08:24 gufw_log.txt
drwxr-xr-x 2               141       153    4096 2011-05-04 08:43 havp
drwxr-xr-x 3 root              root         4096 2011-01-05 17:23 iaxmodem
drwxr-xr-x 2 root              root         4096 2011-04-30 08:05 installer
drwx------ 2 root              root         4096 2009-11-05 04:40 iptraf
-rw-r--r-- 1 root              root            0 2011-05-02 07:42 jockey.log
-rw-r--r-- 1 root              root        34767 2011-05-02 07:42 jockey.log.1
-rw-r--r-- 1 root              root         5010 2010-12-23 04:54 jockey.log.2.gz
-rw-r--r-- 1 root              root          855 2010-12-18 05:38 jockey.log.3.gz
-rw-r----- 1 syslog            adm        913263 2011-05-16 11:22 kern.log
-rw-r----- 1 syslog            adm       6843851 2011-05-15 07:44 kern.log.1
-rw-r----- 1 syslog            adm        556787 2011-05-08 07:19 kern.log.2.gz
-rw-r----- 1 syslog            adm        539786 2011-05-02 07:37 kern.log.3.gz
-rw-r----- 1 syslog            adm        320870 2011-04-24 07:55 kern.log.4.gz
drwxr-xr-x 2 root              root         4096 2010-07-24 00:17 kismet
-rw-rw-r-- 1 root              utmp       292292 2011-05-04 02:22 lastlog
-rw-r----- 1 syslog            adm             0 2011-04-24 08:04 lpr.log
-rw-r----- 1 syslog            adm           144 2011-04-20 15:19 lpr.log.1
-rw-r----- 1 syslog            adm           125 2011-04-17 03:12 lpr.log.2.gz
-rw-r----- 1 syslog            adm           106 2011-04-07 17:41 lpr.log.3.gz
-rw-r----- 1 syslog            adm           106 2011-04-02 15:31 lpr.log.4.gz
-rw-r----- 1 syslog            adm             0 2011-04-03 08:07 mail.err
-rw-r----- 1 syslog            adm           416 2011-04-02 15:32 mail.err.1
-rw-r----- 1 syslog            adm           117 2011-03-31 22:08 mail.err.2.gz
-rw-r----- 1 syslog            adm             0 2011-05-02 07:42 mail.info
-rw-r----- 1 syslog            adm       1181821 2011-04-30 07:29 mail.info.1
-rw-r----- 1 syslog            adm        114135 2011-04-24 08:02 mail.info.2.gz
-rw-r----- 1 syslog            adm        150344 2011-04-18 07:20 mail.info.3.gz
-rw-r----- 1 syslog            adm        237277 2011-04-10 07:50 mail.info.4.gz
-rw-r----- 1 syslog            adm        236033 2011-05-16 11:20 mail.log
-rw-r----- 1 syslog            adm       1219075 2011-05-15 08:05 mail.log.1
-rw-r----- 1 syslog            adm        108901 2011-05-08 07:35 mail.log.2.gz
-rw-r----- 1 syslog            adm        146522 2011-05-02 07:40 mail.log.3.gz
-rw-r----- 1 syslog            adm        114135 2011-04-24 08:02 mail.log.4.gz
-rw-r----- 1 syslog            adm             0 2011-04-10 07:53 mail.warn
-rw-r----- 1 syslog            adm        124151 2011-04-03 16:10 mail.warn.1
-rw-r----- 1 syslog            adm           151 2011-04-02 15:32 mail.warn.2.gz
-rw-r----- 1 syslog            adm           117 2011-03-31 22:08 mail.warn.3.gz
-rw-r----- 1 syslog            adm             0 2011-05-02 07:42 messages
-rw-r----- 1 syslog            adm       1589866 2011-04-30 08:00 messages.1
-rw-r----- 1 syslog            adm        250252 2011-04-24 08:04 messages.2.gz
-rw-r----- 1 syslog            adm        511494 2011-04-18 07:20 messages.3.gz
-rw-r----- 1 syslog            adm        486406 2011-04-10 07:53 messages.4.gz
drwxrws--- 2 root              mixmaster    4096 2009-11-17 21:20 mixmaster
drwxr-xr-x 2 mpd               audio        4096 2011-05-08 07:36 mpd
drwxr-x--- 2 root              adm          4096 2011-05-15 08:08 mrtg
drwxr-s--- 2 mysql             adm          4096 2011-04-29 07:45 mysql
-rw-r----- 1 mysql             adm             0 2011-04-30 08:41 mysql.err
-rw-r----- 1 mysql             adm             0 2011-05-16 07:59 mysql.log
-rw-r----- 1 mysql             adm            20 2011-05-15 08:08 mysql.log.1.gz
-rw-r----- 1 mysql             adm            20 2011-05-14 08:01 mysql.log.2.gz
-rw-r----- 1 mysql             adm            20 2011-05-13 05:59 mysql.log.3.gz
-rw-r----- 1 mysql             adm            20 2011-05-12 00:58 mysql.log.4.gz
-rw-r----- 1 mysql             adm            20 2011-05-11 07:56 mysql.log.5.gz
-rw-r----- 1 mysql             adm            20 2011-05-10 00:51 mysql.log.6.gz
-rw-r----- 1 mysql             adm            20 2011-05-09 07:55 mysql.log.7.gz
drwxr-xr-x 2 nepenthes         nepenthes    4096 2011-04-02 15:36 nepenthes
-rw-r--r-- 1 nepenthes         nepenthes 8917933 2011-04-02 15:36 nepenthes.log
drwxr-xr-x 2 root              root         4096 2010-12-17 16:11 news
drwxr-s--- 2 ntop              adm          4096 2011-04-30 08:08 ntop
drwxr-xr-x 2 root              root         4096 2009-11-17 21:49 openvas
drwxr-xr-x 2 root              root         4096 2010-10-17 07:44 paco
-rw-r--r-- 1 root              root       196276 2011-05-15 23:02 pm-powersave.log
-rw-r--r-- 1 root              root       321923 2011-05-01 18:23 pm-powersave.log.1
-rw-r--r-- 1 root              root         1577 2011-03-31 22:08 pm-powersave.log.2.gz
-rw-r--r-- 1 root              root         1833 2011-03-01 05:56 pm-powersave.log.3.gz
-rw-r--r-- 1 root              root         1784 2011-02-11 14:56 pm-powersave.log.4.gz
drwxr-sr-x 2 proxy             adm          4096 2011-05-16 07:59 polipo
drwxr-x--- 2 privoxy           adm          4096 2011-05-15 08:08 privoxy
-rw-r--r-- 1 root              root            0 2010-10-07 11:58 pycentral.log
drwxr-xr-x 3 root              root         4096 2011-05-15 08:08 samba
-rw-rw-r-- 1 root              dialout         0 2011-05-14 08:13 smsclient.log
-rw-rw-r-- 1 root              dialout         0 2011-04-30 08:50 smsclient.log.0
-rw-rw-r-- 1 root              dialout        36 2011-04-23 08:15 smsclient.log.1.gz
-rw-rw-r-- 1 root              dialout        36 2011-04-16 07:58 smsclient.log.2.gz
-rw-rw-r-- 1 root              dialout        36 2011-04-09 08:20 smsclient.log.3.gz
drwxr-s--- 2 snort             adm          4096 2011-05-16 07:59 snort
drwxr-xr-x 2 speech-dispatcher root         4096 2010-08-12 02:11 speech-dispatcher
drwxr-x--- 2 proxy             proxy        4096 2011-05-16 07:59 squid
drwxr-xr-x 2 stunnel4          stunnel4     4096 2011-02-22 14:17 stunnel4
-rw-r----- 1 syslog            adm        110768 2011-05-16 11:22 syslog
-rw-r----- 1 syslog            adm       1714774 2011-05-16 07:59 syslog.1
-rw-r----- 1 syslog            adm        189945 2011-05-15 08:08 syslog.2.gz
-rw-r----- 1 syslog            adm        330612 2011-05-14 08:01 syslog.3.gz
-rw-r----- 1 syslog            adm        639426 2011-05-13 05:59 syslog.4.gz
-rw-r----- 1 syslog            adm        441205 2011-05-12 00:58 syslog.5.gz
-rw-r----- 1 syslog            adm        105047 2011-05-11 07:56 syslog.6.gz
-rw-r----- 1 syslog            adm        124293 2011-05-10 00:51 syslog.7.gz
drwxr-x--- 2 tomcat6           adm          4096 2011-05-16 08:02 tomcat6
drwxr-s--- 2 debian-tor        adm          4096 2011-04-15 08:10 tor
-rw-r--r-- 1 root              root       279384 2011-05-15 23:02 udev
-rw-r----- 1 syslog            adm             0 2011-02-27 07:40 ufw.log
-rw-r----- 1 syslog            adm          9163 2011-02-21 17:40 ufw.log.1
-rw-r----- 1 syslog            adm           750 2011-02-20 13:08 ufw.log.2.gz
drwxr-xr-x 2 root              root         4096 2010-08-26 12:51 unattended-upgrades
-rw-r----- 1 syslog            adm             0 2011-05-02 07:42 user.log
-rw-r----- 1 syslog            adm         29039 2011-04-30 07:50 user.log.1
-rw-r----- 1 syslog            adm          4680 2011-04-24 07:55 user.log.2.gz
-rw-r----- 1 syslog            adm          7950 2011-04-18 07:17 user.log.3.gz
-rw-r----- 1 syslog            adm          4933 2011-04-10 06:11 user.log.4.gz
-rw-rw-r-- 1 root              utmp       685824 2011-05-16 11:19 wtmp
-rw-rw-r-- 1 root              utmp        19635 2011-05-01 18:23 wtmp.1.gz
-rw-r--r-- 1 root              root          279 2011-04-30 08:10 wvdialconf.log
drwxr-xr-x 2 root              root         4096 2010-05-17 02:50 xapian-omega
-rw-r--r-- 1 root              root        38789 2011-05-16 11:04 Xorg.0.log
-rw-r--r-- 1 root              root        38504 2011-05-15 22:57 Xorg.0.log.old
-rw-r--r-- 1 root              root        17952 2011-04-08 04:34 Xorg.1.log
-rw-r--r-- 1 root              root        28174 2011-02-21 22:15 Xorg.1.log.old
-rw-r--r-- 1 root              root        28181 2011-02-21 22:15 Xorg.failsafe.log
-rw-r--r-- 1 root              root        28181 2011-02-21 21:41 Xorg.failsafe.log.old
lrwxrwxrwx 1 root              root           15 2011-05-16 00:53 yacy -> ../lib/yacy/LOG
-rw-r--r-- 1 root              root      1881022 2011-05-16 11:24 zfone_all.log
-rw-r--r-- 1 root              root      1816036 2011-05-15 23:02 zfone_errors.log
-rw-r--r-- 1 root              root         1037 2011-05-15 23:02 zfone_tmp.log
sophie@sophie-laptop:~$[/B][/COLOR] 

```[B]Here's the output from the third command:
[/B] 
[COLOR=Blue][B]sophie@sophie-laptop:~$ groups root
root : root
sophie@sophie-laptop:~$ [/B][/COLOR]

**and**

[COLOR=Blue][B]sophie@sophie-laptop:~$ groups sophie
sophie : sophie adm dialout fax cdrom floppy tape audio dip video plugdev fuse netdev lpadmin admin sambashare powerdev
sophie@sophie-laptop:~$

[COLOR=Black]Also see the attachments for the permissions on both of these files:[/COLOR][/B][/COLOR]

---

### Post by coljohnhannibalsmith on 2011-05-16
> **coljohnhannibalsmith said:**
> Sounds like a plan:

[B]Here's the output from the first command:
[/B] 
```
[COLOR=Blue][B]sophie@sophie-laptop:~$ tail -n3 /var/log/messages
sophie@sophie-laptop:~$ [/B][/COLOR]
```Not very impressive.  This file is also ***empty.***  But, I've noticed a file sitting right next to it named **/var/log/messages.1**; and it's populated, and appears to contain the normal system log messages.

**Actually the whole* [COLOR=Blue]log-folder[/COLOR]***** is like this... (see attachments)**

---

### Post by m_duck on 2011-05-16
That's really odd. I was always under the impression that suchandsuch.log.# where hash is some number is an old, archive copy of the log to stop the log getting too large. From the looks of it however, where # is 2, the file is also a gzip archive, implying that ***.1*** is the main log and that perhaps /var/log/messages itself is pre-upgrade remains (though I'm unsatisfied with that opinion and welcome anyone to put me straight).

At least we know now that the issue of logs not being displayed is because the log is empty and not due to any permission/ownership issue.

If the case is that the new 'normal' /var/log/messages is /var/log/messages.1, your issue can be fixed by simply tailing messages.1 in your .conkyrc as I'm sure you're aware. To be sure though, we should check that new stuff is getting appended to that file. Can you perform some task which usually gets logged in /var/log/messages and check if it's immediately appended to /var/log/messages.1? You can 'follow' the updates of these logs with the following in terminal (ctrl + c to end):
```
tail -f /var/log/messages.1
```
If it is appended immediately, I can only hazard that /var/log/messages.1 is "the new" /var/log/messages, but unfortunately can't shed anymore light than that!

If that is not the case, get back to me and I shall try and think of something else :-k

---

### Post by coljohnhannibalsmith on 2011-05-16
> **m_duck said:**
> Can you perform some task which usually gets logged in /var/log/messages and check if it's immediately appended to /var/log/messages.1? You can 'follow' the updates of these logs with the following in terminal (ctrl + c to end):
```
tail -f /var/log/messages.1
```If it is appended immediately, I can only hazard that /var/log/messages.1 is "the new" /var/log/messages, but unfortunately can't shed anymore light than that!

If that is not the case, get back to me and I shall try and think of something else :-k

Hello,

I've changed the logging code in .conkyrc to:

```
[B]${color yellow}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/[COLOR=Blue]messages.1[/COLOR] | fold -w50}[/B]

```This should allow me to watch logging events being appended in real-time from within conky.  The last logging event took place on [COLOR=Red]**April 30 07:59:21**[/COLOR]; and apparently this file has not been updated since.  [COLOR=Blue]***Maybe the logging-deamon is broken or was removed by the upgrade to Natty???***[/COLOR]  Also, I'm some what naive as to what events would normally create a log entry.  What can I try to force this; and what is the name of the daemon, so that I can look in Synaptic to see if it's even installed???

**BTW, since the upgrade, Update Manager has not been able to remember the last time I updated the system packages; and I believe this issue is directly related to what we're discussing now.  [COLOR=Blue]*Please see the following thread:*[/COLOR]**

[http://ubuntuforums.org/showthread.php?t=1752337](http://ubuntuforums.org/showthread.php?t=1752337)

Based on everything I've experienced and documented, I'm becomming more and more convinced that the logging daemon is either not present or not running.  I no longer think this is a corrupt file issue; [COLOR=Blue]***although the logging daemon may have been pointed by its programming to a non-existent file...***[/COLOR]




**Hannibal**

---

### Post by m_duck on 2011-05-16
I raise my 'really odd' of the last post to erm, 'incredibly strange'.  It certainly does seem like something has made a bit of a mess of itself. For the record, I'm moving out of the 'knowing' side of the circle to the 'guessing' side now, but they *will* be educated guesses...

/var/log/messages from what I remember contains mostly *bits* of information about *stuff*. Heh, more specifically, the [docs]("https://help.ubuntu.com/community/LinuxLogFiles#Messages Log") state:> The messages log contains informational messages from applications, and system facilities, and is available at /var/log/messages. This log is useful for examining message output from applications, and system facilities which log to the syslog / sysklog daemon at the INFO level.

From what I remember, you should get a fair few entries just from booting up and doing bits and bobs so it's very unusual that there are no logs since April 30th. You didn't do the upgrade at approximately 8am on April 30th did you? :p

Assuming the aforementioned docs are up to date, Ubuntu uses ***syslogd*** as its system logger, so I'd double check that is still installed.

Are any of the other logs getting updated? If syslogd was malfunctioning I would suspect not. Have a look at auth.log or kernel.log or a few of the others. They should certainly have entries. If they haven't been updated since April 30th, I really hope that syslogd has accidentally been removed, and this will all be fixed by reinstalling it... Otherwise I'm running short of ideas. I shall keep thinking though!

---

### Post by coljohnhannibalsmith on 2011-05-16
> **m_duck said:**
> You didn't do the upgrade at approximately 8am on April 30th did you? :p

Assuming the aforementioned docs are up to date, Ubuntu uses ***syslogd*** as its system logger, so I'd double check that is still installed.

Are any of the other logs getting updated? If syslogd was malfunctioning I would suspect not. Have a look at auth.log or kernel.log or a few of the others. They should certainly have entries. If they haven't been updated since April 30th, I really hope that syslogd has accidentally been removed, and this will all be fixed by reinstalling it... Otherwise I'm running short of ideas. I shall keep thinking though!

You guessed it...  That's exactly when I updated my system...:D

I checked Synaptic, and I don't even have  an entry, selected or otherwise called ***syslogd***.  I've got other things with similar sounding names; however the only thing that's selected is something called ***rsyslog***.

Here's what I did...  I opened Synaptic and typed [COLOR=Blue]***syslogd***[/COLOR] in the search box, and again, the only thing selected was [COLOR=Red]***rsyslog***[/COLOR].  I think this is a package that contains a logging daemon; but I don't know if it's the right one, or perhaps I need to have some other things selected as well...

Oh and BTW, ***none*** of my system logs are being updated.  That points directly to the logging daemon.  It's 'not' possible that 'all' those files could be bad...


[COLOR=Blue]***Also, I've attached a screenshot of Synaptic, so you can see which items are available.  If you can compare this with the selected items in your own system, I'd be grateful.***[/COLOR]







**Respectfully, Hannibal**

---

### Post by coljohnhannibalsmith on 2011-05-17
Well,

I got a little frustrated and did a Goggle search to see if I could find a definitive answer about which logging daemon is supposedly correct for Natty; and I couldn't find ***anything*** definitive.  But, the info I found indirectly implied that the correct logging daemon is ***syslogd*** as you have suggested; however syslogd is 'not' a package name ([COLOR=Red]**Linux needs better continuity in its package naming conventions**[/COLOR]); it appears to be part of the ***sys[COLOR=Blue]k[/COLOR]logd*** package; and the kernel logging daemon itself appears to be ***[COLOR=Blue]k[/COLOR]logd***.  I had considered swapping rsyslog and sysklogd earlier; but that required removing ***ubuntu-minimal*** which warns the user 'not' to remove it; and the package also states (sic) [COLOR=Red]**It is also used to help ensure proper [COLOR=Black]upgrades[/COLOR]****, so it is recommended that it not be removed.**[/COLOR] [COLOR=Blue]***OMG catch 22!!!***[/COLOR]

There are also two other syslog options:

[I][B]busybox-syslogd

dsyslog[/B][/I]

Both of these also require the removal of ubuntu-minimal.

Anyway, after convincing myself that I could reinstall ubuntu-minimal after the fact, I decided to go ahead and make the swap; and behold, my system log files ***are*** being updated again.  So, I recoded ***.conkyrc*** back to:

```
[COLOR=Blue]**${color yellow}LOGGING ${hr 2}$color ${execi 30 tail -n3 /var/log/[COLOR=Black]messages[/COLOR]**** | fold -w50}**[/COLOR]
```and conky 'is' tailing the messages to its window[COLOR=Blue][B][I]:
[/I]
[COLOR=Black]Here's a sample of the output:

[/COLOR][/B][/COLOR]```
[COLOR=Blue]**May 17 07:02:09**[/COLOR] sophie-laptop syslogd 1.5.0#6ubuntu1: restart.
May 17 07:11:02 sophie-laptop kernel: [37497.050573] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
May 17 07:12:32 sophie-laptop kernel: [37587.051250] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
May 17 07:12:46 sophie-laptop sudo: pam_sm_authenticate: Called 
May 17 07:12:46 sophie-laptop sudo: pam_sm_authenticate: username = [sophie] 
May 17 07:12:46 sophie-laptop sudo: pam_sm_authenticate: /home/sophie is already mounted 
May 17 07:13:02 sophie-laptop kernel: [37617.065798] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
```[COLOR=Blue][B][COLOR=Black]
[/COLOR]* God, was that a nightmare!!!*[/B][/COLOR]

***As an aside, [COLOR=Blue]rsyslog[/COLOR] is version [COLOR=Red]2.6.4-2-ubuntu4[/COLOR]; which seems to indicate that it is intended for [COLOR=Red]Linux kernels => 2.6.4[/COLOR], which are [COLOR=Blue]not[/COLOR] available in Ubuntu yet...***

I still have one problem though... Update manager still will not remeber the last update; so its log file, wherever 'it' is, is still not being updated.  Now what do I do:confused:

[COLOR=Blue][I][B]Perhaps there's some 'other' [COLOR=Black]minimal[/COLOR] package that's needed for logging the latest system update???
[/B][/I][/COLOR]
BTW, you were right bout **var/log/messages.1** being a backup for **var/log/messages**.  I think this is done for system performance reasons.  Also, I suspect the **/var/log/messages.'n'.gz** files (where ***n*** is some number 2,3,4 etc.) are archives that are created after messages.1 gets too big.
[IMG]http://everythingliasophia.files.wordpress.com/2010/05/retired-belt-buckle.jpg[/IMG]
***Me, not the thread...***





Thanks, Col John Hanibal Smith USA ret.

---

### Post by coljohnhannibalsmith on 2011-05-17
I just found this file ***var/log/[COLOR=Blue]dpkg.log[/COLOR]***, that may be relevant; and it's getting updated; but this still isn't being reflected in update-manager.

Here's some sample output:

```
[B]2011-05-17 07:18:45 trigproc bamfdaemon 0.2.90-0ubuntu3 <none>
2011-05-17 07:18:45 status half-configured bamfdaemon 0.2.90-0ubuntu3
2011-05-17 07:18:45 status installed language-pack-ca-base 1:11.04+20110421.1
2011-05-17 07:18:45 status installed bamfdaemon 0.2.90-0ubuntu3
2011-05-17 07:18:45 trigproc python-support 1.0.10ubuntu3 <none>
2011-05-17 07:18:45 status half-configured python-support 1.0.10ubuntu3
2011-05-17 07:18:55 status installed python-support 1.0.10ubuntu3[/B]
```

---

### Post by coljohnhannibalsmith on 2011-05-17
Well,

I rebooted then checked to see which log files were being updated and which were not; and I came up with the following list:

**These log files are now being updated:**

/var/log/alternatives.log
/var/log/auth.log
/var/log/boot.log
/var/log/bootstrap.log
/var/log/daemon.log
/var/log/debug
/var/log/denyhosts
/var/log/dpkg.log
/var/log/fontconfig.log
/var/log/gufw_log.txt
/var/log/kern.log
/var/log/mail.info
/var/log/mail.log
/var/log/messages
/var/log/syslog
/var/log/user.log
/var/log/zfone_all.log

**These log files are still 'not' being updated:**

/var/log/jockey.log     (and is empty)
/var/log/mail.err       (and is empty) - probably only updated when an error occurs...
/var/log/mail.warn      (and is empty) - probably only updated when an error occurs...
/var/log/mysql.err      (and is empty) - probably only updated when an error occurs...
/var/log/mysql.log      (and is empty)
/var/log/pycentral.log  (and is empty)
/var/log/smsclient.log  (and is empty)
/var/log/ufw.log        (and is empty)

**Unable to determine:**

/var/log/nepenthes.log
/var/log/pm-powersave.log
/var/log/zfone_errors.log        - probably only updated when an error occurs...
/var/log/zfone_tmp.log            - probably only updated when an error occurs...

I then tried running update-manager again; and still no luck...:(

---

### Post by coljohnhannibalsmith on 2011-05-17
Well,

I ran *update-manager* again; because I felt like I was missing something...

Then I noticed that some of the packages were failing to download...  Thinking that this 'might' be ***one*** of the causes of update-manager failing to log or reflect the latest update; I opened *software-sources* and unchecked the offending entries. I then ran update-manager again; [B][I]and it did indeed reflect the latest update!!!

[/I] *[COLOR=Blue]It appears that this problem is now solved!!![/COLOR]*[/B]

However, without taking the steps to replace **[COLOR=Black]*rsyslog*[/COLOR]** with ***sys[COLOR=Blue]k[/COLOR]logd*** none of my log files would be getting updated now; and I would still be having this problem.  Many thanks for all your generous help.:D

Also, if you have some additional thoughts about my solution, please post them here...


[COLOR=Blue]***Thanks a million, Hannibal***[/COLOR]

[IMG]http://www.techdigest.tv/money_bags-thumb.gif[/IMG]

---

### Post by coljohnhannibalsmith on 2011-05-17
I just had another thought...

[COLOR=Blue]***I remeber that the owner of the /var/log/[COLOR=Black]messages[/COLOR] file was [COLOR=Black]syslog.[/COLOR]***[/COLOR]

Perhaps I could have also solved this problem by **'chown'**-ing each individual log file to ***rsyslog*** instead.  I may have to do this eventually to maintain compatibility with the new kernels.  That way I can reinstall **ubuntu-minimal**; which may have 'some' functionality I'm not going to be able to live without...   ***It just hasn't presented yet...***

Also, how do I know for sure that  I've changed the ownership of ***all*** of the log files???  I can probably tend to it in **/var/log**; [COLOR=Blue]***but what about the rest of the system???***[/COLOR]  Apparently ***ownership*** of these files may have been the real problem after all.  And the Natty upgrade script simply didn't change them as necessary???

Does anyone know how to track down ***every*** system-log file, and ***chown*** them to ***rsyslog***, or whatever the appropriate daemon is; and then verify that it's been properly done???  Also, I'm thinking that the problem is in the daemon packages themselves; as I don't think ***any*** the the system-log-daemon packages in Synaptic change the ownership of ***any*** of the log files; as they ***must...***  I also suspect that whoever wrote the Natty upgrade script was relying on this to be done ***in the package itself...*** which is erroneous if true.

[COLOR=Blue]***Just a thought....***[/COLOR]




[B]
Hannibal[/B]

---

### Post by m_duck on 2011-05-17
I'm glad you managed to get it sorted! I'm not sure what must have happened.

I can't advise chowning the log files since they will be owned by certain users for a reason. I suspect that syslog is merely the user that whatever system logger that is running runs as - i.e. as you found out there are multiple possible system loggers to use, but be it sysklogd or some other logger, they should run as the user 'syslog', I *imagine*. I suspect the reasons that the other logs are owned by other users is that they are not updated with the rest of the system logs but by the programs that are running them directly, rather than them asking the system logger to do it - i.e. as you can see the dpkg and apt logs are owned by root, since it will be root running those programs and that is when the logs will need to be updated (similarly for clamav).

With regards to the rsyslog version number, I would be inclined to suggest that it's probably just a coincidence.

Out of interest which system logger are you running now? You changed from the standard one, yes? If that is the case it suggests to me that either the stock system logger is broken for some reason, or perhaps it has been updated (with the Natty upgrade) and the old config is incompatible or some silly issue like that, that is (was) stopping it from running.

---

### Post by coljohnhannibalsmith on 2011-05-17
> **m_duck said:**
> I suspect that syslog is merely the user that whatever system logger that is running runs as - i.e. as you found out there are multiple possible system loggers to use, but be it sysklogd or some other logger, ***they should run as the user 'syslog', I imagine.***

Out of interest which system logger are you running now? You changed from the standard one, yes? If that is the case it suggests to me that either the stock system logger is broken for some reason, or perhaps it has been updated (with the Natty upgrade) and the old config is incompatible or some silly issue like that, that is (was) stopping it from running.

I think I get it...  So whatever syslog daemon I use, its files will run under the ***"user"** syslog;*** so It's 'not' necessary to change the ownsership of these files.  Well, that makes sense; and it's great news if you're right...

I switched to the ***sysklogd "package;"*** which claims to use ***syslogd*** and this required the installation of ***klogd***.  I suspect that klogd is responsible for logging the kernel messages.

I'm clueless as to whether the package ***rsyslog*** (which was originally installed with the upgrade to natty) is broken or if it's configuration file isn't set up properly.  I did however ***completely*** remove & replace rsyslog, (prior to switching to sysklogd) which would have replaced the configuration file.  It could still be that it's not configured properly by default.  That's always a possibility.

---

