---
title: "Low disk space on filesystem root"
date: 2024-09-02
forum: Installation &amp; Upgrades
---

### Post by crashlanding on 2024-09-02
After only two or three weeks of use my Ubuntu programming computer has run out of memory.
 On August 26 I was not using the computer when it suddenly displayed this message:
 “Low Disk Space on “Filesystem root”
 The volume “Filesystem.root” has only 811.8 MB disk space remaining. You may free up some space by emptying the trash.”
 
 
 The last two times this happened to me I emptied the trash and re-booted. The two computers this happened to never would re-boot. I want to try to recover some files from the first computer. I twice re-partitioned and re-formatted the drives on the second computer, and re-installed Ubuntu. I thought I had it set up perfectly, but now it is happening again.
 Instead of emptying the trash I chose the other option “Examine”. This shows that my var folder is nearly full. And there is a new message: “Could not scan some of the folders contained in “/”. Error opening directory ‘/etc/cups/ssl’: Permission denied”.
 I use this computer to write programs for Ubuntu using RAD Studio on a Windows computer that is connected to the Ubuntu computer via a network cable. I am using Ubuntu 20.04.6 LTS because it is still the newest version of Ubuntu that is supported by RAD Studio.
 The only things I have installed on this computer are Screenshot, and the stuff to support RAD Studio. This includes PAServer, and some libraries.
 Studying Disk Usage Analyzer I found that PAServer seems to be using only 114 MB. Lib is using 4.3 GB. Share is using 871 MB. Cache is using 88 MB. SFC is using 287 MB. Local Share Shotwell is using 80 MB. Log seems to be using 1.1 TB, and yet I see only about 5 GB in it. I don’t understand what is using all this memory. I took several pictures of the Disk Usage Analyzer display in case someone wants to look at it. I also looked at the drive using Disks and took screen shots. There are two partitions. The first is the OS, it has 537 MB. 483 MB free 10% full. The second partition is 2 TB, 755 GB free, 63.1 % full.
 
 
 The first two computers came from Dell with Ubuntu installed. I partitioned, formatted and installed Ubuntu from a Flash Drive and let it use defaults, onto that second computer. The same thing has happened every time. I just looked in the trash bin and found there are six files totaling about 1.2 MB.
 
 
 I don’t understand what is causing the problem. Do I need to expand the OS partition ? Does a folder have a size limit I need to adjust ? Please tell me how to fix this problem.

---

### Post by ajgreeny on 2024-09-02
I suspect from what you say that there is something spamming a log file or files in /var/log so have a look in more detail to see what is using all that space.

---

### Post by yancek on 2024-09-02
>  There are two partitions. The first is the OS, it has 537 MB.  

No, it isn't.  There is not way you can do an even minimal install of a current Ubuntu on a 537M partition.  That could be your EFI partition.  There is also no reason you would have log files the size you indicate unless you are making changes/modifying software and getting a lot of errors. Log seems to be using 1.1 TB.  How did you get that information?

Try the following command to get information on log files and their size:  ```
ls -lh /var/log
```

---

