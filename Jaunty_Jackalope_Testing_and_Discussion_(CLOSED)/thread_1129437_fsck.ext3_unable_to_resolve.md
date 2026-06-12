---
title: "fsck.ext3 unable to resolve"
date: 2009-04-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jynyl on 2009-04-18
The system was running Kubuntu 8.10 fine, and Kubuntu 9.04 rc was installed on a separate partition (no resizing of partitions).
Grub (installed with 9.04) presents both systems, but fails when booting to 8.10, with error;
fsck.ext3: unable to resolve 'uuid=347d1883-.....
fsck died with exit status 8

Since this error arrived with installation of 9.04, I'm guessing this is the issue, not a hardware problem.

How can I fix this?

TIA

Peter

---

### Post by meierfra. on 2009-04-19
In order to get a clearer picture of your setup, I suggest to boot into  Kubuntu 8.10 and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by jynyl on 2009-04-19
Thanks for your reply, however, I can't boot into 8.10 (that's the problem).
 So can't run that script.

---

### Post by meierfra. on 2009-04-19
Sorry. I mixed up 8.10 and 9.04

You can run the script from  any version of Ubuntu.  So just run the script from 9.04. (If you can't boot into 9.04 either, use a LiveCD)

---

### Post by jynyl on 2009-04-19
Comparing at fstab for both 8.10 and 9.04, it appears that the 9.04 installer changed the UUID number of the partition that 9.04 was installed on, and after that, 8.10 couldn't find the old UUID for that partition.

To fix it, from 9.04, I edited /etc/fstab in the 8.10 partition, by commenting out the line relating to the old UUID.  Now 8.10 boots fine.

Thanks for your help.

Peter

---

### Post by meierfra. on 2009-04-19
Glad  you got your problem resolved.

---

