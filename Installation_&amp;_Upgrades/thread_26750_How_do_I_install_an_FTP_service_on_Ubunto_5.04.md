---
title: "How do I install an FTP service on Ubunto 5.04"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by crazybill on 2005-04-13
How do I install an FTP service on Ubunto 5.0?

With OpenBSD and remove a # in front of FTP in the /etc/inetd.conf file.
However, that file does not look like it is used in Ubutu 5.0 and has no  FTP listed.

Any help would be appreciated. I have tried installing the SSH but have not had luck talking to the machine with SSH protocol either (See my post under applications) Only SAMBA has worked thus far for network transfers.

If anyone knows how to set up a Hoary Hedgehog machine as an FTP server, it would be greatly appreciated.

There is no problem on the client side with gftp. I have already used that on the machine, but I want to set this machine up as a server so that I can FTP to it from other computers on my network.

Thanks for any help out there.

---

### Post by Dr Gonzo on 2005-04-13
No problem. :)

```
sudo apt-get install vsftpd
```

This is the Very Secure FTP Daemon.  It automatically creates the ftp root under /home/ftp, which is not initially writable.  If you don't want anybody to write to your server, you should be good to go.  If you want to have anonymous ftp users write to your server, you need to add a writable directory as a subdir of /home/ftp and change a few things in /etc/vsftpd.conf -- you might also check that file for any other options you want.

Once you're done configuring the server, don't forget to ```
/etc/init.d/vsftpd restart
```

Enjoy!

---

### Post by az on 2005-04-13
sudo apt-cache search ftp |grep server


Or just use synaptic and search for ftp....

---

### Post by crazybill on 2005-04-13
Dr. Gonzo,

You're the man!   Your instructions were impeccable.  That vsftpd daemon is outstanding!!!! It set up easily and quickly. It was a breeze to configure, it works great, and it seems very secure. Many, many thanks.

---

### Post by Dr Gonzo on 2005-04-13
Yep.  It's the best there is.  I'm pretty sure kernel.org uses it exclusively.

---

### Post by crazybill on 2005-04-13
Thanks, again, Dr. Gonzo.

Anyone else that might be reading this post:  I confirm that  vsftpd is  a superior FTP daemon.  See Dr. Gonzo's instructions further up this post.

---

### Post by neutron on 2005-04-14
Crazybill, if I've understand it correctly a default hoary installation has all the ports closed. Did you modified any other file (open ports, etc.), or did you only modify the vsftp.conf file?

---

### Post by ubuntu_demon on 2005-04-14
[QUOTE=neutron]Crazybill, if I've understand it correctly a default hoary installation has all the ports closed. Did you modified any other file (open ports, etc.), or did you only modify the vsftp.conf file?[/QUOTE]
 When a service/deamon like an ftp server listens on a port that port gets opened automaticaly.. That's why I recommend a firewall if you are paranoid or if you have a server that gets regular visits. (firestarter is nice an easy). A firewall isn't installed by default because it doesn't increase security much when it's just for a desktop machine.

---

### Post by neutron on 2005-04-14
Demon, thnx for your quick answer!

---

### Post by crazybill on 2005-04-14
I only modified the /etc/vsftpd.conf file.  When the FTPd daemon is running, the pot is automatically openned. This version of FTP is not wide open, so for an FTP server, it is great. Also, I am using the machine on a private network.

Crazy Bill

---

