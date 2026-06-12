---
title: "Error attempting to install from alternate usb"
date: 2012-10-30
forum: Installation &amp; Upgrades
---

### Post by paridoth on 2012-10-30
I am trying to install lubuntu 12.10 alternate from a usb stick I made using unetbootin.
 I have checked the md5 on the iso I got from the lubuntu site and it checks out. 
the laptop I am using doesnt have a crdrom drive so I have to use a usb stick, and the standard desktop iso has a graphical error that makes it unuseable.
Here is the error.

[http://imgur.com/92MOA]("http://imgur.com/92MOA")

---

### Post by wojox on 2012-10-30
Did you try what the error stated?

---

### Post by alexxtasi on 2012-12-25
it also affects me!!!
so I tried what the error stated (just run again the "Select and install software" option) several times because the same error appeared!
Finally I tried the next option which installed grub successfully and rebooted the system. But right after that, nothing appears on screen when booting!
any help?

---

### Post by pardalet on 2012-12-25
> **alexxtasi said:**
> it also affects me!!!
so I tried what the error stated (just run again the "Select and install software" option) several times because the same error appeared!
Finally I tried the next option which installed grub successfully and rebooted the system. But right after that, nothing appears on screen when booting!
any help?


Just a stab in the dark, but... could it be that the software installation failed because you don't have an internet connection when installing Ubuntu?

---

### Post by alexxtasi on 2012-12-26
thanks pardalet for the replay...

It is really strange!
I tried this several times

I even tried to install ubuntu-server-12.10 on this machine (so I will try to sudo apt-get install lubuntu-desktop or something similar... ) and the same message appears!!! Then I finished the installation, logged in (fortunately I did it!! ) and I could ping on google (;-)) so I think my nic works fine...

But why then I cant "sudo apt-get install lubuntu-desktop" but an error appears?

---

### Post by pardalet on 2012-12-26
I'm not following you... What error do you get when trying *«sudo apt-get install lubuntu-desktop»*? The [_same one than the OP's_](http://imgur.com/92MOA) or another one?

If the latter, please provide the error output.

---

### Post by alexxtasi on 2012-12-27
you are right! I will try to be more specific

1. first I tried to install lubuntu-12.10-alternate and the "Select and install software" error appeared (just like in the photo you provided). Continuing the installation (grub install...) and rebooting the system nothing happens...

2. then I tried to install ubuntu-server-12.10 but the same error appeared! (my thought was to install ubuntu server and then install the lubuntu core system).

3. in the ubuntu server system.... trying "sudo apt-get install lubuntu-core" it gives the "E: unable to locate package lubuntu-core". The same when I try "sudo apt-get install lubuntu-desktop"

the system can ping to google so there is a connection... but cant install anything unless the ubuntu server cdrom is mounted! (this is the way I managed to install openssh-server and its the only package I managed to install!!!)

so there might be a problem with the apt-get ?

when I "sudo apt-get update" ....
"Ign cdrom://Ubuntu-Server 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal InRelease"
so maybe the "Select and install software" error caused this sources error!
but how can I fix it?

(I am wondering if this is for another topic ! :-))

---

### Post by alexxtasi on 2012-12-28
> **pardalet said:**
> Just a stab in the dark, but... could it be that the software installation failed because you don't have an internet connection when installing Ubuntu?
you where right! I tried again (using the ubuntu-server cd once again) and everything with the installation went right.
Probably the internet connection was unstable when I tried for the first time... bad luck ;-)

I ll try lubuntu-alternate once again to see what happens

thanks for your time anyway

---

