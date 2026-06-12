---
title: "Screwed up upgrade from 9.10 to 10.04"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by vampire666eng on 2010-05-02
Alright, let's start saying that **I screwed up**: I pressed a combination of keys that I shouldn't have pressed during the upgrade process from ubuntu 9.10 to 10.04 (it was installing "the new stuff").

The result is that the PC didn't complete the upgrade (I practically stopped the upgrade and rebooted) and when I select ubuntu in grub (I have a multiboot with windows XP and Seven), I have no GUI and just a command interface.

Is there a way to remedy and continue the upgrade/installation process or am I screwed up and have to do a clean install?

Thanks

P.S. Lesson learned: do not do anything unnecessary when upgrading.

---

### Post by phillw on 2010-05-02
Hi,

you can try ```
sudo apt-get install --no-install-recommends ubuntu-desktop
``` which *should* go get it for you.

Regards,

Phill.

---

### Post by vampire666eng on 2010-05-02
Thanks for the reply.
Well something did change but I still have problems.

when I tried the command you wrote, it told me that dpkg was interrupted and I had to run the following command:
```
sudo dpkg --configure -a
```

I did and then I retried but it told me that I had to
```
sudo apt-get -f install
```

I did and then I retried but it told me that I had to
```
sudo apt-get autoremove
```

I did and when I retried 
```
sudo apt-get install --no-install-recommends ubuntu-desktop
```

it told me everything was ok.

So I rebooted, but I received a very strange blank screen with colored blocks and characters (which where changing colors).

Then I rebooted and at ubuntu boot I pressed one of the F (function) keys of the keyboard (I don't know which one since I pressed them all :oops: ...is it F4 maybe?:oops:), and I was able to logon.
Then I run the update manager and downloaded and installed everything it was showing.
I rebooted (it asked me to) and I received the same strange screen with colored blocks ans characters.
The problems is that now even if I hit the Function key on the keyboard at ubuntu boot, the OS hangs in the logon page.

I guess that at this point I need a clean reinstall. :(

Anyway, thanks for your help. I appreciate it.

---

### Post by vampire666eng on 2010-05-21
Just wanted to say that I did a clean reinstall. :)

---

