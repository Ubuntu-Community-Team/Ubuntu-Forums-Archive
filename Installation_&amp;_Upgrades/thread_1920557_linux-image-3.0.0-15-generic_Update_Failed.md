---
title: "linux-image-3.0.0-15-generic Update Failed"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by Nelix on 2012-02-05
Hello all, 

Initiated normal update for linux-image-3.0.0-15-generic, and it seemed to complete fine.  However, after rebooting, the machine lost all networking capabilities.  Tried to fix it, but made things worse, and now computer won't load to login screen.  

I am now using my previous version, linux-image-3.0.0.14-generic.  How can I eliminate or back-out the 3.0.0-15 update so that I can try again?  Thank you in advance. 

Kind regards, Jack

---

### Post by Nelix on 2012-02-05
I am adding diagnostic information that will hopefully get us closer to the answer on this one.  Thank you in advance.

FYI: I can bring up Ubuntu Fixpack 15 using recovery mode. 

**Observation: **The Network Connection Application has changed from fixpack 14 to 15.  The application is visibly different. 

**Opinion:** The network card, which is built into the mother board, is not being recognized by fixpack 15. 

**Fix:** Need help... not sure what to do.  

**Diagnostic Information:**

       **Ubuntu 11.10 Fixpack 14**
**Command:** **sudo ethtool eth0**
Settings for eth0:

 Supported ports: [ TP ]
Supported link modes:   10baseT/Half 10baseT/Full 
                        100baseT/Half 100baseT/Full 
                        1000baseT/Full 
Supports auto-negotiation: Yes
Advertised link modes:  10baseT/Half 10baseT/Full 
                        100baseT/Half 100baseT/Full 
                        1000baseT/Full 
Advertised pause frame use: No
Advertised auto-negotiation: Yes
Speed: 1000Mb/s
... 
Link detected: yes


    **Ubuntu 11.10 Fixpack 15**
**Command:** **sudo ethtool eth0** 
   Settings for eth0:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available


   **Ubuntu 11.10 Fixpack 14**
**Command: sudo lshw -class network**

     *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: ##:##:##:##:##:##
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz


   **Ubuntu 11.10 Fixpack 15**
**Command: sudo lshw -class network**
 *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 06
       width: 64 bits
       clock: 33MHz

---

### Post by pasoleatis on 2012-02-05
There is something rotten in the upgrade process. I lost all drivers after a kernel update. I think there are more with this kind of problem.

---

### Post by dino99 on 2012-02-05
to deal with installation, use synaptic:

sudo apt-get install synaptic
sudo synaptic

then remove the broken kernel : 1 image & 2 headers = 3 packages

note: what is fixpack ?

---

### Post by Nelix on 2012-02-06
First and foremost, thank you for your responses. 

I downloaded the synaptic program as you have advised.  However, I decided to hold off on removing the package, and instead, try to address the issue itself.  I have a feeling that a lot of people will run into this as well.  

I believe I need to let the kernel know how to recognize the Ethernet card. Hence, that is the solution I will be looking for unless someone advises otherwise. 

Again, thank you very much for your responses.  It is good to know there are other people out there working to make Ubuntu a top notch product.  

**Aside: **
Fixpack is an IBM db2 term they use to describe updates, enhancements, and fixes that are released between major releases of the product.  It is a succinct term, and I drew a parallel between db2 fixpacks and the linux-image updates.  I plan to refrain from using that term in the future.

---

