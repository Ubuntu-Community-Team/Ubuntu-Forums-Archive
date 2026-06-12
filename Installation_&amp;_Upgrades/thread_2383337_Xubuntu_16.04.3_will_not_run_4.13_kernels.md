---
title: "Xubuntu 16.04.3 will not run 4.13 kernels"
date: 2018-01-23
forum: Installation &amp; Upgrades
---

### Post by lou6 on 2018-01-23
I recently installed xubuntu 16.04.3 on my laptop but 3 successive kernel upgrades (via software updater) to 4.13.x.x have failed to boot.  I've been removing the 4.13 kernels via synaptic and editing /boot to remove the offending kernels there, then running update-grub to get back to 4.10.0.42 (the kernel that will boot).  Not a good way to go thru life - is there a way to mod my system to accept 4.13 or should I just stop accepting new 4.13 kernels?

Not a noob but not an expert here - can someone help?  Thank you.

edit: as I continued to investigate this I found a thread that dealt with the same problem on systems with nvidia graphics - my laptop has an nvidia chip but the thread was written by some VERY experienced ubuntu users and was more complex than my limited experience could handle - hope someone can help me. TIA

---

### Post by tinylagarto on 2018-01-23
I do not own an Nvidia card but I heard about problems with 4.13. 

This bug report is just one example: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742302](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742302)

Though as you are on an LTS release you could also boot to 4.4. It has the new patches and is an LTS kernel.

---

### Post by vasa1 on 2018-01-23
I started off with 16.04.2, not the very first 16.04 release as ```
$ cat /var/log/installer/media-info
Kubuntu 16.04.2 LTS "Xenial Xerus" - Release amd64 (20170215)
$
```shows.

There's no 4.4 left today and I didn't remove it myself. All the same, what does```
dpkg -l | grep -E "ii  linux" | cut -c 1-100
```show for you?

I have```
$ dpkg -l | grep -E "ii  linux" | cut -c 1-100
ii  linux-base                                      4.0ubuntu1                                      
ii  linux-firmware                                  1.157.14                                        
ii  linux-generic-hwe-16.04                         4.13.0.31.51                                    
ii  linux-headers-4.13.0-26                         4.13.0-26.29~16.04.2                            
ii  linux-headers-4.13.0-26-generic                 4.13.0-26.29~16.04.2                            
ii  linux-headers-4.13.0-31                         4.13.0-31.34~16.04.1                            
ii  linux-headers-4.13.0-31-generic                 4.13.0-31.34~16.04.1                            
ii  linux-headers-generic-hwe-16.04                 4.13.0.31.51                                    
ii  linux-image-4.13.0-26-generic                   4.13.0-26.29~16.04.2                            
ii  linux-image-4.13.0-31-generic                   4.13.0-31.34~16.04.1                            
ii  linux-image-extra-4.13.0-26-generic             4.13.0-26.29~16.04.2                            
ii  linux-image-extra-4.13.0-31-generic             4.13.0-31.34~16.04.1                            
ii  linux-image-generic-hwe-16.04                   4.13.0.31.51                                    
ii  linux-libc-dev:amd64                            4.4.0-112.135                                   
ii  linux-signed-generic-hwe-16.04                  4.13.0.31.51                                    
ii  linux-signed-image-4.13.0-26-generic            4.13.0-26.29~16.04.2                            
ii  linux-signed-image-4.13.0-31-generic            4.13.0-31.34~16.04.1                            
ii  linux-signed-image-generic-hwe-16.04            4.13.0.31.51                                    
ii  linux-sound-base                                1.0.25+dfsg-0ubuntu5                            
$ 
```

---

### Post by lou6 on 2018-01-24
Thanks for replying, vasa1 -

I can't get to the machine in question right now (it's at another location) but I can tell you what the result will be.  I have only kernel 4.10.0.42 installed  (and booting correctly).  I did have 4.13.0.26, 4.13.0.28 and 4.13.0.31 but none of those would boot- each attempt resulted in the machine displaying the grub menu.  I removed all the 4.13.x.x kernels via Synaptic (leaving only 4.10.0.42) which boots just fine and that's where I stand today.  I don't know why 4.13.x.x kernels won't boot but I suspect it has something to do with the fact that my machine (Dell Latitude e6430) has both an Intel graphics chip and an nVidia graphics chip (I ran "lspci | grep VGA" and that is what it told me).

