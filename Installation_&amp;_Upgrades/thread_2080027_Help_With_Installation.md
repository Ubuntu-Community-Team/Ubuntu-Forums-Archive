---
title: "Help With Installation"
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by MegaNaught on 2012-11-02
So, I have decided to switch to a Linux OS (I am tired of Windows bogging down my computer), but I am struggling trying to get Ubuntu installed. 

I have a Dell Inspiron 1525 (32 bit)and I have downloaded Ubuntu (the 32 bit version) and burned it onto a CD. I click to "Install or Run program" and then click on "Demo or Fully Install" and am given the choices of Reboot now, manually reboot later, or reboot from CD. I have rebooted, several times, but I always reboot right back to Windows with no choice to install Ubuntu. I have been working on this for four hours now and have hopped from site to site (including Ubuntu) trying to figure out what the problem may be. However, I am struggling. I have not updated BIOS yet as I am waiting to see if that could actually be the problem or not. Any help would be greatly appreciated!

Thanks,
MegaNaught

---

### Post by tokyobadger on 2012-11-02
Some more info would help - I guess you are using the Windows installer of 12.10 (32-bit)?

Are you sure it's a CD? Should be a DVD as far as I know.

Have you set your BIOS to boot the PC from CD before hard-disk?

---

### Post by ibjsb4 on 2012-11-02
Yes, more info please.

Is this a wubi install? Are your installing ubuntu inside windows.

---

### Post by critin on 2012-11-02
> **MegaNaught said:**
> So, I have decided to switch to a Linux OS (I am tired of Windows bogging down my computer), but I am struggling trying to get Ubuntu installed. 

I have a Dell Inspiron 1525 (32 bit)and I have downloaded Ubuntu (the 32 bit version) and burned it onto a CD. [COLOR=Red]**I click to "Install or Run program" and then click on "Demo or Fully Install" and am given the choices of Reboot now, manually reboot later, or reboot from CD. I have rebooted, several times, but I always reboot right back to Windows with no choice to install Ubuntu.**[/COLOR] I have been working on this for four hours now and have hopped from site to site (including Ubuntu) trying to figure out what the problem may be. However, I am struggling. I have not updated BIOS yet as I am waiting to see if that could actually be the problem or not. Any help would be greatly appreciated!

Thanks,
MegaNaught

Is Windows still open here?  You don't RUN a live cd/dvd of linux from windows like you would any other cd.  It must be booted.

Set the bios or use the Boot Key shown on the bios screen when it first boots up.  Hit the boot key before windows starts to load.   Choose to boot from the dvd.

The live ubuntu will come up and you can choose how to run it.  I suggest TRY live and try it out before installing.  It can be then be installed from the live dvd's desktop.

Edited to add:  UNLESS you are installing Wubi as asked by post # 3.

---

### Post by MegaNaught on 2012-11-03
First of all, yes, it is a DVD. I goofed on typing that one. Secondly, I think it is a wubi install, but I don't want to run it inside of windows, I want to partition my hard drive (I have almost 40gb of space available). 

I clicked the "reboot now" option, but did not hit the boot key. I guess in my naivete I thought the boot option would automatically come up. I will try rebooting and hitting the boot key. I will let you all know if that works. 

Also, thank you very much for the quick replies.

---

### Post by ibjsb4 on 2012-11-03
If you Have the wubi install dvd it cannot be used to install ubuntu on a separate partition.

Download from the link below.  The second choice on the list.  I say second choice because your lappy is 64 bit and even though 32 bit will work just fine you will squeeze a little bit more performance out of it.

Also 12.04 is a bit more stable than 12.10 and I think a better choice for a beginner.

Edit:

[http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml](http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml)

---

### Post by MegaNaught on 2012-11-03
> **ibjsb4 said:**
> If you Have the wubi install dvd it cannot be used to install ubuntu on a separate partition.

Download from the link below.  The second choice on the list.  I say second choice because your lappy is 64 bit and even though 32 bit will work just fine you will squeeze a little bit more performance out of it.

Also 12.04 is a bit more stable than 12.10 and I think a better choice for a beginner.

Edit:

[http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml](http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml)

That link you placed is not wubi, correct? Again, I appreciate the help.

