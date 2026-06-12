---
title: "Some questions on Karmics ..."
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Thura on 2009-09-21
I have upgraded to Karmic ...
When I boot up from grub, it show a black screen ...
But, it works fine if I remove 'vga=791' from grub entry, but only in text mode, xsplash isn't loading ... Is there any parameters I needed to pass to kernel (like 'usplash') ?

During startup it shows a lot of errors, where can I view the log for those messages ? It show this error for each service it loads

> Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, 

And it also stop at command prompt, without loading gdm ...

When I typed, 

```
sudo start gdm
sudo] password for thura: 
gdm start/running, process 4941

(thura@~) restart gdm
restart: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1000 pid=5307 comm="restart) interface="com.ubuntu.Upstart0_6.Job" member="Restart" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init))

(thura@~) stop gdm
stop: Unknown instance:
``` 

And finally I make it work by just typeing 'gdm' ;)

---

### Post by VMC on 2009-09-21
> **Thura said:**
> I have upgraded to Karmic ...
When I boot up from grub, it show a black screen ...
But, it works fine if I remove 'vga=791' from grub entry, but only in text mode, xsplash isn't loading ... .

You'll also notice grub giving you notice "vga= is depreciated" . Look up "gfxpayload" in grub manual.

---

### Post by kappa962 on 2009-09-21
Where is the grub manual?

---

### Post by VMC on 2009-09-21
> **kappa962 said:**
> Where is the grub manual?

Read about it on this [**blog**]("http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html").

---