### Post by crashlanding on 2024-09-02
I got that information either from Disks, or Disk Usage Analyzer. Here is the result of ls -lh /var/log:
&#65279;```
chris@LMTProg2:~$ ls -lh /var/log
total 1.6T
-rw-r--r--  1 root              root               0 Sep  1 00:00 alternatives.log
-rw-r--r--  1 root              root             38K Aug 12 15:21 alternatives.log.1
-rw-r-----  1 root              adm                0 Aug 11 00:00 apport.log
-rw-r-----  1 root              adm              226 Aug  9 21:53 apport.log.1
drwxr-xr-x  2 root              root            4.0K Sep  1 00:00 apt
-rw-r-----  1 syslog            adm              13K Sep  2 20:30 auth.log
-rw-r-----  1 syslog            adm              48K Sep  1 00:17 auth.log.1
-rw-r-----  1 syslog            adm             3.1K Aug 24 23:30 auth.log.2.gz
-rw-r-----  1 syslog            adm             4.6K Aug 17 23:30 auth.log.3.gz
-rw-r-----  1 syslog            adm             1.9K Aug 10 23:30 auth.log.4.gz
-rw-------  1 root              root               0 Aug 13 00:00 boot.log
-rw-------  1 root              root             11K Aug 13 00:00 boot.log.1
-rw-------  1 root              root             10K Aug 11 00:00 boot.log.2
-rw-r--r--  1 root              root            102K Mar 16  2023 bootstrap.log
-rw-rw----  1 root              utmp               0 Sep  1 00:00 btmp
-rw-rw----  1 root              utmp               0 Mar 16  2023 btmp.1
drwxr-xr-x  2 root              root            4.0K Sep  2 00:00 cups
drwxr-xr-x  2 root              root            4.0K Mar 14  2023 dist-upgrade
-rw-r--r--  1 root              adm              89K Aug 12 15:23 dmesg
-rw-r--r--  1 root              adm              87K Aug  9 21:45 dmesg.0
-rw-r--r--  1 root              root               0 Sep  1 00:00 dpkg.log
-rw-r--r--  1 root              root            1.3M Aug 12 15:21 dpkg.log.1
-rw-r--r--  1 root              root             32K Aug 12 15:21 faillog
-rw-r--r--  1 root              root             11K Aug 12 15:18 fontconfig.log
drwx--x--x  2 root              gdm             4.0K Jul 12  2021 gdm3
-rw-r--r--  1 root              root             46K Aug 12 15:23 gpu-manager.log
drwxr-xr-x  3 root              root            4.0K Mar 16  2023 hp
drwxrwxr-x  2 root              root            4.0K Aug  9 21:44 installer
drwxr-sr-x+ 3 root              systemd-journal 4.0K Aug  9 21:45 journal
-rw-r-----  1 syslog            adm              508 Sep  2 17:32 kern.log
-rw-r-----  1 syslog            adm             4.0K Sep  1 00:00 kern.log.1
-rw-r-----  1 syslog            adm             1.6K Aug 25 00:00 kern.log.2.gz
-rw-r-----  1 syslog            adm              27K Aug 18 00:00 kern.log.3.gz
-rw-r-----  1 syslog            adm              25K Aug 10 18:37 kern.log.4.gz
-rw-rw-r--  1 root              utmp            286K Aug 12 15:21 lastlog
drwxr-xr-x  2 root              root            4.0K Mar 22  2022 openvpn
drwx------  2 root              root            4.0K Mar 16  2023 private
drwx------  2 speech-dispatcher root            4.0K Jan 19  2020 speech-dispatcher
-rw-r-----  1 syslog            adm             980G Sep  2 21:10 syslog
-rw-r-----  1 syslog            adm             559G Sep  2 02:24 syslog.1
-rw-r-----  1 syslog            adm              15G Sep  1 01:10 syslog.2.gz
-rw-r-----  1 syslog            adm             7.0G Aug 31 02:26 syslog.3.gz
-rw-r-----  1 syslog            adm              15G Aug 30 01:10 syslog.4.gz
-rw-r-----  1 syslog            adm             7.1G Aug 29 02:29 syslog.5.gz
-rw-r-----  1 syslog            adm              15G Aug 28 01:08 syslog.6.gz
-rw-r-----  1 syslog            adm             6.8G Aug 27 02:34 syslog.7.gz
-rw-r--r--  1 root              root               0 Sep  1 01:10 ubuntu-advantage.log
-rw-------  1 root              root            4.8K Aug 12 15:01 ubuntu-advantage.log.1
-rw-r--r--  1 root              root               0 Sep  1 01:10 ubuntu-advantage-timer.log
-rw-r--r--  1 root              root            2.3K Aug 12 09:16 ubuntu-advantage-timer.log.1
drwxr-x---  2 root              adm             4.0K Sep  1 01:10 unattended-upgrades
-rw-rw-r--  1 root              utmp            2.7K Aug 12 15:23 wtmp
chris@LMTProg2:~$
```

---

### Post by ubfan1 on 2024-09-03
Looks like syslog.  examine it to see what's writing so much into it.  It's just text (until compressed) so cat syslog | less should work.

---

### Post by crashlanding on 2024-09-03
I tried cat syslog | less...I tried it twice.
It seems to delete everything in terminal, except (END) The scroll bar becomes very short. When I try to scroll up to see if anything is there (END) goes to the bottom of the terminal and the rest of the lines above it have only a hyphen at the beginning. There are 24 hyphens and then (END)
I lose control of terminal and have to close it. That is, I can not get a command line. When I try to close terminal it tells me there is still a process running in this terminal. Closing the terminal will kill it. After a few minutes It still doesn't seem to be doing anything so I killed it.
Should I run cat syslog | less  again and wait ? Can I open this file with a text editor ?

---

### Post by ActionParsnip on 2024-09-03
You can free space with the below commands:
```

