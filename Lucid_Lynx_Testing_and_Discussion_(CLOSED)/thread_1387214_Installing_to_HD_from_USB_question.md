---
title: "Installing to HD from USB question"
date: 2010-01-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by the.scarecrow on 2010-01-21
I have been using Lucid Alpha 1 and now Alpha 2 by booting from a USB I created from the .iso. I have set aside 1.8GB for updates and configuration changes I make and then I use it as much as I can to see if I can find any problems to report with it.

So far its all working 100% for me, this helps build my confidence using Ubuntu and perhaps I will start to be able to report bugs in the future.

On my Hard Drive I use Karmic (no problems here either). My question is when I install Lucid to the Hard Drive from the USB, will I get a basic installation or will I get an installation including all the configuration changes I have made?

For example I will have installed Skype, gPodder, restored all my Evolution Mail data, Firefox bookmarks and restricted-extras. All working fine when I boot from the USB so will that all be included on the HD installation when I do it?

I'm just curious, thanks for your help. Also is this form of testing from the USB of any help to the developers were I to find anything to report?

---

### Post by VMC on 2010-01-21
> **the.scarecrow said:**
> ... My question is when I install Lucid to the Hard Drive from the USB, will I get a basic installation or will I get an installation including all the configuration changes I have made?

For example I will have installed Skype, gPodder, restored all my Evolution Mail data, Firefox bookmarks and restricted-extras. All working fine when I boot from the USB so will that all be included ...
Great question. I only use DVD-RW , I wouldn't know, but if it does restore what you have installed I may have to use USB installs.

So when you boot up using that USB does it show the menu as the DVD/CD - LiveCD, Install, etc?

Interesting question, hopefully someone that has used the USB install will know more.

---

### Post by the.scarecrow on 2010-01-21
> **VMC said:**
> Great question. I only use DVD-RW , I wouldn't know, but if it does restore what you have installed I may have to use USB installs.

So when you boot up using that USB does it show the menu as the DVD/CD - LiveCD, Install, etc?

Interesting question, hopefully someone that has used the USB install will know more.

Yes, when I boot with the USB in, all the initial options are the same as booting from the CD-R .iso, it boots much faster too. I use a 4GB USB and its a fantastic feature, almost as good as having Lucid on your HD.

---

### Post by the.scarecrow on 2010-01-21
There is one point I just remembered. If you do the updates they can make the USB un-bootable so you have to re-format and create the USB. This happend to me once when I did all the updates so I excluded all the recommended updates and just did the main ones. However, I suspect even these could break the USB.

---

### Post by C.S.Cameron on 2010-01-21
The kernel on a persistent flash drive is frozen, not easy to change.
All the changes on the drive are saved in a file named casper-rw. 
In your case casper-rw is about 1.8 GB in size, when it gets full you can't write to it any longer. updates will fill it quickly. Kernal items that are updated can not be flushed.
If it gets filled, you do not have to reformat, You can delete casper-rw and install a new one from another flash drive or download one from pendrivelinux.com

If you use it to install Ubuntu to a hard drive only the original info is installed, nothing from casper-rw is installed.

---

### Post by the.scarecrow on 2010-01-22
Thanks for your very helpful and informative reply C.S.Cameron. The information you have provided will help me a lot in the future.

---

