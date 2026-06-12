---
title: "update failure on .ICEauthority &amp; separate /home"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by shy_guest on 2010-03-26
I created a separate /home partition after installing Karmic on a new computer using this HowTo : 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

 I copied all the files from /home/user using

**find . -depth -print0 | sudo cpio --null --sparse -pvd /new/**

On booting after the change, the new /home is correctly on a separate partition **BUT** during boot I get a message :

 Could not *update ICEauthority* file /home/user/.*ICEauthority*

I checked and the **ownership and permissions** for /home/user/.*ICEauthority are **correct**.* The suggested remedy of deleting the file & waiting for it to be recreated doesn't work either.

But when I compare other hidden files in the new /home/user directory, quite a few now have their ownership changed to root.

& I am unable to connect to my external monitor because of a permission problem (probably connected).

Any ideas or suggestions ?

---

### Post by viralmeme on 2010-03-26
> **shy_guest said:**
> when I compare other hidden files in the new /home/user directory, quite a few now have their ownership changed to root.

Boot from the Ubuntu Cd and try changing ownership and file permissions.

$chown -R user:group files
$chmod -R +rwx files

---

### Post by dbloom on 2010-04-21
i just ran a clean install of 9.10 with separate /home partition, copied over my old files, and now have the exact same issue (w/.ICEauthority, etc).  

were you able to resolve this?  was it simply a permissions issue?

thanks.

---

### Post by shy_guest on 2010-05-02
This is not a solution - just the way it should be done.

I reinstalled rather than track down & change any files that didn't have the right settings/owner.

In the reinstall, I chose to partition manually & set the mount point /home on a separate partition from the mount point /.

Everything seems to work as it should.

---

