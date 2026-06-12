---
title: "Installing MPICH2 in ubuntu."
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by ksyz_1 on 2008-06-30
Hi..
 I have problem in installing MPICH2 in ubuntu. Iam following the procedure given in [https://help.ubuntu.com/community/MPICHCluster](https://help.ubuntu.com/community/MPICHCluster). But to begin when I type /etc/hosts in the root. It says "bash: command not found". 

Also I tried installing MPICH2 given in [http://www.mcs.anl.gov/research/projects/mpich2/documentation/files/mpich2-doc-install.pdf](http://www.mcs.anl.gov/research/projects/mpich2/documentation/files/mpich2-doc-install.pdf). When configuring MPICH2, specifying installation directory and running configuring script in source directory as specified in the manual, it says "bash: command not found for |&"

Both the ways did not work. Do I need to change any settings? Could any one give some information regarding this. 

Thanks in advance,
Satya.

---

### Post by Partyboi2 on 2008-07-01
> Hi..
 I have problem in installing MPICH2 in ubuntu. Iam following the procedure given in [https://help.ubuntu.com/community/MPICHCluster](https://help.ubuntu.com/community/MPICHCluster). But to begin when I type /etc/hosts in the root. It says "bash: command not found". Im assuming you are stuck at the first part.
To edit your /etc/hosts file as it says, you need to open the file with a text editor program.
In the terminal type
```
gksudo gedit /etc/hosts
``` then make the changes and save..

---

### Post by ksyz_1 on 2008-07-01
Thanks for your reply. I've changed the hosts and giving a try with 5 processors ( 1 master and 4 slaves). I have a question in installing NFS as said in second step. How can I install NFS in ub0? I think I already installed NFS before making hosts. Should I install again? At present the path in terminal looks this way name@name-laptop:~$. How can change to name@ub0:~$.
Thanks for your time..
Satya.

---

