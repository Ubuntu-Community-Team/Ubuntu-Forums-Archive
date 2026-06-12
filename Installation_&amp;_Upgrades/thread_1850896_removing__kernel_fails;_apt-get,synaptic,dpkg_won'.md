---
title: "removing  kernel fails; apt-get,synaptic,dpkg won't work"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by sowdust on 2011-09-27
Hello,

it's been a while now that whenever I tried to update something with apt-get i get this error:

```
Removing linux-image-2.6.35-24-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
/etc/default/grub: 13: nomodeset: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-24-generic.postrm line 328.
dpkg: error processing linux-image-2.6.35-24-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.35-25-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
/etc/default/grub: 13: nomodeset: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postrm line 328.
dpkg: error processing linux-image-2.6.35-25-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.35-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
/etc/default/grub: 13: nomodeset: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-27-generic.postrm line 328.
dpkg: error processing linux-image-2.6.35-27-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.35-28-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
/etc/default/grub: 13: nomodeset: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-28-generic.postrm line 328.
dpkg: error processing linux-image-2.6.35-28-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-2.6.35-30-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
/etc/default/grub: 13: nomodeset: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-30-generic.postrm line 328.
dpkg: error processing linux-image-2.6.35-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.35-24-generic
 linux-image-2.6.35-25-generic
 linux-image-2.6.35-27-generic
 linux-image-2.6.35-28-generic
 linux-image-2.6.35-30-generic
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

```


now, it never gave me too much trouble, that's why I waited to have some time before facing the problem, but now I would like to solve it, since it sometimes gives me problem when I try to remove unnecessary software or configuration files.

Thank you in advance!

---

### Post by dino99 on 2011-09-27
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo dpkg-reconfigure -phigh -a

sudo apt-get update
sudo apt-get install -f

sudo synaptic
select & remove/purge the unneeded kernel(s), both 2 headers & image for each kernel removed (its a good idea to let 2 kernels installed in case of failure with one)

---

