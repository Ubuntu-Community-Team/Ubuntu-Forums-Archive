---
title: "How can I install Kubuntu over Ubuntu using a live cd?"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by wersdaluv on 2007-05-09
I already have Ubuntu Feisty installed. Now, I want to install Kubuntu over it.

I have with me a CD of Kubuntu Feisty. Can I use the Kubuntu Live CD to install the Kubuntu desktop over Ubuntu? If so, how?

---

### Post by janga on 2007-05-09
If you have a fast internet connection, you dont need the Live CD.
Just type in
```
sudo apt-get update && sudo apt-get install kubuntu-desktop
```If you dont, start synaptic and unselect all internet sources, so that the CD-Rom is the only the source . Then do the same as above.

---

### Post by wersdaluv on 2007-05-10
I currently have a very slow internet connection so I want to use the live CD instead. I tried what you told me, but kubuntu-desktop is not available in synaptic even if I added the Kubuntu CD as a software resource.

What do I do?

---

### Post by zvacet on 2007-05-10
You can not install kubuntu-desktop from live CD.You need alternate CD to do that.other option is to go to the **synaptic>edit>mark by task** and chek kubuntu-desktop.That will download it via net.

---

### Post by Shinobi326 on 2007-05-10
Is there any danger in botching your Ubuntu desktop/settings?

I finally have Ubuntu to the way I like it but I am curious about Kubuntu and how that would work and function.  Is there a way to boot into either desktop?

---

### Post by roon on 2007-05-12
Shinobi after you install Kubuntu you'll find the Kubuntu ( KDE ) option in the logon screen.

---

