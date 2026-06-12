---
title: "double grub entries 10.04?"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by alh on 2010-05-01
Loved karmic. Updated to 10.04 OK except for a couple of things. No sound icon on the task bar and it's not in the 'add to taskbar list'. Not a major problem, just put it in the 'start programs section'. 
Annoying thing is after selecting from the grub boot menu, the machine seems to be suffering some indesision as the cursor sits on the top lhs of the screen flashing and the screen modulates between various degrees of darkness. Then the machine boots OK. Certainly slower than karmic - not quicker as reported. Seems to be some conflict happening. There is a duplication of the kernal entries for default and safe. Mabe this is the problem. I have run update-grub2, but it keeps giving me double entries. 
Would be good if someone knows how to fix it.
Anyway; when it's up and running all ok.

---

### Post by lisati on 2010-05-01
> **alh said:**
> There is a duplication of the kernal entries for default and safe. Mabe this is the problem. I have run update-grub2, but it keeps giving me double entries. 


It is normal for the kernel numbers to match for "default" and "safe" etc. If there have been kernel updates, it is also normal for there to be more than one entry for "default" and "safe", with different numbers for the kernel - this is so that if something doesn't work quite right on your system with the updated versions you're in with a chance of being able to do some troubleshooting with the older versions.

---

### Post by alh on 2010-05-01
> **lisati said:**
> It is normal for the kernel numbers to match for "default" and "safe" etc. If there have been kernel updates, it is also normal for there to be more than one entry for "default" and "safe", with different numbers for the kernel - this is so that if something doesn't work quite right on your system with the updated versions you're in with a chance of being able to do some troubleshooting with the older versions.
 
Thanks for your reply. The kernel numbers are identical for all entries. Two for default and two for safe. There have been no kernel updates since instalation yesterday. Head scratcher eh?:confused:

---

### Post by partsdale on 2011-07-05
bump?
:)

---

### Post by nzjethro on 2011-07-05
You could use Grub Customiser to show only the kernels you want, or Burg to have a graphical Grub menu with only the kernels you want present.

Other than that, you could play around with the files in your /boot directory, and delete the kernels you don't want (then run update-grub). [This guide]("http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/") also appears to offer some solutions.

---

### Post by ubume2 on 2011-07-05
> **nzjethro said:**
> 
Other than that, you could play around with the files in your /boot directory, and delete the kernels you don't want (then run update-grub). [This guide]("http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/") also appears to offer some solutions.

I advise you not to "play around"  with the files in /boot!!! The url nzjethro refers to is a good guide.

Edit: 
If you have a double or triple boot( 2 or more linuxes), your grub may be picking up a duplicate kernel entry from a previous grub install, especially if you used custom grub entries. I've had that happen.

If this wasn't a fresh install of 10.04, that could explain the duplicate, somehow. :confused: 

To customize grub, see this url:
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

---

