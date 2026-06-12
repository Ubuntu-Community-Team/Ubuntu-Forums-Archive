---
title: "Failed to install Gutsy"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Bo Rosén on 2007-10-18
I already have Feisty running on this machine but wanted to make a clean install.  I get dumped into a console with the following message:
```

udevd-even [2266]:run_program:'/sbin/modprobe" abnormal exit

```

Any ideas?

---

### Post by tech9 on 2007-10-18
make sure that you manually format the partition if you want a clean install, otherwise you will also have the fiesty partition as well

---

### Post by oedipuss on 2007-10-18
same problem, we must have typed our posts at the same time :)

---

### Post by pipolibo on 2007-10-18
I have exactly the same problem, the latest kernels failed to boot in beta version so i try to do a clean install, but the screen shows that message, hope there is a solution, using old kernel right now.
I'd read in the forums and only feisty related messages, none about gutsy except yours.

---

### Post by tech9 on 2007-10-18
> **pipolibo said:**
> I have exactly the same problem, the latest kernels failed to boot in beta version so i try to do a clean install, but the screen shows that message, hope there is a solution, using old kernel right now.
I'd read in the forums and only feisty related messages, not about gutsy except yours.

no problems installing here, but I made sure to install gutsy on a clean HD

---

### Post by oedipuss on 2007-10-18
It occurs way before installing. I can't even run the liveCD defects test, same message.
Also, there's something like :
BUG: kernel cannot dereference NULL pointer at address 0x000000
when I try to run it without the 'splash' and 'quiet' options. (F6 at selection list)
Do you see that too ?

---

### Post by oedipuss on 2007-10-18
Hmm removing some of the hard disks seems to bypass the problem.. 
Too bad I had to remove the one I was planning to install gutsy on. 
I just hope it boots after installation with the drives connected

---

### Post by Bo Rosén on 2007-10-18
> **oedipuss said:**
> 
Do you see that too ?

No, I get another message.
The install proper doesn't start for me either. Booting without splash and quiet gives me the following bit.
```
 [64.180479] end_request: I/O error, dev fd0, sector 0
```The floppy drive? This is an odd one.

---

### Post by oedipuss on 2007-10-18
Ah yes, had that too, but then disabling the floppy drive made it go. The one about the kernel is some pages upwards, just before the modprobe:abnormal exit error.
There were also some related messages about hda (or sda accordingly). 
I think it was disconnecting my hda that bypassed it.

---

### Post by Bo Rosén on 2007-10-18
I couldn't see any errors re drives, other than the one about fd0, but at the rate things scroll by I could easily have missed something. Disabling the floppy in the BIOS makes that message go away but gives me other errors. just before modprobe exits abnormally 

```
EIP: [<c01fe8ab>] strstr+0x1b/0x50 SS:ESP 0068:dfe2dcd4 udevd_event [2261] etc etc...
```

---

### Post by pipolibo on 2007-10-18
I disconnected the slave HD and it works, for now,,,

---

### Post by oedipuss on 2007-10-18
Well, after installation, the problem persists. It's one of the hard disks for some obscure (at least to me) reason. Apart from that , however,  with the culprit removed, gutsy runs smooth and fast.

Try removing your hard disks one by one. Hopefully, the one you wish to install gutsy on will work.

---

### Post by Bo Rosén on 2007-10-18
Thanks, I'll try that. I may not have time until Saturday though.

---

### Post by fran6co on 2007-10-19
I'm having the same problem with Kubuntu 7.10.
I have two hard drives, a Western Digital and a Seagate. The Seagate seems to be causing the problem. If I disconnect the hard drive it boots. In Feisty and previous versions I had no problem.
I can't get a full report on the bug because I don't know how to get it. (I can't save it anywhere without the ide working).
It seems to be a problem with the 2.6.22 modules.
Thanks in advance

---

### Post by Bo Rosén on 2007-10-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/154591](https://bugs.launchpad.net/ubuntu/+bug/154591) [br].[/br] ---------------------------- [br].[/br] [br].[/br]                 Disabling disks didn't work. I've added a comment to bug 154591

---

### Post by bobg-m on 2007-10-21
Try adding all_generic_ide as a boot option just after splash on the live cd bootmenu (hit F6). This gets the live CD up and running, then I run into these problems here.....

[HTML]http://ubuntuforums.org/showthread.php?t=584601[/HTML]

---

### Post by Bo Rosén on 2007-10-21
I am an idiot. I saw that thread earlier and tried all_generic_ide without success. I spelled it wrong. Now writing this from the live cd. Thanks.

---

