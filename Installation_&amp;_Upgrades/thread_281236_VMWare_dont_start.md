---
title: "VMWare dont start"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by emil.s on 2006-10-20
I don't know were i should post this, but i try here. :p 

```
root@Sandnabba: /home/emil # vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
```
I have no idea. :confused: 

I use Ubuntu Edgy, and VMWare 1.0.1

---

### Post by Nais on 2006-10-21
I'm having the same problem. I installed VMware Server 1.0.1 build-29996 on both dapper and edgy. The installs went perfectly on both. However nothing happens after I run it on edgy. The process shows up in the system monitor, I just get nothing else.

Might this have anything to do with the kernel version? On edgy I'm using 2.6.17-10-generic.


UPDATE: I did get it running by using a workaround on another thread ```

 LD_PRELOAD=/usr/lib/libdbus-1.so.3:$LD_PRELOAD vmware
```

I'm still not clear on what the problem was though.

---

### Post by emil.s on 2006-10-24
> **Nais said:**
> I'm having the same problem. I installed VMware Server 1.0.1 build-29996 on both dapper and edgy. The installs went perfectly on both. However nothing happens after I run it on edgy. The process shows up in the system monitor, I just get nothing else.

Might this have anything to do with the kernel version? On edgy I'm using 2.6.17-10-generic.


UPDATE: I did get it running by using a workaround on another thread ```

 LD_PRELOAD=/usr/lib/libdbus-1.so.3:$LD_PRELOAD vmware
```

I'm still not clear on what the problem was though.

It works! Thank you! :)
I hope a new build of VMWare will be released soon...

---

### Post by TrAvELAr on 2006-10-24
Mine works flawlessly.  You'll need to re-run vmware-config.pl.  This will rebuild the kernel modules and everything should then start just fine.  

On a side note, I had to (re)install linux-headers.

---

### Post by Rob_H on 2006-10-26
> **Nais said:**
> UPDATE: I did get it running by using a workaround on another thread ```

 LD_PRELOAD=/usr/lib/libdbus-1.so.3:$LD_PRELOAD vmware
```

I'm still not clear on what the problem was though.

Thanks! I can access Quicken again! So apparently the current version of VMWare Server is expecting an older library...?

---

### Post by abelthorne on 2006-10-27
I have the same problem since I've upgraded Dapper to Edgy a few hours ago. Reconfiguring VMWare had no effect (it was needed anyway because I changed kernel as I was using K7 with Dapper). I'll try the workaround.

Anyway, does that mean that we need a new version of VMware Server or a new version of the lib ?

---

### Post by dro0g on 2006-10-27
this worked for me, thanks!

---

### Post by Rob_H on 2006-10-27
> **abelthorne said:**
> Anyway, does that mean that we need a new version of VMware Server or a new version of the lib ?

It seems VMware is not compatible with the new GNOME/GTK libs, so they'll probably release an update. 

Looks like the workaround disables theme support. The console window looks like hell. But at least it works.

---

### Post by nbx909 on 2006-10-27
I had this problem in dapper and doing ```
sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
``` worked, i'm interested if this will work hin edgy since i want to upgrade asap.  There is already a discussion about this in the closed beta edgy discussion, i haven't read threw all of it to see if they found a fix [http://ubuntuforums.org/showthread.php?t=247350&page=1](http://ubuntuforums.org/showthread.php?t=247350&page=1)

Edit Read threw it all and it looks like [http://blog.gnu-designs.com/2006/08/07/fix-vmware-vmw_have_epoll-error-message-with-current-distributions/](http://blog.gnu-designs.com/2006/08/07/fix-vmware-vmw_have_epoll-error-message-with-current-distributions/) is the accepted fix.

---

### Post by ampop on 2006-10-27
> **Nais said:**
> I'm having the same problem. I installed VMware Server 1.0.1 build-29996 on both dapper and edgy. The installs went perfectly on both. However nothing happens after I run it on edgy. The process shows up in the system monitor, I just get nothing else.

Might this have anything to do with the kernel version? On edgy I'm using 2.6.17-10-generic.


UPDATE: I did get it running by using a workaround on another thread ```

 LD_PRELOAD=/usr/lib/libdbus-1.so.3:$LD_PRELOAD vmware
```

I'm still not clear on what the problem was though.

Thank you NAis, it solved my problem.
I did:
```
cd /usr/bin/
cp vmware runvmware
chmod 777 vmware
sudo gedit vmware
```
Delete all lines and put:
```
#!/bin/sh
LD_PRELOAD=/usr/lib/libdbus-1.so.3:$LD_PRELOAD runvmware
```
```
chmod 555 vmware
```
And it's done.

---

### Post by Meersie on 2006-10-27
Brilliant ampop !

Thanks to you and all the previous posters things are working over here :)

---

### Post by qntgeek on 2006-10-27
x

---

### Post by newpants2003 on 2006-12-11
thanx a lot! works very well.

---

### Post by cacharreo on 2006-12-11
I have the same problem, but my VmWare works perfectly:-k

---

### Post by fnjordy on 2006-12-12
Wow, just bumped into this, I go for slightly different method:
```

$ cd /usr/bin
$ sudo bash
# mv vmware vmware-real
# cat > vmware
#!/bin/sh
LD_PRELOAD=/usr/lib/libdbus-1.so exec /usr/bin/vmware-real
*((( press Ctrl+D to exit )))*
# chmod +x vmware
*((( press Ctrl+D to exit )))*

```

I have no pre-defined LD_PRELOAD and exec uses the same process instead of keeping the shell around.

---

