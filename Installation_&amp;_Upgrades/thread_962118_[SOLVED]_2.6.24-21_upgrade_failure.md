---
title: "[SOLVED] 2.6.24-21 upgrade failure"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by flash19 on 2008-10-28
Ok, I upgraded a while ago to the latest kernel (2.6.24-21)  And my computer won't boot into it. It just hangs on the boot screen.  If I Use recovery mode I get:
==============
Bug:  soft lockup-CPU#0 Stuck for 11s!  [Modprobe:1466]

Pid: 1466,  Comm: Modprobe   Tainted :G       D (2.6.24-21 generic #1)
Eip: 0060:  [<co31c3f7>]  Eflags:00000286 CPU:0
Eip is at _Spin_lock + 0x7/0x10


Then there is a bunch more junk that I didn't feel like copying :)


I am using the -19 kernel right now, and wonder if I could just skip 21 and get 8.10?  Is that possible?  Otherwise tell me how to uninstall 21 and I'll see what I can do from there.

---

### Post by lptr on 2008-10-29
Good morning,

> **flash19 said:**
> ...
I am using the -19 kernel right now, and wonder if I could just skip 21 and get 8.10?  Is that possible?  Otherwise tell me how to uninstall 21 and I'll see what I can do from there.

In your case I would suggest to modify Grubs menu.lst as suggested here:
[http://ubuntuforums.org/showpost.php?p=5975048&postcount=22](http://ubuntuforums.org/showpost.php?p=5975048&postcount=22)

rob*

---

### Post by alexcckll on 2008-10-29
Folks, a few of us are trying to get a wide view of this issue.. please oculd you join us on this thread - [http://ubuntuforums.org/showthread.php?t=948584&page=13](http://ubuntuforums.org/showthread.php?t=948584&page=13)

We're trying to get what would be termed a Master Call (in corporate IT terms) raised.

---

### Post by flash19 on 2008-10-29
>  Re: 2.6.24-21 upgrade fails
I edited the text file at
/boot/grub/menu.lst

and commented out the lines that refer to the new kernel 2.6.24-21-generic, leaving the file as before with
2.6.24-21-generic

I did not uninstall the new kernel.

What I want to know is will I run into problems if I continue with the old kernel? Is it important to change to the new kernel?

(It didn't work for me, but I didn't begin the long process of figuring out why.)

Is he saying to remove all references to the -21?  "leaving the file as before with
2.6.24-**19**-generic"


alexcckll, Do you want my complete post above dumped into the other thread?

---

### Post by alexcckll on 2008-10-29
> **flash19 said:**
> Is he saying to remove all references to the -21?  "leaving the file as before with
2.6.24-**19**-generic"


alexcckll, Do you want my complete post above dumped into the other thread?
Would be good... 
Could you also chuck in more detail about your machine?  Say - make, model, output from lspci etc?

---

### Post by flash19 on 2008-11-08
I solved my problems by going to 8.10 everything is working fine so far!  Thanks alexcckll for trying to help!

---