> /var/log/syslog
> /var/log/syslog.1

```
Now you have space to work in, wait a short while and see if these files are ballooning again. Now they are a reasonable size, you can see what is spamming the file and address it

---

### Post by crashlanding on 2024-09-03
When you say something may be spamming a log file, do you mean over the internet, like a hack ? This computer was connected to the internet only while I installed Ubuntu, PAServer, and the libraries.

---

### Post by deadflowr on 2024-09-03
> When you say something may be spamming a log file, do you mean over the internet, like a hack ? 

Not necessarily.
More like there is some odd issue in the system that's causing it to post repeating lines over and over.

You don't know until you look at the logs and see.

usually you'll find one line repeating over and over
(or sometimes it's several lines in a block that keep repeating)

But once you see what it is, you can usually figure out how to stop it.

---

### Post by ActionParsnip on 2024-09-03
> **crashlanding said:**
> When you say something may be spamming a log file, do you mean over the internet, like a hack ? This computer was connected to the internet only while I installed Ubuntu, PAServer, and the libraries.

Not really. Something is writing to the log a lot. Once it's a reasonable size you read it. Not everything is necessarily a "hack".

---

### Post by crashlanding on 2024-09-03
chris@LMTProg2:~$ /var/log/syslog
bash: /var/log/syslog: Permission denied
chris@LMTProg2:~$ sudo /var/log/syslog
[sudo] password for chris: 
sudo: /var/log/syslog: command not found
chris@LMTProg2:~$ sudo /var/log/syslog
sudo: /var/log/syslog: command not found
chris@LMTProg2:~$ /var/log/syslog
bash: /var/log/syslog: Permission denied
chris@LMTProg2:~$ sudo /var/log/syslog.1
sudo: /var/log/syslog.1: command not found
chris@LMTProg2:~$ /var/log/syslog.1
bash: /var/log/syslog.1: Permission denied

---

### Post by oldfred on 2024-09-03
You have massive log files:
> -rw-r-----  1 syslog            adm             980G Sep  2 21:10 syslog
-rw-r-----  1 syslog            adm             559G Sep  2 02:24 syslog.1
-rw-r-----  1 syslog            adm              15G Sep  1 01:10 syslog.2.gz


Trying to open them may crash system as too large to just view.
You can see  last 10 entries & if not enough try 20 or 100.

 tail -n 10 /var/log/syslog

---

### Post by ActionParsnip on 2024-09-03
> **crashlanding said:**
> chris@LMTProg2:~$ /var/log/syslog
bash: /var/log/syslog: Permission denied
chris@LMTProg2:~$ sudo /var/log/syslog
[sudo] password for chris: 
sudo: /var/log/syslog: command not found
chris@LMTProg2:~$ sudo /var/log/syslog
sudo: /var/log/syslog: command not found
chris@LMTProg2:~$ /var/log/syslog
bash: /var/log/syslog: Permission denied
chris@LMTProg2:~$ sudo /var/log/syslog.1
sudo: /var/log/syslog.1: command not found
chris@LMTProg2:~$ /var/log/syslog.1
bash: /var/log/syslog.1: Permission denied

They aren't commands, they are text based log files.

If you run:
```

tail -f /var/log/syslog

