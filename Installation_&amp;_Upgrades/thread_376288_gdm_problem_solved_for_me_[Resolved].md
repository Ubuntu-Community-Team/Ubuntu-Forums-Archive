---
title: "gdm problem solved for me [Resolved]"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by BMWolfgang on 2007-03-04
Hello,
a week ago I had upgraded my well running 6.06 to 6.10, online, onto Laptop AcerTM22420.
Well, the 6.06 was running fine before, now I had sorted out a few problems on 6.10, but still encountering problems with gnome and gdm.
Browse through a lot of pages, find that a lot of users seem to have similar problems, like "can not run gdmsetup",
getting error messages like 
"Failed to connect to socket, sleep 1 second and retry
  Trying failed command again. Try 2 of 5."
and other gnome / gdm login problems

Now I found on this page :
[https://launchpad.net/ubuntu/+source/gdm/+bug/66034](https://launchpad.net/ubuntu/+source/gdm/+bug/66034)

And guess what, with a simple 
# mv S13gdm S21gdm
as user root in the /etc/rc2.d/    directory,
ALL is working fine for me now. (.gdm_socket is present in the /tmp)

I understand, now the gdm is started somewhat later than other processes on the bootup.

Hope this finding might help others, please leave a short note if it did.

Greetings from Germany

Wolfgang

---

### Post by virtualXTC on 2007-03-05
Thank you much!

---

