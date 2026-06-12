---
title: "Can't turn off the computer after upgrade to 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by Jarks on 2011-10-14
Kubuntu 11.10 on notebook HP ProBook 4525s:

Hi, 
after upgrade 11.04 -> 11.10 I can't turn the computer off. When I click on shutdown button, KDE disappears then the splash shows up and stays forever. I have to use the power off switch. What's wrong?

Thanks.

---

### Post by user333 on 2011-10-14
Can you shut down with the ```
shutdown
``` command? If not post the error message.

---

### Post by garvinrick4 on 2011-10-14
For now open a terminal and use these until this gets figured out for you.
```
sudo shutdown -h now
```
above for shutdown
```
sudo shutdown -r now
```
above for reboot

---

### Post by Jarks on 2011-10-14
Thanks, but I can't. 
I can switch from the splashscreen to the console (CTRL+ALT+F1) but I can't write anything. The keyboard doesn't work.

---

### Post by user333 on 2011-10-14
Well... can't you just use konsole or xterm?

---

### Post by Jarks on 2011-10-14
> **user333 said:**
> Well... can't you just use konsole or xterm?

Nope it's the same. But I've found the problem by hitting ESC on splashscreen. The last message there was something about umounting NFS volume. So I went to /etc/fstab, removed lines of connection to my home computer and shutting down works again. It's weird because I had no problems in 11.04.

there was this record In fstab:
```

# homecomp.local:/mnt/multimedia /mnt/homecomp-multimedia   nfs    rsize=8192,wsize=8192,timeo=14,intr,rw,users    0    0

```

---

