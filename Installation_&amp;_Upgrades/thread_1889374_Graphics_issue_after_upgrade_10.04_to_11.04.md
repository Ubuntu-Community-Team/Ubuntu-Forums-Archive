---
title: "Graphics issue after upgrade 10.04 to 11.04"
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by mulanee on 2011-12-01
Hi,
I have an old workstation under xubuntu; I use it as samba and apache server.
After trying to upgrade my xubuntu from 10.04 to 11.04, it failed so I decided to keep it like this.
One day, under graphic session, I agreed to the update request; I got the message that it will be a reduced update.
I said Ok.
Update is done, but after reboot I see nothing on the screen except strange things, look at the pictures.
[http://img839.imageshack.us/img839/4286/img3095b.jpg]("http://img839.imageshack.us/img839/4286/img3095b.jpg")
[http://img69.imageshack.us/img69/6703/img3096vr.jpg]("http://img69.imageshack.us/img69/6703/img3096vr.jpg")
Impossible to do anything, I can't log locally.
It nervertheless works as server ([http://ebgy.ath.cx]("http://ebgy.ath.cx"))
I can access to the station with a client with ssh, and the version is known as 11.04
What can I do to have the usual prompt locally?
I tried to upgrade again from my client station but the system doesn't recommand to do it with ssh, So I gave up.
No CDROM reader available.
Config:
[http://ebgy.ath.cx/phpsysinfo3/index.php?disp=dynamic]("http://ebgy.ath.cx/phpsysinfo3/index.php?disp=dynamic")
Thank you.

---

### Post by raja.genupula on 2011-12-01
Boot into recovery mode and from there failsafeX mode ....reinstall the graphics drivers

---

### Post by mulanee on 2011-12-01
Maybe I was not clear.
The problem occurs before graphics session.
Normally I should arrive in console mode.

---

### Post by mulanee on 2012-01-01
In grub menu, no issue, it works.
After selection of old version/2.6.35-22-generic (recovery mode), it doesn't work, I get graphics issue so I can't read nothing on the screen.
Thank you for your next support.

---

### Post by MAFoElffen on 2012-01-01
> **mulanee said:**
> In grub menu, no issue, it works.
After selection of old version/2.6.35-22-generic (recovery mode), it doesn't work, I get graphics issue so I can't read nothing on the screen.
Thank you for your next support.
Try this... 

- Log in through ssh
```

sudo apt-get clean
sudo apt-get -f install
sudo apt-get dist-upgrade
sudo shutdown -r 1

```

I've learned the hard way- never accept doing a "Partial" upgrade.  All my servers. my desktops and test boxes... If it's offering a partial upgrade in the GUI Upgrade Manager, I go commandline and do an aptitude update, aptitude upgrade... usually without problem.

---

### Post by mulanee on 2012-01-01
I did everything, but again it doesn't work
I found a way to launch a graphic session by launching
Previous Linux version then 2.6.38-11-generic (recovery mode) then resume.
Sure it's not the best way.
I can send graphics log to help but which one?

---

### Post by mulanee on 2012-01-08
Up !!
default grub option doesn't work.
repair mode works.

---

### Post by mulanee on 2012-01-11
I don't understand why I can launch a graphic session in repair mode and not in normal mode.
I can try to reinstall graphic driver in failsafex mode, how to do it?
Thank you.

---

### Post by mulanee on 2012-01-14
I have reinstalled xorg without success

What can I do?

Thank you.

---

### Post by mulanee on 2012-01-14
[IMG]http://img839.imageshack.us/img839/4286/img3095b.jpg[/IMG]

---

### Post by mulanee on 2012-01-21
Up

---

### Post by mulanee on 2012-01-27
Up

---

### Post by mulanee on 2012-03-07
Up

---

### Post by mulanee on 2012-04-07
up

---

### Post by mulanee on 2012-04-14
Is there any guru linux here.
Even somebody else?

---

### Post by mulanee on 2012-05-19
up

---

### Post by mulanee on 2012-07-30
up

---

### Post by mulanee on 2012-10-22
Up

---

