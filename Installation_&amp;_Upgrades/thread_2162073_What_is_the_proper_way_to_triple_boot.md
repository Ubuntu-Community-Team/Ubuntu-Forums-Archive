---
title: "What is the proper way to triple boot"
date: 2013-07-13
forum: Installation &amp; Upgrades
---

### Post by gorellana09 on 2013-07-13
Hello folks,

I am currently triple booting Win Vista/Xubuntu 11.10/Linux Mint 15. Since I had been unable to update my Linux distros since Xubuntu 11.10 due to kernel problems with my laptop I had not bothered with this but now that I can I would like to update both my distros. The problem I have is that every time I install one distro, the grub2 from that distro takes over and breaks the boot splash screen from the other distro. So right now I have the grub2 from Linux Mint 15 and Linux Mint 15 splash screen come up on boot nicely, but now my Xubuntu 11.10 splash screen is broken I no longer get the nice splash screen, instead I get ugly text. I would love to install the latest Xubuntu 13.04 ontop of the existing Xubuntu 11.10 but I know thatt if I do so the nice beautiful splash screen from Linux Mint 15 will be broken. Is there a way to prevent this? I know this sounds like such a small issue however I am ocd and it drives me insane. Any help will be appreciated.

---

### Post by carl4926 on 2013-07-13
You can switch from one to the other easily. Boot to xubuntu and in a terminal do
```
sudo update-grub

``````
sudo grub-install /dev/sda

```

reboot and you will see xubuntu back in control

---

### Post by carl4926 on 2013-07-13
Only 11.10 is no longer supported of course
So no security patches!

Booting to Mint and doing the same thing will restore Mint control of grub

---

### Post by gorellana09 on 2013-07-13
Thanks for the reply Carl, that worked. I guess my question is if there is a way to do it when I install Xubuntu 13.04 this weekend so that I don't have to do this each time? I will be switching back and forth from Mint to Xubuntu a lot and I'd hate to have to see the ugly text on one when I boot into it.

---

### Post by carl4926 on 2013-07-13
> **gorellana09 said:**
> Thanks for the reply Carl, that worked. I guess my question is if there is a way to do it when I install Xubuntu 13.04 this weekend so that I don't have to do this each time? I will be switching back and forth from Mint to Xubuntu a lot and I'd hate to have to see the ugly text on one when I boot into it.

I'm not sure I understand.

Once you install Xubuntu, presumably over the older Xubuntu version you have, your new Xubuntu will take over grub and have a entry for booting Mint 15 too.

Personally I'd keep Xubuntu in control of Grub because the kernel will change in ubuntu distros, where it doesn't in Mint unless you override the default update settings.

But the verbose text that you are seeing, I don't get. It just stays pretty much black. But I though Mint 15 put a plymouth splash in place. Not sure.
But I'd try to stop worrying about it.

---

### Post by oldfred on 2013-07-13
Grub also remembers where to reinstall, so on a major update to grub code it will reinstall to sda's MBR.

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates, if you unchoose everything then the entry on where to reinstall should be blank:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by gorellana09 on 2013-07-13
Thank you both for your replies. I guess yeah my only problem is with the splash screen that I wish both splash screens would remain unaffected by grub but I guess what I am understanding is that there is no way to avoid this? I guess I will just have to learn to cope with it, will be hard given my ocd. :/

---

