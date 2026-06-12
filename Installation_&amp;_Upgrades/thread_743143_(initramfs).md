---
title: "(initramfs) ???"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by comeonfeet on 2008-04-02
hello,

when i try to install linux via the cd, after a while it pops up in msdos mode and says 

(initramfs) 

not sure why,  i deleted my hard drives before installing linux could be because of that. I can also type stuff in so please help me!

would be much appreciated

---

### Post by wyth on 2008-04-02
Same problem after an upgrade from 7.10.  Looking into it now.

---

### Post by comeonfeet on 2008-04-02
> **wyth said:**
> Same problem after an upgrade from 7.10.  Looking into it now.

wow thanks for the speedy reply

---

### Post by Elijah.j on 2008-04-02
I am also getting the error. I'm trying to install xubuntu on my New lenovo thinkcentre mt/m 8807-a77. It has a stat hdd and slimline cdrom. 

I have tried to install ubuntu live cd and alt. also xubuntu and its alt cd. 
every time i get this error. 

pci cannot allocate resource region 7 of bridge 0000:00:1c.0 
after that it brings up a busybox prompt that says
initramsfs ata2.00:failed to set xfermode err_mask=0x4
then just repeats that once more and freezes.

---

### Post by wyth on 2008-04-02
I rolled back to 7.10 last night and tried again today. I wasn't sure what exactly went wrong, because I walked the dogs during the upgrade, and my wife logged me off before it was done. I thought the problem resulted from that. Reinstalled, booted, same busybox initramfs issue.

Have to remember, though, that we're still in beta here.  I'm not worried about this issue  eventually being worked out; the machine I'm having trouble with is a Dell 530n that came with Ubuntu pre-installed, so I know it's going to be supported.  

That said, it may be worth heading over to Launchpad and checking in on any bug reports, and submitting one if there isn't an existing bug report.  If the developers don't know about the issue, they won't be addressing it.

---

### Post by wyth on 2008-04-02
Some similar bug reports:
[LIST]
[*][Hardy will not boot after upgrade]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/205757")
[*][Boot fails (to busybox) when using raidtools (8.04)]("https://bugs.launchpad.net/ubuntu/+bug/208474")[/LIST]Seems it may have something to do with sata drives.  Also, I'm curious if its a kernel issue; was anyone able to boot into a previous kernel after the upgrade?

---

### Post by Elijah.j on 2008-04-02
I have never installed ubuntu on my lenovo befor so i have not been able to try anyother kernals. although i did try a xubuntu cd burnt when 7.1 first came out and then one brunt just today. both of them give the same problem.

---

### Post by blokkendoos on 2008-04-03
Hello,

Get busybox in 7.10 with kernel 2.6.22-14-generic.

But can work in 7.10 with kernel 2.6.20-16-generic

There are sata-ports on the motherboard, but they are not in use.

Would love to know a solution.

tia
pabl k

---

### Post by Elijah.j on 2008-04-03
I was able to get xubuntu 6 to install but it was stuck in 640x480 and no osund or networking. 
then i put in the xubuntu 7.1 cd and tried safe gfx mode and it somehow worked. i am typing this on the live cd while its intalling. i will post back if it worked or not.

---

### Post by Elijah.j on 2008-04-03
Installed just fine. but will not boot in to xubuntu.

---