I suppose I can continue running the working 4.10 kernel until later this year when Bionic Beaver is available but who knows what problems will arise then?  I'd like to solve this and get current 4.13 kernels to boot normally.

---

### Post by vasa1 on 2018-01-24
If I understand correctly, 4.10 won't get any more updates (including security-related ones).

---

### Post by lou6 on 2018-01-24
vasa1 - This is the output of the dpkg you suggested.

> ii  linux-base                                 4.0ubuntu1                                 all       
ii  linux-firmware                             1.157.14                                   all       
ii  linux-headers-4.10.0-42                    4.10.0-42.46~16.04.1                       all       
ii  linux-headers-4.10.0-42-generic            4.10.0-42.46~16.04.1                       i386      
ii  linux-headers-4.13.0-26                    4.13.0-26.29~16.04.2                       all       
ii  linux-headers-4.13.0-26-generic            4.13.0-26.29~16.04.2                       i386      
ii  linux-headers-4.13.0-31                    4.13.0-31.34~16.04.1                       all       
ii  linux-headers-4.13.0-31-generic            4.13.0-31.34~16.04.1                       i386      
ii  linux-headers-generic-hwe-16.04            4.13.0.31.51                               i386      
ii  linux-image-4.10.0-42-generic              4.10.0-42.46~16.04.1                       i386      
ii  linux-image-extra-4.10.0-42-generic        4.10.0-42.46~16.04.1                       i386      
ii  linux-libc-dev:i386                        4.4.0-112.135                              i386      
ii  linux-sound-base

I'm not at all sure that the presence of multiple graphics drivers is the cause of the 4.13 kernels not booting - that's just something I ran across while trying to solve this.  There may be a clue in a log somewhere but I have no idea where to start looking - I'm a retired programmer with decades of large mainframe experience but that does not help me here :)

---

### Post by lou6 on 2018-01-24
vasa1 - this is the thread that mentioned nVidia as being the cause of the 4.13 boot problem:

[https://ubuntuforums.org/showthread.php?t=2382206](https://ubuntuforums.org/showthread.php?t=2382206)

---

### Post by tinylagarto on 2018-01-24
> **vasa1 said:**
> 

There's no 4.4 left today and I didn't remove it myself. All the same, what does```
dpkg -l | grep -E "ii  linux" | cut -c 1-100
```show for you? 


Ok. That should be because of opting in to the newer hwe kernels. I am on 17.10 so I do not see any 4.4 option but as Ubuntu 16.04 came with 4.4 it should still be installable, just in case.

---

### Post by lou6 on 2018-01-25
Does anyone know if there is a bug report on this issue (meltdown/hwe kernels that won't boot)?

(1)  I've seen several suggestions that involve keeping linux-image-hwe installed so that updates will continue in hopes that a fix will come along.  There's a certain logic to this, I guess, but I don't enjoy having to fix the system every time a bad kernel shows up (3 times so far).

(2)  At this point I'm running 4.10.0.42 which boots fine but I will receive no security updates...

Before I close this thread I'd appreciate any advice from those more knowledgeable than I (which would include most of you) re: which of the above approaches I should take (1 or 2, above).

Thanks for the help.

---

### Post by Qew on 2018-01-25
I think that you should do what some others here have suggested, and install the 4.4 kernel. That will keep you up to date with security fixes and it's LTS. I'd also keep the HWE install and check each update if your system will boot from it. Once it does, you can switch to it full time, while still keeping the 4.4 kernel for emergencies (it'll still get updated).

I installed Ubuntu 16.04 when it came out and have gone with the HWE updates when they became available. That installed a new kernel (4.8) and kept my 4.4. Each kernel version update has kept the 4.4 kernel for me to use if needed (I haven't had to use it, though). So, I'd suggest installing the 4.4 kernel and use that for now to keep secure.

---

### Post by lou6 on 2018-01-25
Just found this:

[Bug #1742675 &#8220;after upgrade to linux-image-extra-4.13.0-26-gener...&#8221; : Bugs : linux package : Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742675") 

Seems to explain my problem - hope it gets fixed soon.

I'll mark this thread closed now - thanks to all who posted.

---

