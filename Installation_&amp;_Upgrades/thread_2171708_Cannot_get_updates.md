---
title: "Cannot get updates"
date: 2013-09-01
forum: Installation &amp; Upgrades
---

### Post by Lloydb39 on 2013-09-01
Using 12.04 on a Dell laptop. There are 47 updates available, the notification says. Update manager won't run and it says I must do "dpkg configure" but when I do it tries to install "bcmwl" and that is the kiss of death for this computer. It always crashes. Is there a way to block that package and get the others I may or may not need? Everything is working fine so I presume I could just keep using what I have without updates? (This situation resulted from a previous fix that solved a problem with the wireless card driver.)

---

### Post by Frogs Hair on 2013-09-01
There is an option to freeze package versions in the synaptic package manager if installed. I don't know the effects on other packages though . Post the out put of of the following terminal command in code tags. You may not be able to install anything with the package system tied up.  ```
sudo apt-get update 
```

---

### Post by ibjsb4 on 2013-09-01
I don't know if synaptic will work in your 'dpkg' situation, but you can try to [lock the package]("http://www.ubuntugeek.com/how-to-lock-package-versions-from-synaptic-package-manager.html").

```
sudo apt-get install synaptic
```

---

### Post by ian-weisser on 2013-09-01
The entire exact error message, and any other associated warning and errors, would be helpful.

Are you subscribed to a bcmwl ppa?
Has this kind of issue ever happened before with kernel updates?

If an updated package (likely associated with an updated kernel) is really the issue, then you have two choices:
1) Pin (freeze) the version so future updates will be rejected. This will also prevent future kernel updates.
2) Reinstall your bcm fix after each kernel update in the future.

Which option do you prefer to pursue?

---

### Post by Lloydb39 on 2013-09-01
```
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Get:5 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                 
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:7 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Get:8 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [8,935 B]     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [415 kB]       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [85.1 kB]      
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [28.0 kB]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,803 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [325 kB] 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [7,031 B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [94.6 kB] 
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,358 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [699 kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [84.1 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [216 kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.0 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,633 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [72 B]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [307 kB]
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [149 kB]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en [8,064 B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en [2,637 B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [125 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Get:38 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en [1,299 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Get:39 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [51.8 kB]
Fetched 2,771 kB in 11s (233 kB/s)                                             
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

---

### Post by Lloydb39 on 2013-09-01
install synaptic did this:
lloyd@lloyd-Inspiron-1150:~$ sudo apt-get install synaptic
[sudo] password for lloyd: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by Lloydb39 on 2013-09-01
"The entire exact error message, and any other associated warning and errors, would be helpful.

Are you subscribed to a bcmwl ppa?
Has this kind of issue ever happened before with kernel updates?

If an updated package (likely associated with an updated kernel) is really the issue, then you have two choices:
1) Pin (freeze) the version so future updates will be rejected. This will also prevent future kernel updates.
2) Reinstall your bcm fix after each kernel update in the future.

Which option do you prefer to pursue?"

I really don't know what all that means. I guess freeze the version sounds best. How would I accomplish that? The bcm fix< i think, was to blacklist bcmwl and do "bcm 43 mod" and a few other things (detailed in an earlier thread marked "solved" in the wireless forum). 
I appreciate the suggestions, guys, even those I don't understand.

---

### Post by ian-weisser on 2013-09-01
Try the command **sudo dpkg --configure -a** and show us the result.

---

### Post by Lloydb39 on 2013-09-02
Interesting. This time when I did dpkg configure it didn't crash. Apparently it updated. BUT, I immediately lost all access, wireless and wired. I had to reboot and roll back to an earlier version to get it to work on Ethernet, which is where I am now. Here's the output from the dpkg command:
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.1) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-51-generic
Building for architecture i686
Building initial module for 3.2.0-51-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-51-generic/updates/dkms/

depmod.....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-51-generic

---

### Post by Lloydb39 on 2013-09-02
Also, I think I gave you inaccurate information previously. What I blacklisted was not bcmwl but the driver for a USB wireless device I was using when I was not able to use the BCM4306 card. They were in conflict. I must have done something in resolving all that to preclude updates.

---

### Post by ian-weisser on 2013-09-02
> **Lloydb39 said:**
> I really don't know what all that means.

It means that the kernel handles hardware compatibility. Many hardware manufacturers contribute code to the kernel so their devices work perfectly with Linux, and many users never have any problems with hardware (like wireless).

Some manufacturers, however, refuse to contribute their linux drivers, or refuse to update them. Since that compatibility cannot be included in the kernel, you must manually add that functionality yourself later...like making a Broadcom wireless card work.

When you upgrade your kernel, any changes you made to the older (working) kernel are lost.
This means that your finally-working hardware will suddenly stop working. That should seem familiar to you.

To prevent kernel upgrades from revering (breaking) your hardware, you can freeze (pin) your kernel version. This will prevent a new kernel from being installed. However, it also means that you will prevent kernel-related security updates, and you won't be able to upgrade to the next version of Ubuntu. Pinning is generally considered a temporary solution.

The more robust -but somewhat annoying- solution is to re-apply the fix each time you upgrade the kernel. This can be scripted so it's not onerous. This means you can upgrade the kernel as much you wish, and you can upgrade to newer versions of Ubuntu.

The best solution, of course, is for hardware manufacturers to contribute code to the kernel, so their devices work without any fiddling at all.

---

