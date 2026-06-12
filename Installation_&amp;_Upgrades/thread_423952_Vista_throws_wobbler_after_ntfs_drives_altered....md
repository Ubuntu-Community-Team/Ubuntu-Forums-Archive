---
title: "Vista throws wobbler after ntfs drives altered..."
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by quark_77 on 2007-04-26
Hi All,

I've been using ntfs-3g drivers to dual boot for a while now (in their beta form on edgy) with Windows XP. I have recently made two upgrades, Edgy>Feisty and XP>Vista. Here's the dilemma. I decided I needed more space for Linux, so I fired up gparted, wiped out an empty partition (backed up) and rebooted. Now here's the problem - Vista doesn't seem to like my fiddling. I've read the warnings about not using NTFSIX on Vista so I haven't, nor am I using anything from ntfsprogs. I have one other ntfs drive that has been used on ntfs-3g, do I need to format this one too in order to boot Vista again? I'd rather not have to re-install it and unfortunately I need a few Windows apps that don't work under wine... So basically, can I rescue my Windows install?

Thanks in advance for your help!!

Quark_77

---

### Post by quark_77 on 2007-04-26
Last time I had this problem I solved it by deleting my C: drive using gparted and reinstalling but I really don't want to have to do that...

Once again, thanks for any advice.

---

### Post by quark_77 on 2007-05-11
From what I have found out there isn't a workaround to this - aka don't use ntfsfix on vista drives and don't mess with them until vista-compatible ntfs changes are available. Re-installed by the way.

---

