---
title: "RS400 [Radeon Xpress 200M]"
date: 2010-01-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2010-01-22
I have a RS400 [Radeon Xpress 200M] card in my laptop, it is using the radeon driver.

It consistently crashes (freezes/blackscreen). Anyone else suffering?

---

### Post by benmoran on 2010-01-22
I've got a Dell Inspiron 1501 with the Radeon Xpress 1150. It's really similar to your card from what I could find out. Mine doesn't crash at all, but I get a borked display when I try to change the resolution.. I'm thinking in my case it's caused by RandR. 

Did you try using the Xorg Edgers PPA? It's got much more recent Radeon builds than what's shipped by default.

---

### Post by yasasflash on 2010-01-22
Hey my lap is ASUS one with RADEON XPRESS 200m. It instantly crashes when booted into kernal 2.6.32.11 (Lucid)
don't know where do i have to go from here.

---

### Post by Peter09 on 2010-01-22
Ahh glad to see I'm not alone in my gloom.....(one always feels better when someone else is in the **** with you :D ). I must admit Lucid has been a disaster for me, I've not had a working system at all.

---

### Post by xebian on 2010-01-22
Am I the lucky one? I use the plain vanilla radeon drivers and composting works very well.

---

### Post by Reiger on 2010-01-22
From lshw:
```

*-pci                                                                                                                             
          description: Host bridge                                                                                                     
          product: ATI Technologies Inc                                                                                                
          vendor: ATI Technologies Inc                                                                                                 
          physical id: 100                                                                                                             
          bus info: pci@0000:00:00.0                                                                                                   
          version: 01                                                                                                                  
          width: 32 bits                                                                                                               
          clock: 66MHz                                                                                                                 
          configuration: latency=64                                                                                                    
        *-pci:0                                                                                                                        
             description: PCI bridge                                                                                                   
             product: RS480 PCI Bridge                                                                                                 
             vendor: ATI Technologies Inc                                                                                              
             physical id: 1                                                                                                            
             bus info: pci@0000:00:01.0                                                                                                
             version: 00                                                                                                               
             width: 32 bits                                                                                                            
             clock: 66MHz                                                                                                              
             capabilities: pci bus_master cap_list                                                                                     
             resources: ioport:7000(size=4096) memory:f8800000-f88fffff memory:8ff00000-afefffff(prefetchable)                         
           *-display UNCLAIMED                                                                                                         
                description: VGA compatible controller                                                                                 
                product: RC410 [Radeon Xpress 200M]                                                                                    
                vendor: ATI Technologies Inc                                                                                           
                physical id: 5                                                                                                         
                bus info: pci@0000:01:05.0                                                                                             
                version: 00                                                                                                            
                width: 32 bits                                                                                                         
                clock: 66MHz                                                                                                           
                capabilities: pm msi bus_master cap_list                                                                               
                configuration: latency=64 mingnt=8                                                                                     
                resources: memory:90000000-9fffffff(prefetchable) ioport:7800(size=256) memory:f88f0000-f88fffff memory:f88c0000-f88dff
```

(Sticker on the notebook case claims it is a Xpress X1100 car tho.) Anyway: as long as I use radeon.modeset=0 things work, just fine.

---

### Post by yasasflash on 2010-01-23
> **xebian said:**
> Am I the lucky one? I use the plain vanilla radeon drivers and composting works very well.
Would you tell us how did you install it xebian.

---

### Post by mick222 on 2010-01-23
When i installed Lucid I had a lot of problems getting graphics to work ,my computer ran in low graphics mode,no compositing. The drivers from xorg-edgers are working great Iyou could try them.See here [https://launchpad.net/~xorg-edgers](https://launchpad.net/~xorg-edgers) remember they are expeimental so you could break x,but so far so good for me.

---

### Post by Lollerke on 2010-01-23
It's a bug with old Radeon cards.Pls click on this bug affects me too here: (if you have the "black screen and nothing happens" problem) [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/509273](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/509273)

---

### Post by jerrylamos on 2010-01-23
This one's working, I think, mostly (for an Alpha)

ATI Technologies Inc RC410 Radeon Xpress 200

The /boot/grub/grub.cfg is rather wierd looking with a bunch of crazy undecipherable stuff:

menuentry "Ubuntu, with Linux 2.6.32-11-generic-pae" {
        recordfail
        set quiet=1
        insmod ext2
        set root=(hd0,7)
        search --no-floppy --fs-uuid --set 42482367-4b8f-4277-a30c-bf63129ec04d
        linux   /boot/vmlinuz-2.6.32-11-generic-pae root=UUID=42482367-4b8f-4277
-a30c-bf63129ec04d ro   ipv6.disable=1 quiet splash
        initrd  /boot/initrd.img-2.6.32-11-generic-pae
}

?

Jerry

---

