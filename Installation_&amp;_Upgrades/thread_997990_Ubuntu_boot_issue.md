---
title: "Ubuntu boot issue"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by kumorisenshi on 2008-11-30
I recently switched to ubuntu from xp. when i installed the upgrade to 8.1 the system wouldnt boot. I found that it was still trying to boot off of an older kernel version. If i switch it the then new version in the boot menu it is fine. Is there a way to make it boot on the newer version, and if not how do i safely remove the old kernel?

---

### Post by Herman on 2008-11-30
:) Normally when we get a new kernel, the script called update-grub will be run automatically and your new kernel will be detected and a new GRUB menu will be generated with the new kernel at the top of your list of Ubuntu entries.

You can always run update-grub from the command line,
```
sudo update-grub
```That should give you a new menu.list file with your latest kernel at the top of the list.

If you mean the selection bar in your GRUB menu is not automatically hilighting the item at the top of the list, (you needed to scroll up), then probably you or someone has changed the setting called 'default' in your /boot/grub/menu.lst file.
 [default]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc"). - set which O.S. will be booted automatically by the timer if no-one presses a key
If you read the above link it will explain to you all about how to use that setting.
Maybe you should replace number there after the word default with the word saved. 

You can go into synaptic package manager and uninstall old kernels, but that's not necessary for most people, they don't do any harm except for taking up a little bit of hard disk space. With the large hard disks most people have nowadays no-one would ever notice that little bit of hard disk space. Maybe if you are running Ubuntu in a 4 GB USB drive it would matter.
On the other hand, if they won't boot then they won't be useful to you so you can remove them if you like. 
Here's a link about that, [Remove Ubuntu Kernels You Don't Need]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/") - Tombuntu,  

If you still have trouble, please run 'sudo gedit /boot/grub/menu.lst' and post a copy of your menu.lst file here so someone can see what is needed to give you more help.

Regards, Herman :)

---

### Post by kumorisenshi on 2008-11-30
:guitar:Ok so when i looked i realized that it is loading the newest version. i am at work so i cant post the menu or the log, but when i go to the grub menu and load the previous version it runs fine. 8.10 wont load for some reason. When i go into the recovery mode it stops at one of the io ports and wont go any further. But it does fine on 8.04. Ill try to get the menu and the log posted when i get off duty. Thanks again

---

