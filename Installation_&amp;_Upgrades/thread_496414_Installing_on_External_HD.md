---
title: "Installing on External HD"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by snooty on 2007-07-09
Hi,

I want to install Ubuntu onto an external HD which is connected through a PCMCIA USB adaptor.

Is it possible? Should I install GRUB onto the external or internal HD?
Will GRUB be able to recognize the PCMCIA card?

Please help.

---

### Post by snooty on 2007-07-09
---bump---

Help please.

---

### Post by Onay on 2007-07-09
I'm a newbie, so I won't be able to offer you any help, but I can tell you about my experiences.

I installed ubuntu 7.04 fiesty fawn on my external hard drive, partitioned it into an nfts section, a linux section, and a shared section. After installing, the GRUB boot loader was installed on my main, internal hard drive. I couldn't boot to windows unless I did so through the external hard drive to the internal one. Confusing, I know. So I went into windows and got a program that I could use to restore my Master Boot Record which was corrupt due to GRUB (it was called MBR fix). Unfortunately, now, When I try to boot from the external hard drive, I get an error message that says it cannot load the OS.

So I recommend you do more research than I did so that you don't experience the same problems. Also if anyone can help me boot into ubuntu from the BIOS without getting that error message then that would be great.

---

### Post by acelin on 2007-07-09
I need help as well with grub- her is what I did-

Put Cd and External hard drive in- boot from cd- select install- 
Select install on desktop when liverun has finished
Select manual parttion- 
On step seven, there is an advanced option- i think this is where you would change where grub was located- I have had the same problems, with grub messing up my normal boot options. 

Looks like we have to figure out what to type in on step 7's advanced options in order to have grub install on the external hard drive.

Help!!!!

This was much easier on Drapper!

---

### Post by confused57 on 2007-07-09
> **acelin said:**
> I need help as well with grub- her is what I did-

Put Cd and External hard drive in- boot from cd- select install- 
Select install on desktop when liverun has finished
Select manual parttion- 
On step seven, there is an advanced option- i think this is where you would change where grub was located- I have had the same problems, with grub messing up my normal boot options. 

Looks like we have to figure out what to type in on step 7's advanced options in order to have grub install on the external hard drive.

Help!!!!

This was much easier on Drapper!
You'll need to type in the external hard drive designation assigned when you partitioned & installed Ubuntu(e.g. /dev/sda, /dev/sdb)...if you have only 1 internal hard drive, your external drive is probably /dev/sdb, which is what you would enter in order to install grub to the mbr of your USB drive.

---

### Post by snooty on 2007-07-10
For those who are looking, here are the resources I found regarding dual boot:

[_Link #1_]("http://ubuntuforums.org/showthread.php?t=80811")
[_Link #2_]("http://users.bigpond.net.au/hermanzone/")

And here is one that looks like the solution for me:

[_Click Me_]("http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html?ca=dgr-lnxw02aFireBoot")

However, I can't understand them. I'm a newbie. I just tried Ubuntu LiveCD and I thought: cool, I want to use it. But I definitely can't follow what these links say...

So, may I make a suggestion to the development team: why not integrate a simple dual boot solution in the next Ubuntu release and make it portable? Coz I believe so many people would appreciate and benefit from it.

Thanks and bye.

---

