---
title: "Ubuntu 12.04 - ASUS Notebook X201E - generic updates Problems!"
date: 2015-08-19
forum: Installation &amp; Upgrades
---

### Post by terravalta on 2015-08-19
Hello,

I am using a ASUS Notebook X201E. During the generic updates on 2015.08.19 and in July, I noticed the following Terminal screen messages (see also attached Screenshot):-
 

 

 Setting up linux-image 3.2.0-89-generic (3.2.0-89.127)...

 

 Error! Problems with depmod detected. Automatically uninstalling this module.

 

 DKMS: Install Failed (depmod problems). Module rolled back to built state.
 

 Unable to find an initial ram disk that I know how to handle.
 

 Will not try to make an intrid.


Questions: a) Is the above a problem?

                b) Is their a fix?

Thanks in advance of any replies.

---

### Post by dino99 on 2015-08-19
your screenshot show a bunch of kernels installed; you will soon or later get an other issue: no more free space on /boot  :o
having the latest and previous working kernel is enough; so purge the others to get back some space into /boot (each 'kernel' has 2 headers + 2 images)
you can easily do that removal with 'synaptic'

about the depmod and dkms errors, run into a terminal:
> sudo apt-get update
sudo apt-get install -f
sudo adpkg --configure -a

---

### Post by ronnie-vc10 on 2015-09-21
Hello dino99
apologies for delay in replying...ill!

Thanks for info, I will try these and report back.

Best regards and big thanks
Ronnie

---

