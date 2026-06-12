---
title: "Kernel 2.6.26-4"
date: 2008-07-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by plun on 2008-07-15
Installed and works.... :)

- Sound OK

- nVidia.... works ! :KS

- Compiz OK


- Boot splash broken


- New entry for Grub, Last succesful kernel


Kernel description
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-intrepid.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-intrepid.git;a=summary)


Seems to be 2.6.26 final....


Thanks devs  !

---

### Post by Trueno22 on 2008-07-15
**compiz....................fails**

i can turn it on fine woble it a bit but eventually crashes. I don't notice when it does or what causes it.  No flicker or nothing just the spcial effects are gone.
[B]
bootsplash................fails[/B]

thought it was my setting changes in the startup manager that were causing it

---

### Post by Nullack on 2008-07-15
I noticed a bunch of SELinux binaries come in, AppArmor is still absent.....

I going to test if vga= works yet, not having high res TTYs is painful. I dont use the boot splash as I find it interferes with my testing observations on boot time.

---

### Post by plun on 2008-07-16
> **Trueno22 said:**
> 
[B]
bootsplash................fails[/B]

thought it was my setting changes in the startup manager that were causing it

I have tested with different vga values and screen resolutions without any luck. I am also using startup-manager

Bug report for this.

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/249037](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/249037)

---

### Post by autocrosser on 2008-07-16
My issue is that at times I have nothing--at times red & white + green & white alternating vertical lines--at times text-only with splash enabled & at times well-spaced white dots on the full screen.

Copied to the bug report.

I remember that this was typical during Edgy development.....

I have been working with variations of this bug for a while---take a look at:  [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662)
The only thing missing is the bios warnings I was getting during the -1 & -2 kernels.

---

### Post by plun on 2008-07-16
Ok,thanks


What is default values for /boot/grub/menu.lst

ro quiet splash vga=791   within mine


```
## ## End Default Options ##

title Ubuntu intrepid (development branch), kernel 2.6.26-4-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.26-4-generic root=UUID=ae6cb871-2fd7-490d-afb8-93b97a82fb3e ro quiet splash vga=791
initrd /boot/initrd.img-2.6.26-4-generic
quiet
```


Then you also have /etc/usplash.conf

```
# Usplash configuration file
xres=1024
yres=768
```

What more controls this.... ???

---

### Post by stari4ek on 2008-07-16
according to documents of v86d, which works in pair with uvesafb "vga=xxx" can't work at all. Cause this flag is for vesafb, which is absent in -3, -4 kernels.
I've tried flags from docs: video=uvesafb:xxxxxxxx, but it doesn't work too.

I think that we have to wait some comments from developers, about how it should work.

I've tried to tune uvesafb, according to documents, but didn't succeeded:
1. boot system without "vga=xxx" and "splash" in grub command to be able see boot messages
2. reload uvesafb module:
$sudo modprobe -r uvesafb && sudo modprobe uvesafb
3. if you check terminal now (Ctrl+Alt+F1) you'll find that its became blanked. as I understand it means that uvesafb start working.
4. now you can check /sys/class/graphics/fb0/modes for available modes for uvesafb
5. According v86d documents, You have to load module with next option:
mode=XXXX, where XXXX is mode from modes mentioned before.
or   use command for grub like:
video=uvesafb:XXXX,mttr:3,ywrap

ok. I've found suitable mode for me: 1280x800p-60, but I can't use it with direct mode loading nor with grub. 
Maybe, We need rebuild iniramfs with uvesafb?

Any ideas?


PS. and sorry for my bloody English.

---

### Post by plun on 2008-07-16
> **stari4ek said:**
> 

PS. and sorry for my bloody English.

Well, mine is even worse....):P


Thanks for including more facts !

---

### Post by Nullack on 2008-08-13
Hmmm the frame buffer bug has not gotten any love since:

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/246269](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/246269)

I note that Fedora is going kernel mode setting and using plymouth in Fedora 10.......

Whats the plan for Intrepid?

---

### Post by RAOF on 2008-08-13
> **Nullack said:**
> ...
I note that Fedora is going kernel mode setting and using plymouth in Fedora 10.......
...

When's Fedora 10 coming out?  Certainly, Intel kernel modesetting should work (at least by the time it's released), and maybe ATI as well.  But you can't rely on it being present in general; what about nvidia/matrox/$RANDOM_CARD?

---

### Post by Nullack on 2008-08-13
Hi there RAOF :)

[http://fedoraproject.org/wiki/Releases/10/Schedule](http://fedoraproject.org/wiki/Releases/10/Schedule)

[http://fedoraproject.org/wiki/Releases/FeatureBetterStartup](http://fedoraproject.org/wiki/Releases/FeatureBetterStartup)

Do you know what the plan is for Intrepid with having high resolution modes so I can more effectively use my TTYs in high res?

---

### Post by RAOF on 2008-08-13
Oh, right.  So !{intel, new AMD} gets a text-mode boot.  Fun.

The plan for us is, I believe, that uvesafb gets fixed at some point.

---

### Post by Nullack on 2008-08-13
Lovely, look forward to it mate, thanks.

---

### Post by FrancoNero on 2008-08-13
2.6.27 would be nice, too. to be on the edge... ;-( after all it's not LTS, so why  not go a step further...

---

### Post by zAo on 2008-08-13
2.6.26-5
Intel Video OK
Sound Intel HDA NOK!
> W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted


---

