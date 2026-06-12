---
title: "VMware Tools Installation Problem"
date: 2005-10-11
forum: Installation &amp; Upgrades
---

### Post by linpeiheng on 2005-10-11
My OS is WindowsXP now,I have installed VMware 4.5.2 build-8848 in my windows because I want to try Linux OS.I have installed Ubuntu Linux 5.04 in my VMware Workstation successfully.Then I installed VMware Tools in my virtual Ubuntu Linux.I got this on my screen like this:


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=2826&stc=1&d=1129041384[/IMG]

  
Then when I input "shutdown -r now" to reboot Ubuntu Linux, the X server can not boot again,I got this on my screen like this:


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=2828&stc=1&d=1129041942[/IMG]


  When I chose Yes,I got this:


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=2829&stc=1&d=1129042086[/IMG]


  I am a student in Chinese University,My English is not very good.I like the spirit of Ubuntu,so I tryed to learn Linux.I am a newcomer and  have overcomed many difficulties when I were installing the VMware Tools.I think this is the last problem on installing VMware Tools and appreciate your answer.Enjoy to share with you!:smile:

---

### Post by WildTangent on 2005-10-11
to be honest, i dont think that vmware tools is even neccesary for ubuntu, ive never needed it. just skip it.

-Wild

---

### Post by mlomker on 2005-10-11
VMWare 4.5 may be too old to work with the latest Xorg/kernels.  The new [5.5 release candidate]("www.vmware.com/products/beta/ws/") actually has drop-down selections for Ubuntu.  

Without the tools installed the mouse is pretty difficult to deal with.  I always install the tools.

---

### Post by LiyunYu on 2005-10-11
You may go to /etc/X11 and manually change
the xorg.conf file. There is a line that has your video card and it is something
like this: Device ... PCI (1:0:0) 
comment out that line, - just put a "#" to the most left side of that line, 
then reboot the system, 
Ubuntu should be smart enough to reconfigure your X windows :-)

This works for my Thinkpad 240. 

Thanks, 

Liyun Yu

---

### Post by LiyunYu on 2005-10-11
You may go to /etc/X11 and manually change
the xorg.conf file. There is a line that has your video card and it is something
like this: Device ... PCI (1:0:0) or something like this ( - I did not have my client with me right now)
comment out that line, - just put a "#" to the most left side of that line, 
then reboot the system, 
Ubuntu should be smart enough to reconfigure your X windows :-)

This works for my Thinkpad 240. 

Thanks, 

Liyun Yu

---

### Post by linpeiheng on 2005-10-12
[QUOTE=LiyunYu]You may go to /etc/X11 and manually change
the xorg.conf file. There is a line that has your video card and it is something
like this: Device ... PCI (1:0:0) or something like this ( - I did not have my client with me right now)
comment out that line, - just put a "#" to the most left side of that line, 
then reboot the system, 
Ubuntu should be smart enough to reconfigure your X windows :-)

This works for my Thinkpad 240. 

Thanks, 

Liyun Yu[/QUOTE]


  Thank you for your answer, Liyun Yu. But that does work in my machine.The problem remains and I think VMware Tools Installation program had adjust some option of the X server,it added parameter -br somewhere but this parameter was not acknowledged by Ubuntu Linux. I don't know where the parameter was added,I look over the file /etc/X11/xorg.conf but can not find the parameter -br.Appreciate your answer,Thank you all the time.:smile:

---

### Post by linpeiheng on 2005-10-12
[QUOTE=LiyunYu]You may go to /etc/X11 and manually change
the xorg.conf file. There is a line that has your video card and it is something
like this: Device ... PCI (1:0:0) or something like this ( - I did not have my client with me right now)
comment out that line, - just put a "#" to the most left side of that line, 
then reboot the system, 
Ubuntu should be smart enough to reconfigure your X windows :-)

This works for my Thinkpad 240. 

Thanks, 

Liyun Yu[/QUOTE]


  Do you know where to delete the -br parameter?

---

