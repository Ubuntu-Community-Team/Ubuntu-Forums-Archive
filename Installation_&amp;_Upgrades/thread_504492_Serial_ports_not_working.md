---
title: "Serial ports not working"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by mandrav on 2007-07-19
In Edgy, my serial ports were working fine with minicom and cu. Now, I installed Feisty on a *new* disk (still on the *same* computer though) and none of my serial ports seem to work (2 ports, on-board).

```
mandrav@mandrav-desktop:~$ cu -l /dev/ttyS0 -s 115200
Connected.
cu: write: Input/output error

Disconnected.

```

```
mandrav@mandrav-desktop:~$ stty -F /dev/ttyS0
stty: /dev/ttyS0: Input/output error
```

```
root@mandrav-desktop:/usr/src/linux# setserial -a /dev/ttyS0
Cannot get serial info: Input/output error
root@mandrav-desktop:/usr/src/linux# setserial -a /dev/ttyS0
/dev/ttyS0, Line 0, UART: 16550A, Port: 0x03f8, IRQ: 4
        Baud_base: 115200, close_delay: 50, divisor: 0
        closing_wait: 3000
        Flags: spd_normal skip_test

```

And here's the interesting part of strace output (running "cu"):

```
fcntl64(3, F_GETFD)                     = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
access("/dev/ttyS0", R_OK|W_OK)         = 0
fcntl64(3, F_GETFL)                     = 0x802 (flags O_RDWR|O_NONBLOCK)
fcntl64(3, F_SETFL, O_RDWR)             = 0
**ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, 0xbfb75f58) = -1 EIO (Input/output error)**
access("/dev/ttyS0", R_OK|W_OK)         = 0
fstat64(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 1), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fc7000
write(1, "\7Connected.\n", 12)          = 12
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(0, SNDCTL_TMR_START or TCSETS, {B38400 -opost -isig -icanon -echo ...}) = 0
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 -opost -isig -icanon -echo ...}) = 0
pipe([4, 5])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e62b08) = 11618
close(5)                                = 0
read(0, "\r", 1)                        = 1
**write(3, "\r", 1)                       = -1 EIO (Input/output error)**
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 -opost -isig -icanon -echo ...}) = 0
ioctl(0, SNDCTL_TMR_START or TCSETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
write(2, "cu: write: Input/output error\n", 30cu: write: Input/output error
) = 30
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(0, SNDCTL_TMR_START or TCSETS, {B38400 -opost -isig -icanon -echo ...}) = 0
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 -opost -isig -icanon -echo ...}) = 0
close(4)                                = 0
kill(11618, SIGTERM)                    = 0
rt_sigaction(SIGALRM, {0x8052230, [], SA_INTERRUPT}, NULL, 8) = 0
alarm(2)                                = 0
waitpid(11618, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0) = 11618
--- SIGCHLD (Child exited) @ 0 (0) ---
rt_sigaction(SIGALRM, {SIG_IGN}, NULL, 8) = 0
alarm(0)                                = 2
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 -opost -isig -icanon -echo ...}) = 0
ioctl(0, SNDCTL_TMR_START or TCSETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
**ioctl(3, TIOCNOTTY)                     = -1 EIO (Input/output error)**
close(3)                                = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGCHLD, NULL, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
nanosleep({2, 0}, {2, 0})               = 0
unlink("/var/lock/LCK..ttyS0")          = 0
write(1, "\n", 1)                       = 1
write(1, "\7Disconnected.\n", 15)       = 15
exit_group(0)                           = ?
Process 11617 detached
```

Does anyone have any clue on what to look? I 'm confused as serial port access should be really simple...
Also note this is not a permissions issue (the user is added to the dialout group).

```
mandrav@mandrav-desktop:~$ ls -l /dev/ttyS*
crw-rw---- 1 root dialout 4, 64 2007-07-19 14:57 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2007-07-19 14:57 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2007-07-19 14:57 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2007-07-19 14:57 /dev/ttyS3
```

Oh, another interesting thing to note is this:

```
**root**@mandrav-desktop:/usr/src/linux# cu -l /dev/ttyS0 -s 115200
cu: open (/dev/ttyS0): Permission denied
cu: /dev/ttyS0: Line in use
root@mandrav-desktop:/usr/src/linux# 

```

