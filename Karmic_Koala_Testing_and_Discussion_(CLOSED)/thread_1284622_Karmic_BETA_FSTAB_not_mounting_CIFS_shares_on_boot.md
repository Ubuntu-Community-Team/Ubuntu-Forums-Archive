---
title: "Karmic BETA: FSTAB not mounting CIFS shares on boot"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hybridr6 on 2009-10-06
Hi all, I've just upgraded to the Karmic BETA and have enjoyed the new feature set with this release, but my cifs shares are no longer mounting at boot up. "sudo mount -a" works with no errors at all, yet for some reason the shares are not being mounted from fstab.

Here is what I have in my fstab:
```
//10.10.10.2/Videos /home/ash/Videos cifs noperm,iocharset=utf8,uid=1000 0 0
//10.10.10.2/Music /home/ash/Music cifs noperm,iocharset=utf8,uid=1000 0 0
//10.10.10.2/ash /home/ash/Documents cifs noperm,iocharset=utf8,uid=1000 0 0
//10.10.10.2/ash/Pictures /home/ash/Pictures cifs noperm,iocharset=utf8,uid=1000 0 0 
```

Any help would be greatly appreciated. I apologise if this is an already known bug but, I did a few searches in the forum and launchpad to no avail.

---

### Post by callan79 on 2009-10-07
> **hybridr6 said:**
> my cifs shares are no longer mounting at boot up. "sudo mount -a" works with no errors at all, yet for some reason the shares are not being mounted from fstab.



Hi hybridr6,

My suggestion - whack 'auto' in the options area - i.e. where you have noperm, make that auto,noperm and then the rest of your options.

Let us know how that goes.

BTW check out my other post at [http://ubuntuforums.org/showthread.php?p=8045797](http://ubuntuforums.org/showthread.php?p=8045797) and let me know if you notice any similar behaviour ...

Cheers
Callan

---

### Post by hybridr6 on 2009-10-07
> **callan79 said:**
> Hi hybridr6,

My suggestion - whack 'auto' in the options area - i.e. where you have noperm, make that auto,noperm and then the rest of your options.

Let us know how that goes.

BTW check out my other post at [http://ubuntuforums.org/showthread.php?p=8045797](http://ubuntuforums.org/showthread.php?p=8045797) and let me know if you notice any similar behaviour ...

Cheers
Callan

Thanks for the suggestion Callan, but unfortunately adding "auto" to the options didn't help any. :(

---

### Post by callan79 on 2009-10-07
> **hybridr6 said:**
> Thanks for the suggestion Callan, but unfortunately adding "auto" to the options didn't help any.


Hi hybridr6,

I just noticed in my system, during boot, I get a CIFS mount error too. The devices do actually mount, but I think this is happening AFTER I log into Gnome (i.e. once NetworkManager starts and I get an IP Address).

Curious...

Did you solve your other issues regarding ownership?

Cheers
Callan

---

### Post by hybridr6 on 2009-10-08
> **callan79 said:**
> Hi hybridr6,

I just noticed in my system, during boot, I get a CIFS mount error too. The devices do actually mount, but I think this is happening AFTER I log into Gnome (i.e. once NetworkManager starts and I get an IP Address).

Curious...

Did you solve your other issues regarding ownership?

Cheers
Callan

Yea, what I think is happening is due to the changes in the startup procedures cifs is trying to mount shares before the network is brought up. I'll have to investigate a lil' further. Luckily I don't reboot all that often. :)

I solved the ownership issues by adding noperm in the fstab options. This made the remote uid no longer be enforced locally.

---

### Post by anibalojeda on 2009-10-14
A very anoying bug, i found this [https://bugs.launchpad.net/ubuntu/karmic/+source/mountall/+bug/447649?comments=all](https://bugs.launchpad.net/ubuntu/karmic/+source/mountall/+bug/447649?comments=all)

Where they claim is fix but my share dont get mounted after boot. I can do this after login using sudo mount -a 

Anyone any idea.

---

### Post by svasie on 2009-10-16
There is a bug opened around this issue:

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/451432?comments=all](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/451432?comments=all)

Please, subscribe to it.

---

