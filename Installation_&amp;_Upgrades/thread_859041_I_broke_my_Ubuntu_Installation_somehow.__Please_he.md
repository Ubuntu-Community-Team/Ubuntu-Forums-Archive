---
title: "I broke my Ubuntu Installation somehow.  Please help!!!"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by anuban on 2008-07-14
Everything was working perfect on my laptop.
Yesterday I was playing with it to install something and I ran some chmod +x command on usr/lib/ to delete one folder and now I can't seem to access configuration files.
When I try to access User Accounts, it throws this error, "You are not authorized to access the configuration". My wifi is also not working.
Not sure where is the problem.

Can someone help me please?:(

I have fair knowledge of Ubuntu, been using it for 1 year or so.

Thanks
Anurag Bansal

---

### Post by PmDematagoda on 2008-07-14
Are you sure that it was a chmod +x command you executed and not a chown command?

---

### Post by anuban on 2008-07-14
> **PmDematagoda said:**
> Are you sure that it was a chmod +x command you executed and not a chown command?
Yes I am sure...
Whatever but is there any solution or do I need to reinstall.
That's the only way.
 
Thanks

---

### Post by PmDematagoda on 2008-07-14
> **anuban said:**
> Yes I am sure...
Whatever but is there any solution or do I need to reinstall.
That's the only way.
 
Thanks

It does seem strange that adding execution permissions broke almost everything, but about fixing it, it is possible, but it involves restoring the old permissions one-by-one so you would be better off just reinstalling Ubuntu.

---

### Post by anuban on 2008-07-14
Thanks a lot.
That's what I figured.
But it is strange, such a small thing can break Ubuntu.  Sorry to experience that.
Anyways, I always love Ubuntu.

---

### Post by bushda on 2008-07-14
Wouldn't it save this guy a lot of time if he booted with a live CD, mounted his HD, navigated to the affected folder, and just restored permissions?

My /usr/lib looks like it's all owned by root.root and permissions are 644 for files and 755 for directories.

---