---

### Post by tokyobadger on 2012-11-03
@MegaNaught: what is the iso called? The regular installer should be ubuntu-12.10-desktop-i386.iso (for 32-bit 12.10 release) and weighs in at 753M

[this would be the page where you choose 12.10 or 12.04 install images or opt for the wubi installer](http://www.ubuntu.com/download/desktop)

If you want a separate install skip the wubi and grab one of the images 12.10/12.04 32-bit (if you haven't already got it on the dvd you are trying to boot from) at the links on this page

You will need to set your PC to boot from CD before HDD in the BIOS

---

### Post by ibjsb4 on 2012-11-03
> **MegaNaught said:**
> That link you placed is not wubi, correct? Again, I appreciate the help.

No that is not wubi, you will be given the option to install side by side.  And 12.04 will fit on a CD; DVD is not necessary.

Edit:  Also burn at low speed.

---

### Post by ibjsb4 on 2012-11-03
Also if you don't already know.  You can use "Thread Tools" located at about the top of this thread to subscribe for email notification when you get a reply.  Just something handy to know  :)

Tis bedtime.  Good night and good luck ..

---

### Post by MegaNaught on 2012-11-03
> **tokyobadger said:**
> @MegaNaught: what is the iso called? The regular installer should be ubuntu-12.10-desktop-i386.iso (for 32-bit 12.10 release) and weighs in at 753M

[this would be the page where you choose 12.10 or 12.04 install images or opt for the wubi installer](http://www.ubuntu.com/download/desktop)

If you want a separate install skip the wubi and grab one of the images 12.10/12.04 32-bit (if you haven't already got it on the dvd you are trying to boot from) at the links on this page

You will need to set your PC to boot from CD before HDD in the BIOS

This is the iso I was using: ubuntu-12.10-desktop-i386.iso. I think I was accidentally opting for the wubi. Thank you for clearing that up. I appreciate it.

> **ibjsb4 said:**
> No that is not wubi, you will be given the option to install side by side.  And 12.04 will fit on a CD; DVD is not necessary.

Edit:  Also burn at low speed.

That's what I am downloading now and when it gets done, I am going to burn it and try booting with it. Once again, thank you.

---

### Post by tokyobadger on 2012-11-03
I was about to say that you couldn't have been accidentally opting for wubi, BUT, I just took a look inside my own 12.10 iso and saw that wubi.exe is included there.

Let me clarify, I don't have windows on any machine at home (haven't had since 2002) so I had no idea that wubi.exe was on the regular install iso as well.

I guess what happened is that after you burned the iso to DVD wubi.exe autoran and that's where you got the dialogue boxes you initially referred to.

Whether you use the 12.10-i386 or the 12.04-i386 (that you're now downloading) I am now 99% certain your problem is the boot order of your devices in your BIOS which is why on reboot you went straight back into windows namely because the HDD is the first selected device

Switch the order to boot from CD first and you should see the Ubuntu installer load up

---

### Post by MegaNaught on 2012-11-03
> **tokyobadger said:**
> I was about to say that you couldn't have been accidentally opting for wubi, BUT, I just took a look inside my own 12.10 iso and saw that wubi.exe is included there.

Let me clarify, I don't have windows on any machine at home (haven't had since 2002) so I had no idea that wubi.exe was on the regular install iso as well.

I guess what happened is that after you burned the iso to DVD wubi.exe autoran and that's where you got the dialogue boxes you initially referred to.

Whether you use the 12.10-i386 or the 12.04-i386 (that you're now downloading) I am now 99% certain your problem is the boot order of your devices in your BIOS which is why on reboot you went straight back into windows namely because the HDD is the first selected device

Switch the order to boot from CD first and you should see the Ubuntu installer load up

Success!! I have successfully installed Ubuntu and I am using it as I type this. It was simply needing to hit the boot key and install from a CD/DVD RW. 

I have left Windows on (just partitioned the hard drive) for now until I get used to the Linux system. 

Thank you everyone for your help!

---

### Post by ibjsb4 on 2012-11-03
Congrads  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by tokyobadger on 2012-11-03
Congratulations - have fun

---

### Post by critin on 2012-11-05
<snipped as issue is solved>
Good luck!

---

