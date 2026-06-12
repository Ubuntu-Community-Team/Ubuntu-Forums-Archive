---
title: "How install the Alternate without cd drive ?"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by lolobuell on 2008-05-01
Hi,

I've got an old pc without cd drive and I would like to install Ubuntu Alternate on it.
I've got a usb key but I only find how to install the live cd with it but not the alternate cd.
Please help me :)

---

### Post by jamesstansell on 2008-05-01
The trick is to mount the iso file in loopback mode.  Then you could copy them to your usb key, run the install directly, or even add the files to Synaptic.

I don't have any links handy, but let me look though my history.

Here are the three commands I used last week to upgrade my 7.10 to the 8.04 RC.  In hindsight it might have been wise to add ",ro" to the -o option, to make the mount read-only.

$ mkdir /tmp/hardy
$ sudo mount ubuntu-8.04-rc-alternate-i386.iso /tmp/hardy/ -o loop
$ sudo /bin/sh /tmp/hardy/cdromupgrade

There's a blog posting from someone named Phil, I think in New Zealand, around 2006 about how to add a loopback mount to Synaptic sources.  I'd have to look it up if you're interested.

Regards,

-jim.

---

### Post by lolobuell on 2008-05-01
Thanks for your answer.
So I just have to download the alternate iso, tape these 3 commands and that's all ?

---