### Post by sowdust on 2011-09-27
thank you dino for your answer; the error is still the same though :(

```
E: linux-image-2.6.35-24-generic: subprocess installed post-removal script returned error exit status 1
E: linux-image-2.6.35-25-generic: subprocess installed post-removal script returned error exit status 1
E: linux-image-2.6.35-27-generic: subprocess installed post-removal script returned error exit status 1
E: linux-image-2.6.35-28-generic: subprocess installed post-removal script returned error exit status 1
E: linux-image-2.6.35-30-generic: subprocess installed post-removal script returned error exit status 1


```

---

### Post by drs305 on 2011-09-27
It would be a hack, but we could disable the scripts causing the errors by making them unexecutable. Before progressing, which kernel are you currently using (uname -r).

---

### Post by sowdust on 2011-09-27
2.6.35-23-generic

---

### Post by drs305 on 2011-09-27
Disclaimer: Running this command may eliminate the error messages by preventing the post-removal scripts from running. It *may* stop the error messages. It's a hack because the scripts really should be run, but since they can't for some reason we may be able to stop the request. Fragments may still be around. Hopefully if this works you can then install later kernels if desired and you will be allowed to do so. 
```

for i in 24 25 27 28 30; do sudo chmod -x /var/lib/dpkg/info/linux-image-2.6.35-$i-generic.postrm;done
```

If it doesn't work, to return things as they were, which I'd recommend, run the command again, changing -x to +x

---

### Post by sowdust on 2011-09-28
thank you very much for your suggestion.
I tried the hack but unluckily it did not work.

I still get the same error message for each kernel:

```
Removing linux-image-2.6.35-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
/etc/default/grub: 13: nomodeset: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-27-generic.postrm line 328.
dpkg: error processing linux-image-2.6.35-27-generic (--remove):
 subprocess installed post-removal script returned error exit status 1

```

---

### Post by drs305 on 2011-09-28
If you can open Synaptic, can you open the Custom Filters, Broken button (lower left) to see broken packages? I think *dino99's* commands should do the same thing, but this is a GUI method that would be worth trying.

You can check the status of the kernel installation in /var/lib/dpkg/info/status to see what it reports:
```
grep -A1 "Package: linux-image" /var/lib/dpkg/status

```

---

### Post by sowdust on 2011-09-29
mmm it's weird because there's no package in the "Broken" filter, while all of these problematic kernel updates are under the filter "marked changes" and cannot be unmarked (when i try it has no effect whatsoever).

The output of **grep -A1 "Package: linux-image" /var/lib/dpkg/status** is:

```
Package: linux-image-2.6.35-30-generic
Status: deinstall ok half-installed
--
Package: linux-image-2.6.35-28-generic
Status: deinstall ok half-installed
--
Package: linux-image-2.6.35-23-generic
Status: install ok installed
--
Package: linux-image-2.6.35-22-generic
Status: install ok installed
--
Package: linux-image-2.6.38-11-generic
Status: install ok half-configured
--
Package: linux-image-generic
Status: install ok unpacked
--
Package: linux-image-2.6.35-27-generic
Status: deinstall ok half-installed
--
Package: linux-image-2.6.35-24-generic
Status: deinstall ok half-installed
--
Package: linux-image-2.6.35-25-generic
Status: deinstall ok half-installed
```

---

### Post by drs305 on 2011-09-30
About the last thing I can offer is to edit the *status* file (after making a backup) and removing all the sections relating to the kernels causing the error message. Each section starts with "Package:" and ends with a blank line before the next "Package:" line. You could try removing just one of them and see if that error disappears. If it does, delete the rest of the "Package: linux-image..." sections, but *make sure to leave the -23 and -22 kernel entries intact*.

You could try removing these kernel entries to see if APT stops nagging you about them:
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.orig
gksu gedit /var/lib/dpkg/status
```

---

### Post by sowdust on 2011-10-01
thanks for this. I tried but when i ran apt-get upgrade it said that i had unmet dependencies for the packages linux-image-generic, linux-generic etc....
in the end it said that it encountered problem processing
 linux-image-2.6.38-11-generic
 memtest86+
 ubuntu-standard
 grub-pc
 linux-image-generic
 linux-generic

I guess for now i'll go back to the original version of /var/lib/dpkg/status.orig

---

### Post by drs305 on 2011-10-01
> **sowdust said:**
> thanks for this. I tried but when i ran apt-get upgrade it said that i had unmet dependencies for the packages linux-image-generic, linux-generic etc....
in the end it said that it encountered problem processing
 linux-image-2.6.38-11-generic
 memtest86+
 ubuntu-standard
 grub-pc
 linux-image-generic
 linux-generic

I guess for now i'll go back to the original version of /var/lib/dpkg/status.orig

Actually, I am a bit encouraged by that message. 

Looking back at your errors, one of them is not listed as "deinstall" but as "half-installed" [noparse](.38)[/noparse]. Since it is still trying to install that one, if it is removed from the list it may have generated those errors. You could try just removing the ones listed as "deinstall"; just maake sure you remove only the ones listed as "deinstall" and leave all the others alone.

If you attempt to re-edit, make sure you still have an original that you don't edit (i.e. don't mistakenly edit the status.orig until you copy it back to *status*.

---

### Post by sowdust on 2011-10-03
actually none of them is marked just as deinstall in the status file and every combination i try gives me roughly the same error, just relative to different packages :(

---

### Post by drs305 on 2011-10-03
> **sowdust said:**
> actually none of them is marked just as deinstall in the status file and every combination i try gives me roughly the same error, just relative to different packages :(

I could have been clearer. What I was proposing was to remove the linux-image Package sections which were labeled:
> Status: deinstall ok half-installed
These would be the 24, 25, 27, 28 and 30. 

You may have already tried this, but I wanted to clarify what I wrote in case you hadn't and wish to attempt removing these from the status file.

---

### Post by sowdust on 2011-10-08
Sorry if it took me a while to reply, but i do not have an internet connection where i live during the week.

I did what you suggested and the problems with the linux-images were solved indeed, but now the error message is just changed to 

```
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
 * dkms: running auto installation service for kernel 2.6.38-11-generic         
 *       bcmwl (5.100.82.38+bdcom)...                                    [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
/etc/default/grub: 13: nomodeset: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-11-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-11-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up memtest86+ (4.10-1.1ubuntu1) ...
/etc/default/grub: 13: nomodeset: not found
dpkg: error processing memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on memtest86+; however:
  Package memtest86+ is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (1.99~rc1-13ubuntu3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          /etc/default/grub: 13: nomodeset: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-11-generic; however:
  Package linux-image-2.6.38-11-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.11.26); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 linux-image-2.6.38-11-generic
 memtest86+
 ubuntu-standard
 grub-pc
 linux-image-generic
 linux-generic


```

---

### Post by drs305 on 2011-10-08
We didn't try to 'eliminate' the -11 kernel in the previous attempt to fix things. 

First, ensure you are not using the [noparse]38-11 kernel[/noparse]:```

uname -r
```
Then try editing your modified *status* and removing the references to the -11 kernel, as you did all the others.

Please make sure you have a backup of the *original* status file so we can put things back the way they were if necessary.

---

### Post by sowdust on 2011-10-11
I tried and the linux-image-* problem does not come up anymore after i took all the references out, but i still have problems with  memtest86+ , ubuntu-standard and grub-pc:
```
/etc/default/grub: 13: nomodeset: not found
dpkg: error processing memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on memtest86+; however:
  Package memtest86+ is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (1.99~rc1-13ubuntu3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          /etc/default/grub: 13: nomodeset: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 memtest86+
 ubuntu-standard
 grub-pc
```

I tried to delete those too, but the entries where regenerated each time i ran the apt-get upgrade, giving the same error.

by the way, what could all this be caused by?

---

### Post by drs305 on 2011-10-11
A. We can keep plugging away at this if you like:

```
sudo dpkg --configure memtest86+
```
Note, when I run this it says it is already configured, but it also says there were errors. In my case, the 'errors' are most likely due to the fact that I have disabled memtest so it doesn't appear in my Grub menu. This specific 'error' - being disabled -  is not causing your problem.

You can also try running the following to configure multiple packages if the above is fixed but another similar message appears:
```
sudo dpkg --configure -a
```

B. I have no idea... ](*,)

---

### Post by sowdust on 2011-10-12
: ( 

not even if i try to --reinstall ...
i think i will just keep it this way until i decide to follow a massive approach to solve it (like formatting and installing the next ubuntu version).

thank you very much for your help!

---

