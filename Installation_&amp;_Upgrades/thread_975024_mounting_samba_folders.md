---
title: "mounting samba folders"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by chris_tikva on 2008-11-08
Hi,

I have 3 machines in my setup, one running ubuntu, one running xp and one running vista. 

With the file browser in ubuntu I can browse the shared folder on xp with no problem but it won't find the shared folder on vista even though the xp machine can see it with no problem. It finds the vista machine but the "windows shares" is empty. Is there something I've missed?

Secondly I've been trying to use smbmount to mount the windows folders to a convenient place by typing:

sudo smbmount //neon-win/shareddocd /home/chris/neon

but get "could not find target server. TCP name neon_win/shareddocs not found. No IP address specified and host name not found.

Nevertheless the file browser finds it with no problem. The IP address comes from DCHP and the host name appears in the router list.

What am I doing wrong?

Thanks,

Chris

---

### Post by FrostyFlames on 2008-11-08
Using the name of the machine can be problematic some times, I personally use the IP of the machine with the shares on it.
```
sudo mount -t cifs -o user=<USERNAME_FOR_SHARE>,password=<PASSWORD_FOR_SHARE> //<IP_of_share_host>/<shared_storage_name> /<mount_point_for_share>
```
This assumes you have some kind of login needed to access the shares. If you don't, remove the "-o user=...,password=..." part. To remove the mount you can just use:
```
sudo umount /<mount_point_for_share>
```

---

### Post by chris_tikva on 2008-11-08
Thanks, I tried that and it worked.

The problem is that because the router assigns the IP address each time I switch on, it's a pain to have to do an "ipconfig" on the target machine before I mount the share. Is there a way to make using the computer name less problematic? After all, the file browser seems to be able to find it with no problem.

Chris

---

### Post by minkey32 on 2009-03-19
You could try to set up your router to give the computers a static IP when they connect.  the router will have a dynamic one from your ISP but your computer connected to the router can be static.

---

