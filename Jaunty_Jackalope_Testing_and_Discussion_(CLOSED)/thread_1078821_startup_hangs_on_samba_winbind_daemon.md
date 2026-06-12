---
title: "startup hangs on samba winbind daemon"
date: 2009-02-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ugkbunb on 2009-02-23
I was having some issues getting an XP computer on my network to recognize my samba share and share files / printers. For some reason when I issued 

$sudo /etc/init.d/samba start

It would act like it was starting up the samba daemon but actually would immediately shut it self down.

$sudo /etc/init.d/samba stop 
complained about no process to kill.

After purge and re-installing + fiddling with my smb.conf I now somehow have broken my computer even more. Now if I try and start up with samba or winbind installed my computer hangs indefinitely trying to start up each of the respective daemons. The fix is to bootup in recovery-mode to netroot and to remove the respective packages. I have reverted back to the default smb.conf and I am still having this behavior. Any tips/suggestions/comments are welcome.

---

### Post by ugkbunb on 2009-02-24
bump - guess I am the only one? looks like a re-install is on the horizon

---

### Post by brambles on 2009-02-24
Same here

mark@snowy 11:22 AM~ $ sudo /etc/init.d/samba restart
[sudo] password for mark: 
 * Stopping Samba daemons                                                       start-stop-daemon: warning: failed to kill 3891: No such process
                                                                         [ OK ]
 * Starting Samba daemons                                                [ OK ] 
mark@snowy 11:22 AM~ $ ps -A |grep smb
mark@snowy 11:22 AM~ $ 

No smbd running just nmbd

Jaunty 64 bit

If have time I'll check for bug

---

