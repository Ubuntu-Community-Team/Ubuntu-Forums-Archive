---
title: "Thoughts on this possible dual boot setup?"
date: 2012-10-03
forum: Installation &amp; Upgrades
---

### Post by linkylingtoncarl on 2012-10-03
Hello all,

I would like to run Ubuntu 12.04 alongside my current installation of Windows 7, however I am having some trouble with deciding on how I would like to configure it. Since the bulk of my files are already installed to my NTFS drive, I was thinking that I could create a small partition for Ubuntu (say 12GB) and create links in my /home folder that would correspond to my respective C:\users folders in windows. I feel like this would be a good option as opposed to migrating all of my files over to Ubuntu and possibly having duplicates for each OS. So basically I would be using Ubuntu as my primary OS but all of my files would be stored on my windows NTFS drive. (I am also doing this because I don't want to fully abandon my windows yet, as I have many games installed.) What are your thoughts on this? 


my system: lenovo thinkpad w520 | intel i7 2760QM | 8GB DDR3 | 500GB hard disk |
windows 7 professional

---

### Post by 2F4U on 2012-10-03
OK, these are just my personal thoughts about it. I wouldn't use the system partition on Windows to store data on it, and I wouldn't point from Ubuntu to it and change files on the system partition. Just too dangerous to screw up things. If you can afford, create a seperate data partition for both Windows and Ubuntu (can be NTFS) and use it from both operating systems. Would also make things easier if, for example, the Windows partition is unusable due to some reason.

---

### Post by Mark Phelps on 2012-10-03
Strongly agree with 2F4U -- writing to your Windows OS partition is asking for trouble.  And if that happens, it's likely that Windows will then be unbootable -- making it VERY difficult to fix it.

Also, Windows and Linux have very different filesystems, and very different ways of handling permissions.

Which means, while it is OK to have a shared NTFS Data partition to use multimedia files (pictures, video, audio) in both Windows and Ubuntu, do NOT try to share files from your Linux /home folder -- through links or any other way.

---

### Post by linkylingtoncarl on 2012-10-03
Thanks for the input. I have decided as an alternative option to run Ubuntu through a virtual machine and mount files from my Windows drive as needed, using the shared folders option that is included in the guest additions.

---

