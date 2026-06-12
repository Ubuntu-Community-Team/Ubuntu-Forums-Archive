---
title: "Collecting kernels!"
date: 2005-11-27
forum: Installation &amp; Upgrades
---

### Post by adam.tropics on 2005-11-27
After a fresh install, upgrading to i686 then taking the update on top of that, I am left with 3 kernels! Should I remove the unused ones altogether or is it enough simply to edit grub and forget all about them!! I'm sure either would work, but is there a 'preferred method'??

---

### Post by 23meg on 2005-11-27
If you're not critically low on disk space, I'd suggest leaving them in place, at least for a while, since if you have trouble booting with one kernel at some point, you can try the others.

If you do want to remove them, just use apt-get / synaptic to do it.

---

### Post by adam.tropics on 2005-11-27
Good plan. Just wanted to be sure leaving them there wouldn't wreck anything, so thanks for the reassurance.

---

### Post by SickTwist on 2005-11-27
Do not manually remove them from the grub menu, though. They are listed in the section of the grub menu that is automatically manipulated when doing kernal installs/removals. Changing this part of the menu might confuse the program that does the parsing.

---

### Post by adam.tropics on 2005-11-27
I just did:

 sudo gedit  /boot/grub/menu.lst

and #commented out the entries I wanted it to ignore and all went well. I did I would have to admit, leave one 'spare' showing up, as to be honest I am fairly sure to mess it up again at some point!! (This install though i am armed with a notebook and pen! I have a bad habit of forgetting what I have changed when things go wrong......it helps!)

---

### Post by 23meg on 2005-11-27
Whenever you have to dpkg-reconfigure your kernel image or install a new kernel, you'll lose those changes. That's why I recommended doing it through apt. If everything fails you can still boot into recovery mode and download a new kernel image via apt. If you're not even able to connect to the net, you can use the CD to reinstall a stock kernel.

---

### Post by xyz on 2005-11-27
Hi-
I found this on [http://occy.net](http://occy.net)
Could a wise person tell me if this is the (or a) way to remove/purge/reinstall kernels?I still have "the old Hoary" kernel.Thank you.
> See what kernel images you are running:
dpkg -l linux-image\* linux-restricted-modules\* linux-headers\*|grep ^ii

Purge those kernel packages:
sudo aptitude purge linux-restricted-modules-$(uname -r) linux-image-$(uname -r)

Clean up /lib/modules:
sudo rm -rf /lib/modules/$(uname -r)

Now reinstall your kernel:
sudo apt-get --reinstall install linux-image-$(uname -r) linux-restricted-modules-$(uname -r) linux-headers-$(uname -r)

Now reboot your system...
sudo reboot

NOTE: This was using Ubuntu Hoary stable. Other distro's or versions of Ubuntu might not work. I'm sure it probably should work on most Debian/Ubuntu systems though.

Use at your own risk!

---

### Post by SickTwist on 2005-11-27
[QUOTE=adam.tropics]I just did:

 sudo gedit  /boot/grub/menu.lst

and #commented out the entries I wanted it to ignore and all went well. I did I would have to admit, leave one 'spare' showing up, as to be honest I am fairly sure to mess it up again at some point!! (This install though i am armed with a notebook and pen! I have a bad habit of forgetting what I have changed when things go wrong......it helps!)[/QUOTE]

It may be a better idea to play with the default options located near the top of menu.lst. This one looks like it may be what you could edit to display less kernels on the menu:

```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
```

---

### Post by SickTwist on 2005-11-27
[QUOTE=xyz]Hi-
I found this on [http://occy.net](http://occy.net)
Could a wise person tell me if this is the (or a) way to remove/purge/reinstall kernels?I still have "the old Hoary" kernel.Thank you.[/QUOTE]

System --> Administration --> Synaptic Package Manager

Search for "linux-image" (without quotes).

You'll see a list of kernels. The ones marked in green are installed. From here you can right click on a kernel and select "Mark for complete removal". Once you have identified all of packages you wish to remove, click "Apply". Synaptic may ask you if you wish to remove the modules that go with that kernel as well--this is OK so mark those to be removed also.

*Note: Be sure to leave at least one kernel installed in order to boot the system. There is a failsafe that requires you to type "Yes" in the terminal when trying to remove the currently running kernel but other than that check there is nothing preventing you from removing every kernel installed. If you do this accidentally, the system will run fine (until it's rebooted) so just be sure to have at least 1 kernel installed.

---

### Post by xyz on 2005-11-27
[QUOTE=SickTwist]System --> Administration --> Synaptic Package Manager

Search for "linux-image" (without quotes).

You'll see a list of kernels. The ones marked in green are installed. From here you can right click on a kernel and select "Mark for complete removal". Once you have identified all of packages you wish to remove, click "Apply". Synaptic may ask you if you wish to remove the modules that go with that kernel as well--this is OK so mark those to be removed also.

*Note: Be sure to leave at least one kernel installed in order to boot the system. There is a failsafe that requires you to type "Yes" in the terminal when trying to remove the currently running kernel but other than that check there is nothing preventing you from removing every kernel installed. If you do this accidentally, the system will run fine (until it's rebooted) so just be sure to have at least 1 kernel installed.[/QUOTE]


Thank you very much.I really appreciate!
I asked what  you thought about the [quote] because I'm trying to learn (among everything else) console a bit.

---

