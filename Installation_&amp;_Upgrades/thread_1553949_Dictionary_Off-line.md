---
title: "Dictionary Off-line"
date: 2010-08-15
forum: Installation &amp; Upgrades
---

### Post by gpdas on 2010-08-15
I would like to install a good  off-line dictionary like Oxford with phonetics. Any idea !!! I am using Ubuntu 10.04.

---

### Post by lykwydchykyn on 2010-08-15
The way I do it is to install dictd server.  Then you can choose from a number of dictionary modules to install to your dictd server -- you probably want WordNet or GCIDE (dict-wn and dict-gcide packages, respectively).

Once you do that, I can use any dict client like gdict and set it to use localhost.

---

### Post by gpdas on 2010-08-16
Hi, Thanks for giving me some hints. I am new to Ubuntu. Please tell me the exact procedure/ Commands to install the off-line English to English dictionary.

---

### Post by lykwydchykyn on 2010-08-16
- Open synaptic
 - Install these packages: dictd, dict-wn, dict-gcide, gnome-utils
 - Run "gnome-dictionary"
 - Go to "edit->preferences"
 - Click "add" to add a source
 - Call it "My Dictionary" or something like that, then change the server from "dict.org" to "localhost"
 - Click "add".  Select "My Dictionary" as your default.

---

### Post by gpdas on 2010-08-25
I run gnome-dictionary from terminal. One new window opens. There I set as per the description. But it shows error ' Unable to contact localhost:2628.

---

### Post by lykwydchykyn on 2010-08-25
Can you tell me what these say:
```

ps -e |grep dict

```

```

sudo netstat -tnap |grep dict

```

---

### Post by gpdas on 2010-08-26
1052 ?        00:00:00 dictd
 1969 pts/0    00:00:00 gnome-dictionar


I ma getting these line when 
ps -e | grep dict 
is given.

---

### Post by lykwydchykyn on 2010-08-26
That means dictd is running.  The second command would tell you what port, so you can verify that your port setting is correct.

---

### Post by gpdas on 2011-01-13
Hello, in my Ubuntu 10.04 I am not able to install off-line dictionary.The  2nd command i.e 
sudo netstat -tnap}grep dict
gives no output. Pl help.

---

### Post by lykwydchykyn on 2011-01-14
What do you get from 
```

sudo apt-get install dictd

```

---

### Post by gpdas on 2011-01-14
If i give 
sudo apt-get install dictd
The following comes

dictd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by lykwydchykyn on 2011-01-17
So it's installed but not running.  That means either it's not configured to run at boot, or it's crashing.  What happens with this command:

```

sudo service dictd restart

```

Followed by this command
```

sudo grep dictd /var/log/syslog

```

---

### Post by gpdas on 2011-01-21
Pl see  the output of the two commands.

gpdas@gpdas-laptop:~$ sudo service dictd restart
[sudo] password for gpdas: 
 * Restarting dictionary server dictd                                    [ OK ] 
gpdas@gpdas-laptop:~$ sudo grep dictd /var/log/syslog
gpdas@gpdas-laptop:~$

---

### Post by gpdas on 2011-01-22
Finally I install Goldendict from Ubuntu Software center. Immediately my Off-line Dictionary started working. Thanks to the people who had taken interest in this.

---

