---
title: "Changing hostname permanently"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by sefa on 2010-07-23
Hi,

I am new to Ubuntu 10.04 and so far I love it!!! I recently created a LiveUSB and I am running Ubuntu from my USB drive with preserve mode. 

I changed the /etc/hostname and /etc/hosts files with my new hostname and everytime I reboot those files are going back to original state and change the hostname back to ubuntu...

The rest of my installed applications and settings are preserved... Is there a way to permanently change the host name?

Thanks,
Sefa

---

### Post by endotherm on 2010-07-23
try
```

sudo hostname <newhostname>

```
and let us know if that works. I had been about to tell you to edit /etc/hostname and reboot, but it seems youve tried that

---

### Post by sefa on 2010-07-23
Hi,

I tried 

```

sudo hostname server1

```

after the reboot the hostname is reverted back to ubuntu... Any ideas?

Thanks,
Sefa

---

### Post by wojox on 2010-07-23
You need to edit two files with root privileges.

```
gksudo gedit /etc/hosts
```

```
gksudo gedit /etc/hostname
```

---

### Post by sefa on 2010-07-23
I did try to edit those two files with root privileges. Any ideas? Have anyone run into the same issue?

---

### Post by wojox on 2010-07-24
> **sefa said:**
> I did try to edit those two files with root privileges. Any ideas? Have anyone run into the same issue?

Edit those two files changing only the hostname and reboot.

---

### Post by doublewitt on 2010-07-31
> **wojox said:**
> You need to edit two files with root privileges.

```
gksudo gedit /etc/hosts
```

```
gksudo gedit /etc/hostname
```

This fixed it for me - **thanks**...!

---

### Post by efflandt on 2010-08-01
For a live/install iso the system boots before persistent data is mounted, so you might need to copy those /etc/hostname and /etc/hosts to the home directory of the default ubuntu user, edit how you want them, then add these lines to **.profile** of ubuntu user:

sudo cp /home/ubuntu/hostname /etc/hostname
sudo cp /home/ubuntu/hosts /etc/hosts

Note that files that begin with dot are normally hidden, but you can see them in File Browser by hitting Ctrl+H, or with **ls -a** in terminal.

---

