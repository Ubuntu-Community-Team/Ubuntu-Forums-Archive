---
title: "[SOLVED] update errors"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by Firecad2006 on 2008-10-27
i don't know if im in the right area? but heres my problem i have 2 updates and every time i try to update them i get this error, can someone please help.


E: /var/cache/apt/archives/libmpeg3cv_2.1.0-git20081018akirad2_i386.deb: trying to overwrite `/usr/lib/libmpeg3hv-1.5.0.so.1.0.0', which is also in package libmpeg3hv
E: /var/cache/apt/archives/libquicktimecv_2.1.0-git20081018akirad2_i386.deb: trying to overwrite `/usr/lib/libquicktimehv-1.6.0.so.1.0.0', which is also in package libquicktimehv

---

### Post by icanfly0307 on 2008-10-27
are you trying to update as root? if not, the overwriting process will fail. and what do you mean by "update"? are you trying to update the packages or the entire distro?

---

### Post by Firecad2006 on 2008-10-27
no, and im trying to update some files for cinelerra, how do i update under root?

---

### Post by icanfly0307 on 2008-10-27
log in as root and update with the same procedure that caused you to fail in your personal account.  just out of curiosity... how exactly ARE you trying to update? ie synaptic, apt, package manager?

---

### Post by Firecad2006 on 2008-10-27
log in as root iv never done that, and i use the package manager

---

### Post by icanfly0307 on 2008-10-27
is this computer your own, or is it in your workplace or something? you must have set up your root password during installation if this computer is your own...

---

### Post by Firecad2006 on 2008-10-27
its my computer, i have only one account that i use

---

### Post by icanfly0307 on 2008-10-27
looks like your going to have to set up a root account. enter this code in the terminal...

sudo su

Enter the user password, and then: 

passwd

Enter the root password you wish to use as root. Now, you can log on as root if you wish.

Also, your going to have to allow the system to log root in from the login screen. Go to sytem --> preferences --> Login Window or preferences... something like that.

Then, click around on the tabs, somewhere around in the dialog box, you will find an option allowing you to log in as superuser aka root from the login window...

PS. ill be back in the evening, so i might not be able to reply to your next post immediatly... good luck until then...

---

### Post by Firecad2006 on 2008-10-27
i did what you said and nothing was updated

---

### Post by Firecad2006 on 2008-10-28
i dont know why but my computer just installed all the updates :)but thanks for helping me this is why i love linux, people helping people

---

