---
title: "/etc/lilo.conf file not found in ubuntu 11.04"
date: 2011-06-20
forum: Installation &amp; Upgrades
---

### Post by sunandi on 2011-06-20
Hi everyone,
I am trying to install kernel 2.6.39.1 on ubuntu 11.04

I am fllowing this link 
[http://www.sysdesign.ca/guides/linux_kernel.html](http://www.sysdesign.ca/guides/linux_kernel.html)
But may this link is little old

It mentions a file /etc/lilo.conf to edit but this file is unavailable.

Can anyone point me where I can find this file 
or 
if the page which I mentioned is old then can anyone give me the link which guides me correctly abt how to install kernel 2.6.39.1 in ubuntu 11.04?

---

### Post by coffeecat on 2011-06-20
A *little* old? It's prehistoric. :wink:

Having said that, I'm surprised that even in 2004, the author of that page didn't consider that many people would be using a distro that used grub rather than lilo.

Whatever, if you really want to compile your own kernel, here are a couple of Ubuntu documentation links for you to look at:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

[https://help.ubuntu.com/11.04/installation-guide/i386/kernel-baking.html](https://help.ubuntu.com/11.04/installation-guide/i386/kernel-baking.html)

But if all you want is the 2.6.39 kernel in Natty, you will find it a lot easier to enable the [kernel-ppa repository]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/"). If you want to do this, open a terminal, and:

```
sudo add-apt-repository ppa:kernel-ppa
sudo apt-get update
```Don't upgrade with apt-get upgrade from the terminal because for some reason it holds back the 2.6.39 packages. Instead, open Synaptic, click on "mark all upgrades", and then "apply". It will install the 2.6.39.0 kernel, not the -1, but that's what I'm running on my Natty, and it seems fine. Now reboot and you will be using the 2.6.39 kernel.

---

### Post by luvr on 2011-06-20
> **coffeecat said:**
> Don't upgrade with apt-get upgrade from the terminal because for some reason it holds back the 2.6.39 packages.
To overcome this issue, you should do an **apt-get dist-upgrade** instead; that's the action that *Synaptic* takes as well.

---

### Post by sunandi on 2011-06-20
Thanks Coffeecat for suggesting this

But why Ubuntu is having a different way of installing and compiling a kernel?

---

### Post by coffeecat on 2011-06-20
> **luvr said:**
> To overcome this issue, you should do an **apt-get dist-upgrade** instead; that's the action that *Synaptic* takes as well.

Thanks for that. Yes, that explains it. :)

> **sunandi said:**
> But why Ubuntu is having a different way of installing and compiling a kernel?

I'm not sure I understand what you mean. The kernel you get from the kernel-ppa repository is pre-compiled for you. It's no different from the standard repository one in that respect, except that it's a later version.

The links I posted differ in the details from what you found, but the essence of compiling a kernel is the same.

---

### Post by sunandi on 2011-06-26
Hi CoffeeCat,
How will I get to know that which FLAVOR I have to build?
amd64 or i386?

Output of :
sunandi@ubuntu:/host/linux_views/natty_priv/sunandi_view1$ uname -a
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

I think i386 but still confirming, excuse me if I am asking supremely stupid question, quite new to this 

Thanks

---

### Post by dino99 on 2011-06-26
deb=compiled

---

### Post by luvr on 2011-06-26
> **sunandi said:**
> Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 **x86_64 x86_64 x86_64**

Since the output says *"x86_**64**"* that would be amd**64.**

---

### Post by sunandi on 2011-06-26
Hi All,
Thanks a lot for your responses.
I am following [http://blog.avirtualhome.com/2010/11/06/how-to-compile-a-ubuntu-10-10-maverick-kernel/](http://blog.avirtualhome.com/2010/11/06/how-to-compile-a-ubuntu-10-10-maverick-kernel/)
to comple kernel 2.6.38-9.43.

But it is failing while executing command:
[COLOR=#007800]skipabi[/COLOR]=[COLOR=#c20cb9]**true**[/COLOR] [COLOR=#007800]skipmodule[/COLOR]=[COLOR=#c20cb9]**true**[/COLOR] fakeroot debian[COLOR=#000000]**/**[/COLOR]rules binary-branch_1
branch_1 is my git branch.

Can anybody give me some pointers about how to debug this?

---

### Post by sunandi on 2011-06-26
last few console prints
[B]run-parts: executing debian/tests/README
run-parts: failed to exec debian/tests/README: Exec format error
run-parts: debian/tests/README exited with return code 1
run-parts: executing debian/tests/check-aliases[/B]
Checking for dupe aliases in branch_1...
              aes_x86_64 / aesni_intel          : aes
          twofish_x86_64 / twofish_generic      : twofish
              aes_x86_64 / aes_generic          : aes
          salsa20_x86_64 / salsa20_generic      : salsa20
     ghash_clmulni_intel / ghash_generic        : ghash
                   viafb / vt8623fb             : pci:v00001106d00003122sv*sd*bc*sc*i*
               carminefb / mb862xxfb            : pci:v000010CFd0000202Bsv*sd*bc*sc*i*
                 tpm_tis / tpm_infineon         : acpi*:IFX0102:*
                 tpm_tis / tpm_infineon         : pnp:dIFX0102*
                radeonfb / radeon               : pci:v00001002d00007835sv*sd*bc*sc*i*
                radeonfb / radeon               : pci:v00001002d00007834sv*sd*bc*sc*i*
                radeonfb / radeon               : pci:v00001002d00005D57sv*sd*bc*sc*i*
                radeonfb / radeon               : pci:v00001002d00005C63sv*sd*bc*sc*i*
........................................................................................................................
........................................................................................................................
........................................................................................................................
........................................................................................................................
........................................................................................................................
              snd_oxygen / snd_virtuoso         : pci:v000013F6d00008788sv000013F6sd00008788bc*sc*i*
                 dm_raid / dm_raid45            : dm-raid5
                 dm_raid / dm_raid45            : dm-raid4
              r8192e_pci / r8192se_pci          : pci:v000010ECd00008192sv*sd*bc*sc*i*
make: *** [install-branch_1] Error 1

How to know whats going wrong?

---

### Post by mörgæs on 2011-06-26
First of all, why do you want to compile? I would not recommend it for a beginner (and actually, after using Ubuntu since release 5.10 I have never had the need myself).

---

### Post by sunandi on 2011-06-26
Hi morgeas,
I have to do it someday....... :-)
So started now.

Thanks,

---

### Post by luvr on 2011-06-27
> **mörgæs said:**
> First of all, why do you want to compile?

Perhaps he simply wants to learn?
Like you, I haven't had to compile a kernel ever since I started to use Ubuntu, but I do remember the early Slackware days, when compiling your own kernel was often essential to get all hardware components operational. While it may initially be a frustrating experience, compiling your own kernel and getting it right does eventually give you a sense of achievement.

---

### Post by sunandi on 2011-06-27
But I think with Ubuntu it looks fairly simple, but unfortunately I got stuck in this issue.
Also, I dont know how and where to look when a kernel compilation fails

---

### Post by mörgæs on 2011-06-27
All respect for learning, but if you want to find out the inner workings of a Linux distro, Arch might be a better choice. People in the Arch community are used to building it all from scratch.

---

### Post by oldos2er on 2011-06-27
> **sunandi said:**
>  I dont know how and where to look when a kernel compilation fails

Try the packaging and compiling subforum.

---

### Post by sunandi on 2011-06-28
Tons of Thanks to TOZ... who forwarded me this remarkable link to compile kernel and load.

[http://parabing.com/2011/04/28/ubuntu-natty-a-custom-kernel-is-what-you-want/](http://parabing.com/2011/04/28/ubuntu-natty-a-custom-kernel-is-what-you-want/)

Only thing which is left now is to build a specific version of kernel and building my own module and load it to kernel.... this sounds interesting !!!

I realized one thing though that this is definitely not difficult with Ubuntu :-)

---

