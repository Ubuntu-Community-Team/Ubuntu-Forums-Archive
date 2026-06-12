---
title: "upgrade to 8.10 beta broke laptop"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jlh68 on 2008-10-04
When I used the "upgrade" package manager to upgrade from 8.04LTS to 8.10 beta.  I have been upgrading this way since 7.04 without any problems, until today.  Now by laptop will not boot past the black screen with white letters on it.  In other words no GNOME Window manager or X-org, just a screen with which I don't know what to do to get booted up.  I even tried going back to 8.04LTS and I had the same results.

Does anyone know what I should do next?  I do not want to do a clean install as I will loose all my files.

---

### Post by tigerstripedcat on 2008-10-04
1) If it gives you grub, try selecting a different kernel, if that's an option.

2) If it gives you grub, try selecting the "safe-mode" option.

3) If you truly can't get anything, reboot with a "live" cd, hopefully you're using a live cd for your install.  When you get in you can reset grub.  Not sure if I can remember how, but this might work:

[http://remmirath-en.blogspot.com/2007/10/linux-how-to-reset-grub-mbr.html](http://remmirath-en.blogspot.com/2007/10/linux-how-to-reset-grub-mbr.html)

4) If you can't boot with your "live" cd then something worse is going on, you'll have to get into your bios and reset to default and reset configuration settings.

After reading your post again, it seems like it might be booting up but the xserver isn't starting correctly.  If it does boot up with lots of text (I'm not sure what you mean by "white letters") like it's starting services when it's done, log in and try

$sudo /etc/init.d/gdm restart
 (or kdm if you're using kde)
Take note of any errors and then try
$ more /var/log/Xorg.0.log | grep EE
and
$ more /var/log/Xorg.0.log | grep WW
and take note of the errors and come back here

you can also try 
$ sudo dpkg-reconfigure xserver-xorg

good luck

---

### Post by Sef on 2008-10-04
Moved to Ibex forum.

---

### Post by jlh68 on 2008-10-04
$ sudo dpkg-reconfigure xserver-xorg

I tried the above command and got the following message "xserver is not installed and no info is available"

$sudo /etc/init.d/gdm restart  this returned the message "/etc/int.d/gdm: command not found"

$ more /var/log/Xorg.0.log | grep EE  trturned (WW) warning, (EE) error, (NI) not implemented, (??) unknown, (II) Loading extension MIT-SCREEN-SAVER (ee) nO DEVICES DETECTED."

$ more /var/log/Xorg.0.log | grep WW  RETURNED " -bash: syntax error near unexpected token '(WW)'."

To me it looks like the install removed the xserver.

Now I need that good luck;
Thanks

---

### Post by jlh68 on 2008-10-06
This worked:  $ sudo dpkg-reconfigure xserver-xorg  I now am able to use my laptop.

But now I have a problem with clicking any subfile in the [Places] menu, that smplayer is opened up, instead of the selected file.

I feel that this is a preferences/options setting or something like that, but I do not know where to look or how to solve this.

---

### Post by ssam on 2008-10-06
> **jlh68 said:**
> 
But now I have a problem with clicking any subfile in the [Places] menu, that smplayer is opened up, instead of the selected file.


see [http://ubuntuforums.org/showthread.php?t=935979](http://ubuntuforums.org/showthread.php?t=935979)

---

### Post by jlh68 on 2008-10-10
Just a note to all those trying Intrepid Ibex, stick with it as it gets better and better with each upgrade/update.  I had some trouble at first and it has worked out so that now my laptop is working just fine.  I am finding the many improvements as I hunt around my system.  

I am about ready to upgrade my two PC's from 8.04LTS to 8.10 beta.  Although I might wait for the 8.10 release.

---

### Post by bikeboy on 2008-10-10
Now that it's working, DO A BACKUP OF ANYTHING YOU DON'T WANT TO LOSE!. Doing this *before* the upgrade would have been better of course. Also, install with a separate /home partition so you can do clean installs while keeping your files.

---

