---
title: "Install of 15.04 Desktop does not restart at the end on Hyper-V 2012 R2"
date: 2015-04-24
forum: Installation &amp; Upgrades
---

### Post by keymoo on 2015-04-24
The installation completes, and when I click Restart Now, it never comes back.

[IMG]http://i.imgur.com/GTXxhWV.png[/IMG]

 If I turn off the VM, eject the media and start it, it seems to boot OK. Also, once booted, if I shut down it never completes:

[IMG]http://i.imgur.com/Sp0U3CA.png[/IMG]

---

### Post by keymoo on 2015-04-24
```
apt-get install --reinstall apparmor
```

fixed it

---

### Post by nlee2 on 2015-04-24
My 15.04 gen2 vm still hangs at 90% shutdown even after reinstall of apparmor. 

Also running update-grub hangs so I am stuck with a low res display.

---

### Post by keymoo on 2015-04-24
Ah ok, mine's a Gen1 VM. Haven't tried Gen2. I also made sure that network time sync was off in Hyper-V for this VM, and I enabled Guest Services.

---

### Post by keymoo on 2015-04-30
> **keymoo said:**
> ```
apt-get install --reinstall apparmor
```

fixed it

Actually, this worked once, but now it doesn't work. Shut down just hangs there.

---

### Post by brianbuchanan on 2015-07-20
I just ran into this myself.  Installing Ubuntu 15.04 Desktop amd64 under Hyper-V on Windows 10 TPP Build 10162.

I found [Bug 1447038]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1447038") which seems to be related.  In my case a poweroff/on seems to have worked.  

During install a message about installing grub was on the screen for a very long time and in details I saw a message about memory taking a long time.  Because of that message I'm wondering if Hyper-V's dynamic memory could be an issue.  I'm going to try turning that off, but right now it's installing new updates.

---

