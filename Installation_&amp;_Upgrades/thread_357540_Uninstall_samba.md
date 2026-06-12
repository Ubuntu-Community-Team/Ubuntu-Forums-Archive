---
title: "Uninstall samba"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by ruialexbarbosa on 2007-02-09
I need to uninstall samba but I get this error. How do I remove it?

Thanks

invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba

---

### Post by ffxr on 2007-02-09
did u stop the samba service?
sudo /etc/init.d/samba stop

---

### Post by dannyboy79 on 2007-02-09
i have already helped a guy with this. something must be wrong with the way samba gets installed lately???!!!??? all you have to do to fix this is do sudo rm /etc/rc2.d/S91samba and then you can remove samba. if you're problem is that samba isn't starting at bootup it's because all your symlinks are messed up, you should have these symlinks in the following folders:
/etc/rc0.d/K19samba
/etc/rc1.d/K19samba
/etc/rc2.d/K09samba
/etc/rc2.d/S20samba
/etc/rc3.d/K09samba
/etc/rc3.d/S20samba
/etc/rc4.d/S20samba
/etc/rc5.d/S20samba
/etc/rc6.d/K19samba

to create a symlink you would use this command in a terminal.
first cd to each one of the locations that I have posted above and then do
ln -s /etc/init.d/samba Xxxsamba

as you can see from above there is NO S91samba symlink anywhere in dapper therefore there shouldn't be any S91samba symlink in Edgy or Fiesty as long as they are all still using init. good luck

where X equals the correct letter and the little x's equal the correct numbers I showed you above. good luck

---

### Post by ruialexbarbosa on 2007-02-11
Thanks guys, I managed to get it sorted and I uninstalled it.

---

### Post by dannyboy79 on 2007-02-12
please, whenever you solve something do not just simply put, "I solved it". this does not help others when they have the same issue. it's best to get in the habit for the entire forum that when you post back that explain how you solved it and not just that you solved it. thanks from the entire forum if you post HOW  you solved this.

---

