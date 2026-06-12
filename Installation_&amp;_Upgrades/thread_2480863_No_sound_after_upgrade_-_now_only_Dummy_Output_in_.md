---
title: "No sound after upgrade - now only Dummy Output in Sound"
date: 2022-11-12
forum: Installation &amp; Upgrades
---

### Post by peyre on 2022-11-12
I upgraded to Xubuntu 22.10 yesterday and everything seemed fine.  But today, no sound.  The system starts up with sound muted and turned all the way down.  If I look in Sound -> Output Devices, all it shows there is "Dummy Output".  I'm not using any headphones or other speakers on this computer, just the built-in speakers.

If it comes to it, is there an easy way to undo the upgrade?  I could always keep it on the LTS.

---

### Post by Claus7 on 2022-11-12
Hello,

I faced exactly the same problem upgrading from 22.04 to 22.10 development:
[https://ubuntuforums.org/showthread.php?t=2478657](https://ubuntuforums.org/showthread.php?t=2478657)

As you can see I couldn't solve the issue but to do a clean install. You could take a look on some proposals that might help you solve you issue. 

I think that even if this issue is not new for ubuntu upgrade, the fact that there is a transition from pulseaudio to pipewire might make things more difficult.

Regards!

---

### Post by peyre on 2022-11-12
Thanks Claus, I'll have a look.

---

### Post by peyre on 2022-11-14
Well for what it's worth, the article didn't help.  Was worth a try though.

---

### Post by Claus7 on 2022-11-16
Hello,

couldn't find a solution either. I just would advice you to check out a startup disk. If it is working at least you know that in a clean install it will work as it should. In case it doesn't you might have to downgrade, yet I doubt it. While checking about the same issue I found out that this happens due to a faulty upgrade and not because the new OS won't be compatible. It was a main reason to try clean install as well.

Regards!

---

### Post by peyre on 2022-11-16
Thanks Claus, I didn't think to try booting from a live disk.  I've reinstalled 22.04 from scratch and am getting it all configured; I've left it at LTS so I don't have to go through this again, hopefully.

---

### Post by Claus7 on 2022-11-16
Hello,

I attempted the upgrade to 22.10 due to the okular feature of displaying non latin characters and the fix they had with poppler with this release. This might migrate to 22.04 as well, yet it wasn't available at the time. It took me a couple of minutes to try the usb stick, so I was certain that if attempting a clean install, things would work normally, as they finally did. I hope I had a better solution, yet what I tried didn't work.

Regards!

---

