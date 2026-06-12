---
title: "How to download all the sources files of Ubuntu Kernel?"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by erogol on 2011-02-11
I have an assignment as a CS student to code over Ubuntu Kernel but I am surely a beginner. I need to download all the source files of the Ubuntu kernel source code, make some changes then compile and use it as a custom kernel. May you give some suggestions and commands to achieve these?

Thanks every one!

---

### Post by tejendra on 2011-02-11
hi 
if you want to see the code then visit 
[COLOR=#0e774a]**lxr**.linux.no/linux/[/COLOR]
[COLOR=#0e774a][/COLOR] 
or if you want to install and compile linux kernel then download a kernel from 
**kernel.org/** and compile it with some commands listed below
Step 1: Extract the file by using
tar -xvf [File Name]
and after extracting go into the extracted directory and issue below listed commands;
 
[COLOR=black][FONT=Calibri]a.[/FONT][/COLOR][COLOR=black][FONT=Times New Roman]       [/FONT][/COLOR][COLOR=black][FONT=Calibri]Make menuconfig[/FONT][/COLOR]
[COLOR=black][FONT=Calibri]b.[/FONT][/COLOR][COLOR=black][FONT=Times New Roman]      [/FONT][/COLOR][COLOR=black][FONT=Calibri]Make [/FONT][/COLOR]
[COLOR=black][FONT=Calibri]c.[/FONT][/COLOR][COLOR=black][FONT=Times New Roman]       [/FONT][/COLOR][COLOR=black][FONT=Calibri]Make modules[/FONT][/COLOR]
[COLOR=black][FONT=Calibri]d.[/FONT][/COLOR][COLOR=black][FONT=Times New Roman]      [/FONT][/COLOR][COLOR=black][FONT=Calibri]Make modules_install[/FONT][/COLOR]
[COLOR=black][FONT=Calibri]e.[/FONT][/COLOR][COLOR=black][FONT=Times New Roman]      [/FONT][/COLOR][COLOR=black][FONT=Calibri]Make install[/FONT][/COLOR]
this will install and compile your kernel.
 
**if your problem got solved mark this thread as solved**

---

### Post by oldos2er on 2011-02-11
If you're using 10.10, try **apt-get source linux-image-2.6.35-26-generic**

---

### Post by erogol on 2011-02-13
> **tejendra said:**
> hi 
if you want to see the code then visit 
[COLOR=#0e774a]**lxr**.linux.no/linux/[/COLOR]
[COLOR=#0e774a][/COLOR] 
or if you want to install and compile linux kernel then download a kernel from 
**kernel.org/** and compile it with some commands listed below
Step 1: Extract the file by using
tar -xvf [File Name]
and after extracting go into the extracted directory and issue below listed commands;
 
[COLOR=black][FONT=Calibri]a.[/FONT][/COLOR][COLOR=black][FONT=Times New Roman]       [/FONT][/COLOR][COLOR=black][FONT=Calibri]Make menuconfig[/FONT][/COLOR]
[COLOR=black][FONT=Calibri]b.[/FONT][/COLOR][COLOR=black][FONT=Times New Roman]      [/FONT][/COLOR][COLOR=black][FONT=Calibri]Make [/FONT][/COLOR]
[COLOR=black][FONT=Calibri]c.[/FONT][/COLOR][COLOR=black][FONT=Times New Roman]       [/FONT][/COLOR][COLOR=black][FONT=Calibri]Make modules[/FONT][/COLOR]
[COLOR=black][FONT=Calibri]d.[/FONT][/COLOR][COLOR=black][FONT=Times New Roman]      [/FONT][/COLOR][COLOR=black][FONT=Calibri]Make modules_install[/FONT][/COLOR]
[COLOR=black][FONT=Calibri]e.[/FONT][/COLOR][COLOR=black][FONT=Times New Roman]      [/FONT][/COLOR][COLOR=black][FONT=Calibri]Make install[/FONT][/COLOR]
this will install and compile your kernel.
 
**if your problem got solved mark this thread as solved**


Is there any difference between any other kernel that I'll download from another sources or is there any official version of kernel?

---

### Post by tejendra on 2011-02-15
there is no diffrence if you are using linux kernel. if the files don't have dpendecies you can also get it from any source. The same procedure will work on all the kernels.

---

