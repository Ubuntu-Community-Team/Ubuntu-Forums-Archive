---
title: "Problem updating"
date: 2005-05-25
forum: Installation &amp; Upgrades
---

### Post by Genesius on 2005-05-25
Running XP/Ubuntu dual-boot w/Linux on a second HD. I'm in fine, but can't run either Update Manager or Package Manager. When I try it asks me for my password but nothing happens after I enter it. If I try to run either again before rebooting I get an error "failed to run /usr/sbin/synaptic: child terminated with 1 status"

---

### Post by Xian on 2005-05-25
It sounds like that particular user may not be a member of the [Sudoers](http://www.ubuntulinux.org/wiki/RootSudo) group. Are you able to run other applications or commands with the sudo preface. For example, can you run the command below from a terminal?

```
$ sudo gedit
```

---

### Post by Genesius on 2005-05-25
Nope, it tells me I'm not in the Sudoers file. So how do I get myself added?

---

### Post by Xian on 2005-05-25
This [THREAD](http://www.ubuntuforums.org/showthread.php?t=34184&highlight=knoppix) would be good to read.

---

### Post by Genesius on 2005-05-25
Read the thread, tried the instructions to boot to a root shell & use nano /etc/sudoers to add myself. When I try to save the file, I get an error that it can't overwrite the file because it's read-only. . .
 ](*,)

---

### Post by Genesius on 2005-05-26
Got it!   \\:D/ 

Was looking through some other threads, and found a comment about booting into recovery mode. Did that & was able to use visudo to add myself to the sudoers file.

---

### Post by cu_ on 2005-06-12
[QUOTE=Genesius]Got it!   \\:D/ 

Was looking through some other threads, and found a comment about booting into recovery mode. Did that & was able to use visudo to add myself to the sudoers file.[/QUOTE]
 I had the same problem.  I fixed it by adding the user to the admin group.  By default, ubuntu sets up everyone in the admin group as sudoers.  So, all you have to do is add the user to admin group and off you go....

---

