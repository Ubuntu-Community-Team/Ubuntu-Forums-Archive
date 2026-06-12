---
title: "How to install deb files"
date: 2005-04-24
forum: Installation &amp; Upgrades
---

### Post by Oleks70 on 2005-04-24
I have downloaded few deb files on desktop and now try to in stall them with Sudo 
dpkg -1  name.deb and i get this:
 
alex@ubuntu:~$ sudo dpkg -i lookup_1.08b-5_i386.deb
dpkg: error processing lookup_1.08b-5_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 lookup_1.08b-5_i386.deb
alex@ubuntu:~$

I have searched but couldnt find anything .Thank you

---

### Post by az on 2005-04-24
That should be an "i", and not a one ("1")
sudo dpkg -i <package>


Did you download it to your home or to your Desktop?

ls look*
cd Desktop
ls look*

You can do
sudo dpkg -i loo*.deb
to make your life easier.  You can also use tab completion.

Type 
cd (tab)
play around with tab completion to get used to it.  It makes the command like much easier to use.  You should be able to zip about your hard drive faster by unix comman line than with windows explorer....

---

### Post by Oleks70 on 2005-04-24
Oh yea i put them in desktop dir instead of home. THx

---

