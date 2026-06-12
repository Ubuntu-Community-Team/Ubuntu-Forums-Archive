---
title: "Fork Bomb"
date: 2023-07-24
forum: Installation &amp; Upgrades
---

### Post by visu12 on 2023-07-24
[IMG]C:\Users\bjpj6821\Desktop\01-how-to-crash-your-linux-system-with-fork-bomb.png[/IMG]

Fork bomb keeps oncoming although we have made ulimit as unlimited.

---

### Post by ActionParsnip on 2023-07-24
We can't see that image. That top line only works for people sat at your PC. It doesn't work over the internet.

Use a service like photobucket or even facebook to hold the image online then give us the URL of the image. We can then see what you want us to see

---

### Post by Holger_Gehrke on 2023-07-24
A fork bomb is basically a recursion without a stop condition. To stop fork bombs from taking all resources on the system, you need to limit the allowed depth of recursions. 'ulimit' doesn't have a setting specifically for this, although the maximum stack size ('-s') might do some good. There is a variable FUNCNEST which can be set to the maximum acceptable calling depth. This does not just limit recursions it limits all functions calling functions, so you should not set this limit too low.

Holger

---

### Post by QIII on 2023-07-24
Rebooting should stop a fork bomb.  But if it starts running as a result of compromise, things may become difficult.

You certainly don't want the maximum number of processes to be unlimited.  The fork bomb will just fill them up.

Is this a personal machine?  A work machine?

Admins will sometimes use a fork bomb in pen testing.

---

### Post by visu12 on 2023-07-25
Rebooting is the only option to stop this [IMG]C:\Users\bjpj6821\Desktop\Untitled.jpg[/IMG]. Its a recording server in night time when nobody monitors the server at that time we loose valuable recording due to this.

---

### Post by visu12 on 2023-07-25
kindly guide how to go with [COLOR=#000000]maximum stack size [/COLOR]

---

### Post by Holger_Gehrke on 2023-07-25
That's probably not a fork bomb. The error message says something about a resource not being available. Looks more like it's trying to restart something after it crashed before the clean-up was completely done. Posting the script that produces this error might give us enough insight into what's going on to attempt a solution.

Holger

---

### Post by Rubi1200 on 2023-07-25
I agree with Holger that seeing what script/s are being run can help us with solutions. But, I also have a question: you say this is a recording server but it appears to have a GUI; why is that?

From a security standpoint, this is not considered to be good practice.

---

### Post by visu12 on 2023-07-25
Its a normal ubuntu server & some java application running on it & nothing running with script . Its a 24*7 environment as it runs suddenly while in operation we encounter this issue.

---

### Post by Holger_Gehrke on 2023-07-25
I may not know all the Java applications around, but almost all of the non-trivial ones I've seen were started by a script which sets all the options for the VM and performed various house-keeping tasks before actually starting the application. You seem to underestimate how deeply scripting - and especially shell scripting - is embedded in the Linux and Unix way of doing things. For example there's more than 300 shell scripts (counted by doing 'for i in /usr/bin/*; do file $i|grep shell;done|wc -l') out of less than 2800 files in /usr/bin on my machine.

Holger

---

### Post by visu12 on 2023-07-25
Kindly guide what needs to be done or what more info you need to share you.

---

### Post by Doug S on 2023-07-26
There are many people here willing to help, however you seem reluctant to supply information as to what your system is doing. It is not clear what resource is being exhausted causing the "bash fork: retry: Resource temporarily unavailable" message.

Have a look at, and perhaps monitor, "/sys/fs/cgroup/pids/user.slice/pids.current" watching for growth before the event. (Assuming the limit is number of processes, which might not be true.)

Example:

```
$ cat pids-mon
#! /bin/dash
#
# pids_mon Smythies 2023.07.26
#       Monitor the number of user processes running forever.
#       Adjust the sleep time per your requirements.
#

while [ 1 ];
do
   cat /sys/fs/cgroup/pids/user.slice/pids.current
   sleep 2
done
```
And it running while I spin out processes elsewhere:

```
$ ./pids-mon
10
10
10
10
2556
13237
23868
34427
44967
55492
66085
76694
83940
83940
83940
83940
83940
83940
^C
``` And on the other terminal window:

```
doug@s19:~$ ~/c/waiter 100000 100 60 2 999999 0 > /dev/null
fork: Resource temporarily unavailable
doug@s19:~$ killall waiter
```So I hit a limit at around 83940 threads.
I am user 1000, and am hitting its limit:
```
$ cat /sys/fs/cgroup/pids/user.slice/user-1000.slice/pids.max
83941
``` I could raise that limit and go further. See a post I did [over on ask]("https://askubuntu.com/questions/845380/bash-fork-retry-resource-temporarily-unavailable/883677#883677") for more details.

EDIT: In your case you might be hitting other limits first, which I forgot I have increased for my system. Have a look for processes and signal limits also:

```
doug@s19:~/freq-scalers/k515/pid-per-second$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
[COLOR="#FF0000"]pending signals                 (-i) 400000[/COLOR]
max locked memory       (kbytes, -l) 65536
max memory size         (kbytes, -m) unlimited
open files                      (-n) 131072
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
[COLOR="#FF0000"]max user processes              (-u) 400000[/COLOR]
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
```

---

### Post by visu12 on 2023-07-30
Is there any permanent solution for this apart from reboot

---

