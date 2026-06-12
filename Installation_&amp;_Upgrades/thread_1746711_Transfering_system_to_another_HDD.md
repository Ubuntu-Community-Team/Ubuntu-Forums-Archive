---
title: "Transfering system to another HDD"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by LordNodens on 2011-05-02
Hi to all! I have a question regarding the migration of the system to a new HDD. I currently have an 80GB HDD that has Windows 7 x64 installed and another 80GB HDD that has Ubuntu 11.04 x64 installed. The boot loader uses Grub2. I want to migrate the 80GB disk that hosts Win7 to a new 500GB HDD using Acronis True Image Home 2011 and then migrate the other 80GB disk that hosts Ubuntu to a new 800GB HDD following the steps described in the following page: [http://www.ehow.com/how_7184450_copy-ubuntu-another-hard-drive.html](http://www.ehow.com/how_7184450_copy-ubuntu-another-hard-drive.html)

Is this going to work or everything will be messed up with Grub2? Any other suggestions?

---

### Post by LordNodens on 2011-07-08
OK, I transfered Ubuntu to the new HDD using CloneZilla. No problem at all, even with grub2. Then I transfered Windows to the other new HDD. The only problem I had after the transfer finished is that I couldn't startup Windows with Grub2, but it was easily fixed in Ubuntu.

---

### Post by tgalati4 on 2011-07-08
Why don't you share with us the procedure that you used and the fix that you required?  I'm sure that would help others who need to migrate a multiboot system.  Did you use all the steps in the link that you referenced?  Or were there differences that you had to figure out?

---

### Post by LordNodens on 2011-07-11
OK, that's what I did in brief:

1. Created a bootable USB containing CloneZilla.
2. Connected the new HDD.
3. Rebooted to CloneZilla.
4. Copied the files and grub2 settings from the old HDD to the new one. Everything is done automatically. I didn't use the image file option. The program is very simple to use.
5. Removed the old HDD and put the new one in place.
6. Booted to Ubuntu (and Windows) without any problem.
7. The old HDD is created 1:1 to the new one, so the other HDD space is left unallocated.
8. Created a bootable USB containing Gparted.
9. Rebooted to Gparted.
10. Deleted the extended partition/linux-swap. Expanded the main partition to include the unallocated space. Left a space unallocated (the size of the extended partition). Created an extended partition/linux-swap using the unallocated space I left in purpose. You can test all these virtually before applying any changes.
11. Booted to Ubuntu (and Windows) without any problem. All HDD space used.
12. Connected the 2nd new HDD.
13. Booted to Windows.
14. Used Acronis True Image Home to clone disk.
15. Rebooted in order to start the procedure.
16. Removed the old HDD and put the new one in place.
17. After that choosing Windows in Grub didn't do anything. So I booted to Ubuntu, used the program Burg-manager from Super-Boot-Manager program (I am using Burg in Ubuntu in order to have a theme when booting) and then re-applied the settings I used. This automatically solved my problem regarding Windows. Also Burg settings are lost after migrating Ubuntu to a new HDD.
18. Rebooted and everything worked alright in Ubuntu and Windows.

---

