---
title: "kernel panic"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by Bashed on 2007-05-02
I have no idea what has happened, but after rebooting I get this during the boot:

Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: unable to mount root fs on unknown block (0,0)

I did not even touch anything with kernel so I have no idea why I'm getting this.

---

### Post by Bashed on 2007-05-02
Sorry to bump this up, but can someone please help me fix this critical problem so I can get back into my system? Thanks.

---

### Post by ali4949 on 2007-05-02
did you try recovery mode??
just in case if you dont already know .. press esc when grub is loading and then select recovery kernel and see if you can get into the system.. also if you are just getting to the command prompt type startx to get into the window manager.. hopefully this will get you started back again

---

### Post by Bashed on 2007-05-02
unfortunately recovery mode shows me the same error, so I cannot get into command mode. I don't even know the cause of this, can you at least hint me what might cause this and how to resolve it, possibly with a live cd?

---

### Post by dannymichel on 2007-05-22
> **TalkJesus said:**
> Sorry to bump this up, but can someone please help me fix this critical problem so I can get back into my system? Thanks.
I swear I've never seen more ignored threads and or posts on ANY discussion board.

---

### Post by regomodo on 2007-07-13
hi. did you get this sorted?

I have exactly the same issue with the same error. I don't remember touching  anything since my last reboot and now i can't boot. Not even in recovery mode.

However, i can boot up in kernel 2.6.20-15 no problems. Just doesn't seem to like ...-16

Basically a bump

[edit] got it sorted by running $ sudo update-initramfs -u. It was rather easy as i could get in using ...-15. If you can't it's a bit harder with chrooting. Whatever that is.

---

### Post by JayBachatero on 2007-08-05
> **regomodo said:**
> hi. did you get this sorted?

I have exactly the same issue with the same error. I don't remember touching  anything since my last reboot and now i can't boot. Not even in recovery mode.

However, i can boot up in kernel 2.6.20-15 no problems. Just doesn't seem to like ...-16

Basically a bump

[edit] got it sorted by running $ sudo update-initramfs -u. It was rather easy as i could get in using ...-15. If you can't it's a bit harder with chrooting. Whatever that is.

You are the man.  I've had a few months w/o using Ubuntu just cause of this error.  I tried searching before and didnt find anything so decided to give this another shot and found your answer,  Thanks :)

---

