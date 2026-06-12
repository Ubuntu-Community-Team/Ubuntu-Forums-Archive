---
title: "upgrading 9.10 to 10.04: mount /tmp as noexec error"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by Micronaut on 2010-04-15
Hello,

I was attempting to upgrade Karmic to 10.04 beta 2 using upgrade-manager -d

I received the following error message:

Cannot run the upgrade

This is usually caused by a system where  /tmp  is mounted noexec.  Please remount  /tmp  without noexec and run the upgrade again.

How do I set up /tmp to enable the upgrade process?

Thanks for any assistance

---

### Post by punjabi_tt on 2010-04-18
Hi, 

U can try this

mount -o remount exec /tmp

---

### Post by zZ0nN on 2011-10-13
Awesome! Worked for upgrade from 11.04 to 11.10 too!

---

### Post by dfarrell07 on 2011-10-13
I had the same error as the OP when upgrading from 11.04 to 11.10. I tried the fix posted, and received this error:

> sudo mount -o remount exec /temp
mount: you must specify the filesystem type

Still Googling, but does anyone have any help? I suspect others will find this thread, as it is one of the first Google results for that error message. Thanks!

Edit:

This may be helpful. When I run ls -l in /, I get:

> drwxrwxrwt  20 root root   440 2011-10-13 20:48 tmp

So it looks like it is executable to all user types.

---

### Post by dfarrell07 on 2011-10-13
I may have figured it out. In my /etc/fstab file, I had added this line to mount my /temp folder in RAM, for added speed.

> # Added by daniel, cite: [http://setlinux.blogspot.com/2011/05/install-ubuntu-1104-and-migrate.html](http://setlinux.blogspot.com/2011/05/install-ubuntu-1104-and-migrate.html)
# Should make /temp be mapped into RAM
tmpfs /tmp tmpfs nodev,nosuid,noexec,mode=1777 0 0

Notice that I had set /temp to noexec. I took that bit out (the noexec bit), and am about to see if all is now well.

Update: Removing the noexec bit from fstab solved my trouble. Upgrade to 11.10 now progressing well.

---

### Post by sco0bydo0byd0p3 on 2011-10-15
> **dfarrell07 said:**
> I may have figured it out. In my /etc/fstab file, I had added this line to mount my /temp folder in RAM, for added speed.



Notice that I had set /temp to noexec. I took that bit out (the noexec bit), and am about to see if all is now well.

Update: Removing the noexec bit from fstab solved my trouble. Upgrade to 11.10 now progressing well.
Not one to point out the obvious, but "temp" <> "tmp" - 
output of ls -l > drwxrwxrwt  20 root root   440 2011-10-13 20:48 tmp
not "temp", but tmp...
this is why your original "sudo mount -o remount exec /temp" command failed.
-sco0b.

---

### Post by isa saids on 2013-03-07
Thank you.

---

### Post by isa saids on 2013-03-07
> **punjabi_tt said:**
> Hi, 

U can try this

mount -o remount exec /tmp


[COLOR=#000000]Thank you. It works when I upgraded Ubuntu 12.10 to Ubuntu 13.04[/COLOR]

---

