---
title: "VirtualBox vs VMWare: Which is better any why?"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by kspn on 2007-06-29
Hi

I have been using VMWare on my WinBlows PC for a while and I have a couple of VMs that I need to keep using but I was wondering if anyone could give me a definitive comparison on the differences between these two virtualisation products.

I am willing to convert if one is better than the other but I need a compelling reason that is different to 'Virtual Box is better than VMWare'

If anyone can help it would be appreciated.

I am currently using VMWare Server and I like the fact that it runs as a complete background task. I have seen no errors or faults with the implementation. (and the face that the Server is free is also a bonus)

Thanks

---

### Post by jackmc on 2007-06-29
I have found virtualbox far easier to use. Eveything worked straight away - didn't need to set up internet, and can share files with Ubuntu fairly easily.

I switched because something screwed up in VMware and ruined my XP..

---

### Post by kspn on 2007-06-29
> **jackmc said:**
> Eveything worked straight away - didn't need to set up internet
What do you mean by this?
I have never had to setup anything special in my VM's.

---

### Post by litemotiv on 2007-06-29
i've tried a number of VM's so far, including:

Vmware Server
Vmware Player 1/2
Qemu
KVM/Qemu (1:16-1)
Virtualbox 1.4

both the vmware products demanded a lot of resources from my computer, i never got them to work for a while without seeing the swap file increase eventually (core2duo e6600 / 2GB). the overall perfomance of both is good, though it does seem to have a sense of 'lagginess' now and then (maybe because of it's swapping). guest-os startup and shutdown time is also quite long, and they're big installs (vmware player 1 was already around 100mb, player 2.0 around 170mb -- i think).

qemu runs pretty good, but has some definite shortcomings in video support. kvm's virtualisation speed is still not really up to par, and video support is dramatically poor there (the latest version for instance hasn't got support for the --std-vga setting which you need for higher screen resolutions). it's still a young project and it certainly shows potential, but at the moment i don't consider it to be useful enough. if native kernel support has been improved in time and the drivers are streamlined i'll surely try them again. the open source aspect makes prety aimable and the install sizes are tiny compared to the others, also for the lack of an extensive gui/frontend. 

and then virtualbox 1.4, wow, it blew my mind! awesome performance (feels nearly native), easy to use, excellent 'tools' package with good video support, a built-in filesharing protocol for guest/host mapping, instant snaphsots etc. etc. at this moment, i would say virtualbox definitely is the way to go if you want easy, fast and stable VM'ing. package size is a bit bigger than kvm/qemu, but still small compared to the vmware products. 

(btw, i tried all with the same guest-configurations; win xp pro with 256/384/768/1024 memory.)

one thing i still need to figure out about virtualbox though is how i can prevent it from stealing certain key-combinations. left-alt+click for instance, which i use all the time in photoshop, seems to be captured and redirected instead of giving back the proper action. if anyone has a suggestion how to fix this i'd definitely be interested. ;)

edit: i just found out that disabling mouse integration seems to be a workaround

---

### Post by reanjr on 2007-09-20
In regards to your mouse issue:

It is probably your Window Manager intercepting the Alt-click, not VirtualBox.  In many Window Managers Alt-click-dragging allows you to reposition a window without moving the cursor all the way to the title bar.  By disabling mouse integration you allow VirtualBox to take control of the mouse so your Window Manager doesn't intercept it.  Try disabling that feature in your Window Manager and see if that works for you.

---

### Post by olieviya on 2007-09-27
> **reanjr said:**
> In regards to your mouse issue:

It is probably your Window Manager intercepting the Alt-click, not VirtualBox.  In many Window Managers Alt-click-dragging allows you to reposition a window without moving the cursor all the way to the title bar.  By disabling mouse integration you allow VirtualBox to take control of the mouse so your Window Manager doesn't intercept it.  Try disabling that feature in your Window Manager and see if that works for you.

Thanks for that, do you have any idea how to disable this in KDE since it seems to me to be built (Move Window) in as in Keyboard Shortcuts it's not assigned a key, I can assign it a key and then I have Alt and the new key-combination working at the same time.:confused:

---

### Post by Stever22 on 2007-12-15
I have tried both VMware server and Virtual Box under Ubuntu.

Here is a good article:

[http://steveit.ca/2007/12/15/virtualbox-vs-vmware-server-under-ubuntu/](http://steveit.ca/2007/12/15/virtualbox-vs-vmware-server-under-ubuntu/)

---

### Post by ericesque on 2007-12-15
I have tried VMware and Virtualbox.  My experience was much better with Virtualbox.  Definiley faster, more intuitive, and ...well, it worked.  In VMware, I was able to install after a number of attempts.  Then as soon as I clicked anything in XP (as guest), it crashed.

Could be me, but I think I gave VMware it's fair chance to work-- and it really didn't want to.

---

### Post by JangMunho on 2007-12-15
Virtual Box doesn't support dual-core, so only one core of my core 2 works.
Virtual Box cannot use a physical hd. That means I cannot install linux on a mobile hard disk easily by Vbox.

Vmware is good enough, but seems everytime after I compile the kernel myself, it won't run.

Virtual machine is nothing...

---

