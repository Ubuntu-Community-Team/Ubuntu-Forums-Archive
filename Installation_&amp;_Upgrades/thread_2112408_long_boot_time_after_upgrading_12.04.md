---
title: "long boot time after upgrading 12.04"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by Yehonal on 2013-02-04
hello guys
i've just upgraded my 11.10 64bit to 12.04 64bit and now my boot time is about 2 minutes :/ ( you can see bootchart log at below of this post, in attachment )
i can boot a clean installation of 12.04 on same hardware conf. in just 15-20 seconds
How can i speed up it?

( i won't uninstall mysql/apache/php services because i need them )

thanks in advance

---

### Post by MAFoElffen on 2013-02-04
Sorry to inform you that your attached jpeg file uploaded as a tiny file that is unreadable when enlarged. I'm sure if I cannot make it out, that others that might be able to help, cannot also. I'm familiar with bootchart log, so I know there is a lot of useful info there, just cannot make out yours.

Could you please try it again or try another way?

---

### Post by Yehonal on 2013-02-04
> **MAFoElffen said:**
> Sorry to inform you that your attached jpeg file uploaded as a tiny file that is unreadable when enlarged. I'm sure if I cannot make it out, that others that might be able to help, cannot also. I'm familiar with bootchart log, so I know there is a lot of useful info there, just cannot make out yours.

Could you please try it again or try another way?

oh sorry, i've uploaded tar file now :)

---

### Post by MAFoElffen on 2013-02-04
Here's mine to compare (attached), 43 seconds.

Will compare with yours tomorrow morning. Will then see if I need to upload one of my server's bootcharts to compare.

---

### Post by MAFoElffen on 2013-02-07
Okay, so here is one of my Ubuntu Servers running 13.04(D). You can see that starting up server services (LAMP, SSH Server, SAMBA, CUPS, TomCat, etc.) adds a wait to it. Note this server is just a server, so it's not loading an XServer or a graphical desktop environment. Still, while booting up 2 RAID arrays with 20 drives. It still takes 01.11.43... Which is twice as long as my desktop, but about a minute under yours?

Do you have mounts and shares that are stalling?

---

### Post by oldfred on 2013-02-08
I have never understood boot charts, but look at log files. If you have a gui there should be Log File Viewer otherwise just look in /var/log.

 I usually look at dmesg first but there are many log files. In demesg I look for outright errors, long times with no activity so driver is having issues or repeated attempts at loading a driver and either failure or success.

---