```

You can watch the file as it is updated, and with what

---

### Post by deadflowr on 2024-09-03
+1 to running with tail
it'll only output the last 10 lines. So less stress on system resources.
If that's not enough you can run with -n XXX like
```
tail -n 100 /var/log/syslog
```
which will output the last 100 lines.

But 10 lines might be enough to see what's happening.

---

### Post by yancek on 2024-09-03
Probably best to examine the end of the log files as suggested.  If you are using some specific software or modifying or trying to configure some software program and getting errors you will fill up your logs quickly.  Since you are the only one who knows what the computer is being used for, you will need to decide but viewing the log files would be a good start.

---

### Post by crashlanding on 2024-09-03
chris@LMTProg2:~$ tail -n 10 /var/log/syslog
Sep  3 13:37:11 LMTProg2 org.gnome.Nautilus[26693]: >
Sep  3 13:37:11 LMTProg2 org.gnome.Nautilus[26701]: >
Sep  3 13:37:11 LMTProg2 org.gnome.Nautilus[27090]: >
Sep  3 13:37:11 LMTProg2 org.gnome.Nautilus[27083]: >
Sep  3 13:37:11 LMTProg2 org.gnome.Nautilus[26715]: >
Sep  3 13:37:11 LMTProg2 org.gnome.Nautilus[26708]: >
Sep  3 13:37:11 LMTProg2 org.gnome.Nautilus[26693]: >
Sep  3 13:37:11 LMTProg2 org.gnome.Nautilus[26701]: >
Sep  3 13:37:11 LMTProg2 org.gnome.Nautilus[27083]: >
Sep  3 13:37:11 LMchris@LMTProg2:~$ tail -n 10 /var/log/syslog.1
Sep  3 01:10:56 LMTProg2 org.gnome.Nautilus[26701]: >
Sep  3 01:10:56 LMTProg2 org.gnome.Nautilus[27090]: >
Sep  3 01:10:56 LMTProg2 org.gnome.Nautilus[26693]: >
Sep  3 01:10:56 LMTProg2 org.gnome.Nautilus[26708]: >
Sep  3 01:10:56 LMTProg2 org.gnome.Nautilus[26715]: >
Sep  3 01:10:56 LMTProg2 org.gnome.Nautilus[26701]: >
Sep  3 01:10:56 LMTProg2 org.gnome.Nautilus[27083]: >
Sep  3 01:10:56 LMTProg2 org.gnome.Nautilus[27090]: >
Sep  3 01:10:56 LMTProg2 org.gnome.Nautilus[26708]: >
Sep  3 01:10:56 LMTProg2 org.gnome.Nautilus[26693]: >
chris@LMTProg2:~$ tail -n 10 /var/log/syslog.2.gz
&#65533;E&#65533;:&#65533;V=&#65533;&#65533;&#65533;UvR&#65533;&#65533;"&#65533;&#65533;&#65533;xI&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;B&#65533;o&#65533;(&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;_C&#65533;d&#65533;a]&#65533;&#65533;&#65533;&#65533;&#65533;rY&#65533; &#65533;&#65533;-o&#65533;&#65533;&#65533;&#65533;&#65533;E&#65533;&#65533;&#65533;q&#65533;&#65533;&#65533;?&#65533;C&#65533;&#65533;'&#65533;_&#65533;&#65533;&#65533;GA9&#65533;&#65533;<m&#65533;&#16783;&#65533;
              &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1327;&#65533;y6&#65533;.&#65533;&#65533;&#65533;&#1821;&#65533;4&#65533;~&#65533;&#65533;&#65533;C&#65533;&#65533;&#65533;&#65533;)&#65533;&#65533;<{6&#65533;&#65533;_&#65533;/&#65533;5&#65533;Q&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;c÷&#65533;&&#65533;pum&#65533;L)S&#660;&#65533;LY}c)&#65533;&#65533;<&#766;6&#65533;e&#65533;&#65533;=&#65533;o&#65533;&#65533;
~&#65533;N&#1127;Ln &#65533;).&#950;&#65533;&#882;Y&#65533;&#65533;l&#65533;&#65533;&#65533;gzM&#65533;^&#65533;(~&#65533;&#1521;
_&#65533;g
&#65533;R&#65533;&#65533;o&#65533;~&#65533;4|&#65533;+K&#65533;{&#65533;&#65533;&#65533;0&#65533;o&#65533;m8;)lHV+&#65533;&#65533;&#65533;U-&#65533;&#65533;G&#65533;^&#65533;&#435;J>n&#65533;&#65533;+&#65533;i&#65533;a&#65533;
E&#65533;_Ed&#65533;h&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;S
              ]6&#65533;w&#65533;&#65533;;f&#65533;1O&#65533;&#65533;W~
&#65533;&#65533;&#65533;8&#660;}f&#927;  &#65533;&#65533;&#65533;&#65533;&#65533;Kz~&#65533;&#65533;-&#65533;&#65533;&#65533;:&#65533;&#65533;&#65533;&#65533;q5&#65533;o&#65533;)&#65533;1/&#65533;&#65533;&#65533;&#65533;v     &#65533;O8&#65533;&#65533;~&#65533;&#65533;&#65533;&#1407;&#65533;&#65533;&#65533;&#65533;&#65533;5Z&#65533;#&#65533;&#65533;&#65533;[&#65533;&#65533;&#65533;&#65533;&#65533;}&#65533;F&#65533;&#65533;&#65533;__|&#65533;f&#65533;`&#65533;&#65533;&#65533;?&#65533;m}&#65533;&#65533;ZWZ&#65533;&#65533;&#2019;&#65533;&#65533;&#65533;&#326;l&#65533;4*-&#65533;&#65533;&#65533;&#65533;&#65533;&#687;?`&#65533;Q&#65533;&#65533;&#65533;/&#65533;>&#65533;f~j
~XJs&#65533;/&#65533;<&#65533;5x&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;)&#65533;&#65533;&#65533;j&#65533;&#65533;&#65533;&#65533;=-|&#65533;&#65533;ox&#65533; S&#65533;"&#65533;{?&#65533;x&#65533;&#65533;>&#65533;v{&#34386;&#65533;&#65533;&#65533;Cx&#65533;&#65533;9&#65533;&#65533;&#2026;2&#1300;&#65533;&#65533;K&#65533;&#65533;&#65533;;0&#65533;f&#65533;|&#65533;U&#65533;&#65533;*&#65533;&#65533;
     bC&#65533;&#65533;&#65533;&#65533;%&#65533;5&#65533;,ev&#65533;2&#65533;&#65533;[~=&#65533;/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;_&#65533;Q&#65533;&#65533;*&#65533;&#65533;&#65533;/#&#65533;&#65533;&#65533;z&#65533;&#65533;&#65533;^X&#65533;&#65533;&#65533;&#65533;&#65533;/&#65533;&#65533;@&#65533;&#65533;&#65533;&#65533;&#65533;\&#65533;T&#65533;&#65533;\&#65533;&#65533;y     &{&#65533;5iÚ>&#65533;z,&#65533;*&#65533;f&#65533;&#65533;.&#65533;&#65533;&#27267;7fe&#65533;&#65533;aq&#65533;?&#65533;Z6&#65533;&#65533;,&#65533;"&#65533;lkIg&#65533;
