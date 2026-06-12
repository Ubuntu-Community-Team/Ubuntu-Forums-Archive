---
title: "MD5 checksum error, ./pics/logo-50.jpg"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by winsbury on 2014-05-13
Having a strange problem installing 32bit 14.04LTS Server on a genuine Intel PIII rack mount 1.2GHz 4Gib ECC RAM with 2 x 40Gb raid array currently running Windows Server 2003, ie its a 'proper' albeit aged dedicated server machine. 

It boots the install CD perfectly and the install disc passes self test on other PC's here ( not servers ) but whenever I try to install on this machine or run the self test I get the error ./pics/logo-50.jpg failed MD5 checksum. 

According to this forum some older machines with very low ram have the same issue but this machine more than exceeds the minimum spec. 

Ive checked the bios and there's no options to configure the RAM any differently Ive also tried several discs and downloaded the torrent as well as the main .iso file all with the exact same results.

Any ideas gratefully received.

---

### Post by winsbury on 2014-05-14
Update: Have now tried a variety of CD / CD-RW discs all of which pass the self test MD5 on other machines but consistently fail  on the ./pics/logo-50.jpg failed MD5 checksum whenever I use the target server itself to run the test. 

The installation fails every time shortly after entering the keyboard country details and returns me to a menu where there is an option to execute an Ash shell.  From the shell #free shows the system has total memory of 6086504 available ( 6Gb ) which is what is physically in the box although Windows 2003 only ever saw just under 4Gb of it so I don't see how this can be a lack of memory issue.

I there any way to install without using the CD perhaps ?

---

### Post by mastablasta on 2014-05-14
yes there is a USB install or net install option. you are trying to install 32 bit server image with PAE enabled correct? does the CPU support PAE?

by the way self test tests the burned CD. if the CD drive is not working well it could also fail. so could it be the drive is mafuncitoning? ;) can you move CD drive form another mashcine to server to check this? and if drive is the issue you should be able to install it.

there is also net install image. only i image you still need a way to install it to computer first. another option would be to install next install on USB and then image it over to server using clonezila or similar.

i don't know how to do the raid in linux (at least not yet).

---

### Post by mörgæs on 2014-05-15
> **mastablasta said:**
> does the CPU support PAE?

Yes, it's a Pentium 3.

---

### Post by sudodus on 2014-05-15
> **winsbury said:**
> Update: Have now tried a variety of CD / CD-RW discs all of which pass the self test MD5 on other machines but consistently fail  on the ./pics/logo-50.jpg failed MD5 checksum whenever I use the target server itself to run the test. 

The installation fails every time shortly after entering the keyboard country details and returns me to a menu where there is an option to execute an Ash shell.  From the shell #free shows the system has total memory of 6086504 available ( 6Gb ) which is what is physically in the box although Windows 2003 only ever saw just under 4Gb of it so I don't see how this can be a lack of memory issue.

I there any way to install without using the CD perhaps ?

When the CD passes the md5sum test on other machines, it is OK.

Maybe the computer (the motherboard or processor) cannot manage 6 GB RAM in the early boot mode. Remove 4 GB, leaving only 2 GB, and try if  the CD passes the md5sum test, and can install the 14.04 LTS server.

> **mastablasta said:**
> yes there is a USB install or net install option. you are trying to install 32 bit server image with PAE enabled correct? does the CPU support PAE?

by the way self test tests the burned CD. if the CD drive is not working well it could also fail. so could it be the drive is mafuncitoning? ;) can you move CD drive form another mashcine to server to check this? and if drive is the issue you should be able to install it.

there is also net install image. only i image you still need a way to install it to computer first. another option would be to install next install on USB and then image it over to server using clonezila or similar.

i don't know how to do the raid in linux (at least not yet).

Yes, it can be a bad CD drive too.

> **mörgæs said:**
> Yes, it's a Pentium 3.

+1. Pentium 3 has PAE capability.

-o-

There might be a regression with some driver in 14.04 LTS. Sometimes it is better to run an old version of the operating system in an old computer, so I suggest that you try Ubuntu Server ***12.04.4 LTS*** (or Ubuntu mini.iso 12.04 LTS). It has 5 years of support (until April 2017).

---

### Post by LastDino on 2014-05-15
While you're at it, do check if those RAMs are of compatible frequency. Probably not the issue, but it can hamper your machine. My PC is from similar day and age and I had simlar problems till I decided to shift to new mobo with DDR3 support.

---

### Post by mörgæs on 2014-05-15
The logo-50 error has been around for several years, also on disks which pass the MD5 test. I don't have any god explanation why.

Hardware errors are unlikely in this case. 
Reverting to 12.04 could work, but I consider that a last resort.

Before that I suggest that you try the [minimal 14.04]("https://help.ubuntu.com/community/Installation/MinimalCD"). When/if that works you can add the server packages.

---

