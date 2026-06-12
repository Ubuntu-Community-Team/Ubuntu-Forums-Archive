---
title: "Burning ISO results in errors"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by xvedejas on 2008-03-01
I've twice tried to burn an iso for Ubuntu 7.10 desktop edition. The first time I was able to boot the live CD but two error windows came up (asking me if I wanted to delete something?) and clicking the "Install" on the desktop would do nothing. The second time I couldn't even start the live cd; there was an error when trying to open the kernel and it said I needed to reboot.

I tested the CD's for defects; they both had errors.

I've burnt the exact same thing on another computer and it worked perfectly. I wondering what might be wrong with my cd drive that isn't letting me do this. I followed the burning ISO guide using infra-recorder (again, I've done this successfully on another computer).

Any more information:

When I burned an ISO last time, it was at a significantly slower write speed. On this computer, for some reason, the only option in Infra Recorder was maximum speed. Could this be the cause of the errors?

I'm using 700MB CD-R's; same as when I got it to work on another computer.

Any help appreciated.

---

### Post by overdrank on 2008-03-01
> **xvedejas said:**
> I've twice tried to burn an iso for Ubuntu 7.10 desktop edition. The first time I was able to boot the live CD but two error windows came up (asking me if I wanted to delete something?) and clicking the "Install" on the desktop would do nothing. The second time I couldn't even start the live cd; there was an error when trying to open the kernel and it said I needed to reboot.

I tested the CD's for defects; they both had errors.

I've burnt the exact same thing on another computer and it worked perfectly. I wondering what might be wrong with my cd drive that isn't letting me do this. I followed the burning ISO guide using infra-recorder (again, I've done this successfully on another computer).

Any more information:

When I burned an ISO last time, it was at a significantly slower write speed. On this computer, for some reason, the only option in Infra Recorder was maximum speed. Could this be the cause of the errors?

I'm using 700MB CD-R's; same as when I got it to work on another computer.

Any help appreciated.

Hi and yes the speed could cause the errors. Have you tried and use the cd you burned on the other system to install with?

---

### Post by xvedejas on 2008-03-01
> Hi and yes the speed could cause the errors. Have you tried and use the cd you burned on the other system to install with?

Yes; I was installing with a friend. He scratched up the CD so bad there's no way it will work again.

---

### Post by xvedejas on 2008-03-01
Is there any way I can get Infra Recorder to let me record at lower speeds? Because there is no option here but there was on my friend's computer...

---

### Post by xvedejas on 2008-03-01
Would trying the alternate install CD do anything?

Keep in mind I'm trying to dual-boot with Vista.

---

### Post by overdrank on 2008-03-02
> **xvedejas said:**
> Would trying the alternate install CD do anything?

Keep in mind I'm trying to dual-boot with Vista.

I would doubt it,  if you burn another cd and it checks with errors again then you may want to try another cd burner.

---

### Post by xvedejas on 2008-03-02
I tried burning on the only other computer I have access to. Infra recorder seemed to mix up its two drives (the one that burns was letter E but it said it was D), and when I put a disk in the correct drive it said there was none there. No luck still.

---

### Post by Pumalite on 2008-03-02
Download ImgBurn: [http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Install it.
Go to Mode>ISO>Burn

---

### Post by xvedejas on 2008-03-02
Okay, the CD now seems to work. The problem is this; when the partition manager thing comes up, there is no guided option! The only choices are "use entire disk" and "manual". Why is this? What do I do?

---

### Post by Pumalite on 2008-03-02
Go Manual; in the space you have:
10 GB for '/'
1 GB for /swap (in laptops, /swap=RAM)
The rest for /home
Then press 'Forward'

---

### Post by xvedejas on 2008-03-02
before I attempt it, how exactly do I do this? Is there a guide online I could print?

---

### Post by overdrank on 2008-03-02
> **xvedejas said:**
> before I attempt it, how exactly do I do this? Is there a guide online I could print?

Hi and this may help
[https://help.ubuntu.com/community/WindowsDualBoot#head-3e767efbc5271731d48fb40918ad5a0d85b3655d](https://help.ubuntu.com/community/WindowsDualBoot#head-3e767efbc5271731d48fb40918ad5a0d85b3655d)
And also this link
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by xvedejas on 2008-03-02
For some reason this time guided did appear. But trying to resize using guided or manual resulted in this error window: "An error occurred while writing the changes to the storage device".

what is wrong here? I'm going to go ahead and check this disk for errors.

---

### Post by overdrank on 2008-03-02
> **xvedejas said:**
> For some reason this time guided did appear. But trying to resize using guided or manual resulted in this error window: "An error occurred while writing the changes to the storage device".

what is wrong here? I'm going to go ahead and check this disk for errors.

Hi and I have heard that some users having to resize vista from within vista.

---

### Post by xvedejas on 2008-03-02
I tried once more and it worked. huh.

Anyways, I have a new problem. It doesn't really fit under installation, but you can find it here;

[http://ubuntuforums.org/showthread.php?p=4442714#post4442714](http://ubuntuforums.org/showthread.php?p=4442714#post4442714)

---

