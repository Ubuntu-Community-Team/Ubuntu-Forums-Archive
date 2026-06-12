---
title: "install lockups"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by vividvew on 2007-02-27
I am a longtime Gentoo user trying to get edgy up and running. No I'm not jumping ship to Ubuntu but am looking for a bit more of the fit and finish in the desktop department.

My problem is that the GUI environment on the livecd locks up randomly for the 32 and 64 bit versions of edgy. No kernel panic. No messages. Just hard lockup of all input and output. ctrl-alt-backspace and ctrl-alt-del are both unresponsive. The amount of time before lockup varies but is reproducible every time. Once I got  it to work long enough to get edgy installed but then had the same problem in the installed environment.

I was hoping someone who know of an issue and a workaround for my setup. I read something about Ubuntu kernels having problem with SMP systems and thought it might be related but couldn't be sure.

I tried the same version of the kernel in Gentoo(obviously w/o all the options used by edgy) and did not have any problems.

Hardware:
Asus K8N-DL bases on Nvidia Nforce4
2x opteron 252
4x 512 OCZ ddr400 registered
Nvidia 7300 LE PCI-express

Let me know if there are any details left out that I should include and thanx. 

-vividvew

---

### Post by vividvew on 2007-02-28
No one. This does not speak well to my first attempt w/ Ubuntu, the distro that is supposedly taking over the world as easy to use linux. 

I am not a newbie who is causing himself problems. I don't know if there are many Gentoo people running around these forums, but trust me if nothing else we tend to know what we are doing. 

I have tried 6.10 23bit and 64bit kernels, 6.06 32 bit kernel. I tried the nv driver w/ and w/o glx and dri enabled. I have also tried the nvidia driver w/ and w/o dri and glx enable in the xorg.conf. 

Always the same problem. Random lockups  in X windows. I can't find any useful output in any of the relevant log files. /var/log/messages shows no helpful errors. /var/log/Xorg.0.log also shows nothing useful and no errors other than some font and stylus crap, I have no stylus and my fonts look fine so.... 

I have none of these problems in Gentoo or Fedora or elive. I sooo do not want to use Fedora as my desktop distro. Coming from Gentoo, dependency hell is just not something I will deal with. Elive is not ready for prime time yet so, that leaves me with Ubuntu.
Any one?

---

### Post by Kateikyoushi on 2007-02-28
I used gentoo as well, generally apt as easy to use as ports so you will like it, once you get it up and running which might not take as long as gentoo. Personally on my notebooks and even the desktop edgy and feisty works out of the box.
I often see these hard lockups on similar systems, your best bet is to use the alternate install cd which runs in text mode and after the core system is up install the desktop environment.

---

### Post by vividvew on 2007-03-01
Thanx for the reply. Unfortunately I have tried the alternate install. I can get the system installed w/o errors using text install but then I have the same problems in my installed environment as the install cd. Hard lockup in X windows. no warning.

---

