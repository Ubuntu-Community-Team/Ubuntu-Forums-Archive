---
title: "mldonkey edgy doesn't start at boot time"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by samy-delux on 2006-10-30
Hey guys,

I installed mldonkey-server on my server machine and it works good.
The only problem I have is that I have to start it manually every time i boot the system. I configured it for startup at boot time, and the link in rc2.d exists, but mldonkey doesn't start.
I see 4 lines by mldonkey in the syslog but that's it. No error or anything.
Wenn I start mldonkey manually by using the init.d script it works like a charm and the first 4 lines in the syslog are the same, there are just more lines by mldonkey...

Is this a general bug? How can i solve this?

Thanks for your help!

so long,
Samy

---

### Post by samy-delux on 2006-11-01
Hey,

I tried to start MlDonkey with a second script that has a "sleep 300" in it, so it would start MlDonkey 5 minutes after boot time. But that doesn't work either. The script gets executed, but MlDonkey doesn't start.
There is also no error in syslog.
Here are the 3 lines that get written to syslog on startup:
> Nov  1 15:45:32 Server mldonkey_server: Set niceness of the process: 0
Nov  1 15:45:32 Server mldonkey_server: Set uid/gid of the process (105, 1001)
Nov  1 15:45:32 Server mldonkey_server: Set umask of the process: 18


But manual start works fine.
Any ideas??

so long,
Samy

---

### Post by roadboy on 2006-11-02
I have the same problem. I did an update for rc.d scripts. First deleted the current scripts with update-rc.d mldonkey-server remove and then created new rc.d scripts with update.rc-d mldonkey-server defaults but nothing changed :(

---

### Post by chantra on 2006-11-02
This bug has been reported on [launchpad]("https://launchpad.net/distros/ubuntu/+source/mldonkey/+bug/66023").
I've supplied a work arround.
Get the patch, cd /etc/init.d
sudo patch -p0 < /path/to/mldonkey.patch

Hope this helps

---

### Post by roadboy on 2006-11-03
> **chantra said:**
> This bug has been reported on [launchpad]("https://launchpad.net/distros/ubuntu/+source/mldonkey/+bug/66023").
I've supplied a work arround.
Get the patch, cd /etc/init.d
sudo patch -p0 < /path/to/mldonkey.patch

Hope this helps
It worked! Thanks a lot :)

---

### Post by chantra on 2006-11-04
A pleasure ;)

---

### Post by samy-delux on 2006-11-05
Thanks, works for me too...

---

### Post by oskarloko on 2006-11-05
A minor fault is mldonkey shows this message when it starts.

> 
DNS resolution does not work


I've reported it as 
Bug #70466
on launchpad.

[https://launchpad.net/distros/ubuntu/+source/mldonkey/+bug/70466](https://launchpad.net/distros/ubuntu/+source/mldonkey/+bug/70466)

But mldonkey works really WELL !! ;) 

Just see SANCHO gui on: [http://sancho-gui.sourceforge.net/](http://sancho-gui.sourceforge.net/)

(and allow ports 17440 17444 )

---

### Post by chantra on 2006-11-05
yep, the bug about the dns resolution is going to be solved when mldonkey will have been sync-ed from debian.
anyway, that dns thing is just a warning and does not affect the usuability of mldonkey, therfore there is no need to bother :)

---

