---
title: "after upgrading from 12.10 to 13.04 I stille have message &quot;New release...&quot;"
date: 2013-05-12
forum: Installation &amp; Upgrades
---

### Post by progreccor on 2013-05-12
after upgrading from 12.10 to 13.04 I stille have message "New release '13.04' available."
why?

> Welcome to Ubuntu 13.04 (GNU/Linux 3.8.0-19-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Sun May 12 15:07:04 MSK 2013

  System load:  0.1                Processes:           160
  Usage of /:   1.2% of 450.54GB   Users logged in:     0
  Memory usage: 8%                 IP address for eth0: ********
  Swap usage:   0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

New release '13.04' available.
Run 'do-release-upgrade' to upgrade to it.



---

### Post by matt_symes on 2013-05-12
Hi

Sounds like you motd message has become a bit confused.

Let's check. Please post the output of

```
ls -l /var/lib/ubuntu-release-upgrader/release-upgrade-available
```

```
cat /var/lib/ubuntu-release-upgrader/release-upgrade-available
```

```
cat /var/run/motd
```

Kind regards

---

### Post by progreccor on 2013-05-12
[PHP]v@ugu:~$ ls -l /var/lib/ubuntu-release-upgrader/release-upgrade-available
-rw-r--r-- 1 root root 74 &#1072;&#1087;&#1088;.  27 10:12 /var/lib/ubuntu-release-upgrader/release-upgrade-available
v@ugu:~$ cat /var/lib/ubuntu-release-upgrader/release-upgrade-available
New release '13.04' available.
Run 'do-release-upgrade' to upgrade to it.
v@ugu:~$ cat /var/run/motd
Welcome to Ubuntu 13.04 (GNU/Linux 3.8.0-19-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Sun May 12 16:44:16 MSK 2013

  System load:  0.13               Processes:           160
  Usage of /:   1.2% of 450.54GB   Users logged in:     1
  Memory usage: 10%                IP address for eth0: *.*.*.46
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/

New release '13.04' available.
Run 'do-release-upgrade' to upgrade to it.
[/PHP]

---

### Post by progreccor on 2013-05-12
what should I do?
during upgrade I think always gone right

---

### Post by ibjsb4 on 2013-05-12
I think I just turn it off using software sources, updates>release upgrade.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab)

---

### Post by progreccor on 2013-05-12
I am using ubuntu server.
And I need that new updates will be shown for me

---

### Post by matt_symes on 2013-05-12
Hi

Remove the release upgrade notification file. It will get recreated with a new time stamp.

```
sudo rm /var/lib/ubuntu-release-upgrader/release-upgrade-available
```

Then run this command to create the file /var/run/motd from the motd scripts in /etc/update-motd.d

```
sudo bash -c 'for file in /etc/update-motd.d/*; do "$file"; done > /var/run/motd'
```

Kind regards

---

### Post by progreccor on 2013-05-12
Thank you **[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1067998_10.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1067998") 				 				 					 						 	[[COLOR=#C61919][B]matt_symes**[/COLOR]]("http://ubuntuforums.org/member.php?u=1067998")
[/B]
It's really help me.

---

