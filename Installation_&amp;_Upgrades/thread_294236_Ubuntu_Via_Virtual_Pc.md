---
title: "Ubuntu Via Virtual Pc"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by only_samurai on 2006-11-06
Hey, I'm trying to install Ubuntu onto my WinXp machine but I want to use a VirtualPc. I've set it up with a harddisk and 512 ram, but it gets stuck installing ubuntu. Here is what it displays:
[   30.620409] invalid opcode: 0000 [#1]                                       
[   30.661215] Modules linked in:                                              
[   30.679013] CPU:    0                                                       
[   30.679037] EIP:    0060:[<c0102035>]    Not tainted VLI                    
[   30.679083] EFLAGS: 00000246   (2.6.17-10-386 #2)                           
[   30.680462] EIP is at mwait_idle+0x15/0x30                                  
[   30.680649] eax: c03ce008   ebx: c03ce000   ecx: 00000000   edx: 00000000   
[   30.680834] esi: c03ce008   edi: c03c2800   ebp: 00495007   esp: c03cffdc   
[   30.681057] ds: 007b   es: 007b   ss: 0068                                  
[   30.681305] Process swapper (pid: 0, threadinfo=c03ce000 task=c03516a0)     
[   30.681533] Stack: 01020800 00039400 c0101fdc c03d067b c02d875b c03d0210 000
0000 c041bd40                                                                  
[   30.687083]        c0100199                                                 
[   30.687366] Call Trace:                                                     
[   30.687845]  <c0101fdc> cpu_idle+0x1c/0x60  <c03d067b> start_kernel+0x1fb/0x
d0                                                                             
[   30.688772]  <c03d0210> unknown_bootoption+0x0/0x270                        
[   30.689250] Code: e8 c1 32 1c 00 90 eb ca 8d b4 26 00 00 00 00 8d bc 27 00 0
 00 00 56 53 fb bb 00 e0 ff ff 31 c9 21 e3 8d 73 08 eb 13 89 f0 89 ca <0f> 01 c
 8b 43 08 a8 08 75 0c 89 c8 0f 01 c9 8b 43 08 a8 08 74                         
[   30.706079] EIP: [<c0102035>] mwait_idle+0x15/0x30 SS:ESP 0068:c03cffdc     
[   30.723251]  <0>Kernel panic - not syncing: Attempted to kill the idle task!
[   30.724276]                                                                 
i'm new to linux so this makes very little sense to me. anyone have a clue what s wrong with my install? i used the md5 checksum and it matches so i know its not corrupted.

---

### Post by spd106 on 2006-11-07
I tried this recently with dapper, but ran out of lab time at Uni so I didn't finish the install. It did appear to lock up towards the end though.

Might be better to use the alternative CD. I'll give it a go next time I'm in the lab.

---

### Post by spd106 on 2006-11-08
Ok, I had no problems installing Dapper from the Desktop CD. To get it to boot you need to select safe graphics mode and vga 640x480x32. Then just go through the install procedure.

Edgy doesn't seem to want to work properly, the safe mode workaround isn't working. 

Hmmm...

---

### Post by MacPC on 2006-11-08
I tried to install Ubuntu on Virtual PC. But somehow the window come out too small. When it comes to the partitioner page, I couldn't navigate. Tried both live CD and alternative method, none of them work.

---

### Post by yota on 2006-11-08
After Microsoft acquired VirtualPc from the orginal developer (Connectix) official support for linux, which was  formerly present, was (:evil: intentionally?) removed (see [http://www.microsoft.com/windows/virtualpc/evaluation/overview2004.mspx](http://www.microsoft.com/windows/virtualpc/evaluation/overview2004.mspx) for reference)
This doesn't mean that is not possible to install and use ubuntu on VPC, but some quirks have to be expected. 

Why don't you just use vmware player [http://www.vmware.com/products/player/](http://www.vmware.com/products/player/) which is free as in beer and is the leading virtualization solution?
Images with already installed systems can be found at [http://www.vmware.com/vmtn/appliances/directory/cat/45](http://www.vmware.com/vmtn/appliances/directory/cat/45) and ubuntu is there too.

---

### Post by spd106 on 2006-11-08
Sadly I don't have the admin level to install VMWare, otherwise I would definitely consider it. Anyway it's nice to be in a Uni that's part of the Microsoft Academic Alliance and running Linux in their emulator.

I've figured a workaround for the ubuntu-6.10-Desktop cd, but it's a bit tricky.


1) At the boot screen select **safe graphics mode**, then press **F4** and select **640x480x32**.

2) At the desktop make sure you are not within VPC, ie the mouse can still leave the screen, then hit **Ctrl + Alt + F1**

   You should now see at load of text ending with ubuntu@ubuntu~$

3) Enter **sudo nano /etc/X11/xorg.conf**

   You will now be in a text editor

4) Scroll or page down untill you get to the "screen" section. You will see the default depth is set to 24

5) Change the DefaultDepth to **16**

6) Hit **Ctrl + o**, followed by **y**, to save the changes, then **Ctrl + x** to exit

    You should be back at the prompt

7) Type **sudo telinit 1** 

    Wait until it changes to root@ubuntu 

8) Type **telinit 5**

You should now be returned to the desktop. You will have to do this each time, unless you install to a vhd.

---

### Post by timothy_duncan on 2006-11-11
does the above procedure applies only to properly boot the live cd of virtualpc?  i tried booting kubuntu6.10 in virtualpc (and hopefully install it there) but was having the same problem..

---

