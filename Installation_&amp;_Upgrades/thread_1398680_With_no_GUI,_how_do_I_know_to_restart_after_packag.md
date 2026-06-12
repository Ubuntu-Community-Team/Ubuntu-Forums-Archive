---
title: "With *no* GUI, how do I know to restart after package update?"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by anarkhos on 2010-02-04
I have a Ubuntu web server that I ssh into from time to time.

I run this:
sudo apt-get upgrade -y

to update the packages.  When I do this on my desktop, I see a sometimes see a dialog notifying me I need to restart Ubuntu for changes to be completed.  Is there a CLI way to see if Ubuntu needs to be restarted after updates?  

Let's say that I didn't notice text saying `you need to restart` while I was doing the package upgrade.  Is there a way to checking to see (say in a day or 2 after the upgrade) if the package manager is still waiting on a reboot?

---

### Post by Leppie on 2010-02-04
you should only have to restart when you receive kernel updates.

---

### Post by anarkhos on 2010-02-04
So a followup please.  I would only need to reboot my server if I see a package called `linux-headers-xyz` in the upgrade list?

---

### Post by stlsaint on 2010-02-04
Not really every single time you see headers being update but just to be on the safe side when you see the kernel being update or added to then go ahead and reboot but i rarely get updates that require me to reboot on my servers.

---

### Post by shriramrs31 on 2010-02-05
> **anarkhos said:**
> 
Let's say that I didn't notice text saying `you need to restart` while I was doing the package upgrade.  Is there a way to checking to see (say in a day or 2 after the upgrade) if the package manager is still waiting on a reboot?

My understanding is that u need a restart only after kernel updates. In this case, since u are still working in the older kernel, you are in the safe side if you don't restart. you can keep working. If you want to log into the new kernel, you can restart and select the new kernel from boot menu.

---

### Post by Leppie on 2010-02-05
if you want to avoid restarting for most kernel updates, you could install ksplice's uptrack: [http://www.ksplice.com/](http://www.ksplice.com/)
it's free for ubuntu.

---

### Post by anarkhos on 2010-02-05
> **Leppie said:**
> if you want to avoid restarting for most kernel updates, you could install ksplice's uptrack: [http://www.ksplice.com/](http://www.ksplice.com/)
it's free for ubuntu.
Very cool, thanks for suggesting that.

I found the download page at: [http://www.ksplice.com/uptrack/download](http://www.ksplice.com/uptrack/download)

---

### Post by tubasoldier on 2010-02-05
Ksplice is great. And there isn't any real reason to restart your servers.

However, to answer your original question for future reference:

```
sudo shutdown -r now
```

the -r option will reboot the machine. 
substitue the -h option and it will halt.

'now' is the time limit to shutdown/restart
you can set the time in minuites, say 30 or 90 if you want it to reboot/shutdown in a specified time.

I haven't read much about days but i'm sure there is a way to set the time limit for days. Or you can just use 1440 minuites per day.

---

