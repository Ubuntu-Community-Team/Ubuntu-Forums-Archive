---
title: "Ubuntu control panel"
date: 2022-06-09
forum: Installation &amp; Upgrades
---

### Post by lts1375 on 2022-06-09
Ubuntu appears in my software center but it doesn’t appear in my control center, therefore I can’t open it. I’ve tried all the basic stuff like rebooting and reinstalling but nothing works. (I’m using an hp laptop btw, I don’t know if that affects anything)

---

### Post by deadflowr on 2022-06-09
> Ubuntu appears in my software center 
What software center?

---

### Post by yancek on 2022-06-09
What control center and what control panel are you referring to?  What do you mean by doesn't appear?  Ubuntu is an operating system not an application.  What are you rebooting and reinstalling?

---

### Post by TheFu on 2022-06-09
Ubuntu is an entire operating system, not a program run under some other OS.

---

### Post by mIk3_08 on 2022-06-09
> **lts1375 said:**
> Ubuntu appears in my software center but it doesn&#8217;t appear in my control center, therefore I can&#8217;t open it. I&#8217;ve tried all the basic stuff like rebooting and reinstalling but nothing works. (I&#8217;m using an hp laptop btw, I don&#8217;t know if that affects anything)
Please elaborate more about your issues/concern as many here in this community are will to help you. 
> **yancek said:**
> What control center and what control panel are you referring to? What do you mean by doesn't appear? Ubuntu is an operating system not an application. What are you rebooting and reinstalling?
Yes, yancek. Maybe this guy really needs help. 
> **TheFu said:**
> Ubuntu is an entire operating system, not a program run under some other OS.
Yeah. That's right TheFu. Operating System is the driver of your system hardware while application software is one of the passenger who rides with the driver Operating System.

---

### Post by TheFu on 2022-06-09
I suspect the OP is looking inside MS-Windows and sees "Ubuntu" there somewhere.
My point is that Ubuntu needs to be booted into either as a VM or dual-boot to be used.
MSFT has something that is sorta like Ubuntu that runs under WSL2, but this has some limitations that aren't part of normal Ubuntu setups.

---

### Post by QIII on 2022-06-10
@lts1375:  a picture would be worth a thousand words in this case.

Please use the attachment facility (the paperclip) to attach an image to a new post.  Please do not simply try to paste an image into the post.

---

### Post by mIk3_08 on 2022-06-10
> **QIII said:**
> @lts1375:  a picture would be worth a thousand words in this case.
Please use the attachment facility (the paperclip) to attach an image to a new post.  Please do not simply try to paste an image into the post.
Yes. I agree with QIII. screenshot would be best if it shown to us here in this community. Regards and Cheers.

---

### Post by lts1375 on 2022-06-10
When i click the windows button. I go to my software center and under applications i can see Ubuntu. The status also stated that the operating system is installed on my computer. However, when i go to my control panel, and i go to my programs &  features, Ubuntu is not listed anywhere. But other software like R runs perfectly fine and appears in my programs& features. Unfortunately, I can’t post a picture for data integrity reasons

---

### Post by QIII on 2022-06-10
Hello!

Please post an image, first redacting whatever is necessary to protect yourself.  That will help us understand your difficulty.
 
Are you trying to do this on a Windows machine?  The terminology you are using suggests that such is the case.

Ubuntu is not a program like an R IDE or Microsoft Office.  It is an operating system like Windows, IoS, MacOS, Android, etc.  There is, however, a subsystem called Windows Subsystem for Linux (WSL) that allows Windows to virtualize minimal versions of some Linux distributions.  It's not something you click to start like Excel.

---

### Post by TheFu on 2022-06-10
What is this "windows button?"  Do you mean the "Super key"? [https://help.ubuntu.com/stable/ubuntu-help/keyboard-key-super.html.en](https://help.ubuntu.com/stable/ubuntu-help/keyboard-key-super.html.en)

Also, which OS are you booting?  It sounds like  MS-Windows.  Ubuntu isn't MS-Windows.  They are vastly different operating systems.

---

### Post by MAFoElffen on 2022-06-11
Well...

To A Windows OS user... Windows 10, 11, Server... Who is using a Windows Store version of Ubuntiu,that installs under WSL2... It is confusing to them.

They /=don't realize that even though WSL is said to be a compatibility layer. that Ubuntu is running as a Virtual Machine with Hyper-V extensions under the covers. Ubuntu is available as an "App: in the Windows Store, which is a VM running in WSL2.

As such, there is no control of it from Control Panel in Windows. It is a stand alone OS, running as a VM. It's a good taste to introduce Ubuntu to new users. What they should know, is that it is a stand-alone OS, but running wirthin Windows as a VM...

Translation of Control Panel in Windows to something in Ubuntu = "Settings"...

(EDIT: Assumption of a needed Tech translation.)

---

