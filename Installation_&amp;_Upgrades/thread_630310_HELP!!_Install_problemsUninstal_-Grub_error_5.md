---
title: "HELP!?! Install problems/Uninstal -Grub error 5"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by flip49 on 2007-12-03
Hello

  I am having a problem.

  Here's the story.. I had an sony laptop around which had several problems..(XPhome/15gb) So I had given up on it, and thought I would try to do a complete clean install of Ubuntu on it. The laptop has no cd/dvd so I removed the HD put it into an external case (usb) and plugged it into my Dell laptop to do the install. I ran the install cd from the dell telling the wizard to install into the external HD from the sony.. Everything seemd to go fine, I had the demo running well and the install completed. I then put the HD back into the sony and restarted with no luck (operating system not found?) ..but worst of all my Dell laptop is no longer working and when it boots up I get the message : Grub Loading stage1.5, Please wait... ERROR 5??

  What up with this?? I just want to get my DELL back working!! I tried booting from windows cd and running repair..no luck!?! I'm freaking out cause I need access to files today for work!

 Thanks pleanty for your time and any help!

Phil
PS I have both the alternate and live installs from Ubuntu.


*I also tried putting the Sony HD back in external connecting to Dell and restarting but no luck.. same message appears grub error 5
*When I boot my Dell with either of the install cds (live & alternate) I get this error: Grub error 21

---

### Post by meierfra on 2007-12-04
I think I know  what happened:  Ubuntu installed the boot loader (Grub) to the internal drive of the Dell laptop. But a second part of Grub is on the Sony drive. So you are only able to boot if both hard drives are plugged into the same computer. If this is the case I can give you detailed instruction  how to fix it. But I first need some information:

Plug your Sony hard drive via the external case into your Dell. Try to boot into Ubuntu.
If that did not work, boot the Dell from the Ubuntu Live CD. 

In any case open a  terminal (Applications->Accessories->Terminal)
Type 

```
sudo fdisk -l
```
("l" is a lower case L)

and post the output. Also let  me know whether you were able to boot into Ubuntu or had to use the Live CD.

---

