---
title: "Deleting one of 2 Kernels installed?"
date: 2006-09-22
forum: Installation &amp; Upgrades
---

### Post by Spankmaster79 on 2006-09-22
Hi,

I recently used the Software-update Tool of Xubuntu and accidently included linux-386 version 2.6.15-27 and linux-image-386 in it. I did have 2.6.15-26 before. 

I didn't want to update and now I have 2 Booting options in the GRUB. Either one of the kernels. They both boot fine but I don't need them actually. I only want to keep the 2.6.15-26

Also why is the Software-update Tool giving me the option of linux-386 version 2.6.15-25 when this should be older than 2.6.15-26

So now I want to deinstall 2.6.15-27 in Synaptic so I choose the paket linux-image-2.6.15-27-386 that should be removed and dependencies are linux-386, linux-restricted-modules-386 and linux-restricted-modules-2.6.15-27-386.

Can I savely do this? It tells me no version on linux-386, that's what is making me think.... :confused: 

Greetz
spanky

---

### Post by carontis on 2006-09-22
I think you can remove one of twos, but remember it's a safe idea to keep at least your new kernel and the last one (working) that you were using before. If one day you'll get trobles, you'll have possible chance to boot from the old one.

---

### Post by wieman01 on 2006-09-22
I have done it once as well and I have not had a problem since. So I consider it safe... just to give you some comfort.

---

### Post by Spankmaster79 on 2006-09-22
thx, it helped. It only deinstalled what it should!!!

---

### Post by wieman01 on 2006-09-22
> **Spankmaster79 said:**
> thx, it helped. It only deinstalled what it should!!!
Great! Actually I haven't tried before but the comfort DID help, didn't it? ;-)

---

