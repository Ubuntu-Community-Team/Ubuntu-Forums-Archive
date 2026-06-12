---
title: "Virtual PC 5.2 does not 'Ubuntu'"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by inhuman on 2006-10-12
Received Dapper Drake and tried to install yesterday under Virtual PC 5.2. Menu came up. Choose 'Start or Install'. Progress bar came up and went. Then, immediately, it went to console and gave this very inhuman error message:

[4294667.296000] ACPI: Unable to locate RSDP                                   
[   61.801625] isapnp: checksum for device 1 is not valid (0x89)               
[   61.809970] isapnp: checksum for device 2 is not valid (0xbe)               
[   61.967707] invalid operand: 0000 [#1]                                      
[   61.967907] PREEMPT                                                         
[   61.968449] Modules linked in:                                              
[   61.968904] CPU:    0                                                       
[   61.968924] EIP:    0060:[<c01011c6>]    Not tainted VLI                    
[   61.968929] EFLAGS: 00000246   (2.6.15-23-386)                              
[   61.969843] EIP is at mwait_idle+0x16/0x30                                  
[   61.970060] eax: c0386008   ebx: c0386000   ecx: 00000000   edx: 00000000   
[   61.970257] esi: c0386008   edi: c037b800   ebp: 0044c007   esp: c0387fdc   
[   61.970535] ds: 007b   es: 007b   ss: 0068                                  
[   61.970815] Process swapper (pid: 0, threadinfo=c0386000 task=c0331a00)     
[   61.971091] Stack: c0386000 00039400 c01010dc 00020800 c03887c6 00004000 000
4000 c03d3b60                                                                  
[   61.972998]        c0100199                                                 
[   61.973616] Call Trace:                                                     
[   61.974258]  [<c01010dc>] cpu_idle+0x1c/0x60                                
[   61.977136]  [<c03887c6>] start_kernel+0x176/0x1d0                          
[   61.978225] Code: 75 c3 5a 5b c3 e8 ab b4 1e 00 eb 8f 89 f6 8d bc 27 00 00 0
 00 56 53 fb bb 00 e0 ff ff 21 e3 8d 73 08 eb 16 90 31 c9 89 f0 89 ca <0f> 01 c
 8b 43 08 a8 08 75 0c 89 c8 0f 01 c9 8b 43 08 a8 08 74                         
[   61.992853]  <0>Kernel panic - not syncing: Attempted to kill the idle task!

Ouch! :-|

1. Anyone have any idea what this means? How do I get Dapper Drake to install?

2. Virtual PCs are widely used, and predate Dapper Drake. Could this not have been tested for? Understand it didn't work with Virtual PC 2004 either. Do I have to get Virtual PC 2004 to get it to work? Why doesn't it work under 5.2?

3. When I did a search for existing stuff on "Virtual PC 5.2" it gave me 250 entries to look up, none of which were for "Virtual PC 5.2" but seemed to keyword match anything with "virtual" or "pc". How about a phrase search?

Thanks!

---

### Post by doggie on 2006-10-12
do you really need to do it in vp ?? 
why dont you just put the cd in the drive and boot the live ubuntu??...:-k :-k

---

### Post by Fatjoint on 2006-10-13
If you have to use a VM, download VMware Player - it's free now from [www.vmware.com](www.vmware.com).  After you've installed VMware, search the VM sections for the Ubuntu Server VM they've already created, then install whatever apps you want to it.

---

### Post by ocertain on 2006-10-13
I'm running Edgy Efy (6.10 Beta) in Virtual PC 2004 on a Windows XP PC. Other than having to deal with a mostly unreadable install GUI, I managed to get the system installed and up an running pretty easily. If you're running Windows you can get VPC 2004 for free now.

One caveat, you'll have to modify a config file after the install and a reboot. There is information here in the forum (and on the web) on how to do it. It isn't difficult.

One other note. I see people asking the question - why bother with VPC when you can boot to the CD and use Ubuntu directly off the CD? 

For me, it's a matter of convenience. I have to use Windows XP at work since I'm a programmer working in .Net and much of my work is in VB.Net. There is no alternative in Linux for VB.Net, at least, not as far as I've been able to find. Having Ubuntu on a VPC allows me to play around in the enviornment without having to reboot. And that is a major plus in my book.

-Olice

---

### Post by gn2 on 2006-10-13
The free VM Ware server will allow you to install to a Virtual PC, and it works nicely with Ubuntu.

---

### Post by cogsprocket on 2006-10-13
Virtual PC is really not intended for anthing other than Windows VMs.  Your best bet is tu use VMWare Server or Player as has been suggested or use Parallels which seems to perform a bit better than other virtualization software.

To summarize.  Virtual PC should always be a last resort.

---

### Post by inhuman on 2006-10-22
Thanks for your replies.

I tried download Virtual PC 2004 and installing Ubuntu on that. It wasn't successful. There are some instructions for doing this somewhere on the Ubuntu web site, but it took a very long time to load and hung during the install. The instructions are pretty technical to follow; require interrupting the install with cat-like reflexes. I also noticed it thrashes the CPU; ie. fan screams and CPU runs at 100%. In conclusion: I don't recommened running Ubuntu under Virtual PC Server 2004.

I did have Virtual PC 5.2 and that was much nicer, because it *did* have a Linux addon which integrated Virtual PC 5.2 with Windows very nicely. You could drag and drop between them, and the CPU idled properly. Unfortunately some bright spark changed the Linux kernel about a year ago so Linux no longer worked virtually (e.g. RedHat Fedora 1 works, but RedHat Fedora 2 etc. do not. This was reported at the time, but doesn't look like it was fixed. The 'fix' was not to upgrade, or to get an update to your virtual host program - see next paragraph.) If you try and install Ubuntu under Virtual PC 5.2 you get a similar looking bug (posted above). In conclusion: If you're using Virtual PC 5.2, you can only use Redhat Fedora 1. Not Ubuntu, or later Linuxes.

Aside: Virtual PC 5.2 was the last version before Microsoft bought Virtual PC out. They bought out Virtual PC 2004, which had the Linux add-on removed (forget the above patch!). :-( Anti-trust, anyone? :-| Virtual PC 2004 is available free(!!) from the Microsoft Web site, and is a very compact 20Mb(!!!); 1 hour by dialup. [FILE: Virtual PC 2004 SP1.zip] Seems it is possible to run Linux under it (ocertain says he got edgy efy, which I gather is the next version of Ubuntu?), but not an easy task (for humans. :-))

Fatjoint suggested VMWARE. This seems to be the only option for Ubuntu. Would be nice if VMWARE cleaned up their web site; they have so many different versions of their software it's hard to tell what does what; e.g. VMWARE Server vs. VMWARE Player. What's what? From Fatjoint gather VMWARE PLayer is what is needed for Ubuntu. I'll try downloading this...

Doggies suggested booting Ubuntu direct. Unfortunately I (and probably a lot of other people) already have Windows PCs, so a clean install of Ubuntu would lose all our existing work (the CD cover warns this), and even if backed up leaves us with files/applications we can't take with us. Using a virtual pc lets us migrate to Linux in an orderly fashion. Also lets people try Ubuntu without having to wipe their existing OS (which I think many people wouldn't be willing to do.) Can I suggest that the Ubuntu builders look at better supporting virtual envrionments in future releases? One of the things that was attractive about Ubuntu was the "Linux for Humans" tag, but installing Ubuntu in virtual environments is not for the faint hearted.

Thanks again for all your replies!

---

### Post by gn2 on 2006-10-22
Firstly, you can run Ubuntu from the live CD without ever having to install it.

Re-boot with CD in drive and CD before hard drive in BIOS boot order.

NOTHING will be installed unless you specifically tell it to install.

VMWare server will let you load from an OS install disc, or run a live CD inside aVirtual machine. VMWare player will only run pre-configured appliances which you will have to download. It is free of charge.

[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

Parallels desktop seems to have more features, but there's a charge. Free to try though...

[http://www.parallels.com/en/download/](http://www.parallels.com/en/download/)

Can you fit an additional hard drive?

If so read this: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

Hope that helps?
.

---

