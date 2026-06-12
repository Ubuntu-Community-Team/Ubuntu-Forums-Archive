---
title: "Windows Onto Current Drive With Linux Partition"
date: 2006-04-30
forum: Installation &amp; Upgrades
---

### Post by Harold P on 2006-04-30
Hello, I'll keep this short and sweet. Are there any guides on installing Windows XP onto a current Linux installation? If there are, could someone possibly lean me in the right direction? :)

Thanks in advance,
Harold

---

### Post by chriscando on 2006-04-30
[QUOTE=Harold P]Are there any guides on installing Windows XP onto a current Linux installation?[/QUOTE]

What did you have in mind? A dual boot environment where you can select which os to use upon bootup?  Or run Windows inside Linux using something like Vmware?  Am I on the right track?

---

### Post by Harold P on 2006-04-30
Oh, I meant as in installing it on a different partition that my hard drive already has Linux on it. When I installed Linux side by side with windows, the guide I used helped me to easily distinguish how to put Linux onto a current Windows machine, but now I want to do the opposite (I've totally wiped out Windows), and install Windows side-by-side onto my existing Linux drive. If that made any sense? :S

I don't want install Windows as an application under Linux like "VMWare". Does that help better explain my question?

---

### Post by chriscando on 2006-04-30
Ok, I see. So you want to dual boot Linux and windows.  Assuming you have space you could just pop in your windows cd and install it on a free partition. The problem is that windows will overwrite your bootloader and will not recognize your Linux installation. All you have to do is reinstall grub.  I've never done this with Ubuntu but I have with Live CDs like Mepis and its pretty easy, assuming it correctly reinstalls grub.  If not, you won't be able to get back into Linux.

One other thing. I have had problems booting windows from grub when windows is not on the first partition. I ended up having to manually edit grub to fix this.

---

### Post by Sef on 2006-05-16
To dual boot read this excellent tutorial:

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

