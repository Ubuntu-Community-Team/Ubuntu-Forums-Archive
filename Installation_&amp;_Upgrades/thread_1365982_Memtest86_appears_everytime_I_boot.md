---
title: "Memtest86 appears everytime I boot"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by Noobie101 on 2009-12-27
I installed Ubuntu from my harddrive. When finished, it told me to restart.

 After restart the memtest86 appears. 

At first I waited until it reach 100 on the top "pass" and say "no error" then it started to run the test again so I press the ESC and make it restart but after restart it keep coming back to Memtest86 and I coulndn't get into Ubuntu or Window.

Help please!:confused:

---

### Post by buccaneere on 2009-12-27
Memtest86 is a boot entry in boot/grub/menu.lst

Without knowing any better, I'd be guessing that it has been selected as the default boot option.

See my menu list:


> title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=c750b94d-415d-4015-8d90-54500d601b5d ro quiet splash
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=c750b94d-415d-4015-8d90-54500d601b5d ro single
initrd		/boot/initrd.img-2.6.24-25-generic



title		Ubuntu 8.04.3 LTS, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c750b94d-415d-4015-8d90-54500d601b5d ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c750b94
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=c750b94d-415d-4015-8d90-54500d601b5d ro quiet splash
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=c750b94d-415d-4015-8d90-54500d601b5d ro single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=c750b94d-415d-4015-8d90-54500d601b5d ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet


title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=c750b94d-415d-4015-8d90-54500d601b5d ro single
initrd		/boot/initrd.img-2.6.24-23-generic


[COLOR="Red"]title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
d-415d-4015-8d90-54500d601b5d ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet[/COLOR]

---

### Post by Noobie101 on 2009-12-27
Ok. I see how last two have the word point to memtest rather than karnel.
Then what should I do? How do I get the menu list like that?

---

### Post by Noobie101 on 2009-12-28
The grub didn't load and since I can't find any discussion about this problem so I decided to use window cd to override the boot sequence which worked but halfway  because I can get into window but there are other problems.

First since I did a couple steps of window installation just to fix the boot sequence. Therefore there is another list of Window(incomplete installation) that I have to find and delete.

Second I think I went wrong at some point during installation so Linux end up took all my backup partition and which is now swap space for ubuntu that I can't use plus all my backup files were in there. No hope I guess.

Third at the moment I haven't get into the unetbootin menu to get into ubuntu yet (since it still say unetboot so that means ubuntu is not installed yet right? So the installation failed?)

Well, I didn't backup any files so it will be a pain if I lost everything. I just hope I get everything back for now.(Fortunately I can get my window back):(

---

