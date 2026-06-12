---
title: "Installing Windows"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by BloodyDream on 2012-12-29
I'm giving my old desktop to my mom, and I want to install Windows 7 and replace Ubuntu with it. SO I basically want no trace of Ubuntu on it haha. Should I clear Ubuntu off of the drive beforehand? Or will Windows replace it during the installation? It shouldn't be difficult, but I want to make sure that I do it correctly.

---

### Post by darkod on 2012-12-29
Windows does not recognize linux partitions correctly, but it can see them as partitions that are there.

You can simply start the win7 install and at the partitioning step, delete all current partitions and create the new ones as you wish. So, no need to do anything in advance.

You can always boot ubuntu cd in live mode and use Gparted to delete all partitions, but as I said there is need for it. It's up to you.

---

### Post by HBurd on 2012-12-29
I'm also going to be installing Windows over Ubuntu. When you say "delete all current partitions" do you mean absolutely every one or is there some essential one that should be left. 

I know this is quite likely a dumb question, but I just want to confirm since I don't know much about partitions and I don't want anything to go wrong.

---

### Post by gnush on 2012-12-29
Do you want to completely wipe the hard drive, not leaving any trace of anything? If so, I'd suggest using *dd* or *badblocks*.

If you don't care about that, you should be able to just fire up the Windows 7 installer and let it format and partition the hard drive for you.

---

### Post by darkod on 2012-12-29
> **HBurd said:**
> I'm also going to be installing Windows over Ubuntu. When you say "delete all current partitions" do you mean absolutely every one or is there some essential one that should be left. 

I know this is quite likely a dumb question, but I just want to confirm since I don't know much about partitions and I don't want anything to go wrong.

If you want to completely remove ubuntu and install windows on the whole hdd, that answers the question for you. For a windows only system you don't need any of the linux partitions.

---

### Post by HBurd on 2012-12-29
Thanks, that's just what I need to know.

---

