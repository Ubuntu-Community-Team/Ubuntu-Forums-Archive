---
title: "Can I install Ubuntu Netbook Remix with Wubi?"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by csh on 2010-02-26
My friend asked me to help him install Ubuntu on his Netbook. In his Netbook, there is a hidden partition which store the files used for reinstall Windows and system recovery. We don't have external optical drive to create the recovery discs.In order to reduce the risk of the recovery partition affected by Ubuntu installation, the best is to install Ubuntu Netbook Remix through Wubi.

But, is it possible to install Ubuntu Netbook Remix through Wubi? If yes, kindly please tell me the steps. If no, is there any other possible way to make Ubuntu Netbook Remix can be installed by Wubi?

---

### Post by Arkitekt on 2010-02-26
Yes, WUBI for Karmic should allow you to select UNR under Desktop Environment. If not you can always install the Desktop version through WUBI and then use synaptic to add the netbook remix packages manually.

---

### Post by csh on 2010-02-27
> **Arkitekt said:**
> Yes, WUBI for Karmic should allow you to select UNR under Desktop Environment. If not you can always install the Desktop version through WUBI and then use synaptic to add the netbook remix packages manually.

Thank you!

---

### Post by steveneddy on 2010-02-27
You may be happier using a virtual machine like VirtualBox.

It is lots more stable than wubi.

---

### Post by csh on 2010-02-27
> **steveneddy said:**
> You may be happier using a virtual machine like VirtualBox.

It is lots more stable than wubi.

Yes but my friend don't want to use virtual machine. 

Using virtual machine will consume huge amount of memory, make sharing files harder. And, we are students of computer science course, and our tasks involving physical hardware. So, we must not use virtual machine.

---

### Post by vginer on 2010-04-26
> **steveneddy said:**
> You may be happier using a virtual machine like VirtualBox.

It is lots more stable than wubi.

Excuse me for going into the conversation, but I am also thinking about installing UNR through Wubi in my old 12'1'' laptop.

What do you mean by "lots more stable than wubi"? Isn't Wubi stable enough?

Is it an acceptable option? Which are the risks??

Thank you in advance for your help.   :)

---

### Post by yongjhen on 2010-04-27
> **vginer said:**
> Excuse me for going into the conversation, but I am also thinking about installing UNR through Wubi in my old 12'1'' laptop.

What do you mean by "lots more stable than wubi"? Isn't Wubi stable enough?

Is it an acceptable option? Which are the risks??

Thank you in advance for your help.   :)

I use Ubuntu/UNR through Wubi on my Asus W5F and HP mini 2140.
Wubi puts ext3 partition in your Windows NTFS, and configures grub to boot from it.
So I think unless ntfs-3g (the NTFS driver Ubuntu uses) is buggy, it is just as stable as a normal Ubuntu/UNR installation.
And unlike using virtual machine, it uses your hardware directly.
Filesystem performance will not be great, of course, but I never do a benchmark ;)

---

### Post by Dayofswords on 2010-04-27
other than a boot issue on a machine from 2000, i havent had an issue with wubi

i say, use it. but dont keep important things on it for too long just in case.

---

