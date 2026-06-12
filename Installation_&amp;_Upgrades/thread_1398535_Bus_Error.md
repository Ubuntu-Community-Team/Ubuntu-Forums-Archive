---
title: "Bus Error"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by thecaligarmo on 2010-02-04
So I know that I caused this error, but I can't seem to figure out how to fix it. (This is what i get for using a wildcard!)

So I ran the code:
```

sudo apt-get autoremove openssh*

```

And halfway through an error was thrown and now I can't seem to apt-get install anything or apt-get remove anything. It also kicked me off of the graphical interface and keeps throwing bus errors. 

"Couldn't connect system to bus" and mentions the directory: "/var/run/dbus/system_bus_socket". I also now can't access the command line and hope to get access to that soon.

I'm currently using Ubuntu Server 9.10

ANY help would be tremendously helpful.

---

### Post by thecaligarmo on 2010-02-04
So I just checked the computer and this is the latest error I'm getting:

```

[2087881.224042] INFO: task rsyslogd:563 blocked for more than 120 seconds.
[2087881.228113] [2087761.224115] "echo 0> /proc/sys/kernel/hung_task_timeout_secs disables this message

```

If that helps? I tried doing ctrl+c to get out and back to the command line, and that's not working currently.


And more info:
I'm now getting the following:
```

end_request: I/O error, dev sda, sector 456655

```
It keeps showing this over and over and using ctrl+c doesn't do anything. Pressing esc also seems to do nothing. I can't get back to the command line.

ANY help would be appreciated!

---

