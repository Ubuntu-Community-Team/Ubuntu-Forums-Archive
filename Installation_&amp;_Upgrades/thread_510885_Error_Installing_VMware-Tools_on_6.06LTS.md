---
title: "Error Installing VMware-Tools on 6.06LTS"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by veletron on 2007-07-27
Hi

I feel that I have now tried everything that I can find online or think of myself to get vmware-tools installed on 6.06LTS, but it simply will not install. Installation always fails with a message: 

"Unable to copy the source file ./installer/services.sh to the destination file
/etc/init.d/vmware-tools."

I have tried to various suggestions on this forum (along with other forums) to no avail - it seems a great deal of people are getting this exact same error. Some claimed to have solved it. I tried their solutions but they dont work on my install.

I have installed gcc, the appropriate headers etc etc. The install directory is owned by root and chmodded 755. There is nothing at all thats non-standard about my ubuntu install.

The really annoying thing is that it installed without issues on 6.10. I moved to 6.06LTS for the LTS!

Why the heck wont the tools install?? I really need this such that my windows host can shutdown the ubuntu VM when it stops. Without the vmware-tools it just 'kills the power' to the VM. The full text from the install attempt is shown below:

Nigel

-----

root@coniston:/home/nwebber/vmware-tools-distrib# ./vmware-install.pl
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

Unable to copy the source file ./installer/services.sh to the destination file
/etc/init.d/vmware-tools.

Execution aborted.

root@coniston:/home/nwebber/vmware-tools-distrib#

---

### Post by kidders on 2007-07-28
Hi there,

My first instinct is to wonder whether the destination file already exists, or the source file doesn't. Is either the case?

---

### Post by veletron on 2007-07-28
Hi

Yep, the source file does exist, and the destination file is not present. There's no sensible reason why the installer should fail at this point, but it appears to be an error that numerious others have encountered...!

Nigel

---

### Post by kidders on 2007-07-29
Hmmm... so much for that!

I wonder if the problem is in the installer script's "internal_sed" subroutine. The script attempts to open two files & feed data from one into the other. The values of $src, $dst and $append at the time of the error would be interesting. Perhaps a few diagnostic "print" statements would shed some light on the problem?

My best guess is that the path of the source file is probably relative. Perhaps tweaking the line my **$cInstallerDir = './installer';** so the directory path is absolute would do the trick. It's hard to tell without actually running the script, which isn't something I want to do ... my vmware works fine just the way it is!

---

