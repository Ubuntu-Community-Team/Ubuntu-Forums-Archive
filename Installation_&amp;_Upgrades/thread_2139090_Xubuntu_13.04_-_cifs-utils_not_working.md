---
title: "Xubuntu 13.04 - cifs-utils not working"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by Alan.Brown on 2013-04-26
I have just upgraded two computers to Xubuntu 13.04.   Now the External USB drive connected to the Modem/Router cannot be mounted.   This has been working OK for months until today when I upgraded

The relevant line in **/etc/fstab** is:
> # Network USB Drive - ie the USB Flash Drive connected to the Modem
//192.168.0.1/USB                             /home/user/USB     cifs    uid=1000,gid=1000,guest,_netdev     0       0


I have tried reinstalling **cifs-utils** but that does not help.
 
In Dolphin I can access the drive by going **Network > Samba Shares > USB  Readyshare... &c.**

---

### Post by Toz on 2013-04-26
Can you mount the share manually?
```
sudo mount -t cifs -o uid=1000,gid=1000,guest,_netdev //192.168.0.1/USB /home/user/USB
```

Do you get any error messages?

---

### Post by Alan.Brown on 2013-04-26
I tried your suggestion and got the following

> mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)



This has been working OK until the upgrade.  I have the same problem on three different computers - all have been upgraded.

---

### Post by Alan.Brown on 2013-04-26
I have found a solution.    Add the option **sec=ntlm** - this works both in a manual mount and from fstab

The **fstab** entry is now -
> # Network USB Drive - ie the USB Flash Drive connected to the Modem
//192.168.0.1/USB                             /home/user/USB     cifs    sec=ntlm,uid=1000,gid=1000,guest,_netdev     0       0


I found the solution here - **[http://aptosid.com/index.php?name=PNphpBB2&file=viewtopic&t=2566](http://aptosid.com/index.php?name=PNphpBB2&file=viewtopic&t=2566)**

I have no idea why this works  :(

---

### Post by Steve R. on 2013-04-26
Thanks for the post.  Mounting my USB Drive failed with the upgrade to Ubuntu 13.04. The solution you posted worked for me too. Thanks.

---

### Post by Rabreu on 2013-04-29
That worked for me.Thanks.

---

### Post by rkuhnjr on 2013-04-29
Thanks for this, I was racking my brain for a good hour trying to understand why my cifs mounts were not mounting.
For anyone else coming across this post I was getting the following error on my cifs samba based shares.

mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)


in fst tab (added bold as mentioned):
//**.**.**.**/Backups /mnt/nas/Backups cifs **sec=ntlm,**rw,auto,guest,users

After which run mount -a 


Thanks!

---

### Post by mvidberg on 2013-05-01
I have a DLINK DNS-321 NAS unit and was having the same problem.  It's been working for years and all of a sudden after updating, it stopped.  Adding the sec=ntlm to my fstab worked for me as well.

---

### Post by merrillholt on 2013-05-03
Worked for me on Kubuntu accessing a remote disk on an Apple Airport Extreme. Thanks.

---

### Post by jamesisin on 2013-06-23
Adding sec=ntlm didn't work for me.  Here is my thread if anyone has any insight.

[http://ubuntuforums.org/showthread.php?t=2156972](http://ubuntuforums.org/showthread.php?t=2156972)

---

### Post by davidilieberman on 2013-07-04
That did the trick for me. Thanks!

---

