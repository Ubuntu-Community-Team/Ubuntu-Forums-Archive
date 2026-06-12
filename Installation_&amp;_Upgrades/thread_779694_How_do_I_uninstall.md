---
title: "How do I uninstall"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by Malikius on 2008-05-02
Unbuntu software and keep my Windows XP Pro. I have it on 3 other computers and I need to get access back to my Windows XP without the boot up prompt asking me to pick an OS. 

Eagerly awaiting an answer. :KS

---

### Post by LeoSolaris on 2008-05-02
So long as you installed it properly and you can boot into XP from Grub, all you have to do if you're in Ubuntu is mount the partition XP is on and you will have access to your files. If you need Windows to run at the same time Ubuntu is running use VMware or something similar to make a virtual instance of Windows. Just note that is a virtual instance, so gaming doesn't work. Search the forum for VMware for a how to, I am sure there is at least one.

Leo

EDIT: Oh wait you want to remove Ubuntu...   sorry it's late and I did not read it throughly. Ya know, if you still want to keep Ubuntu, you can edit grub's menu.lst so Windows boots without asking. (leaving you 5 seconds or so to hit ESC to pick Ubuntu.

Just Use:

```
sudo gedit /boot/grub/menu.lst
```

To completely remove Ubuntu from a system, put the Live CD back in and go to GParted (or qparted if your using Kubuntu) From there just delete the partitions and expand XP back to fill the space. As for restoring the MBR... Hopefully someone else can help ya there. You should be able to do it with XP's install CD, just tell it to repair. At least I am fairly sure that should do it, I have never had to so google it just to be safe

---

### Post by Malikius on 2008-05-10
Thanks man I appreciate the help. I want to have Ubuntu on the computer in the kitchen, only. I need to use my laptop (computer in question) to have only XP Pro on so I can travel with it. Still love Ubuntu's OS but I want to have that at home. Also, can you guide me to where I can use the VNC Linux and Windows so I can control any computer with it running from the internet please? VNC and RDP is confusing to me still.

---