&#65533;|&#65533;hOpj&#65533;&#65533;&#65533;&#65533;&#65533;
            2&#65533;&#65533;&#65533;)&#65533;1&#65533;_x&#65533;G/&#65533;&#65533;&#65533;&#65533;&#65533;2&#65533;&#65533;&#65533;&#65533;&#65533;c&#65533;&#65533;&#65533;~PB&#65533;&#65533;
:z&#65533;Tjv&#65533;p&#65533;&#65533;^&#65533;R&#65533;b&#65533;L&#65533;e&#680;&#65533;s&#65533;}&#65533;;D&#65533;&#65533;"^[.S&#1174;uY&#65533;,U&#65533;?Q&#65533;&#65533;"&#65533;)e&#65533;'2&#65533;&#65533;0
]&#65533;&#44968;&#65533;-&#65533;   &#65533;&#65533;&#65533;&#65533;2"&#65533;&#65533;&#65533;&#65533;z&#65533;,&#65533;?qQ&#65533;(SE&#65533;&#65533;&#65533;L)S&#65533;t&#65533;&#65533;&#65533;&#65533;L&#65533;&#65533;(&#65533;&#65533;:n&#65533;)&#65533;<&#65533;:&#65533;:&#65533;p~s;&#65533;&#65533;M&#65533;_&#65533;&#65533;K&#65533;n`&#65533;m&#65533;&#262;&#65533;&#65533;Y&#65533;&#65533;LJ1O&#65533;&#1744;&#65533;&#65533;&#65533;&#65533;&#65533;&#1358;cu&#65533;&#65533;r&#65533;~&#65533;`7S&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;;&#65533;p&#65533;`&#65533;&#65533;o&#65533;F&#65533;yK6&#65533;cy&#65533;f&#65533;&#65533;&#65533;O'PMb~&#65533;&#65533;U&#65533;&#65533;&#65533;&#65533;&#1750;'G"&#65533;:&#998;&#65533;`&#65533;&#65533;&#65533;&#65533;'|st&#65533;&#65533;#&#65533;+/&#65533;d&#65533;U&#65533;T&#65533;,&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;x&#65533;&#65533;5&#65533;W&#65533;&#65533;&#65533;&#65533;
{E&#1798;&#65533;&#65533;&#65533;&#65533;&#65533;F&#65533;&#65533;&#65533;&#65533;+}&#65533;W~&#65533;;&#65533;m&#65533;^8&#65533;)&#65533;&#65533;/m~mO[&#65533;6&#65533;&#65533;&#65533;/,&#65533;&#65533;&#65533;&#65533;J&#65533;f^~&#65533;&#65533;k&#65533;~&#65533;m>0w&#65533;&#65533;|{7g&#65533;&#65533;&#65533;f6&#65533;V&#65533;w3&#65533;&#65533;6_&#65533;&#65533;*&#65533;7&#65533;&#65533; 6&&#65533;&#65533;&#65533;!
&#65533;&#65533;!&#65533;dJ&#65533;&#65533;&#65533;WV&#65533;&#65533;|&#65533;&#65533;r&#65533;&#65533;&#65533;fo&#65533;!`)&#65533;Kx&#65533;E&#65533;78N?&#65533;&#65533;{&#65533;&#65533;g\t&#65533;&#65533;<&#65533;&#299;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;mx&#65533;1&#65533;}&#65533;U&#65533;&#65533;K&#65533;&#65533;m&#65533;&#65533;0&#65533;&#65533;_&#65533;&#65533;&#65533;&#65533;&#65533;!=+&#65533;&#65533;&#65533;&#65533;&#65533;j&#65533;&#65533;&#65533;&#65533;&#65533;a&#65533;n&#65533;l&#65533;  |&#65533;]&#494;&#65533;#1&#65533;_<&#65533;7q7&#65533;&#997;.-&#65533;&#65533;&#65533;*&#1608;&#65533;l&#65533;q[J&#65533;&#65533;P&#65533;&#65533;}&#65533;K/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0
                                                                     &#65533;WMF3EPS&#65533;6&#65533;&#1263;&#65533;~G&#65533;&#65533;_|~&#65533;_k&#65533;&#65533;:{<R&#65533;*&#65533;&#687;&#65533;&#65533;b&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;7}c_&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;IM=&#65533;z&#65533;*6&#65533;&#65533;k&#65533;&#65533;&#65533;&#65533;TS&#65533;5&#65533;?&#65533;&#355;&#65533;&#65533;9&#65533;&#65533;&#65533;&#65533;&#65533;W&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;  S&#65533;l&#65533;2E0&#65533;«=&#65533;&#65533;/_&#65533;)S\&#65533;Mp&#65533;&#65533;&#65533;&#65533;&#65533;]&#65533;&#65533;[Ç&#65533;
                                    &#65533;&#65533;&#65533;&#65533;L&#65533;~&#65533;U&#65533;&#687;&#65533;&#65533;s&#65533;%&#65533;8&#65533;&#65533;&#65533;a&#65533;&#65533;&#65533;{&#65533;&#65533;o&#65533;_&#65533;W&#65533;U~i&#65533;!&#65533;&#65533;&#65533;&#1544;&#65533;}!SFQT&#65533;o&#65533;&#65533;&#65533;&#65533;&#65533;j1&#65533;&#65533;&#65533;&#65533;&#65533;B&#65533;&#65533;&#65533;&#65533;&#65533;M&#65533;_&#65533;?|&#65533;S&#65533;&#65533;1&#65533;&#65533;!&#65533;f&#65533;&#65533;&#65533;&#65533;o&#65533;&#65533;&#65533;&#65533;&#65533;
I am not familiar with Nautilus. How do I check the last 10 lines ?

---

### Post by crashlanding on 2024-09-03
I just looked at 100 lines and it is all Nautilus. I noticed the date/time...that's about three hours ago. I have only used terminal and Text Editor, and copied text tiles to a flash.

---

### Post by ubfan1 on 2024-09-03
The tail wont work on a compressed file. try head syslog.2.gz |zcat  to look at the beginning of the file (add the lines param if you want to see more).

---

### Post by crashlanding on 2024-09-03
head: cannot open 'syslog.2.gz'  for reading: No such file or directory

grip: stdin: unexpected end of file

---

### Post by ubfan1 on 2024-09-03
Either cd to /var/log or include it in the command: head /var/log/syslog.2.gz | zcat

---

### Post by crashlanding on 2024-09-03
I cd'd and tried again.  I got very roughly 1200 empty lines followed by about 100 lines the same as before...Nautilus...There was nothing before the empty lines, like my last command.
I read about Nautilus. I didn't see much about logs. I have a couple of questions.
Are new entries appended to the end of logs ?
These logs show date, time, the program, and a number. Is the number an error number ? Otherwise, what information is being logged ?

---

### Post by TheFu on 2024-09-04
Dude, you are really new to Linux. Learn a little more about the OS.  [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php) would be helpful to at least skim, if not read.  For most administrative things like log file management, you cannot use a GUI safely.  Open a few terminals and get used to typing commands.

Compressed files can't be looked at directly with a text tool or text processing.  They need to be uncompressed, at least temporarily, before allowing other tools to do their jobs.  **gunzip -c file.gz  | less**  or use **gzcat file.gz | less** to avoid leaving uncompressed data on disk.  These methods stream the uncompressed data to stdout for use by the next program in the pipeline.  This is a common MS-DOS, MS-Windows, Unix, and Linux command technique. Nothing new here.

Limiting the size of log files isn't hard.  There's settings to do that.  There's little reason to allow log files to get over 200MB in size, much less multiple GB.  That's just crazy.  

There are 2 major types of logs.  text like syslog and journald logs which are stored much more efficiently.  They contain the same information.  syslog has been used for 40+ yrs. journald was added around 2016 when systemd became the init system on most Linuxen.  Because old people are used to syslog, it hasn't disappeared, though journald is a fantastic, efficient, logging system with all sorts of greatness. Us old people take time to move to new things.  Anyway, below are how those 2 different logging systems can be managed for size.

The settings to control logging are in /etc/systemd/journald.conf.  It is well commented, but if you need more help, there's manpage for journald.conf with more details. Some helpful commands:

```
  journalctl --disk-usage   # See log file disk use
  sudo journalctl --vacuum-size=200M    # Drop log file size to 200M, if possible.
  sudo journalctl --vacuum-time=10d     # Drop logs, over 10 days old

```

=== Finding Huge Files ===
```
  sudo find /  -type f -size +3G -exec ls -lh {} \;
  sudo find /var  -type f -size +500M -exec ls -lh {} \;
  sudo du -sh /* | sort -h
```

For syslog files, the settings are in /etc/logrotate.d/rsyslog  There are other examples in that same directory with different options.   On my system, looks like the syslog is moved weekly and 4 versions are retained with those compressed.  So, perhaps changing your setting from weekly to daily or hourly would help manage the issue ASAP with ballooning syslog files.  Also, it appears you are keeping more than 4. Is that really necessary?  Nobody is going to look through GB and GB of log data manually. NOBODY. Having it is a waste.

Ok, after you limit how large the logs can be, you need to figure out what is constantly adding to the logs and fix that problem.  Often, it is a bad program or hardware failure.

Just so you know what a "reasonable" size is for a syslog, 
```
$ ll /var/log/syslog*
-rw-r----- 1 syslog adm  6463632 Sep  4 10:22 /var/log/syslog
-rw-r----- 1 syslog adm 13463367 Sep  1 00:00 /var/log/syslog.1
-rw-r----- 1 syslog adm   651960 Aug 25 00:00 /var/log/syslog.2.gz
-rw-r----- 1 syslog adm   629197 Aug 18 00:00 /var/log/syslog.3.gz
-rw-r----- 1 syslog adm   643545 Aug 11 00:00 /var/log/syslog.4.gz
```
Two of those files aren't compressed.  .gz means **gzip** was used to compress them.  That means **gunzip** would be used to decompress them.  There are lots of different compressors. Each has their own extension and we are expected to recognize them.  Or we can use the 'file' utility to have the OS tell us the type of file.

```
$ file /var/log/syslog.2.gz
/var/log/syslog.2.gz: gzip compressed data, last modified: Sun Aug 25 04:00:01 2024, from Unix, original size modulo 2^32 13066636

```
That utility should work with almost any type of file on your system with and without extensions, since in Linux/Unix, extensions are for humans.  The computer looks at the file header to determine the type of file it is.  This header is known as a "file signature".   [https://en.wikipedia.org/wiki/List_of_file_signatures](https://en.wikipedia.org/wiki/List_of_file_signatures) using magic numbers.

---

### Post by yancek on 2024-09-04
The link below has some general information on syslog to give you a basic understanding of what it does.

[https://www.sumologic.com/syslog/](https://www.sumologic.com/syslog/)

Why don't you start by deleting the compressed older syslog files?  You can use the command below to do that.  This will still allow you to access the most recent syslog file but will delete many GB.

```
sudo rm /var/log/syslog*.gz 
```

Using the cat command will allow reading of a file but no changes/modifications.  You need to either enter the full path [cat /var/log/syslog] or change to the directory in which the file exists [cd /var/log] then do cat syslog.

Yes, the most recent logs are at the end of the file hence the suggested commands above.

---

### Post by crashlanding on 2024-09-04
I ran that command and it did free up some space.
Thank you for the information, I will read it all.
Is it safe for me to do the same to the other two folders ?
Of course I do use Files quite a bit. But why would Nautilus put all these entries into logs ?

---

### Post by yancek on 2024-09-04
>  Is it safe for me to do the same to the other two folders ?

What folders?  You don't need to delete any folders/directories just the log files.  If you delete the log files, new ones will be created when necessary.  Read the link in my last post.

> Of course I do use Files quite a bit. But why would Nautilus put all these entries into logs ?          

Files is just another name for the Nautilus file manager.  As to why, again, read the link in my last post as to the reasons there are log files.  Mostly to see what is happening when there are problems.

Your earlier post showing the contents of /var/log show 8 syslog files 1GB or larger.  That means something is seriously going wrong with your system.  Since you are the only one who know what you are using the computer for, you will have to make whatever change is necessary.  Reading through the syslog files would be a good place to start.  I don't thing I've ever see that many log files the size of the ones you have.  One possible cause would be if you are trying to configure some specific software and getting a lot of warning/error messages.

---

### Post by crashlanding on 2024-09-04
I have mentioned everything I have done with this computer since installing Ubuntu perhaps a month ago. I see there are at least 1000 new entries from Nautilus just from today. All I have done today is use files, disks and disk usage analyzer. I haven't had time to look at the smaller syslogs. When I said folders I was wondering what to call the different syslog entries. Files ? All of the huge syslog files seem to be filled by Nautilus. I haven't done any software configuring. I got PAServer working and that was weeks ago. I tried for a while to get a desktop shortcut working, but that was a week ago. I will look through the small syslogs now that you suggest it and say there is something seriously going wrong. I hadn't looked at the smaller syslogs because I thought they might be normal. The main thing I saw is that Nautilus used over a TB of space for syslogs.

---

