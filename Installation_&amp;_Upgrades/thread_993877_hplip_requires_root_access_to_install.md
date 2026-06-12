---
title: "hplip requires root access to install"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by rccraven on 2008-11-26
Hi there,
have just reinstalled Ubuntu from a USB stick, and accepted all standard upgrades.
Went to HP for Linux drivers for HP Photosmart, which was there OK. This didn't work, I just got "unable to run" message.
From the main menu, applications- add/remove I get the same version - cool!
However, I try to tun hp-setup and get an error message "you must be root to run this utility"
I've tried su - root and the password isn't my main user one, and it isn't the obvious one either - I just get an authenticatin failure whatever I do.

Any help on how to give main account root privileges, or root password for a standard install for 8.10.

TIA,

Richard

---

### Post by __Ryan__ on 2008-11-26
Root does not have a password with a standard install so you have to give it one manually (unsupported in Ubuntu!).

But you could skip all this an just use sudo to submit root commands in the first place but I always find it useful to be able to log into my system as root in case something goes wrong in my user account.

---

### Post by andrew.mckevitt on 2008-11-26
> **rccraven said:**
> Hi there,
have just reinstalled Ubuntu from a USB stick, and accepted all standard upgrades.
Went to HP for Linux drivers for HP Photosmart, which was there OK. This didn't work, I just got "unable to run" message.
From the main menu, applications- add/remove I get the same version - cool!
However, I try to tun hp-setup and get an error message "you must be root to run this utility"
I've tried su - root and the password isn't my main user one, and it isn't the obvious one either - I just get an authenticatin failure whatever I do.

Any help on how to give main account root privileges, or root password for a standard install for 8.10.

TIA,


Richard

Sounds as though you've installed it ok, but you need to use 'sudo'

```
sudo hp-setup
```

and then use your sign in password when asked for it.

That should work.

---

### Post by aheckler on 2008-11-26
**[COLOR="Red"]NOTE:[/COLOR] Logging in as root is crazy dangerous and telling people how to do so on these forums is actually not allowed. So rccraven, I do not recommend doing what Ryan has told you to do, and I've actually reported his post to the mods.**

---

### Post by rccraven on 2008-11-26
> **aheckler said:**
> **[COLOR="Red"]NOTE:[/COLOR] Logging in as root is crazy dangerous and telling people how to do so on these forums is actually not allowed. So rccraven, I do not recommend doing what Ryan has told you to do, and I've actually reported his post to the mods.**

A Pity. It worked really well, and all I have now is a changed root password. Which, since it's my machine, I don't see a difficulty with. YMMV, obviously.

Cheers,
Richard

---

### Post by rccraven on 2008-11-26
> **andrew.mckevitt said:**
> Sounds as though you've installed it ok, but you need to use 'sudo'

```
sudo hp-setup
```

and then use your sign in password when asked for it.

That should work.

Doh! That worked fine as well, TYVM.

Cheers,
Richard

---

### Post by aheckler on 2008-11-26
Reference this post by the forum mods: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by aheckler on 2008-11-26
Also, you might want to [re-disable your root account]("https://help.ubuntu.com/community/RootSudo#Re-disabling%20your%20root%20account") for safety's sake.

---

### Post by __Ryan__ on 2008-11-26
> **aheckler said:**
> **[COLOR="Red"]NOTE:[/COLOR] Logging in as root is crazy dangerous and telling people how to do so on these forums is actually not allowed. So rccraven, I do not recommend doing what Ryan has told you to do, and I've actually reported his post to the mods.**

I think crazy dangerous is a bit off the deep end.  If you you would have read my post you would have seen that I advised the use of sudo as well. 

There are a variety of reasons to have access to the root account.  In my experience having access to login as root far offsets the drawbacks of any potential security threat, especially on a personal computer.

---

### Post by Rocket2DMn on 2008-11-26
As has already been stated, root login is not supported by Ubuntu's security model.  This is not to say it doesnt' have its uses or is *wrong*, but it typically isn't necessary.  If you really need a root login to perform recovery on your system, that is what the Recovery Mode console is for at the GRUB boot screen.  If you enable a root password, then it will prompt you for one here, which means you're in trouble if you forget it - otherwise it doesn't prompt for a root password in recovery mode.  While this may sound like a security breach, remember that systems aren't really designed to be secure AT the console.

sudo or graphical sudo (gksudo in gnome) is usually adequate for tasks requiring root permissions.

---

### Post by rccraven on 2008-11-26
Reading the other posts, I may disable that account again to make subsequent auto recovery easier.

Thanks for all the help,
Richard

---

