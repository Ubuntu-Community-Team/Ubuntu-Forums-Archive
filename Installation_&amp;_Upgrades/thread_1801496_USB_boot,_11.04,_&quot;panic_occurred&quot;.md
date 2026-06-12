---
title: "USB boot, 11.04, &quot;panic occurred&quot;?"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by pifactory3142 on 2011-07-10
Hi

I'm trying to boot 11.04 on a couple of  Asus eeepc 1000HD machines (one about 3 years old, the other about 2) from a sandisk usb stick.

The process takes quite a few minutes, with lots of characters plus streams of messages many of which look ok, but also lots along the lines of no such file exists.

It seemingly ended with initramfs and advising me to type help for further commands. It gave me the further commands.

The process suddenly leapt back into action and the screen now ends with

[1017.916061] panic occurred switching back to text console.

The newer machine runs Netbook remix ok. Any ideas or are these machines just not up to 11.04?

Thanks.

---

### Post by mörgæs on 2011-07-10
Have you tried Xubuntu 11.04 in stead of Ubuntu?

---

### Post by pifactory3142 on 2011-07-12
Thanks for the response... I'll give it a go.

Why Xubuntu?

---

### Post by pifactory3142 on 2011-07-15
Thanks. Two defunct machines have been revived back to life.

xubuntu now works on both my old Asus Eeepc 1000 and 1000 HD machines.

The first is running a celeron processor and the second an atom.

You need to set up a usb stick for booting xubuntu 11.04... but see [http://alexsleat.co.uk/2010/11/27/ho...untu-usb-boot/]("http://alexsleat.co.uk/2010/11/27/how-to-fix-unknown-keyword-in-configuration-file-ubuntu-usb-boot/")

to fix a small bug... takes 30seconds.

The installation is slow and often looks stuck, but just let it run and answer the occasional question and you'll get there.

Thanks again.

---

