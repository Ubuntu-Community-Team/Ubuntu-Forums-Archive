---
title: "Problems with X windows after kernel update"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by DrDaveyAtoms on 2011-02-02
My problems stem from a stupid mistake I made recently. When trying to clean up old kernels I accidentally deleted the current kernel (2.6.35-24). I then had problems when I reinstalled and found that I could only boot into command line mode. 

I was able to fix this problem but have since installed the latest kernel release (2.6.35-25) and now have the same problem as before. Of course, I could do what I did before but I guess this is going to occur whenever I upgrade in future.

Does anyone have any ideas as to how I can permanently solve this problem? Also, will this be solved when I upgrade to Natty in April?

---

### Post by DrDaveyAtoms on 2011-02-03
Shameless bump. ;)

---

### Post by matt_symes on 2011-02-03
Hi

> **DrDaveyAtoms said:**
> My problems stem from a stupid mistake I made recently. When trying to clean up old kernels I accidentally deleted the current kernel (2.6.35-24). I then had problems when I reinstalled and found that I could only boot into command line mode. 

I was able to fix this problem but have since installed the latest kernel release (2.6.35-25) and now have the same problem as before. Of course, I could do what I did before but I guess this is going to occur whenever I upgrade in future.

Does anyone have any ideas as to how I can permanently solve this problem? Also, will this be solved when I upgrade to Natty in April?

How did you fix the problem before with 2.6.35-24 ? It might give someone an idea of what the problem could be and help others in the same situation.

Kind regards

---

### Post by DrDaveyAtoms on 2011-02-03
Thanks for your reply matt_symes.

The problem initially was that I could no longer reinstall 2.6.35-24 as dpkg was trying to uninstall fglrx each time. 

I was able to solve this, with the help of another fine forum user ([http://ubuntuforums.org/showthread.php?t=1670660&highlight=DrDaveyAtoms](http://ubuntuforums.org/showthread.php?t=1670660&highlight=DrDaveyAtoms)), by modifying the postrm script such that the installation procedure finished regardless of whether there was an error or not.

I do not understand why but when I reinstalled 2.6.35-24 the GUI seemed to work but when I have since installed 2.6.35-25 the GUI does not work.

---

### Post by matt_symes on 2011-02-07
Hi

I have to be honest and say that i have not come across this before so i should bow out.

Here's a cheeky bump for you though.

Kind regards

---

