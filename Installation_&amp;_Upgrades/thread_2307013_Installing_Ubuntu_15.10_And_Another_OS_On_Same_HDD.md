---
title: "Installing Ubuntu 15.10 And Another OS On Same HDD"
date: 2015-12-21
forum: Installation &amp; Upgrades
---

### Post by shane_faulkinbury2 on 2015-12-21
I have Ubuntu 15.10 on a 1 TB HDD and want to install another OS on the same hard drive.  Ubuntu is already installed and I have the other OS on a DVD already.  What are the steps I must go through on Ubuntu to get ready to install are can I just use the DVD to create another partition?

---

### Post by Dennis N on 2015-12-21
> What are the steps I must go through on Ubuntu to get ready to install are can I just use the DVD to create another partition? 

You don't need to do anything from the existing Ubuntu. You use the live Ubuntu version on the Installer to do any preparation of partitions. The installer includes the partition editor, gparted, which can do any disk preparation, like additional partitions. This can be done before (best) taking the "Install Ubuntu" step, or even within the installation process with the "Something Else" option.

Edit: I'm assuming you are installing another Ubuntu flavor here. If it is Windows you plan to install, this won't be useful. If another Linux, use it's installer and see what it can do - it undoubtedly can create new partitions too.

---

### Post by shane_faulkinbury2 on 2015-12-21
Oh yeah, I forgot about gparted!  I'll just use that!  Thanks a lot!

---

### Post by Bucky Ball on 2015-12-21
What is this mysterious 'other OS' you intend to install? 

In any case, it would depend on how much of the hard drive your current install is using. 

1/ Do you have free space? Install the other OS there and do the partitioning during the install (regardless of which OS). 
2/ You don't have free space? Boot from the Ubuntu install media> 'Try Ubuntu'> launch Gparted at the desktop, shrink a partition to create free space. Go to step 1. 

It pays to make a plan with pencil and paper before launching into the digital where you may mess up. Good luck.

*** UPdate: Just read your new post. You can not shrink the / partition with Gparted when you are booted into the OS. You MUST do that in a live session. :)

---

