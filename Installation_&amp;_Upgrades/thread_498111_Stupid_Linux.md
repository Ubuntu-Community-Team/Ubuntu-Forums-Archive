---
title: "Stupid Linux"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by VEGAMO on 2007-07-10
No don't get mad, I don't hate Linux, I just think there is a big problem with it.

I am trying to install Limewire, I downloaded the ubuntu version (which is the OS I HAVE).
and while installing, I did something and by accident it froze the install manager.

So I restart the computer and run the installation again, it tells me that I already have an installation manager running.... -_-

WTF? Linux doesn't kill processes when there is a reboot? wtf am i supposed to do? I tried finding the process in the System monitor but no luck.

Any one know some god damn command that somehow ends this stupid process?

sorry for being a bit mean, hate it when I have to go and ask people for help when it should be simple in the goddamn thing in the first place.

---

### Post by Qrk on 2007-07-10
It doesn't sound like you are having a good day. 

You might be able to fix your problem with this command

```
sudo dpkg-reconfigure -a
```

Linux does kill processes on reboot (its kind of hard not to,) your error message was probably due to an interrupted package manager, not one already running.

Also, limewire on linux is very buggy, many people have problems with it. You'd probably be better off trying something like gtk-gnutella, available in the repositories. It isn't commercial software, doesn't nag you to upgrade, and integrates with Gnome. 

```
sudo apt-get install gtk-gnutella
```

---

### Post by inuyokai on 2007-07-11
Here's a question....

Why would you use limewire? 

Not really anything good found on it anymore since they were sort of shutdown or forced into limited operation...

---

### Post by VEGAMO on 2007-07-11
> **Qrk said:**
> It doesn't sound like you are having a good day. 

You might be able to fix your problem with this command

```
sudo dpkg-reconfigure -a
```

Linux does kill processes on reboot (its kind of hard not to,) your error message was probably due to an interrupted package manager, not one already running.

Also, limewire on linux is very buggy, many people have problems with it. You'd probably be better off trying something like gtk-gnutella, available in the repositories. It isn't commercial software, doesn't nag you to upgrade, and integrates with Gnome. 

```
sudo apt-get install gtk-gnutella
```

Thanks a lot, ill use that instead.

and yah i've been having a hard day.

---

### Post by VEGAMO on 2007-07-11
> **Qrk said:**
> It doesn't sound like you are having a good day. 

You might be able to fix your problem with this command

```
sudo dpkg-reconfigure -a
```

Linux does kill processes on reboot (its kind of hard not to,) your error message was probably due to an interrupted package manager, not one already running.

Also, limewire on linux is very buggy, many people have problems with it. You'd probably be better off trying something like gtk-gnutella, available in the repositories. It isn't commercial software, doesn't nag you to upgrade, and integrates with Gnome. 

```
sudo apt-get install gtk-gnutella
```

Well sadly, that reconfigure stuff is not working, I click yes and yes and yes, and it said Done in the end. However nothing changed.

I need this fixed if I wanna install anything else.

---

### Post by Qrk on 2007-07-11
Are you sure you don't have another package manager running? 

Try running
```
top
```

to see if anything that looks like a package manager is running. If it is, use 

```
sudo kill <processname>
```

---

### Post by Jeremywilms on 2007-07-11
You could manually uninstall. Delete the root folder in you HD Program Files, and I blive the rest is in your Documents.

---

### Post by jordanmthomas on 2007-07-11
> You could manually uninstall. Delete the root folder in you HD Program Files, and I blive the rest is in your Documents.
?!?

Also, if the above commands don't help you out there's always the possibility a lock file is left around. You just need to remove the lockfile (make sure dpkg isn't running first):
```
sudo rm /var/lib/dpkg/lock
```

---

### Post by Jeremywilms on 2007-07-11
> **jordanmthomas said:**
> ?!?

Also, if the above commands don't help you out there's always the possibility a lock file is left around. You just need to remove the lockfile (make sure dpkg isn't running first):
```
sudo rm /var/lib/dpkg/lock
```

"?!?" I mean go C:\program Files\Limewire and delete that. Then go C:\Users\[User]\Documents\Limewire(or somthing like that) and delete that.

---

### Post by rillip on 2007-07-11
> **Jeremywilms said:**
> "?!?" I mean go C:\program Files\Limewire and delete that. Then go C:\Users\[User]\Documents\Limewire(or somthing like that) and delete that.

He's not installing a Windows version and running through Wine.  He's installing an Ubuntu version, so the directory structure you're suggesting doesn't exist.

---

### Post by jordanmthomas on 2007-07-11
Ah, I see what you were going for Jeremywilms.  That makes sense now that you explained it.  :)

---

