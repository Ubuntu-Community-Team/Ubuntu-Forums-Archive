---
title: "Ubantu Installation alongside windows"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by prajwalnp on 2012-02-17
I have windows 7 and I installed ubantu windows installer to run ubantu alongside the windows. It worked for a while and later on when I tried to load the ubantu, it would not run the ubantu on my system as it used to freeze. Then, I uninstalled the ubantu from the windows control pannel and tried to reinstall. Everything went right except when it asked me for the reboot and I reboot the system to complete the installation process, it says:

Completing the ubantu installation. For more installation boot options, press ESC now...

I didn't do anything!

Then the timed count from 5 ended to 0 and the installation froze! 

Thats it! I can't complete the installation and can't use the Ubantu. 

I forcefully turned off my dell inspiration and again selected the ubantu and this time I pressed ESC to try other options as safe more and others but non of them worked. some of them got frozed after loading up untill:

[7212532] [Firmware Bug]: ACPI (PEGP) defines _DOD but not _DOS

Now, I'm just selecting windows at the boot and using the windows. 

When I used to use the Ubantu, I had many pictures saved in a folder on the desktop. But i unstalled that instance of Ubantu. Does that mean I deleted the folder too? is there any ways that I can recover the files from the previous windows ubantu and how do I get the ubantu running alongside the windows?

Thank you very much!

---

### Post by Bucky Ball on 2012-02-17
Welcome. 

Firstly, it is UBUNTU, not Ubantu. ;)

Sounds like you are going for a Wubi install (inside Windows) rather than a full install to a separate partition(s) on your hard drive. Wubi install is for trying Ubuntu to see how you like it. It is slower (and different in many ways) than a hard drive install and not intended as a permanent solution. 

To install *alongside* Windows, you need to download the desktop (or alternate) install ISO (the LiveCD), make a bootable CD from that then restart the machine and boot from the install CD. There are lots of how-tos online to help you with this. Try googling 'Ubuntu windows dual boot'.

I am presuming if you deleted your Ubuntu Wubi install (and related folders) you have also deleted any files which might have been in those folders. You could try some recovery methods but wouldn't know what as not familiar with Wubi installs, presuming that's what you had.

If you know the name of one of your lost files perhaps do a search for it in Windows and see if it turns up. Good luck. ;)

---

### Post by QIII on 2012-02-17
Strangely enough, phoronix did some testing and found Wubi installs to be faster in some ways.  In some cases much faster.

I stopped using the speed recommendation.

It's a strange world.

---

### Post by Bucky Ball on 2012-02-17
> **QIII said:**
> Strangely enough, phoronix did some testing and found Wubi installs to be faster in some ways.  In some cases much faster.



New one on me and certainly not my experience (or that of many others), but haven't tried it for nearly five years so who knows. Link please. ;)

PS: Would depend on *many* factors. ;)

Back to the OP's original issue ...

---

### Post by QIII on 2012-02-17
On my cell on the train home right now, so can't look it up.  I read the article late last week or early this.

Surprised the heck out of me.

Edit:  I just googled "wubi fast phoronix".  Article is from Oct or Nov 2010.

Edit again:

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=1)

Some a little slower, some about the same.  But Wubi flat spanks in database transactions.  However, read the last line or two.  They did the tests on a fresh Win 7 install -- so the disk was relatively unfragmented.

---

### Post by prajwalnp on 2012-02-17
Thank you....It helps...i'm preparing a CD now! Thanks for your help :)

---

### Post by QIII on 2012-02-17
Just so you understand -- I'm not recommending a Wubi install.  The benefits of a real partition installation outweigh a bit of speed (with a caveat in the article) in a couple of areas.

I don't recommend a Wubi install if you are serious about using Ubuntu indefinitely.

---

### Post by bcbc on 2012-02-17
When you uninstall a Wubi install, it permanently removes the virtual disk (root.disk) so any files you had while in Ubuntu are gone (unless you copied them to the /host or some other /media you mounted). If it was on the Desktop then they're gone.

I don't know of any reliable way to recover these files after deletion.

You need to avoid hard shutdowns - it's not good for any OS and can lead to corruption. It's particularly bad with Wubi. Try [Alt+SysRq R-E-I-S-U-B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot") instead.

---

### Post by prajwalnp on 2012-02-18
I did what you said but, only my laptop is acting weird! First, I created a Ubuntu CD and tried to run with the CD making the CD as first boot device. The system was black it froze again. Then later, I created my external HD as a boot for Ubuntu. Luckily it run through. I chose to run Ubuntu from the External HD. It started loading many files until it stopped forever at:

[7212532] [Firmware Bug]: ACPI (PEGP) defines _DOD but not _DOS

My laptop is DELL Inspiration17 R which I just bought 3-4 months ago. Is it my laptop problem? I'm very surprised with the way I'm not being able to run Ubuntu on my laptop only!

Thank you in advance!

---

### Post by prajwalnp on 2012-02-18
I did what you said but, only my laptop is acting weird! First, I created a Ubuntu CD and tried to run with the CD making the CD as first boot device. The system was black it froze again. Then later, I created my external HD as a boot for Ubuntu. Luckily it run through. I chose to run Ubuntu from the External HD. It started loading many files until it stopped forever at:

[7212532] [Firmware Bug]: ACPI (PEGP) defines _DOD but not _DOS

My laptop is DELL Inspiration17 R which I just bought 3-4 months ago. Is it my laptop problem? I'm very surprised with the way I'm not being able to run Ubuntu on my laptop only!

Thank you in advance!

---

### Post by Bucky Ball on 2012-02-18
What release are you running?? 10.04 LTS (the most stable), 11.10? You might want to try 10.04. 

Try this. Boot from the CD and when you get to the screen with the options (first screen) hit F6 (from memory) and choose 'acpi=off', then install. Give that a go. ;)

I have had a search and doesn't seem like that model has much info with Ubuntu. Maybe too new. If you try 'Try Ubuntu' from the first options when you boot from CD (if you can get to that screen) does it work ok from the CD?

---

### Post by prajwalnp on 2012-02-18
I used Ubuntu 10.10. I will try Ubuntu 10.04 and let you! Thanks!

---

