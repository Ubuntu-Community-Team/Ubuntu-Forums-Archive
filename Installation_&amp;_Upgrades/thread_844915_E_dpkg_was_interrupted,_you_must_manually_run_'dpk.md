---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the p"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by jaxstraww on 2008-06-30
How would I correct the item below? I only run FAH on this box but it seems I have a corruption with an update?

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by iaculallad on 2008-06-30
> **jaxstraww said:**
> How would I correct the item below? I only run FAH on this box but it seems I have a corruption with an update?

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Open your terminal and re-issue the command below:

```
sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade

```

EDIT: One command line at a time.

---

### Post by jaxstraww on 2008-06-30
Thanks. I'll run it tonight and see what happens.

---

### Post by Dyffo on 2008-12-29
Hi there - did as you suggest - my system all works fine now . Thanks

---

### Post by marcus-guff on 2009-02-10
I'm a new ubuntu user as well and I ran into the same problem while trying to download software in add/remove applications. I'm pretty sure all of the installs failed and then it gave me the run 'dpkg --configure -a' message. 

So I did as was suggested above and went to the terminal and entered the command: sudo dpkg --configure -a

and this was the result that I got: 

> parse error, in file '/var/lib/dpkg/updates/0150' near line 1:
newline in field name '#padding'

I tried starting in recovery mode and running the dpkg repair thing in there, but no luck.

What do I do now? Please help! 

-very grateful for any help!

---

### Post by dvlchd3 on 2009-02-11
Try running the following command:

```
sudo apt-get -f install
```

If this does not solve the problem attempt running:

```
sudo dpkg --clear-selections
```
Then go back into Add/Remove applications and reinstall all the software you were attempting to install the first time.

---

### Post by ChannelZ28 on 2010-02-16
hi, i got the same error message after updating some files. i am very new to linux, how do i get into my terminal to run command lines? thanks.

---

### Post by Raydawggg on 2010-04-08
This is my First Post..."YAYEE ME!!" I'm excited to meet other Linux enthusiasts here.
Due to my impatience,i updated my 9.10 Stable to 10.04 LTS Beta 1. All went well until i tried 2 add/update my software. I got this error code: "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem." i opened a terminal & typed the command.....unfortunately this happened  


Setting up initramfs-tools (0.92bubuntu71) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for python-central ...
Setting up linux-image-2.6.32-19-powerpc64-smp (2.6.32-19.28) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-19-powerpc64-smp
mkinitramfs: missing ps root /dev/ps3da1 /sys entry
mkinitramfs: workaround is MODULES=most
mkinitramfs: Error please report the bug
update-initramfs: failed for /boot/initrd.img-2.6.32-19-powerpc64-smp
Failed to create initrd image.
dpkg: error processing linux-image-2.6.32-19-powerpc64-smp (--configure):
 subprocess installed post-installation script returned error exit status 2
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-20-powerpc64-smp
mkinitramfs: missing ps root /dev/ps3da1 /sys entry
mkinitramfs: workaround is MODULES=most
mkinitramfs: Error please report the bug
update-initramfs: failed for /boot/initrd.img-2.6.31-20-powerpc64-smp
dpkg: subprocess installed post-installation script returned error exit status 1

Now i love reading & have perused the forums 2 an answer to my situation...yet none of the solutions are working.:confused: I would "HIGHLY" appreciate "ANY" help with this matter...without having 2 do afresh install
THANKS in advance

---

### Post by swaprava on 2010-05-08
> **iaculallad said:**
> Open your terminal and re-issue the command below:

```
sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade

```EDIT: One command line at a time.

Is there any workaround without doing this? I was trying to install flash-plugin for Firefox and whenever I resume, this is what I get: 

```

--2010-05-08 18:39:30--  (try:12)  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.45.2.orig.tar.gz
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection timed out.
Retrying.

```

It keeps on trying without success. It's annoying that nothing else can be done with apt at this point of time, can't this be killed?

---

