---
title: "Can't boot after upgrade to 14.04"
date: 2015-03-11
forum: Installation &amp; Upgrades
---

### Post by huangzhendong on 2015-03-11
Could anyone help me ?? The following is the info of my error, this happens after I update my Ubuntu to Ubuntu14,but the electricity suddenly out.Then I start up my Ubuntu the error

 Comes?
Try(HD0,0):NTFS5:


mount: mounting /dev/loop0 on /root failed: invalid argument
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting: /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have requested /sbin/init.
no init found. Try passing init= bootarg.


busybox v1.21.1 (ubuntu 1:1.21.0-1ubuntu1) built in shell (ash)
Enter 'help' for a list of built in commands.


(inframfs)_

[COLOR=#000000]I have the same problem,but even I tried what say in this thread the error still exist.Could anyone help me ?? The following is the info of my error, this happens after I update my Ubuntu to Ubuntu14,but the electricity suddenly out.Then I start up my Ubuntu the erro c[/COLOR][COLOR=#000000]omes?please help me....
[/COLOR]
[COLOR=#000000]Try(HD0,0):NTFS5:[/COLOR]

[COLOR=#000000]mount: mounting /dev/loop0 on /root failed: invalid argument[/COLOR]
[COLOR=#000000]mount: mounting /dev on /root/dev failed: no such file or directory[/COLOR]
[COLOR=#000000]mount: mounting /sys on /root/sys failed: no such file or directory[/COLOR]
[COLOR=#000000]mount: mounting: /proc on /root/proc failed: no such file or directory[/COLOR]
[COLOR=#000000]Target filesystem doesn't have requested /sbin/init.[/COLOR]
[COLOR=#000000]no init found. Try passing init= bootarg.[/COLOR]


[COLOR=#000000]busybox v1.21.1 (ubuntu 1:1.21.0-1ubuntu1) built in shell (ash)[/COLOR]
[COLOR=#000000]Enter 'help' for a list of built in commands. [/COLOR]


[COLOR=#000000](inframfs)_[/COLOR]

[COLOR=#000000]I have the same problem,but even I tried what say in this thread the error still exist.Could anyone help me ?? The following is the info of my error, this happens after I update my Ubuntu to Ubuntu14,but the electricity suddenly out.Then I start up my Ubuntu the error[/COLOR]

[COLOR=#000000]Comes?[/COLOR]
[COLOR=#000000]Try(HD0,0):NTFS5:[/COLOR]


[COLOR=#000000]mount: mounting /dev/loop0 on /root failed: invalid argument[/COLOR]
[COLOR=#000000]mount: mounting /dev on /root/dev failed: no such file or directory[/COLOR]
[COLOR=#000000]mount: mounting /sys on /root/sys failed: no such file or directory[/COLOR]
[COLOR=#000000]mount: mounting: /proc on /root/proc failed: no such file or directory[/COLOR]
[COLOR=#000000]Target filesystem doesn't have requested /sbin/init.[/COLOR]
[COLOR=#000000]no init found. Try passing init= bootarg.[/COLOR]


[COLOR=#000000]busybox v1.21.1 (ubuntu 1:1.21.0-1ubuntu1) built in shell (ash)[/COLOR]
[COLOR=#000000]Enter 'help' for a list of built in commands.[/COLOR]


[COLOR=#000000](inframfs)_[/COLOR]

I have the same problem,but even I tried what say in this thread the error still exist.Could anyone help me ?? The following is the info of my error, this happens after I update my Ubuntu to Ubuntu14,but the electricity suddenly out.Then I start up my Ubuntu and the error comes.[COLOR=#ff0000]** Another thing I want to say is that my ubuntu was installed by wubi **[/COLOR], thank you very much.
[B]
[COLOR=#ff0000]Try(HD0,0):NTFS5:[/COLOR][/B]

mount: mounting /dev/loop0 on /root failed: invalid argument
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting: /proc on /root/proc failed: no such file or directory

[B][COLOR=#ff0000]Target filesystem doesn't have requested /sbin/init.
no init found. Try passing init= bootarg.[/COLOR][/B]

busybox v1.21.1 (ubuntu 1:1.21.0-1ubuntu1) 
built in shell (ash)
Enter 'help' for a list of built in commands.

(inframfs)_

---

### Post by huangzhendong on 2015-03-11
I tried many ways but the error still exist , do anyone help me ? I am now very worried. The following is the info of my error, this happens after I update my Ubuntu to Ubuntu14 , but the electricity suddenly drop out.Then I start up my Ubuntu  and the error comes .


[COLOR=#ff0000]**Try(HD0,0):NTFS5:**[/COLOR]


mount: mounting /dev/loop0 on /root failed: invalid argument
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting: /proc on /root/proc failed: no such file or directory


[COLOR=#ff0000]**Target filesystem doesn't have requested /sbin/init.**[/COLOR]
[COLOR=#ff0000]**no init found. Try passing init= bootarg.**[/COLOR]


busybox v1.21.1 (ubuntu 1:1.21.0-1ubuntu1) 
built in shell (ash)
Enter 'help' for a list of built in commands.


(inframfs)_

---

### Post by mörgæs on 2015-03-11
Merged your five posts. 
Please stop multiposting.

---

### Post by hakuna_matata on 2015-03-11
> **huangzhendong said:**
> but the electricity suddenly drop out
Do you have a backup which was made immediately before upgrade?

If your file system is corrupted, you should correct a possible corrupted Windows file system before correcting the file system within your root.disk. A helpful how-to is [here]("http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html") even if your root.disk is not missing.

If the Windows file system is fixed, you should try to correct the file system of your root.disk. You can use a [LiveCD]("https://help.ubuntu.com/community/LiveCD"). 

Mount your Windows partition with a file manager like nautilus.

Type the following command in a [terminal]("https://help.ubuntu.com/community/UsingTheTerminal") to check and correct your root.disk:
```
sudo e2fsck -pv /media/*/*/ubuntu/disks/root.disk
```

---

