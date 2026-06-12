---
title: "VMWare uninstall won't clear the disk - help!"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by Squrdel on 2006-10-22
I'm obviously doing something stupid.... I installed VMWare Server and Win XP Pro and it worked fine, except that Mr. Gates refused to activate it. So I installed the Home edition which activated fine but I ran short of disk space with the 2 guest OSs installed. So I decided to start again by uninstalling VMWare and reinstalling it. That goes fine, but when I try to install a guest OS I cant as I dont have enough disk space for the guest files. Clearly the original files have reserved the space and did not clear when I uninstalled. I have then manually removed any files with 'vmware' in it, but no luck.

Does anyone know which config files would carry this info? Or how else to get out of this? Oh yes, when I reboot normally into Dapper I get a message for 'low disk space'.

---

### Post by reacocard on 2006-10-22
try searching for files that end with ".vmdk". these are the files that actually contain the Guest OS's.

Also, next time you create a virtual machine, don't enable the "allocate all disk space now" option. That'll save you a fair bit of space.

---

### Post by Squrdel on 2006-10-25
Thanks, reococard. For the benefit of others reading this later, I had to search for files with 'vm' using nautilus as root and showing hidden files to find all the files that needed to be deleted. After I reinstalled VMWare my disk space was limited by the first installation, as though it was still there. I then opened all text files from the 'vm' search and found a few that retained references to the original installation. After commenting or deleting these lines I was able to start normally with the space restored. I also changed the folder for the disk files on the reinstall which I think made it easier to sort out.:)

---

