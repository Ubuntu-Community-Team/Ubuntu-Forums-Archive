---
title: "booting kernel from installation cd issue"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by nonick2k7 on 2006-08-13
Tried to install Ubuntu linux 6.06
When trying to install...
      Starts loading the Kernel, compression is successful
  
      however when trying to boot it I get this error:
       [4294668.694000] PCI: cannot allocate resource reign 7 bridge 0000:00:1c.0
 
      [4294668.694000] PCI: cannot allocate resource reign 8 bridge 0000:00:1c.0
 
      [4294668.694000] PCI: cannot allocate resource reign 7 bridge 0000:00:1c.1
       [4294668.694000] PCI: cannot allocate resource reign 8 bridge 0000:00:1c.1
 
      [4294668.694000] PCI: cannot allocate resource reign 7 bridge 0000:00:1c.2
 
      [4294668.694000] PCI: cannot allocate resource reign 8 bridge 0000:00:1c.2
 
      [4294668.694000] PCI: cannot allocate resource reign 0 device 0000:00:device
  
        Failed to allocate mem resource #6 ...
  
       
  
      Since the install completed "successfully", when trying to launch the OS (from grub) I get this same error
  
      in addition that that the OS could no mount the needed drive.
  
       
  
      Any assistance would be appreciated. 

numbers on the left side vary, and not all the lines are the same ( couldn't copy them all)

---

### Post by Ziox on 2006-08-13
> **nonick2k7 said:**
> Tried to install Ubuntu linux 6.06
When trying to install...
      Starts loading the Kernel, compression is successful
  
      however when trying to boot it I get this error:
       [4294668.694000] PCI: cannot allocate resource reign 7 bridge 0000:00:1c.0
 
      [4294668.694000] PCI: cannot allocate resource reign 8 bridge 0000:00:1c.0
 
      [4294668.694000] PCI: cannot allocate resource reign 7 bridge 0000:00:1c.1
       [4294668.694000] PCI: cannot allocate resource reign 8 bridge 0000:00:1c.1
 
      [4294668.694000] PCI: cannot allocate resource reign 7 bridge 0000:00:1c.2
 
      [4294668.694000] PCI: cannot allocate resource reign 8 bridge 0000:00:1c.2
 
      [4294668.694000] PCI: cannot allocate resource reign 0 device 0000:00:device
  
        Failed to allocate mem resource #6 ...
  
       
  
      Since the install completed "successfully", when trying to launch the OS (from grub) I get this same error
  
      in addition that that the OS could no mount the needed drive.
  
       
  
      Any assistance would be appreciated. 

numbers on the left side vary, and not all the lines are the same ( couldn't copy them all)

have you tried using the live CD? If that boots, then open up terminal and do:

lspci -v

that's just for troubleshooting, i have no idea how to solve your problem :confused: Sorry.

also, if live CD boots up correctly, then you should try installing from that, though I've heard it is a pain in the @$$

---

### Post by nonick2k7 on 2006-08-13
Ok, there is no connection between the hd mount issue and that kernel booting issue, I fixed the hd mounting issue, i meerely forgot to assign root ("/") partition. The other problem is still the same though, any input/help would be greately appreciated.

about the lspci -v command, what is it supposed to give me? since it lists the hardware I have...

if it helps at all, I am installing ubuntu on HP dv5164ea laptop, dual OS with windows XP.
thanks alot.

---

