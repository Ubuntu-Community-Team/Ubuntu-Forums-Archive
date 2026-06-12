---
title: "wubi vista oneric problem"
date: 2012-02-03
forum: Installation &amp; Upgrades
---

### Post by jw47 on 2012-02-03
I have messed up my installation.  I was dual booting vista and ubuntu 11.04 just fine, then in my ignorance decided to use wubi to upgrade to 11.10, decided to install 11.10 and messed up my partitions, mbr, etc. Now I can not boot vista even with the vista recovery partition.  For a while I couldn't boot anything from the hard drive.  I can boot my ubuntu live usb and I can boot the installed 11.10 (though the network interface is broken).  Please help.

another newbie

---

### Post by darkod on 2012-02-03
From live mode, follow the link in my signature, run the boot info script and post the results as explained there.
I don't understand what exactly you did, since even if you did install wubi it would be inside vista and shouldn't make problems.

---

### Post by jw47 on 2012-02-04
Darko,

Thanks for " reply.  I am having trouble running the script, following is a copy of my terminal as I triy to output the results to a empty document I created in the same folder as the script, which is on the ubuntu live desktop, the file is named simply "jw47" (no quotes). By the way, what are the keyboard shortcuts for "repeat previous command, cut, and paste? The teminal session follows:

ubuntu@ubuntu:~$ sudo bash ./boot_info_script.sh <jw47>
bash: syntax error near unexpected token `newline'
ubuntu@ubuntu:~$ man redirection
No manual entry for redirection
ubuntu@ubuntu:~$ man pip
No manual entry for pip
ubuntu@ubuntu:~$ man pipe
ubuntu@ubuntu:~$ sudo bash ./boot_info_script.sh jw47
bash: ./boot_info_script.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ./home/desktop/boot_info_script060.zip/boot_info_script.sh <jw47>
bash: syntax error near unexpected token `newline'
ubuntu@ubuntu:~$ sudo bash ./home/desktop/boot_info_script060.zip/boot_info_script.sh
bash: ./home/desktop/boot_info_script060.zip/boot_info_script.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ./home/desktop/boot_info_script060.zip/boot_info_script.sh <jw47>
bash: syntax error near unexpected token `newline'
ubuntu@ubuntu:~$ 

jw47

---

### Post by darkod on 2012-02-04
Previous command is with Up arrow.

Don't try to write it into empty file, let it create its own results.txt. Make sure to notice where the .sh file is extracted, and run the command accordingly. The terminal starts in your Home folder, if the script is there it should work with:
sudo bash ./boot_info_script*.sh

Or:
sudo bash ./path/boot_info_script*.sh

---

