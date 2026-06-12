---
title: "unable to log in after dist-update"
date: 2006-02-23
forum: Installation &amp; Upgrades
---

### Post by dedavai on 2006-02-23
After following the upgrade Wiki tutorial, I restared the computer. I saw the usual boot up screen, everything showing "OK" excpet "Starting Gnome Display Manager" which failed. At the end of the start up the system didn't go to a graphical interface. Instead I am brough up to a message

Ubuntu 5.04 "Hoary Hedgehog" hp tty1
hp logon:

(hp is the name of my machine). My old user name/password combination does not work. What's going on? What can I do now?

---

### Post by heimo on 2006-02-23
EDIT: Boot to recovery mode (hit esc at the beginning of boot process to use Grub menu) and use passwd [username] to reset your password. Then you can:

Start by reconfiguring Xorg - or sending us any exact error / warning messages you get.
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by aysiu on 2006-02-23
[QUOTE=dedavai]After following the upgrade Wiki tutorial, I restared the computer. I saw the usual boot up screen, everything showing "OK" excpet "Starting Gnome Display Manager" which failed. At the end of the start up the system didn't go to a graphical interface.[/quote] Believe it or not, this is normal. Sometimes during a dist-upgrade X gets messed up somehow. > Instead I am brough up to a message

Ubuntu 5.04 "**Hoary Hedgehog**" hp tty1
hp logon: This is *not* normal, however... unless you dist-upgraded from Warty to Hoary. Why are you still in Hoary? If you upgraded to Breezy, it should say Breezy Badger.

> 
(hp is the name of my machine). My old user name/password combination does not work. What's going on? What can I do now? This is also not normal. Even if your X is screwed up, you should still be able to log into the console with your username and password.

The only thing I can think of is to boot into recovery mode (can you do that?), which will make you the root user and type ```
adduser --ingroup admin dedavai
``` This will add you as a sudo user--don't use the same username you had before, though. You'll be prompted for a password. After that, reboot again into normal (not recovery) mode and log in as the new user you created and then ```
sudo dpkg-reconfigure xserver-xorg
```

**Edit**: Actually, heimo's solution sounds simpler.

---

### Post by heimo on 2006-02-23
Well, it depends what has happened. Something didn't go as expected during upgrade and we need more information. These commands may also help if some packages were not installed properly:
```

sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get upgrade

```

---

### Post by msinger1 on 2006-02-25
I had (more or less) the same problem.  My exact incident is here [http://ubuntuforums.org/showthread.php?t=136096&highlight=%22gnome+display+manager%22]("http://ubuntuforums.org/showthread.php?t=136096&highlight=%22gnome+display+manager%22") but after findind this thread, I'll be sure to keep my eye on it as well.  Damn, I want my Ubuntu box back.

---

### Post by msinger1 on 2006-02-25
My problem is fixed!!!  Hopefully this will work for you too.

[http://www.ubuntuforums.org/showthread.php?t=136096]("http://www.ubuntuforums.org/showthread.php?t=136096")

---

