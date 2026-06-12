---
title: "compiz crashing in kubuntu"
date: 2009-09-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by KhaaL on 2009-09-05
hi

Since I migrated to karmic I've had lots of troubles having compiz running (which is a vital piece of my computer experience nowdays :) ). Drivers and openGL is working well, and when I try to run compiz this happens:

```
khaal@xeraphim:~/Desktop$ compiz
Checking for Xgl: not present.  
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log                                                                          
Detected PCI ID for VGA:                                                        
Checking for texture_from_pixmap: present.                                      
Checking for non power of two support: present.                                 
Checking for Composite extension: present.                                      
Checking screen 1Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.                                                                    
Checking for Software Rasterizer: Not present.                                  
Checking for nVidia: present.                                                   
Checking for FBConfig: present.                                                 
Checking for Xgl: not present.                                                  
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format                                                                    
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png                                                                
Couldn't find a perfect decorator match; trying all decorators                  
Found no decorator to start                                                     
*** glibc detected *** /usr/bin/compiz.real: double free or corruption (!prev): 0x0000000001783900 ***                                                          
======= Backtrace: =========                                                    
/lib/libc.so.6[0x7fc36a42cd46]                                                  
/lib/libc.so.6(cfree+0x6c)[0x7fc36a43167c]                                      
/usr/lib/libGL.so.1[0x7fc36c222038]                                             
======= Memory map: ========                                                    
00400000-0043b000 r-xp 00000000 08:21 95800                              /usr/bin/compiz.real                                                                   
0063b000-0063c000 r--p 0003b000 08:21 95800                              /usr/bin/compiz.real                                                                   
0063c000-0063d000 rw-p 0003c000 08:21 95800                              /usr/bin/compiz.real                                                                   
013a5000-03dd6000 rw-p 00000000 00:00 0                                  [heap] 
7fc35c000000-7fc35c021000 rw-p 00000000 00:00 0                                 
7fc35c021000-7fc360000000 ---p 00000000 00:00 0                                 
7fc3601f4000-7fc3601fb000 r-xp 00000000 08:21 1400                       /lib/librt-2.10.1.so                                                                   
7fc3601fb000-7fc3603fa000 ---p 00007000 08:21 1400                       /lib/librt-2.10.1.so                                                                   
7fc3603fa000-7fc3603fb000 r--p 00006000 08:21 1400                       /lib/librt-2.10.1.so                                                                   
7fc3603fb000-7fc3603fc000 rw-p 00007000 08:21 1400                       /lib/librt-2.10.1.so                                                                   
7fc3660a3000-7fc3660a7000 r-xp 00000000 08:21 103102                     /usr/lib/compizconfig/backends/libini.so                                               
7fc3660a7000-7fc3662a6000 ---p 00004000 08:21 103102                     /usr/lib/compizconfig/backends/libini.so                                               
7fc3662a6000-7fc3662a7000 r--p 00003000 08:21 103102                     /usr/lib/compizconfig/backends/libini.so                                               
7fc3662a7000-7fc3662a8000 rw-p 00004000 08:21 103102                     /usr/lib/compizconfig/backends/libini.so                                               
7fc3662a8000-7fc3662c2000 r-xp 00000000 08:21 1336                       /lib/libgcc_s.so.1                                                                     
7fc3662c2000-7fc3664c1000 ---p 0001a000 08:21 1336                       /lib/libgcc_s.so.1                                                                     
7fc3664c1000-7fc3664c2000 r--p 00019000 08:21 1336                       /lib/libgcc_s.so.1                                                                     
7fc3664c2000-7fc3664c3000 rw-p 0001a000 08:21 1336                       /lib/libgcc_s.so.1                                                                     
7fc3664c3000-7fc3665b5000 r-xp 00000000 08:21 7872                       /usr/lib/libstdc++.so.6.0.13                                                           
7fc3665b5000-7fc3667b5000 ---p 000f2000 08:21 7872                       /usr/lib/libstdc++.so.6.0.13                                                           
7fc3667b5000-7fc3667bc000 r--p 000f2000 08:21 7872                       /usr/lib/libstdc++.so.6.0.13                                                           
7fc3667bc000-7fc3667be000 rw-p 000f9000 08:21 7872                       /usr/lib/libstdc++.so.6.0.13                                                           
7fc3667be000-7fc3667d3000 rw-p 00000000 00:00 0                                 
7fc3667d3000-7fc3667ea000 r-xp 00000000 08:21 1394                       /lib/libpthread-2.10.1.so                                                              
7fc3667ea000-7fc3669e9000 ---p 00017000 08:21 1394                       /lib/libpthread-2.10.1.so                                                              
7fc3669e9000-7fc3669ea000 r--p 00016000 08:21 1394                       /lib/libpthread-2.10.1.so                                                              
7fc3669ea000-7fc3669eb000 rw-p 00017000 08:21 1394                       /lib/libpthread-2.10.1.so                                                              
7fc3669eb000-7fc3669ef000 rw-p 00000000 00:00 0                                 
7fc366a0b000-7fc366adc000 r-xp 00000000 08:21 103072                     /usr/lib/libprotobuf.so.3.0.0                                                          
7fc366adc000-7fc366cdb000 ---p 000d1000 08:21 103072                     /usr/lib/libprotobuf.so.3.0.0                                                          
7fc366cdb000-7fc366cdf000 r--p 000d0000 08:21 103072                     /usr/lib/libprotobuf.so.3.0.0                                                          
7fc366cdf000-7fc366ce0000 rw-p 000d4000 08:21 103072                     /usr/lib/libprotobuf.so.3.0.0                                                          
7fc366ce0000-7fc366d27000 r-xp 00000000 08:21 103099                     /usr/lib/libcompizconfig.so.0.0.0                                                      
7fc366d27000-7fc366f26000 ---p 00047000 08:21 103099                     /usr/lib/libcompizconfig.so.0.0.0                                                      
7fc366f26000-7fc366f28000 r--p 00046000 08:21 103099                     /usr/lib/libcompizconfig.so.0.0.0                                                      
7fc366f28000-7fc366f29000 rw-p 00048000 08:21 103099                     /usr/lib/libcompizconfig.so.0.0.0                                                      
7fc366f29000-7fc366f2a000 rw-p 00000000 00:00 0                                 
7fc36712f000-7fc36732f000 rw-s 174cd000 00:0e 7625                       /dev/nvidia0                                                                           
7fc36742f000-7fc367430000 rw-s fac06000 00:0e 7625                       /dev/nvidia0                                                                           
7fc367565000-7fc367566000 rw-s fa001000 00:0e 7625                       /dev/nvidia0                                                                           
7fc367566000-7fc367599000 rw-p 00000000 00:00 0                                 
7fc367599000-7fc3675ba000 rw-s 00000000 00:09 0                          /SYSV00000000 (deleted)                                                                
7fc3675e6000-7fc3675e9000 rw-p 00000000 00:00 0                                 
7fc3675e9000-7fc3675ee000 r-xp 00000000 08:21 6830                       /usr/lib/libXdmcp.so.6.0.0                                                             
7fc3675ee000-7fc3677ed000 ---p 00005000 08:21 6830                       /usr/lib/libXdmcp.so.6.0.0                                                             
7fc3677ed000-7fc3677ee000 rw-p 00004000 08:21 6830                       /usr/lib/libXdmcp.so.6.0.0                                                             
7fc3677ee000-7fc3677f0000 r-xp 00000000 08:21 6819                       /usr/lib/libXau.so.6.0.0                                                               
7fc3677f0000-7fc3679ef000 ---p 00002000 08:21 6819                       /usr/lib/libXau.so.6.0.0                                                               
7fc3679ef000-7fc3679f0000 r--p 00001000 08:21 6819                       /usr/lib/libXau.so.6.0.0                                                               
7fc3679f0000-7fc3679f1000 rw-p 00002000 08:21 6819                       /usr/lib/libXau.so.6.0.0                                                               
7fc3679f1000-7fc3679f2000 rw-p 00000000 00:00 0                                 
7fc3679f2000-7fc3679f3000 r-xp 00000000 08:21 105097                     /usr/lib/tls/libnvidia-tls.so.185.18.36
7fc3679f3000-7fc367af3000 ---p 00001000 08:21 105097                     /usr/lib/tls/libnvidia-tls.so.185.18.36
7fc367af3000-7fc367af4000 rw-p 00001000 08:21 105097                     /usr/lib/tls/libnvidia-tls.so.185.18.36
7fc367af4000-7fc3688ce000 r-xp 00000000 08:21 105104                     /usr/lib/libGLcore.so.185.18.36
7fc3688ce000-7fc3689ce000 ---p 00dda000 08:21 105104                     /usr/lib/libGLcore.so.185.18.36
7fc3689ce000-7fc368e07000 rwxp 00dda000 08:21 105104                     /usr/lib/libGLcore.so.185.18.36
7fc368e07000-7fc368e1a000 rwxp 00000000 00:00 0
7fc368e1a000-7fc368e35000 r-xp 00000000 08:21 7972                       /usr/lib/libxcb.so.1.1.0
7fc368e35000-7fc369034000 ---p 0001b000 08:21 7972                       /usr/lib/libxcb.so.1.1.0
7fc369034000-7fc369035000 r--p 0001a000 08:21 7972                       /usr/lib/libxcb.so.1.1.0
7fc369035000-7fc369036000 rw-p 0001b000 08:21 7972                       /usr/lib/libxcb.so.1.1.0
7fc369036000-7fc369039000 r-xp 00000000 08:21 95736                      /usr/lib/libxcb-atom.so.1.0.0
7fc369039000-7fc369239000 ---p 00003000 08:21 95736                      /usr/lib/libxcb-atom.so.1.0.0
7fc369239000-7fc36923a000 r--p 00003000 08:21 95736                      /usr/lib/libxcb-atom.so.1.0.0
7fc36923a000-7fc36923b000 rw-p 00004000 08:21 95736                      /usr/lib/libxcb-atom.so.1.0.0
7fc36923b000-7fc36923e000 r-xp 00000000 08:21 95762                      /usr/lib/libxcb-event.so.1.0.0
7fc36923e000-7fc36943e000 ---p 00003000 08:21 95762                      /usr/lib/libxcb-event.so.1.0.0
7fc36943e000-7fc36943f000 r--p 00003000 08:21 95762                      /usr/lib/libxcb-event.so.1.0.0Aborted (core dumped)


```

Would appriciate help!

---

### Post by taavikko on 2009-09-05
Quick question, since kwin provides similar functions as compiz, why it won't do?
(if the answer is the window borders, I understand ;) )

---

### Post by KhaaL on 2009-09-05
compiz offers a lot more customization options not only in plugins, but also in the basic functionality :)

---

### Post by LittleCannon on 2009-09-06
Same here, but I managed to run compiz through fusion-icon (Reload Window manager).

---

