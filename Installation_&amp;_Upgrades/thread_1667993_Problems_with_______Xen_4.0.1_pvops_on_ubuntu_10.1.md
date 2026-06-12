---
title: "Problems with       Xen 4.0.1 pvops on ubuntu 10.10"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by wendani on 2011-01-15
[SIZE=2]hi all,

I am now installing Xen 4.0.1 installation on ubuntu 10.10. The installation follows the steps described in [https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen).

I meet the following errors when booting:

ext3-fs: sda1 cannot mount because of unsupported optional feature (240)[/SIZE] [SIZE=2]


I think it might be the problem on file system format. What shall I configure to turn on EXT4?
[/SIZE][SIZE=2]I have tried "make linux-2.6-pvops-config CONFIGMODE=menuconfig"

[/SIZE][SIZE=2]and turned on the following file system support in Xen, but it doesnot work at this moment.

 <*> Second extended fs support                       [/SIZE][SIZE=2]            &#9474; &#9474;  
  &#9474; &#9474;    
[*]   Ext2 extended attributes                    [/SIZE][SIZE=2]               &#9474; &#9474;  
  &#9474; &#9474;    
[*]     Ext2 POSIX Access Control Lists                          &#9474; &#9474;  
  &#9474; &#9474;    
[*]     Ext2 Security Labels                        [/SIZE][SIZE=2]             &#9474; &#9474;  
  &#9474; &#9474;    
[*]   Ext2 execute in place support                       [/SIZE][SIZE=2]       &#9474; &#9474;  
  &#9474; &#9474;    <*> Ext3 journalling file system support                       [/SIZE][SIZE=2]  &#9474; &#9474;  
  &#9474; &#9474;    
[*]   Default to 'data=ordered' in ext3                          &#9474; &#9474;  
  &#9474; &#9474;    
[*]   Ext3 extended attributes                    [/SIZE][SIZE=2]               &#9474; &#9474;  
  &#9474; &#9474;    
[*]     Ext3 POSIX Access Control Lists                          &#9474; &#9474;  
  &#9474; &#9474;    
[*]     Ext3 Security Labels                   
<*> The Extended 4 (ext4) filesystem                    [/SIZE][SIZE=2]         &#9474; &#9474;  
  &#9474; &#9474;    
[*]   Ext4 extended attributes                    [/SIZE][SIZE=2]               &#9474; &#9474;  
  &#9474; &#9474;    
[*]     Ext4 POSIX Access Control Lists                          &#9474; &#9474;  
  &#9474; &#9474;    
[*]     Ext4 Security Labels                        [/SIZE][SIZE=2]             &#9474; &#9474;  
  &#9474; &#9474;    
[*]   EXT4 debugging support                       [/SIZE][SIZE=2]              &#9474; &#9474;  
  &#9474; &#9474;    
[*] JBD (ext3) debugging support                       [/SIZE][SIZE=2]          &#9474; &#9474;  
  &#9474; &#9474;    
[*] JBD2 (ext4) debugging support            
[/SIZE][COLOR=#888888] 
[SIZE=2]
[/SIZE][/COLOR][SIZE=2]On the next screen, it gives me another error msg "The disk drive for / is not ready yet or not present"

And if I press S for skip, it finally give me "init: Plymouth main process (947) killed by SEGV signal"[/SIZE]

---

