---
title: "Feisty update destroyed my Feisty install"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by apostoj on 2007-04-06
Howdy,

After being stoked that I got online with my wireless card on Feisty, I allowed all the updates to happen....all 280 of them.  
Feisty froze...
Now I can't back to Feisty...I just get the a lot of white text on a black background that goes to root.
It try's and try's to recover it's self it just keeps falling to a command prompt.

I would like to just blow away the Feisty install and not destroy my XP side.
How can I blow away the Feisty with making my pc unbootable to the XP side.

Let's see...I would like to turn my dual boot to a single boot and reinstall Feisty?

Hope this makes since.

John

---

### Post by Najand on 2007-04-06
there is a bug with kernel 2.6.20-10~14
So can you post the contents of your /etc/fstab
ant the output of "fdisk -l" command?

---

### Post by Salpiche on 2007-04-06
if you still have the WinXp disk all you have to do s boot from it, select recovery "r" it will take you to a command  shell, from there select the win part, type your admin passwd, then when on c:\  use command "FIXMBR" then yes, and "FIXBOOT",  then type exit and reboot, it should take you back to the windows logon screen.
I have done this several times for friends that tried linux and had a hard time getting used to it.

---

### Post by apostoj on 2007-04-06
Najand,  I wish I could do what you wish.  However,  I am weak and pathectic at this time and feel like a feeb with my Linux skills.  Grabing and getting and placing is just another part of my learning curve I hope you understand.

How the hell would I do that anyway?

John

---

### Post by apostoj on 2007-04-07
Salpiche,

Thank you for those all those commands I totally forgot about.  It fixed my problem I am online with ubuntu and will continue to struggle with the command line and terminal process.  
I miss all the power and was seduced by the ugly MS monster.

BTW - Vista is just a pig,  Microsoft drove a wedge between myself and that crap.
What a bloated incredible over hype piece of poo poo....

Thanks again
John

---

