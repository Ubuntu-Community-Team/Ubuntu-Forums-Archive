---
title: "Only i386 kernels working?!"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by Shck on 2006-08-17
Some time ago I could use just fine i386, i686 and K7 kernels (I have AMD Duron), but nowadays if i try to boot any of i686 or K7 kernels, system just hangs and nothing happens.. All of i386 kernels are working properly, any idea what could have happened?
Really strange...

[Edit: Feel free to move this topic to another sub-forum, as this ain't so much about 'Installation problems']

(And sorry about bad spelling, english isn't by any means my native language.)

---

### Post by Greycloak on 2006-08-17
I'm using the K7 kernel as I type this...no problems here.

---

### Post by Shck on 2006-08-17
K7 and i686 kernels USED to work with me too with no problems at all, and then suddenly - Ubuntu just won't boot if I don't hit ESC and pick some i386 kernel. Kinda annoying =(

---

### Post by Shck on 2006-08-17
No ideas? Anyone? Because this feels really strange, I haven't change one single component from my computer since that problem one day just occured. First I thought that whole Ubuntu is somehow broken, but trying several BIOS-setting and stuff I just tried to boot with i386 kernel (before trying to find my rope..), and whoa - it booted like a charm. So what the hell is happening here.

---

### Post by Shck on 2006-08-20
Ok, got that one working, now every kernel is working just as they used to..
Just had to change from /boot/grub/menu.lst file all of nolapic to lapic.
No idea what that nolapic/lapic really even means, before every kernel worked just fine with that nolapic option but some reason now it just had to be lapic. Go figure.

---

