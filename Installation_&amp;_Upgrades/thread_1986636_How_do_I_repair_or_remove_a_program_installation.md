---
title: "How do I repair or remove a program installation?"
date: 2012-05-25
forum: Installation &amp; Upgrades
---

### Post by ebn on 2012-05-25
Sir, 
      I attempted to install adobe flash plugin on ubuntu 10.04.Installation was stopped when 82% completed.But it showed installed when after restarted my  computer(Desktop ).When I tried to install other software,It shows an error message:
"Previous installation hasn't been completed.The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software."
How can I solve this problem?how do I repair the installation or remove the installation?
        
   ebn

---

### Post by ebn on 2012-05-25
**How do I repair or remove a program installation?** 			
 			 			 		   		 		 		Sir, 
      I attempted to install adobe flash plugin on ubuntu  10.04.Installation was stopped when 82% completed.But it showed  installed when I restarted my  computer(Desktop ).When I tried to  install other software,It shows an error message:
"Previous installation hasn't been completed.The installation could have  failed because of an error in the corresponding software package or it  was cancelled in an unfriendly way. You have to repair this before you  can install or remove any further software."
How can I solve this problem?how do I repair the installation or remove the installation?
        
   ebn

---

### Post by kc1di on 2012-05-25
> **ebn said:**
> **How do I repair or remove a program installation?** 			
 			 			 		   		 		 		Sir, 
      I attempted to install adobe flash plugin on ubuntu  10.04.Installation was stopped when 82% completed.But it showed  installed when I restarted my  computer(Desktop ).When I tried to  install other software,It shows an error message:
"Previous installation hasn't been completed.The installation could have  failed because of an error in the corresponding software package or it  was cancelled in an unfriendly way. You have to repair this before you  can install or remove any further software."
How can I solve this problem?how do I repair the installation or remove the installation?
        
   ebn
Hi EBN,

In a terminal here what to do:

```
sudo dpkg --configure -a
```
that will finish the install if possible. if not
your can remove it by typing
```
sudo apt-get purge <name of the program>
```

---

### Post by ebn on 2012-05-27
> **kc1di said:**
> Hi EBN,

In a terminal here what to do:

```
sudo dpkg --configure -a
```
that will finish the install if possible. if not
your can remove it by typing
```
sudo apt-get purge <name of the program>
```
Thanks for helping me to solve the problem.I solved it .

---

