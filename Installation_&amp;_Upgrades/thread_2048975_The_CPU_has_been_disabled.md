---
title: "The CPU has been disabled"
date: 2012-08-27
forum: Installation &amp; Upgrades
---

### Post by rudyb on 2012-08-27
Hello,

I've been using ubuntu 12.04 on my old laptop in vmware workstation 7.x without any problem.

Just today i got my new laptop with core i7 vpro processor, and installed vmware workstation 7.x on it again. 

When trying to use ubuntu 12.04 image i get the error:

"
The CPU has been disabled by the guest operating system. You will need to power off or reset the virtual machine at this point.
"

I googled for it, but no answer worked for me. All the hits i got where from users trying to run mac osX on there vmware.

I did try editing the vmware config file with the options op PAE = true, and some more from the mac forums.

No go.

Now i thought lets try to install a new fresh image.
But even the install DVD will not boot, producing the same error.

Now i am lost : help !

NB: all windows vm's work like a charme. Only the ubuntu's will not boot.

thanks for any help.

---

### Post by BadRoy on 2013-03-01
I'm seeing exactly the same thing - did you find a solution by chance?

---

### Post by Gyokuro on 2013-03-01
Hi

Could you please let me know which 12.04 release you have downloaded (amd64 or i386) and which kernel are you using (3.5 or 3.2) as we had a problem with 3.5 kernels and we are using 3.2 which works but only on two workstations as most got upgraded to vmware workstation 8. However most system testing/development work get done via kvm.

---

