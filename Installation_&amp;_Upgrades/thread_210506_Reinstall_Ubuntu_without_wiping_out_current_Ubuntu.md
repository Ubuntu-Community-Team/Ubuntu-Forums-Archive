---
title: "Reinstall Ubuntu without wiping out current Ubuntu partition?"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by kuriharu on 2006-07-07
Hi,

I had an great install of Ubuntu working until I foolishly tried to install XGL. I've learned my lesson and won't try that again, but now that I've f---ed up Ubuntu and I need to reinstall it (apparently, installing XGL screws up OpenGL).

On top of that, my wireless doesn't work AGAIN. OpenGL is messed up AND wireless is dead. Rather than spend 3 weeks getting wireless to work like I did the first time, I figure I'd just reinstall Ubuntu from scratch. 

Can I reinstall Ubuntu without destroying the current partition? Or do I just save my documents and go back to *sigh* Windows?

---

### Post by Athropos on 2006-07-07
Do you have your /home mounted on a different partition ? If so, you may reinstall Ubuntu over your current installation. You just have to tell the installer to not touch the partition with your documents, and to tell it to mount it at /home.

If you have only one partition for your whole Linux system, then it's time to correctly partition your disk :)

---

### Post by fluxam on 2006-07-07
I sympathise with the plight because I, too, had similar misfortune after attempting to install XGL. 
[I've also had weird problems making Ubuntu use the UAC3553B for my USB-connected Philips mini stereo. In fact, it froze so hard a few minutes ago while connecting that I had to remove the battery. (After a restart with "startx," the mini stereo worked and seems, for the moment, to be okay.)]
If it is critically important to set up a different partition for /home , then that should be how the installation procedure defaults. Ubuntu is supposed to protect novices!
I also would have liked to be able to scrape GRUB out of the drive so I could do a fresh Windows install and then use Partition Magic, with Boot Magic as the boot manager. Is there any tool to do that?

---

