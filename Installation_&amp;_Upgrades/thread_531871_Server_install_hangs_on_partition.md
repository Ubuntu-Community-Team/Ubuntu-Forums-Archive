---
title: "Server install hangs on partition"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by WhosRodney on 2007-08-22
Hello,
I'm trying to install 6.06 LTS server edition, but I'm having some trouble.  The install goes fine (it doesn't detect my onboard ethernet, but that's ok) until the partitioner is supposed to run.  But instead of the partitioner, it just gives me a blank screen.  I can kill the partitioner with Ctrl-C, and then the installer proceeds with the partitioner confirmation screen, though it doesn't show any partitions.

My system is as follows:
MSI K9AGM2 (AMD 960G chipset)
AMD 4200+ 64-bit X2 Dual core
1 80GB SATA hard drive
1 80GB IDE hard drive
1 IDE cd drive

Thanks for any help :)

---

### Post by kaens on 2008-07-17
I know this is an old post, but it's the first google hit for "ubuntu server hangs at partitioner", so I thought I'd chime in here.

You can see what's going on by hitting Ctrl-Alt-F2 , and then do a ps | more. partman is probably on there, and 

```

tail /var/log/partman

```

will tell you what the partitioner is up to. In my case, I had kept an external drive plugged in (500 gig) that I had used to do some backing up prior to install, and it was scanning everything on the drive. Stopping the process and rebooting with the drive unplugged fixed the problem for me.

---

