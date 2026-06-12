---
title: "update-initramfs: Generating /boot/initrd.img-2.6.36-020636-generic hangs"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by Bloemetjesgordijn on 2010-11-01
Hi guys,

I just removed a proprietary (fglrx ) driver which didnt work out well.

Now all my updates hanging on: 

Setting up initramfs-tools (0.98.1ubuntu6) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-2.6.36-020636-generic (2.6.36-020636.201010210905) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.36-020636-generic

And I dont know how to solve it...besides a clean install.

Please help

---

### Post by Bloemetjesgordijn on 2010-11-02
BUMP 

pls can anyone help me

---

### Post by Bloemetjesgordijn on 2010-11-04
help......pls anyone??

---

### Post by Bloemetjesgordijn on 2010-11-06
I did a: 
sudo dpkg --purge --force-all linux-image-2.6.35-22-generic

started synaptic, and in broken packages tried to fix it...didnt solve it.

Please help. I allready did a re install / clean install

---

### Post by brdhse1 on 2011-01-20
Same problem here, no idea how to fix it.  Anyone?

dpkg.log ends with this:
011-01-20 20:40:54 startup packages configure
2011-01-20 20:40:54 configure initramfs-tools 0.98.1ubuntu6 <none>
2011-01-20 20:40:54 status half-configured initramfs-tools 0.98.1ubuntu6
2011-01-20 20:40:54 status installed initramfs-tools 0.98.1ubuntu6
2011-01-20 20:40:54 status triggers-pending initramfs-tools 0.98.1ubuntu6
2011-01-20 20:40:54 trigproc initramfs-tools 0.98.1ubuntu6 <none>
2011-01-20 20:40:54 status half-configured initramfs-tools 0.98.1ubuntu6

---

### Post by brdhse1 on 2011-01-27
Please help.  I've spent hours googling this problem, and though there are countless people posting this same problem, I haven't been able to find a solution.

Again, upgrading the latest kernel (2.6.35-25) hangs with:
> 
Unpacking linux-image-2.6.35-25-generic (from .../linux-image-2.6.35-25-generic_2.6.35-25.44_amd64.deb) ...
Done.
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic


And all subsequent attempts to run an update end with this:
> 
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-image-2.6.35-25-generic but it is not installed
E: Unmet dependencies. Try using -f.



Things I have tried:
1) sudo dpkg --purge --force-all linux-image-2.6.35-25-generic
2) sudo apt-get -f install
3) sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-25-generic; however:
  Package linux-image-2.6.35-25-generic is not installed.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.25.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-generic
 linux-generic

4) Everything in this thread: [http://ubuntuforums.org/showthread.php?t=1357523](http://ubuntuforums.org/showthread.php?t=1357523)
5) And this thread:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?p=8522143](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=8522143) 


I'm desperate.  Please help.

---

### Post by timsdeepsky on 2011-01-27
Sadness....
I had a similar problem with Maverick not booting and having the initramfs problem,,a week ago....After a lot of searching i could only fix it with a complete re-install....

---

### Post by brdhse1 on 2011-01-28
More attempts to fix this:

6) sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic

Interestingly, this hangs and fails to update even the current kernel.

7) Everything on this site: [https://ubuntugenius.wordpress.com/2010/05/24/fix-a-failed-initramfs-update-do-it-before-you-reboot](https://ubuntugenius.wordpress.com/2010/05/24/fix-a-failed-initramfs-update-do-it-before-you-reboot)

---

### Post by brdhse1 on 2011-01-29
I gave up on this and decided to go through the pain of a clean install.  I put the 10.10 x64 disk in, and installed on a new partition.  The box booted fine after the install, so I started the update manager to apply all the updates.  

The clean install hangs on on the update-initramfs when installing the 2.6.35-25 kernel!

Sweet.  Anyone out there with any ideas?

---

### Post by timsdeepsky on 2011-01-29
Maybe hang out with 10.04 until 11.04 comes out..??..I wish i could help you more....

---

### Post by brdhse1 on 2011-02-11
Fixed it.

Found the solution here:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421)
Though the description doesn't match exactly with my problem.

To summarize the steps:
1) Edit /etc/initramfs-tools/initramfs.conf (sudo gedit /etc/initramfs-tools/initramfs.conf in the console) and change the line MODULES=most to MODULES=dep. 

2) Reinstall initramfs-tools and initramfs-tools-bin

Hope this helps someone else.

---

### Post by RSA-2010 on 2011-02-12
I'd found this thread after discovering to my shock and disgust that Ubuntu 10.10 wasn't able to install anything on account of dpkg.  The symptom was that in the Ubuntu Software Center an attempt to install would act like it was frozen, and cancelling would produce a message about dpkg being interrupted or somesuch and not being usable.

I tried some other maneuvers including sudo dpkg --configure -a as recommended by an error message in the command line.   That was useless and brought me to the dreaded "update-initramfs: Generating" hang up.   I also tried the various steps at the UbuntuGenius blog without success.

I'm on something of a hair trigger with Ubuntu.  10.04 was nothing but trouble and would find some new way to spew fail upon every reboot, and, while 10.10 has been a vast improvement (and I've also been much more delicate with it), Wine never worked out of the box.  So once it seemed that I was stuck in some sort of hell where I couldn't update or install anything, I was just disgusted and burned off a different distro and proceeded to install it in another partition.

But, it sucked, so I decided to see if Ubuntu would cooperate.  

Upon login, I tried installing something and got a new error.  

> Traceback (most recent call last):   File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 144, in _process_transaction     not self.is_dpkg_journal_clean():   File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 700, in is_dpkg_journal_clean     for dentry in os.listdir(status_updates): OSError: [Errno 2] No such file or directory: '/var/lib/dpkg/updates/'

This at least had the benefit of being different.

For kicks, I sudo'ed up and made the missing directory just to see what would happen.   I then did an apt-get update and apt-get upgrade and all of the sudden everything was back to normal, even across a restart, and I can install programs again.

So, Ubuntu is safe for another day.

---

### Post by CodigoMono on 2011-08-23
Hi all,

I recently had this problem on Ubuntu 10.10 and the kernel running at the time was 2.6.35-28; and update manager was trying to get up to 2.6.35-30.

I didn't write down exact error messages, but thought I would contribute my solution in case others need it:

The error was reported by  either dpkg or apt-get during the post-installation steps, along the lines of :

update-initramfs: Generating /boot/initrd.img-2.6.35-30-generic
E: /usr/share/initramfs-tools/hooks/fuse_utils failed with return 1.

I debugged it for a bit and found that fuse_utils needs /sbin/mount.fuse to exist; and it didn't on my system - not sure why, dno't care why.

I created a symlink in /sbin  for /sbin/mount.fuse to point to /bin/fusermount ... with
"cd /sbin; sudo ln -s /bin/fusermount ./mount.fuse"

After this I did "sudo apt-get install --reinstall initramfs-tools" ... and it completed successfully :-)

All seems good now.

---

