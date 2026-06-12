---
title: "Ubuntu install help?"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by daveman77 on 2007-03-15
I finally got Ubuntu installed. I am trying to dual boot with XP which I installed first.

My problem is that after I installed Ubuntu and restarted it asked me for my password which I provided correctly. But it gives me an "incorrect username or password" error. The first time it happened I reinstalled and chose a one-letter password figuring I typed wrong. But even with that it gives me the same "incorrect username or password" error.  :( 

Please help! I've never used Linus before and I'm so looking forward to it.

---

### Post by taurus on 2007-03-15
Did you install it using the desktop CD (LiveCD) or the alternate CD?  Remember, Linux is a case sensitive so upper case letters are not the same as lower case letters.

---

### Post by daveman77 on 2007-03-15
I used the desktop cd. I'm positive the password is correct. Its one letter. I tried it in lower case and caps lol.

---

### Post by taurus on 2007-03-15
What's your username that you created during the installing process then?

---

### Post by daveman77 on 2007-03-15
david

---

### Post by taurus on 2007-03-15
Boot into recovery mode from GRUB menu and at the prompt, change the password for david again with

```
passwd david
```
When done, reboot with

```
shutdown -r now
```
and see if you can log in with username david and the new password.

---

### Post by daveman77 on 2007-03-15
Ok I changed the password and its doing the same thing. "incorrect username or password" :(

---

### Post by taurus on 2007-03-15
Boot into recovery mode again and post the output of this command here?

```
ls -la /home
```

p.s.  Are you using Dapper or Edgy?

---

### Post by daveman77 on 2007-03-15
Well, I tried resetting the password again using a longer password and it let me login now. :)  Lets hope it keeps letting me. Thank you so much for your help!

One more thing, I just noticed theres no option for 1280X1024 resolution. Is it possible to view in that resolution? Do I need to install my nvidia drivers first or something?

---

### Post by taurus on 2007-03-15
> **daveman77 said:**
> Well, I tried resetting the password again using a longer password and it let me login now. :)  Lets hope it keeps letting me. Thank you so much for your help!

One more thing, I just noticed theres no option for 1280X1024 resolution. Is it possible to view in that resolution? Do I need to install my nvidia drivers first or something?

Yes, you need to install nVidia driver for your graphic card first before you can go to a higher resolution.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by daveman77 on 2007-03-15
Awesome thanks again mate! That guide to install nvidia drivers seems a bit too confusing to me. I'm afraid to try it.:confused:

---

### Post by taurus on 2007-03-15
Why not use envy.  All you have to do is to download the envy script and run it.  It will do everything else for you.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Guilden_NL on 2008-02-01
Post #6 worked for me as well.  But I have to say that I believe that there is a bug in Ubuntu because this happens all too often to me.

I have Ubuntu on two PCs and three laptops and I'd say it happens approximately once per month at minimum.  I have been going through a lot of pain with our son's laptop this week because he wanted me to load an instance of SUSE which went on to hose the MBR and the Grub.  I had to reinstall Ubuntu because recovery was getting uglier by the minute.  WHAM! Password problem on reinstall.  After resetting the pwd, I got it to the point where I wanted it then the NDISwrapper puked out and after losing many hours over that, reinstalled again this morning and WHAM! Same password problem.

user alex
password bird1

Pretty darned straightforward.  So, anyone aware of an Ubuntu bug, or should I report it?

---

