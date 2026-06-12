---
title: "Problem in  &quot;Linux Kernel v2.6.18.1 Configuration&quot; - ubuntu 9.10"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by sindu4sind on 2010-10-22
**Using Ubuntu 9.10**
 I am installing LTTng Kernel, but facing one problem with kernel configurations:

In installation guide it is mentioned that:[INDENT]**make menuconfig**

**   go to the "General setup" section**
**     Select the following options :**
[B]     
[*] Prompt for development and/or incomplete code/drivers[/B]
[B]     
[*] Activate markers[/B]
[B]     
[*] Immediate value optimization (optional)[/B]
**   Select <Exit>**
**   Select <Exit>**
**   Select <Yes>**
[/INDENT]But in my case situation is different.
Inside General Setup options are : 
[INDENT][B](n) Local version - append to kernel release
[ ] Automatically append version information to the version string[/B]
**  [ ] Support for paging of anonymous memory (swap)  **
**  [ ] System V IPC  **
**  [ ] POSIX Message Queues  **
**  [ ] BSD Process Accounting  **
**  [ ] Export task/process statistics through netlink (EXPERIMENTAL)  **
**  [ ] Auditing support  **
**  [ ] Kernel .config support  **
[B]  
[*] Kernel->user space relay support (formerly relayfs)  [/B]
**  (n) Initramfs source file(s)  **
**  (0) User ID to map to 0 (user root)  **
**  (0) Group ID to map to 0 (group root)  **
**  [ ] Optimize for size (Look out for broken compilers!)  **
**  [ ] Configure standard kernel features (for small systems) --->  **
**  [ ] Linux Trace Toolkit Instrumentation Support**
[/INDENT]I searched each option of kernel configuration inside and outside of general setup but following 2 settings are not available:[INDENT][B]      
[*] Activate markers[/B]
[B]     
[*] Immediate value optimization (optional)[/B]
[/INDENT]although i found[FONT=Courier New] ***[FONT=Century Gothic][SIZE=2]prompt for development and /or incomplete code/drivers[/SIZE][/FONT]***[/FONT] inside ***code maturity level option***. (ie; **Code maturity level options  &#8594; [ ] Prompt for development and/or incomplete code/drivers**)
 
I am new in using ubuntu and specially terminal,  
 so I am looking for a detailed response..

[SIZE=2]**  Raheel A. Memon**[/SIZE]

---

