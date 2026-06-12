---
title: "How do I get grub to run a second grub"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by Noob Programmer on 2010-03-24
This is the largest problem I have with running multiple OS. I have Windows, Ubuntu, and Fedora installed. I don't have any trouble getting grub to find and boot windows. I do however have trouble with ubuntu and fedora. 

Ubuntu was installed before Fedora. I currently want to keep my Ubuntu install so I can't reinstall it at the moment. I just recently installed Fedora 12 replacing an OpenSuse install. During the install it recognized Ubuntu had a bootloader. Besides that, it completely ignored it.

So at the moment Fedora is my primary grub. I am completely capable of manually entering the Ubuntu root and kernel. This has become a serious pain, since I will have to do it after every Ubuntu update. I some how had my previous OpenSuse install to simply redirect to the grub to the Ubuntu partition and would run Ubuntu's grub. This was nice since it allowed a tree like structure to the bootloader and could select the appropriate kernel after selecting the OS. Unfortunately, I've lost how I did that during the install of fedora. At this point I am wondering if anyone knows how I could set that up again, OR explain in full detail how to get grub to automatically add the other OS kernels into the one grub list. I would personally like the first option. I did enjoy the tree like structure. But, at this point I just want something that will work and can easily reproduce if I ever find myself doing a 3 OS install again.

I've already tried the following from the grub on (hd0,3):
```
title Ubuntu
        rootnoverify (hd0,5)
        chainloader +1
```

I can't remember the exact wording but it says that it can't find the file it is looking for and returns me to the grub menu. I know it is the correct partition since I can directly boot with this:
```
title Ubuntu
        root (hd0,5)
        kernel /boot/vmlinuz-2.6.31-20-generic root=UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx ro quiet splash
        initrd /boot/initrd.img-2.6.31-20-generic
```

But that is what I would have to insert manually since I don't know how to get the Fedora grub to read the Ubuntu grub.

Any ideas?

---

### Post by pebo on 2010-03-24
Your ubuntu grub was probably written to (hd0) and was overwritten by fedora. If you haven't changed your ubuntu /boot/grub/menu.lst you could try putting```
title Other Linux
root (hd0,5)
configfile /boot/grub/menu.lst

```in your fedora menu.lst
(That's assuming your ubuntu boot isn't on a separate partition). 
This way fedora grub should read ubuntu grub.
hth ;)

---

### Post by Noob Programmer on 2010-03-24
Thanks that is exactly what I was looking for.

---

