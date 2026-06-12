---
title: "How to add another Linux distro to grub"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by Roberto Rosselli on 2006-08-21
Hi guys,
I'm trying to add another Linux distro (Mandriva) to grub, so that I can dual (well, triple considering XP) boot my box. I could use LILO coming with Mandriva but I want to retain Ubuntu as my primary distro, so please help!

I have a separate /boot partition, this is how my second hd looks like:

/dev/hdb1       /boot
/dev/hdb2       [Ubuntu]
/dev/hdb3       [Mandriva]

and this is the entry (based on the "normal" Ubuntu entries) I added to /boot/grub/menu.lst:

title		Mandriva 2007 beta 2
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-2mdv root=/dev/hdb3 ro quiet splash
initrd		/boot/initrd-2.6.17-2mdv.img
savedefault
boot

Needless to say, it doesn't work so far ](*,) The error message says "Error 15: file not found". Can someone tell me what I'm doing wrong? Thanks in advance.

Roberto

PS A frontend to GRUB, like Mandriva's one, would be most useful ...

---

### Post by Drakkor on 2006-08-21
Yeah, I'm basically trying to do the same , boot Ubuntu,XP, and Damn Small Linux, check this out: It's 3 pages though

[http://www.ubuntuforums.org/showthread.php?t=238988](http://www.ubuntuforums.org/showthread.php?t=238988)

---

### Post by Roberto Rosselli on 2006-08-21
Thanks for the link Drakkor, I'm trying to sort out all the information listed there :) I suspect that the root and/or kernel entry could be wrong, but can't spot the error ...

Roberto

---

### Post by Roberto Rosselli on 2006-08-21
OK, now this is beginning to become scary: I followed the instructions in the excellent tutorial on grub ([http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)) to use the CLI interface and discover more about my hd setup, but when I try a simple find I get this:

[INDENT]grub> find /vmlinuz

Error 15: File not found

grub> find /boot/vmlinuz

Error 15: File not found[/INDENT]

So I tried to specify the hd:

[INDENT]grub> root (hd1,0)

Error 21: Selected disk does not exist[/INDENT]

I wonder what's up with my setup ... help! ](*,) ](*,) ](*,) 

Roberto

---

### Post by Herman on 2006-08-21
Roberto, there are two or three different types of these grub prompts, like : ```
grub>_
``` One kind of grub prompt is the one we get when we are first booting our computer up, and we press our 'c' key from our grub menu instead of waiting until it boots Ubuntu.
Another kind of grub prompt is when we have Ubuntu running already and we open a terminal and type, ```
grub
``` That give us a grub shell, but it isn't a very good grub shell, it can't really do very much. that's the one that gives us the > error 15: File not found And then there's the grub shell we get when we type, ```
sudo grub
``` That kind of Grub shell is a lot more effective. A lot more commands will work properly.

 The CLI grub prompt I think you mean from the web-page that I was illustrating is the first one, the one we get by typing 'c' from a grub menu.
This can also be from a grub menu in [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php") too.

>  title        Mandriva 2007 beta 2
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.17-2mdv root=/dev/hdb3 ro quiet splash
initrd        /boot/initrd-2.6.17-2mdv.img
savedefault
boot That looks okay to me, Roberto, if you are doing something wrong, it's probably something small and hard to spot. Just ry again from the grub prompt and see how you go.

If you still have trouble, please include in your next post, a copy of your output from ```
sudo fdisk -lu
``` Regards, Herman :D

---

### Post by Roberto Rosselli on 2006-08-21
Herman,
many thanks for your explanation, indeed all worked fine after I removed the /boot prefix from the kernel and initrd entries. Mandriva beta doesn't seem to be working well, but that's another story ;)

Ciao!

Roberto

---

### Post by Drakkor on 2006-08-21
Hi,Herman,lol,you seem to be the boot go to guy,lol :D 
Anyway, I changed my boot menu.lst to this, and still get an error 15
"File not found" I really don't know what the kernel and initrd should look like. In fact I have no initrd at all ! Check out Damn Small linux at the bottom. Thanks ! :p 

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

title           Damn Small linux
root            (hd0,6)
kernel          /boot/linux24 root=/dev/hda7 
boot

---

### Post by Herman on 2006-08-22
```
 title           Damn Small linux
root            (hd0,6)
kernel          /boot/linux24 root=/dev/hda7 
boot

``` Hello, Drakkor, mine booted with those commands I gave in a previous post, for booting dsl from Grub CLI, I did test it a few times before posting the commands for you.  dsl doesn't seem to have any initrd.img,  I guess it doesn't need one.  Mine has some extra  options after the  kernel  command in menu.lst though. They didn't seem to be necessary  for me to boot from command  line, but they are in dsl's own grub menu's dsl entry. Maybe try adding those and see if it helps. If not, better check again that you have the right partition numbers, and are not having any syntax errors, although, what you posted looks okay to me. Just try with these extra options as shown below, I have added these to my Ubuntu grub's menu.lst and have booted dsl with it.
```
 title           Damn Small linux
root            (hd0,6)
kernel          /boot/linux24 root=/dev/hda7 quiet vga=normal noacpi noapm nodma noscsi frugal
boot
```I have tested this and it works for me. Good luck with it, and all the best, Drakkor, Regards, Herman :D

EDIT, Drakkor, did you do a dsl 'debian' style install, or a dsl 'frugal' style install? Mine's the 'Debian' style one, in case it makes any difference. :D

---

### Post by Belyel on 2006-08-23
I had sucess adding a SUSE distro to my GRUB loader.  The kink I had was that I installed SUSE on an external drive.  Here's the code that finally worked for me:

```
title SUSE Linux 10.1
root (hd1,3)
kernel /boot/vmlinuz root=/dev/sdb4 vga=0x314 resume=/dev/sda3 splash=silent showopts
initrd /boot/initrd
```

With similar code for the failsafe, but with the options turned off.  I have four partitions on the external drive, one each for media, backups, and other stuff.  Pain in the neck, but with a little tinkering I finally got it.

---

