---
title: "No boot stuck at (initramfs) BusyBox v1.18.5 Ubuntu 12.04"
date: 2012-07-20
forum: Installation &amp; Upgrades
---

### Post by Reneme on 2012-07-20
I am getting stuck at (initramfs) prompt. Not able to boot.

I searched some threads, it said to enter 'exit'.
After i did that, boot process started, but all commands were having '/root/...' prefix and 'No such file or directory' messages.
Then it went back to the (initramfs) prompt.

OS: Ubuntu 12.04 minus libreoffice, docs, translations, games.. (removed using Ubuntu-builder)

---

### Post by darkod on 2012-07-20
Try running boot-repair from live mode:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can run the recommended repair, or only create the bootinfo results and post the link it gives you so we can take a look. After we see the bootinfo we can suggest a solution.

---

### Post by Reneme on 2012-07-20
I cannot reach the desktop using the custom iso, it is stuck on (initramfs), so cannot run script. :(
How to fix the booting, i choose wizard mode while making the iso using ubuntu-builder.[http://code.google.com/p/ubuntu-builder/](http://code.google.com/p/ubuntu-builder/)

---

### Post by darkod on 2012-07-20
I am not  familiar with any custom ISOs, so can't help you there.

But to simply run the bootinfo you can use the standard cd booted in Try Ubuntu (live mode running from the cd). That can help you investigate if your custom cd doesn't boot.

Maybe the custom cd is not made correctly?

---

### Post by Reneme on 2012-07-20
> **darkod said:**
> 
Maybe the custom cd is not made correctly?

I am also thinking that may be the case. I am total newbie in making custom Ubuntu live iso.

Just installed ubuntu-builder and gave it a try.
Removing unwanted stuff, dramatically reduced the size. Its only ~200mb now, after remove libreoffice,ubuntudocs,gnomedocs,translations,games.

I used wizard mode as i dont know much about it. Was hoping someone here might help in fixing it or suggest different app for customizing.

---

### Post by drs305 on 2012-07-20
Since you have removed packages from the normal initial build it will be very difficult for us to know how to fix it. The best option as stated would be to boot a LiveCD, install Boot Repair and run the info script. Even then the part that is broken is probably not Grub but some missing package, but if it is a Grub problem this would give us the best chance of fixing it.

If you have to burn a new CD for this, you might try Boot Repair's own CD or even its [Secure Remix]("https://help.ubuntu.com/community/UbuntuSecureRemix") version.

---

### Post by Reneme on 2012-07-20
> **drs305 said:**
> Since you have removed packages from the normal initial build it will be very difficult for us to know how to fix it. 
The best option as stated would be to boot a LiveCD, install Boot Repair and run the info script. Even then the part that is broken is probably not Grub but some missing package, but if it is a Grub problem this would give us the best chance of fixing it.

If you have to burn a new CD for this, you might try Boot Repair's own CD or even its [Secure Remix]("https://help.ubuntu.com/community/UbuntuSecureRemix") version.

If you mean booting original ubuntu live cd, then i think there is no point in that. How will that fix the custom iso i made. Although, i have no problem re-doing in other method or other customization software, as i have original ubuntu iso.

I hope someone who has customized a ubuntu iso comments here.

---

### Post by drs305 on 2012-07-20
> **Reneme said:**
> If you mean booting original ubuntu live cd, then i think there is no point in that. How will that fix the custom iso i made. Although, i have no problem re-doing in other method or other customization software, as i have original ubuntu iso.

I hope someone who has customized a ubuntu iso comments here.

It wouldn't help your custom ISO. However, if the ISO did produce a workable OS and it was only a Grub issue, Boot Repair would fix it. The odds are that the ISO needs reworking, as I posted earlier.

---

### Post by Reneme on 2012-07-20
> **drs305 said:**
> ..The odds are that the ISO needs reworking, as I posted earlier.

yup, it needs reworking. i used wizard method of ubuntu-builder.
Need reply from someone who has customized ubuntu iso with ubuntu-builder or any other software.
I will give the manual method a try.

---

### Post by klingo on 2012-09-03
Hi, i am having the same issue with 12.04. I've run the boot-repair script with no help, so at least it generated the boot info:
[http://paste.ubuntu.com/1183571](http://paste.ubuntu.com/1183571)
I think i got in to the situation by installing fglrx drivers (and optionally some updates) from xorg-edgers ppa (or uninstalling them?) and tried various thing because this was also a problem. I have already tried everything possible, including hints from forums, etc... I will try to list things i've tried:
1. uninstall fglrx & reinstall xserver-xorg-video-ati & radeon
- these worked for a while but then it broke again
2. booted the older kernel versions
And this worked too for a while. I think it worked exactly one boot and then when I tried to fix the situation, it only broke iniramfs with this kernel version). This is how i broke all four kernels available
3. I booted to Ubuntu 11.10 on another partition, or Live CDs, chrooted to the broken install, reinstalled/uninstalled various packages including kernel images, video drivers, ran grub-install
4. I tried to boot with kernel options irqpoll, root=(dev name not by UUID)
5. I tried the boot-repair gui app, for repairing boot, including the "purge old kernels then reinstall the last" option (or similiar)

And more ... :(

Occassionally, a strange thing happens, that some of my HDDs, like /dev/sdc where the broken linux is, is mapped to /dev/sdg instead. But that wasnt a problem for a long time, because my permanent mounts in fstab are by UUID and worked fine.

Please help

EDIT:
Now I've tried 
dpkg-reconfigure -phigh -a
but nothing happened for about 10 minutes

---

