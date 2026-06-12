---
title: "Openoffice 3?  Xchat?"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by american.swan on 2008-10-22
I am having trouble with these two programs.

Synaptic seems to say I have OO3 installed, but it isn't in my menu lists and I don't know how to get it started.  It seems parts of 2.4 are still installed.

to fix this problem I thought I'd go to chat on xchat, but found that it doesn't work either.

Any suggestions as to how I can get oo working at least.

---

### Post by FuturePilot on 2008-10-22
How did you install OO.o3? 

Are there any errors when running xchat from the terminal?

---

### Post by american.swan on 2008-10-22
> **FuturePilot said:**
> How did you install OO.o3? 

Are there any errors when running xchat from the terminal?

I probably did it all wrong. 

I installed oo3 on top of 2.4 before upgrading using the .deb files. Next I couldn't upgrade online, had to use the Alt ISO.  

I am "using last booted kernal"  Unsure the number.  all my kernels changed over to intrepid.   I didn't manually uninstall old kernels so before I updated I had like 5 kernels to choose from. After upgrading,the kernel on the top of the list at boot time crashes with some error (maybe init.d) and refuses to even reboot without manual assistance.

So something is messed up.  I am "updated" it seems.  Maybe there is some option I need to click to get the latest beta every few days.

I am at work on the problem machine.  Maximum reply time approximately 40minutes

command line: xchat gives me "you must install it" 
I try apt-get
I get The following packages have unmet dependencies:
  xchat: Depends: libperl5.8 (>= 5.8.8) but it is not going to be installed
E: Broken packages

---

### Post by american.swan on 2008-10-23
Found out that after upgrading my repositories hadn't changed or changed in an unhelpful manner.  

Now I might get somewhere.  Updating everything.  We'll see what happens after this update.

---

