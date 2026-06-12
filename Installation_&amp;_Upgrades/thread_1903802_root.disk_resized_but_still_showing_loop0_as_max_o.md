---
title: "root.disk resized but still showing loop0 as max out"
date: 2012-01-03
forum: Installation &amp; Upgrades
---

### Post by tyrate on 2012-01-03
First of all I'm a total noob when it comes to the Ubuntu world but I love working and playing wit the system so I'm becoming a big fan of it but I'm currently having some major issues with disk space when it comes to root.disk and loop0. Since I've installed WUBI Ubuntu 11.10 I've had to resize my root.disk twice because my loop0 filesystem had reached it's max capacity. The 1st time was 7GB to 10GB which worked find but 2nd time I did it I'd increased the capacity to 60GB because the 10GB filled up so quickly. My problem is that my root.disk shows that it has been resized to 60GB but my loop0 still shows as 10GB and max to capacity? Maybe I'm not understanding something but I'd assumed if I resized the root.disk that the /dev/loop0 would also increase in size like it did when I did it the 1st time?      I used POST 2 from bcbc as my reference to resize the root.disk [http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)  So my question is how do I increase my dev/loop0 size?

---

### Post by bcbc on 2012-01-03
Please post output of:
```
ls -al /host/ubuntu/disks
df -h

```

Thanks

---

### Post by tyrate on 2012-01-04
> **bcbc said:**
> Please post output of:
```
ls -al /host/ubuntu/disks
df -h

```
 
Thanks
 
Hey thank you for whatever help you can provide. I really appreciate the reply!
 
```
tyrate@Moserver:~$ ls -al /host/ubuntu/disks                                    
total 10027780                                                                  
drwxrwxrwx 1 root root        4096 2011-12-30 23:35 .                           
drwxrwxrwx 1 root root           0 2011-11-19 19:39 ..                          
drwxrwxrwx 1 root root           0 2011-11-19 19:29 boot                        
-rwxrwxrwx 2 root root 64424509440 2012-01-04 09:20 root.disk                   
-rwxrwxrwx 2 root root   268435456 2011-11-19 14:43 swap.disk                   
tyrate@Moserver:~$ df -h                                                        
Filesystem            Size  Used Avail Use% Mounted on                          
/dev/loop0            9.2G  8.4G  321M  97% /                                   
udev                  996M  8.0K  996M   1% /dev                                
tmpfs                 402M  1.9M  400M   1% /run                                
none                  5.0M     0  5.0M   0% /run/lock                           
none                 1005M  100K 1005M   1% /run/shm                            
/dev/sda1             153G   41G  113G  27% /host                               
/dev/md2              1.8T  600G  1.3T  33% /MediaLocker                        
/dev/sdb1              56G  9.5G   43G  19% /media/Repo1                        
/dev/sdd1             1.4T  1.1T  316G  78% /media/usb0                         
/dev/sdf5             278G   77G  202G  28% /media/Backup                       
/dev/sdf1             341G  195M  324G   1% /media/Repo2                        
/dev/md0              970M  199M  771M  21% /media/91027b55-4f5e-47ae-a0a2-eaf2d
dd4d382                   
```

---

### Post by bcbc on 2012-01-04
That's puzzling. It resized the file, but not the filesystem? 

I've never used it to increase the root.disk by such a large amount, but I don't see why there should be any difference between a small amount and a large amount. All I can suggest is repeating the process with a small difference in the size and see whether that works better.

Personally I have mixed feelings about large root.disks - just because all that data is stored on the single file. I've never lost one myself, but I've seen enough support requests to know that some do.

Let me know how it goes. Thanks

---

### Post by tyrate on 2012-01-05
That did it... thank you!

---

