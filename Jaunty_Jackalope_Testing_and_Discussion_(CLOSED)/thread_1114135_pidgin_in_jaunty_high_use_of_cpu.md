---
title: "pidgin in jaunty high use of cpu"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by pumo on 2009-04-02
couple days ago came updates to jaunty, I think monday or tuesday and after that pidgin uses about 50 percent of cpu.
anybody noticed this ?

after start it goes well and my cpu (amd64 x2 3800+ 2ghz) goes 2x 1ghz but after couple minutes it jumps to full 2ghz and pidgin usess almosta 50%.

I tried to remove .purple directory, no help. disable every plugins didn't help either..

not a big problem, but cpu fan just runs noisy :-)

---

### Post by Yashiro on 2009-04-02
Seen it on Pidgin 2.5.5 on Hardy too. With NO plugins running.
It was so annoying it was un-useable. I rolled back to an older version.

It's probably a Pidgin specific bug, not Jaunty's fault per say.

---

### Post by kzip on 2009-04-02
I'm running Pidgin on Jaunty right now and no problem with CPU usage. 

(Pidigin 2.5.5 out of the repo's with OTR and Extended Preferences plugins).

---

### Post by pumo on 2009-04-03
last evening I try to solve it. and found that / partition 12gb is full! I have /, /boot, /home and swap in own partitions.

it maybe done with this? I did have to go sleep, and didn't found what caused that much space, aptitude clean /aptitude remove didn't help disk space.

---

### Post by nystire on 2009-04-03
What does df -h show you?

---

### Post by pumo on 2009-04-03
> **nystire said:**
> What does df -h show you?

I'll check after work but it was something like this about root partition

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             12G   12G  0G  100% /

---

### Post by nystire on 2009-04-03
What does "du -h /tmp" show?

---

### Post by imthemp3king on 2009-04-03
I am experiencing this same issue with 9.04 beta.  Pidgin almost immediately pegs one core and eventually becomes unresponsive and then closes on it's own without reporting a crash or error.  It's unusable for me at this point and I have installed Empathy for the time being

---

### Post by Yashiro on 2009-04-03
Exactly what I had on Ubuntu 8.04 with Pidgin 2.5.5.
The problem is not present within 2.5.2.

---

### Post by pumo on 2009-04-03
my pidgin is also 2.5.5 and df -h

```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              12G   11G  262M  98% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  108K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   84K  1.5G   1% /dev
tmpfs                 1.5G   84K  1.5G   1% /dev/shm
lrm                   1.5G  2.7M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1             183M   20M  154M  12% /boot
/dev/sda4             277G  179G   85G  68% /home

```

edit: damet, yesterday I did backup scrpit and run by sudo, and somehow it went wrong. 
it dumped to /root/.local folder some stuff 6gb, I cleaned those away.

but this pidgin problem was before my backup mistake..

---

### Post by Yashiro on 2009-04-03
Remove pidgin, pidgin-data, libpurple and libpurple-bin.
And try an older version of pidgin.

The hardy version from here [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Or even the Debian stable or testing versions from here: [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

---

### Post by pumo on 2009-04-03
I don't understand this pidgin, after yesterday there was python update and some else, but I didn't boot after upgrade.
pidgin has been up for one hour, cpu both core "normal" (in my use) 1gh.

only package I installed yesterday was sbackup and menu, and I removed both..

---

### Post by nystire on 2009-04-03
try running 'sudo apt-get purge pidgin pidgin-data' and then 'sudo apt-get install ubuntu-desktop'

The first command will also want to remove ubuntu-desktop, and when you reinstall it, it will pull in the newest pidgin files. The problem maybe with a plugin you enabled, and these 2 commands will reset everything to do with pidgin.

---

### Post by khc on 2009-04-06
> **imthemp3king said:**
> I am experiencing this same issue with 9.04 beta.  Pidgin almost immediately pegs one core and eventually becomes unresponsive and then closes on it's own without reporting a crash or error.  It's unusable for me at this point and I have installed Empathy for the time being

Feel free to file a bug with the debug log: [http://developer.pidgin.im/wiki/TipsForBugReports](http://developer.pidgin.im/wiki/TipsForBugReports)

---

### Post by pumo on 2009-04-07
couple days away from computer and now iots again 50% cpu usage pidgin.

```

top - 19:56:08 up 42 min,  3 users,  load average: 1.44, 1.11, 0.52
Tasks: 148 total,   4 running, 144 sleeping,   0 stopped,   0 zombie
Cpu(s): 28.7%us, 39.1%sy,  0.0%ni, 32.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3055796k total,  1089156k used,  1966640k free,    82012k buffers
Swap:  5855684k total,        0k used,  5855684k free,   480996k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                  
22465 pumo      20   0  536m  38m  19m S   92  1.3   5:19.18 pidgin   
```

---

### Post by ataraxia937 on 2009-04-07
For what it's worth, people are experiencing this problem over in Arch Linux as well. Definitely a Pidgin problem, and not a jaunty one.

---

### Post by cowanh00 on 2009-04-07
> **ataraxia937 said:**
> For what it's worth, people are experiencing this problem over in Arch Linux as well. Definitely a Pidgin problem, and not a jaunty one.

This is a problem with Pidgin as I have it on Intrepid with the latest Debs from getdeb.net.....

---

### Post by Yashiro on 2009-04-07
Remove 2.5.5 and use an older version. 2.5.2 is not affected.

---

### Post by pumo on 2009-04-08
ok, thanks I'll try that.

---

### Post by imthemp3king on 2009-04-10
After installing updates today that included what I think were 2 or 3 for pidgin, I have used it all day without issue.  Version 2.5.5 on Ubuntu 9.04

---

