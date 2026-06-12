---
title: "Unable to use 22.04/24.04 on OracleVM"
date: 2024-05-18
forum: Installation &amp; Upgrades
---

### Post by beldeun on 2024-05-18
I'm not able to use either of the aforementioned versions on Oracle.

Should I be fortunate enough to install it, it either won't load (Black screen), or bring me to the login page where it freezes.

As of this time, however, I cannot even get as far as successfully creating a VM.

The only change I have made since then was removing and reinstalling OVM multiple times.

Also, I've done the same with the image itself to no avail.

Have not come across this within the last year with Ubuntu 22.04 or Kali (Earlier version, I believe).

Additional steps taken:
Max out video memory (128 MB)
Adjust base base memory a bit (32 GB system atm)
Disable/Enable 3D Acceleration

Allocated two CPU cores each time as well.

Any insight would be much appreciated.

---

### Post by MAFoElffen on 2024-05-18
<<This thread would do better if moved to the Virtualization section, where there are mebers using and supporting Oracle VirtualBox.>>

I can't speak on recent VirtualBox from either Oracle Repo's or the VirtualBox Repo from Ubuntu specifically... As I changed over to KVM in 2010, and supported VB users only up until 2017. That is when I stopped using and teaching people how to use VirtualBox. I let others support recent VB versions now. That is unless no one steps up, and I can see someone deserves and needs a response. I mostly support KVM , and VMware Virtual hosts now.

There, in the Virtualization Section of this Forum, are many Members there who use VB with Ubuntu (or other Hosts), of both sources, using Ubuntu (or other Distro or OS) VM's. 

I can report, they I haven't seen anyone report recently (within the past 3 months) of anyone having troubles with any Ubuntu VM's in VirtualBox. But you are.

On basic VM allocations, if your host has 128GB RAM, that makes it simpler for VB. It is more of a challenge on limited host resources. For example, if you only had 8GB RAM, VB would occasionally get a memory allocation error on boot of the VM, where it is looking for contiguous memory to allocate that is free in a single contiguous block, from start to finish. I will mention that the more memory you allocate for a VM, the hrader it is for VB to find those contiguous blocks free to allocate them.

This error in VB, is specifically with VB and how they allocate resources in their code... It doesn't happen with other VM Hosting systems.

So lets hear some details about if the VM installs from the Installer or not. If is does install, but the error occurs on booting the VM after the install. Or if the VM fials and gets and error after boot while running.
 
And what are the specific on-screen errors and/or the specific errors in the VB VM run logs, of why it crashes. For the ones that you said "if I was fortunate enough for it to install"... On the ones that didn't, what were the specific errors, and what did it show in the install logs.

---

### Post by &amp;KyT$0P# on 2024-05-20
What 22.04 iso are you using and what kernel version does it have?

---

### Post by Rick St. George on 2024-05-20
This should be moved to VIRTUALIZATION: However, this is what he will get ...

> 
I would do everything in your power to move off VirtualBox. You're adding substantial security risk to your data and systems by using it. Don't believe me? Just see [https://www.cvedetails.com/vulnerability-list/vendor_id-93/product_id-20406/Oracle-Vm-Virtualbox.html]("https://www.cvedetails.com/vulnerability-list/vendor_id-93/product_id-20406/Oracle-Vm-Virtualbox.html")


Retreived from my Posting regarding same issue! [See Here]("https://ubuntuforums.org/showthread.php?t=2497347")

So ... Forget VirtualBox! We have to find another alternative, and those like me who put years into it, have to start over.
But ... will it work if we REMOVE SNAPS ?!?!?

---

### Post by MAFoElffen on 2024-05-20
Sidenote: 

I had been using and supporting VirtualBox for years. Well, using it up until about 2014, Supporting it up through 2017 with my Computer Science students (back then). It... well, it works most of the time, for what it is.

In 2010, I migrated most of my servers and test cases to KVM. That showed me what I didn't know I was "missing" before, and "could do" that wasn't possible before that. It opened doors and then there were so many possibilities that I could do. 

I'm not going to bad-mouth VirtualBox. It is what it is. It does have some limitations. It does have some challenges in how they decided to do some things. But for most people, they don't need "more"... And they need user friendly that they can pick up and use today, without having to learn a lot about what they want to do.

KVM does require learning a few things to use it.

Back to the OP--- Still waiting to hear more info and details.

---

