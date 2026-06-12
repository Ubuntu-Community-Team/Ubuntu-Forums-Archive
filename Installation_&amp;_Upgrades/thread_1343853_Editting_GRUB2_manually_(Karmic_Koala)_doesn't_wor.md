---
title: "Editting GRUB2 manually (Karmic Koala) doesn't work"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by Cavsfan on 2009-12-02
Thought I might mention this: 
I tried to edit the GRUB2 file manually per the instructions at
_[COLOR=MediumTurquoise][http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)[/COLOR]_
and I set the timeout to 30 seconds from the default 10 (since I am 
dual booting windows 7 64 bit and Karmic Koala 64 bit)
Everything seemed to go fine, but when I entered "sudo update-grub2"
the timeout changed back to 10 seconds. :confused:

I installed startup manager via this command:
"sudo apt-get install startupmanager" and it worked. I changed the
timeout to 30 seconds and even entered  "sudo update-grub2" afterwards, 
re-booted and it stayed at 30 seconds.

So, I just wanted to mention that manually updating the GRUB2 will not stay 
how you changed it. It will revert back to I guess it's default settings when
update-grub2 is entered.

I guess that was the intention; the grub boot loader cannot be edited manually.

---

### Post by darkod on 2009-12-02
I have a dual boot of the same systems. I changed it editing the /etc/default/grub and it worked fine.
Are you sure you changed it in the proper way? Not in grub.cfg right?
Because then it would be normal that sudo update-grub is putting it back. :)

---

### Post by phillw on 2009-12-02
> **darkod said:**
> I have a dual boot of the same systems. I changed it editing the /etc/default/grub and it worked fine.
Are you sure you changed it in the proper way? Not in grub.cfg right?
Because then it would be normal that sudo update-grub is putting it back. :)

+1 darkod - looks like they edited grub.cfg :-\

Phill.

---

### Post by Cavsfan on 2009-12-02
> **phillw said:**
> +1 darkod - looks like they edited grub.cfg :-\

Phill.

Yep, You are correct! DUH! (me).
So, I can edit /etc/default/grub and it will stick?
Thanks!

---

### Post by Cavsfan on 2009-12-02
darkod, I see you are running Ubuntu Desktop 9.10 64bit instead of
Ubuntu 9.10 - Karmic Koala 64bit?
What is the difference, if you don't mind my asking?

---

### Post by darkod on 2009-12-02
No difference, I just didn't enter the Karmic Koala part. 9.10 is Karmic.

Yes, you can edit /etc/default/grub with sudo gedit /etc/default/grub and after any change you need to run sudo update-grub

---

### Post by Cavsfan on 2009-12-02
Thanks!
I changed my document on how to edit the boot GRUB2!

On a similar note, does anyone know how to make a JPG into an .so file?
I am wanting to change the screen that appears on bootup.
I am referring to the Startup-manager Appearance tab and adding a 
usplash theme file (*.so).
It wants it in *.so format.
I downloaded a small jpg from a ubuntu boot theme site and can't get there 
from here! I have searched for a while and cannot seem to find anything on .so files.
Thanks!

---

### Post by Mark Phelps on 2009-12-02
Not meaning to slam startupmanager or its developers, but I've used it in Karmic and determined it's not ready for prime time.

I did a simple thing like change resolutions using the tool and next thing, I get error messages upon boot because the settings were done using a technique that has been deprecated.

I was able to fix it by editing the default file and running update-grub, but that just shows that startupmanager is not in a final state for use in 9.10 at this time.

---

### Post by Cavsfan on 2009-12-02
I concur with you. I changed resolution to 800 x 600 and am now getting an error
that I cannot quite read before it disappears.
Maybe I'll go back to the one used by Jaunty. I noticed a page telling how to do that
somewhere.

---

### Post by darkod on 2009-12-02
The resolution is also set in /etc/default/grub I believe. Mark was talking only about setting it trough starupmanager. Directly in file should be fine as long as the monitor can take it.

---

### Post by Cavsfan on 2009-12-02
Sorry, I meant that I understood what he was saying.
I think these developers are doing one heck of a job and I would never say
anything bad about them to be sure! ;)
I just re-installed my system because I could not get my speakers to play anything.
It may have been caused by pulling the microphone out and plugging the speakers 
in while it was booting up.
This time I am going to not download that startup-manager. Am going to leave it alone.
I am also going to mark this thread as resolved as I found how to edit the Boot menu.
Thanks to all!

---