:( :confused:

Any help would be appreciated... :-k

---

### Post by Kowalski_GT-R on 2007-07-19
> **mandrav said:**
> 

Any help would be appreciated... :-k


Same here,

I'll search for info about "minicom and cu"...

---

### Post by mandrav on 2007-07-20
Well, can anyobody confirm that serial ports work for him/her on Feisty?

---

### Post by estratos on 2007-08-03
Same problem here on Feisty.

```

dberenguer@dberenguer1:~$ sudo cu -l ttyS0 -s 19200
Password:
cu: open (/dev/ttyS0): Permission denied
cu: ttyS0: Line in use

```

I've removed brltty, but same result.

Any idea out there? I really need my serial ports.

Daniel.

---

### Post by mandrav on 2007-08-06
Still nothing on this issue.
May I ask a mod to move this to "General help"? Maybe it's the chosen sub-forum the reason for not getting any response...

---

### Post by estratos on 2007-08-07
Hi Mandrav,

I'm at the point of installing the 6.06 version as it works fine on my other computer.

Daniel.

---

### Post by estratos on 2007-08-07
Mandrav, running Ubuntu Feisty from the CD does free my serial ports so that I'm able to access them without problems.

This tells me that the standard installation adds some processes blocking the serial ports.

Daniel.

---

### Post by mandrav on 2007-08-07
> I'm at the point of installing the 6.06 version as it works fine on my other computer.

Daniel.

Yes, I still use 6.10 at work because of this issue.

> Mandrav, running Ubuntu Feisty from the CD does free my serial ports so that I'm able to access them without problems.

This tells me that the standard installation adds some processes blocking the serial ports.

Daniel.

That's interesting to know. Thanks, I will have a look...

---

### Post by StickyStyle on 2007-08-15
estratos,
Did you get anywhere with the "Line in use"?  I have the exact same issue on my new Feisty install also.

---

### Post by StickyStyle on 2007-08-15
Something I noticed when I try to use minicom to connect to the port is that it always sends me to /dev/tty8 instead of the /dev/ttyS0 like i requested.  And that I have to run minicom as root to even get in.

administrator@radar1:~$ minicom /dev/ttyS0
minicom: cannot open /dev/tty8: Permission denied

---

### Post by leonidas666 on 2007-08-31
I think i have the same problem. I'm running 7.04, and i get Input/output error when i try to access the serial port. When i use a 6.10 Live CD it works.
Is there already a bug report about this issue?

---

### Post by kirys on 2007-09-14
I've the exactly same problem with the serial port is there any workaround yet?
Thank you

---

### Post by StickyStyle on 2007-09-14
I haven't found a solution yet.  The project had to get pushed back so I am waiting on when the client can have me back at which point I will give Gusty a try - just to see.  
Out of curiosity, are any of you on a 64-bit arch?  Mine is on an AMD64 and this is the first time I have used a 64 bit machine, and the first time I have seen this problem (I have the issue also when I run the machine with a i386 kernel).

---

### Post by kirys on 2007-09-15
I have a i386 machine and the same problem :)
I think is not restricted to 64bit cpu.
I need the serial port for my wacom tablet
Cya

---

### Post by kirys on 2007-11-04
also with the kubuntu 7.10 the serial port doesn't work!!!!! please somebody help us ^_^

---

### Post by StickyStyle on 2007-11-05
> **kirys said:**
> also with the kubuntu 7.10 the serial port doesn't work!!!!! please somebody help us ^_^

For me, moving to 7.10 got my serial port to work.  Although oddly enough minicom would still not work with the serial port, but screen (and my modem) did work.

---

### Post by Toshick on 2007-11-09
I have the same problem on Gutsy. My serial port works into one way - i can send commands to modem, and my modem do, what i want, but i dont see responds from modem. I have the same trouble as people few posts up:

#ls -l /dev/ttyS*
crw------- 1 root root    4, 64 2007-11-09 02:05 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2007-11-07 21:12 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2007-11-07 21:12 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2007-11-07 21:12 /dev/ttyS3

#cu -l ttyS0 -s 19200
cu: open (/dev/ttyS0): Permission denied
cu: ttyS0: Line in use

I've tried to find solution about one week, tried different way:
removing blrtty, add getty to inittab (init.d) end etc.
Please, peole who find solution, can you share with it?

---

### Post by rl2000 on 2007-11-14
Hi

I'm very new to Ubuntu, not to linux though. 

I had this issue and found that there was a lock file for the serial port in /var/lock, sudo rm'ing it fixed everything for me.

as for tty8 being standard, run sudo minicom -s to change this behavior.

---

### Post by ank423 on 2007-12-07
I don't know if anyone else has already figured this out, but this helped me.

An strace of a cu -l ttyS0 -s 9600 as root revealed the following:

[FONT="Courier New"]setuid(10)                              = 0
...
geteuid()                               = 10
getuid()                                = 10
getegid()                               = 0
getgid()                                = 0
setregid(0, 0)                          = 0
setreuid(10, 10)                        = 0
open("/dev/ttyS0", O_RDWR|O_NONBLOCK)   = -1 EACCES (Permission denied)[/FONT]

Since the device file (/dev/ttyS0) was owned by root:dialout with mode 660 root couldn't open it as the process was now running as 10:0.

By changing the group of /dev/ttyS0 to root I can now run cu both as root and via sudo.

Hope this helps.

---

### Post by mk4umha on 2008-02-15
I have the same problem, I run minicom -s, save to ttyS0 and quit. reload minicom and it defaults to tty0 no matter what I do.
So i have to manually change the port to ttyS0 everytime i load minicom. I also can't input anything, all I see are outputs.

---

### Post by beyondtherainbow on 2008-03-08
Hi, I know this threat is from October last year .. I found a working solution .. I'm runnning Dapper long time on my FuSi (Fujitsu-Siemens) Lifebook E8010 and use (due to my job as network engineer) very often the serial port from this system. After a new fresh installation with Gutsy and two days with installation of necessary tools and first contact with an unconfigured network device, I ran into your problems ... so what I found out .. missing dialout group .. but after all I found the right help on this web-site: [http://www.debianhelp.org/node/5003](http://www.debianhelp.org/node/5003)
so what I have done: 
when I run the command "groups" under my user the membership of the dialout group was missing. Why - I don't know ...
I ran then:
 sudo delgroup dialout
I have to do because I can't find any dialout group 
then take a look with "ls -aFl /dev/ttyS*":
crw-rw---- 1 root 20 4, 64 2008-03-08 09:33 /dev/ttyS0
 sudo addgroup --gid 20 --system dialout
the 20 is the missing "dialout" group
 sudo gpasswd -a <youruser> dialout
finally:
I built the following one line rule (be careful with == vs. =):

SUBSYSTEM=="tty", KERNEL=="ttyS0", OWNER="plugdev"

and I put it in the file /etc/udev/rules.d/01-my.rules

That works just fine for me, after a reboot of my system...
I don't think the last step is necessary ...

These are my two cents.
Hope this helps!

---

