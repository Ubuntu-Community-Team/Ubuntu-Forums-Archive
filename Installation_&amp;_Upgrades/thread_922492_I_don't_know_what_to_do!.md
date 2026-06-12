---
title: "I don't know what to do!"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by daveaellis on 2008-09-17
I am new to Linux and Ubuntu.
I have loaded the latest version (8.04.1 - desktop -i386) onto a Samsung R20 laptop running Vista Home.
This is so I can try to learn how to use Linux.

It allows me to choose to boot from Ubuntu or Vista, but when I boot from Ubuntu it doesn't produce a desktop. 
Instead it gets to a point where it shows :

ubuntu@ubuntu:~$

what is it waiting for from me please?

---

### Post by mikewhatever on 2008-09-17
What are your computer specs? Try **startx** command.

---

### Post by daveaellis on 2008-09-19
thank you mikewhatever for moving me forward (I'm a complete novice).
I typed in startx, then return
got messages including :
"(EE)Screen(s) found, but none have a useable configuration"
"Fatal server error : no screens found, giving up"

Now I don't at this stage know what all this means, or what I need to do about it, but Google searched and found the following site:

[http://www.linlap.com/wiki/Samsung+R20#Summary](http://www.linlap.com/wiki/Samsung+R20#Summary)

and I now intend to see if I can find a solution there

thanks again

---

### Post by mikewhatever on 2008-09-19
Good luck. Try the guide below too.
[http://psychocats.net/ubuntu/nox](http://psychocats.net/ubuntu/nox)

---

### Post by maddoggschank on 2008-09-19
I have the same problem as this guy, just installed vista fine, then ubuntu after giving it its own partition but at the restart i do not get the option to boot from eather vista or 8.04, it goes straight to ubuntu.  I am not at all smart when it comes to computers, esp. command line, but i can cut and past,
 this might be a dumb question but dont the 2 OSs' need their own partition? or can they be installed on the same partition?
  Any help is greatly appreciated!

---

### Post by simtaalo on 2008-09-19
they can be installed on the same partition, if you do a search there is lots of information about dual-boot systems

---

### Post by mikewhatever on 2008-09-20
> **maddoggschank said:**
> I have the same problem as this guy, just installed vista fine, then ubuntu after giving it its own partition but at the restart i do not get the option to boot from eather vista or 8.04, it goes straight to ubuntu.  I am not at all smart when it comes to computers, esp. command line, but i can cut and past,
 this might be a dumb question but dont the 2 OSs' need their own partition? or can they be installed on the same partition?
  Any help is greatly appreciated!

Normally, you do need separate partitions for different OSs. However, Ubuntu has incorporated a project called Wubi, to allow installing to a file within NTFS partition. I think the option appears at the partitioning stage and is called 'Install in Windows'.

---

