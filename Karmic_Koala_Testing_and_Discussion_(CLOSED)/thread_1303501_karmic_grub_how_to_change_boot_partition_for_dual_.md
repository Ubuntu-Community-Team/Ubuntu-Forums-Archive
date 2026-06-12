---
title: "karmic grub how to change boot partition for dual boot?"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by powel212 on 2009-10-28
I've searched it but can get no clear info.

want to change my default boot option to win7 in grub

```
sudo gedit /boot/grub/menu.lst
```
didn't work

How to configure grub in Karmic?

Any help is appreciated

Powel

Also can't seem to save changes to "nvidia-settings" Can't save changes

---

### Post by philinux on 2009-10-28
Click the grub2 link in my sig. You're in for a shock.

Also these links.

[http://ubuntuforums.org/showthread.php?t=1285897&highlight=grub](http://ubuntuforums.org/showthread.php?t=1285897&highlight=grub)

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub)

---

### Post by Mark Phelps on 2009-10-28
> **philinux said:**
> Click the grub2 link in my sig. You're in for a shock.

+1!

Guess we'd better start getting prepared for the onslaught of all those folks that though hand-editing a few lines in menu.lst was a lot of work -- when faced with the alternatives in GRUB2!

Here's hoping that the Startup Manager developers get their GRUB2-compatible version out REAL SOON.

---

### Post by pythonscript on 2009-10-28
For one thing:

```
gksudo gedit /boot/grub/menu.lst
```

Don't use sudo for graphical apps. It's *much* safer to use gksudo, and for this reason, it's recommended on these forums. Also, if you have a unrelated question about nvidia-settings, why don't you try posting it in a new thread instead of just adding several different topics to this thread?

---

### Post by philinux on 2009-10-28
> **Mark Phelps said:**
> +1!

Guess we'd better start getting prepared for the onslaught of all those folks that though hand-editing a few lines in menu.lst was a lot of work -- when faced with the alternatives in GRUB2!

Here's hoping that the Startup Manager developers get their GRUB2-compatible version out REAL SOON.

Slightly OT.
I've come to the conclusion, rightly or not, that karmic is a testing release for the next LTS. Ext4 is still being developed and grub2 is still beta. And on startup we got a mix of usplash and xsplash. Which gives me this.
[http://ubuntuforums.org/showthread.php?t=1292711](http://ubuntuforums.org/showthread.php?t=1292711)

---

### Post by powel212 on 2009-10-28
Thanks for the help guys

Here's what I did

```
sudo gedit /etc/default/grub
```

change "GRUB_DEFAULT=0" to "GRUB_DEFAULT=4" "4" being win 7 

then

```
sudo update-grub
```

The last line is important as i tried it once without running the grub update command and it didn't stick.

Thanks again

Powel

---

### Post by pythonscript on 2009-10-28
> **philinux said:**
> Slightly OT.
I've come to the conclusion, rightly or not, that karmic is a testing release for the next LTS. Ext4 is still being developed and grub2 is still beta. And on startup we got a mix of usplash and xsplash. Which gives me this.
[http://ubuntuforums.org/showthread.php?t=1292711](http://ubuntuforums.org/showthread.php?t=1292711)

I have to agree; it's seeming more and more that they're just testing features out. After all, for the GUI users, the Software Center is first included in Karmic, but... it's not fully implemented, or it doesn't replace everything thing it "eventually will," etc. Hopefully this means that Lucid will be a light, quick, and robust LTS.

EDIT:  And powel212, did you see my warning about using **gksudo **instead of **sudo**? You really want to keep that in mind.

---

### Post by philinux on 2009-10-28
> **powel212 said:**
> Thanks for the help guys

Here's what I did

```
sudo gedit /etc/default/grub
```

change "GRUB_DEFAULT=0" to "GRUB_DEFAULT=4" "4" being win 7 

then

```
sudo update-grub
```

The last line is important as i tried it once without running the grub update command and it didn't stick.

Thanks again

Powel

Good Job ;)

---

