---
title: "Upgrade to 10.10 failed after power cut"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by eekfonky on 2010-10-08
I can log into a terminal but that's all, please help

---

### Post by sikander3786 on 2010-10-08
In most of the similar cases I have seen, reinstall was the only successful solution.

You can log into a terminal. Recovery mode or at the login screen?

You can try

```
sudo apt-get clean
```

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install -f
```

```
 sudo dpkg --configure -a
```

Make sure you are connected to the internet.

---

### Post by eekfonky on 2010-10-08
Tried it and it does nothing, my problem is that there are files in the $home folder I need

---

### Post by sikander3786 on 2010-10-08
Boot from a live CD, mount your /home partition and copy them over to a safe place.

---

### Post by eekfonky on 2010-10-08
I tried that but I don't know where they live? When I open the $home folder it has a link to private files and won't open, I've tried various solutions with no effect. Is there a simple way?

---

### Post by sikander3786 on 2010-10-08
Sure. Boot into a live cd and post the output of

```
sudo fdisk -l
```


**[COLOR="Red"]EDIT:[/COLOR]** Just realized that will not be necessary. Just type

```
gksu nautilus
```

from Live CD and you'd be able to copy your data.

---

### Post by eekfonky on 2010-10-08
/dev/sda1 is where the folder is the /dev/sda2 is Extended and /dev/sda5 is Linux Swap

---

### Post by sikander3786 on 2010-10-08
Did you see the Edit in my above post. If that doesn't work you can try

```
sudo chmod -R 777 /media/sda1/home
```

after mounting your / partition.

---

### Post by Jakiejake on 2010-10-08
Yeah, I recommend that you backup all your files to an external source
Then if we can't get you back to your original desktop the only other option might be to re-install Ubuntu (10.10 comes out in 2 days or so)
Good Luck :)

---

### Post by eekfonky on 2010-10-08
All I really need are the files in the home folder but all I get is a shortcut to 'acceess-your-private-data.desktop' and when I click on it I'm told it's an 'untrusted application launcher'

If I can get the files a reinstall will do, but the files are they problem

---

### Post by sikander3786 on 2010-10-08
> **eekfonky said:**
> All I really need are the files in the home folder but all I get is a shortcut to 'acceess-your-private-data.desktop' and when I click on it I'm told it's an 'untrusted application launcher'

If I can get the files a reinstall will do, but the files are they problem
What type of files are they? Installed software? They might just have a shortcut on your desktop just pointing towards some other location. You can right click and check the target the link is pointing to.

---

### Post by eekfonky on 2010-10-08
They are just OpenOffice documents and folders, if i could see them I would copy them. But when I try to open my home folder all I get is that link which doesn't work.

---

### Post by sikander3786 on 2010-10-08
I actually couldn't understand. Can you somehow post a screenshot?

---

### Post by eekfonky on 2010-10-08
see attached

---

### Post by sikander3786 on 2010-10-08
So you encrypted your /home. I'll have to do a bit of research on that as I have never been there before. Please hang on.


**[COLOR="Red"]EDIT:[/COLOR]** Okay, a quick Google revealed this.

[http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/](http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/)

---

### Post by eekfonky on 2010-10-08
tried that, nothing happens. I have scoured the net looking before coming to the forum. The home folder wasn't encrypted. It's not actually mine but a friends. He assures me it wasn't encrypted. Maybe it's because I'm booting from the live cd?

---

### Post by sikander3786 on 2010-10-08
```
Maybe it's because I'm booting from the live cd?
```

No.

I feel stumped at this stage. Out of ideas...

Wait for some senior members, they might be able to enlighten you.

Regards.

---

