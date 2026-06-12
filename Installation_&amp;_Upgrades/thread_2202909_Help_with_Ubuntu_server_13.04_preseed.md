---
title: "Help with Ubuntu server 13.04 preseed"
date: 2014-01-31
forum: Installation &amp; Upgrades
---

### Post by deejannon on 2014-01-31
Hello, so I'm having a little trouble. I'm trying to use a preseed to run a script after system setup but right before the installer finishes. My preseed works all the way until running the script. The command fails with an exit code 2 error. Any ideas? Here's the command I'm using.

```
d-i preseed/late_command string cp /cdrom/install/script.sh /target/root; chroot /target chmod +x /root/script.sh; chroot /target bash /root/script.sh
```

---

### Post by isador999 on 2014-02-01
Have you logs in /var/log/syslog once Ubuntu installed  ??  
If you have no logs :  I think Ubuntu Preseed don't like you provide 2 or 3 commands.

Maybe like that..  : 
```
 d-i preseed/late_command string bash /cdrom/install/main-script.sh 
```
main-script.sh could launch more commands.

If it don't works, cause could be the _chroot_ command... 



But it's great !  I didn't know I can make that after preseed  :)

PS : I know I could to open a new post, but like you use preseed :  I've a problem to generate crypted password in my preseed file, I've tried with ```
 echo 'pass' | md5sum 
```  and with ```
 echo 'pass' | mkpasswd.pl 
```.
The crypted pass is provided with ```
 d-i   passwd/user-password-crypted 
```, but I can't to log in with my pass after install..   If you have an idea..

---

