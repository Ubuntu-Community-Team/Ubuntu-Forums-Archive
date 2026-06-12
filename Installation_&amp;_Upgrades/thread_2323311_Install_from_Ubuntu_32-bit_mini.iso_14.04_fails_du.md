---
title: "Install from Ubuntu 32-bit mini.iso 14.04 fails during download of components"
date: 2016-05-04
forum: Installation &amp; Upgrades
---

### Post by swajime on 2016-05-04
I'm attempting to install from the mini.iso 32-bit image of Ubuntu 14.04 LTS from [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
During the download of components, the install fails.  It downloaded several files before failing.

The dialog box says: The installer failed to download a file from the mirror. This may be a problem with your network, or with the mirror. You can choose to retry the download, select a different mirror, or cancel and choose another installation method. Downloading a file failed: [Retry][Change mirror][Cancel]"

Here is the tail of /var/log/syslog:

```
May  4 15:16:41 anna[2234]: DEBUG: retrieving libc6-udeb 2.19-0ubuntu6.7
May  4 15:16:42 anna[2234]: 2016-05-04 15:16:42 URL:http://us.archive.ubuntu.com/ubuntu//pool/main/e/eglibc/libc6-udeb_2.19-0ubuntu6.7_i386.udeb [850868/850868] -> "/var/cache/anna/libc6-udeb_2.19-0ubuntu6.7_i386.udeb" [1]
May  4 15:16:42 anna[2234]: DEBUG: retrieving libcryptsetup4-udeb 2:1.6.1-1ubuntu1
May  4 15:16:42 anna[2234]: Segmentation fault
May  4 15:16:42 kernel: [  100.649789] wget[3544]: segfault at b771bd9d ip b7324a0d sp bffb7090 error 7 in libresolv-2.19.so[b731b000+13000]
May  4 15:16:42 anna[2234]: Segmentation fault
May  4 15:16:42 anna[2234]: WARNING **: package retrieval failed
May  4 15:16:42 kernel: [  100.657934] wget[3551]: segfault at b777cd9d ip b7385a0d sp bfbb8660 error 7 in libresolv-2.19.so[b737c000+13000]
May  4 15:17:36 main-menu[223]: WARNING **: Configuring 'download-installer' failed with error code 6
May  4 15:17:36 main-menu[223]: WARNING **: Menu item 'download-installer' failed.
```

Thanks in advance for anybody who can help,


John

---

### Post by QDR06VV9 on 2016-05-04
All those links work for me...you could have caught those repos in a temp non-working state.
Maybe try again and also check MDsum of the iso that was burned.

---

### Post by swajime on 2016-05-04
I've tried this from two different computers with the same results.
I'm installing to a VirtualBox vm.

md5 mini.iso
MD5 (mini.iso) = a2502844750ecb6477d8fb4ff6b9aaf8

Thanks,


John

---

### Post by swajime on 2016-05-04
When I drop to a shell from the install menu, and try to use wget for any URL, it segfaults.

---

### Post by QDR06VV9 on 2016-05-04
I am Down-loading the 32 bit mini-iso now.
Will report shortly.

---

### Post by QDR06VV9 on 2016-05-04
Yep Huston we have a problem..
Still working on this though...will report with relevant info.

---

### Post by sudodus on 2016-05-04
Have you tried to download and use the **mini.iso** from the links recommended in [***mini.iso***, minimal install, netboot iso]("http://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730")?

---

### Post by QDR06VV9 on 2016-05-04
> **sudodus said:**
> Have you tried to download and use the **mini.iso** from the links recommended in [***mini.iso***, minimal install, netboot iso]("http://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730")?

I myself have not tried that yet.
But Good and Bad news here.
1.The Bad being the 32 bit mini-iso for 14.04 won't work in a V Box.(trying all kinds of different things Network, Mirrors, different network devices)
2.The Good Xenial 32bit mini-iso works as expected.
So maybe a bug needs to be filed against the trusty(14.04LTS 32bit) mini-iso D-load link. Here: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) 
Any way i hope this is useful.

---

### Post by sudodus on 2016-05-04
I think you (runrickus) or I can edit that help page (if it turns out that we should replace the link with a better one).

---

### Post by QDR06VV9 on 2016-05-04
> **sudodus said:**
> I think you (runrickus) or I can edit that help page (if it turns out that we should replace the link with a better one).

Looking for a good link now.:D

---

### Post by QDR06VV9 on 2016-05-04
@swajime I used this link and it worked. [http://cdimage.ubuntu.com/netboot/14.04/](http://cdimage.ubuntu.com/netboot/14.04/)
For my install i used the 14.04 with wily's 4.2 HWE kernel (supported until August 2016)

Let us know to confirm a good link.
Kind Regards

---

### Post by swajime on 2016-05-05
The image at that link worked.

Thank you for helping out with this.


John

---

### Post by QDR06VV9 on 2016-05-05
Your Welcome.

---

### Post by sudodus on 2016-05-05
I edited the help page with the faulty mini.iso files: [General link that seems reliable](https://help.ubuntu.com/community/Installation/MinimalCD#General_link_that_seems_reliable)

Now I'm waiting for a reaction from the maintainer of that page :-P

---

