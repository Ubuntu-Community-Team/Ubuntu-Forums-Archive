---
title: "Live CD  - P4C800-E Dx"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by Intrepid One on 2007-04-23
I Have tried to install Ubuntu on my machine here and every time i try to install it, It just hangs giving me a black screen with this really nice flashing cursor, I mean it this cursor is amazing it knows what it has to do and man does it do it well :lolflag:  , no but seriously  

Below is a list of hardware that i have 

Asus P4C800-E Dx
Intel 2.4 C 800 FSB
2 x 1 Gig Mushkin PC 4000
Ati Radeon X800
Aopen DVDRW 
SoundBlaster Audigy 
2 x 36 Gig WD Raptor SATA
2 x 250 Gig Seagate SATA 

After looking around here i see that there are soem BIOS issues it looks like, i will have to look and see how ancient this BIOS is .

---

### Post by bdowd on 2007-04-23
See these two other posts about your p4c800 ASUS motherboard

Kernel errors after upgrading from Edgy to Feisty
I just upgraded from Edgy to Feisty using the Update Manager. After upgrading my Terminal windows are flooded with these messages from syslogd:

Apr 21 07:38:40 jcomputer kernel: [35273.930290] EDAC MC0: UE page 0x1fffc, offset 0x0, grain 4096, row 0, labels ":": i82875p UE
Apr 21 07:38:41 jcomputer kernel: [35274.930089] EDAC MC0: UE page 0x1fffc, offset 0x0, grain 4096, row 0, labels ":": i82875p UE
Apr 21 07:38:42 jcomputer kernel: [35275.929888] EDAC MC0: UE page 0x1fff0, offset 0x0, grain 4096, row 0, labels ":": i82875p UE

I get one message every second. I suspect this has something to with my motherboard, an ASUS p4c800-Deluxe, as it uses an Intel 875p chipset.

Has anyone seen these messages? Do you know how to fix it?

Cheers,
Jacob
Reply With Quote Multi-Quote This Message Quick reply to this message
brdhse1
View Public Profile
Send a private message to brdhse1
Find all posts by brdhse1
Add brdhse1 to Your Buddy List
  #2   Report Post  
Old 1 Day Ago
bdowd bdowd is offline
First Cup of Ubuntu
	  	
Join Date: May 2006
Beans: 6
Re: Kernel errors after upgrading from Edgy to Feisty
I have the same error except that this was on a blank install (on a machine which had previously run 6.10. The MB speaker is beeping each and every second. It stopped when I re-booted my computer, but syslogd is announcing the error occurs every second which is apparent when the console (within the GUI) is opened ... making it most useless.
EDAC MC0: UE page 0x1f908, offset 0x0, grain 4096, row 0, labels ":": i82875p UE
Funny thing: P4C800 Motherboard from ASUS
Last edited by bdowd : 1 Day Ago at 08:44 PM.
Edit/Delete Message

---

### Post by rbmorse on 2007-04-23
Are your drives are in RAID configuration, as your component list suggests? I don't know if the installer supports that.

---

### Post by TexMex657 on 2007-07-02
> **bdowd said:**
> See these two other posts about your p4c800 ASUS motherboard

Kernel errors after upgrading from Edgy to Feisty
I just upgraded from Edgy to Feisty using the Update Manager. After upgrading my Terminal windows are flooded with these messages from syslogd:

Apr 21 07:38:40 jcomputer kernel: [35273.930290] EDAC MC0: UE page 0x1fffc, offset 0x0, grain 4096, row 0, labels ":": i82875p UE
Apr 21 07:38:41 jcomputer kernel: [35274.930089] EDAC MC0: UE page 0x1fffc, offset 0x0, grain 4096, row 0, labels ":": i82875p UE
Apr 21 07:38:42 jcomputer kernel: [35275.929888] EDAC MC0: UE page 0x1fff0, offset 0x0, grain 4096, row 0, labels ":": i82875p UE

I get one message every second. I suspect this has something to with my motherboard, an ASUS p4c800-Deluxe, as it uses an Intel 875p chipset.

Has anyone seen these messages? Do you know how to fix it?

Cheers,
Jacob
Reply With Quote Multi-Quote This Message Quick reply to this message
brdhse1
View Public Profile
Send a private message to brdhse1
Find all posts by brdhse1
Add brdhse1 to Your Buddy List
  #2   Report Post  
Old 1 Day Ago
bdowd bdowd is offline
First Cup of Ubuntu
	  	
Join Date: May 2006
Beans: 6
Re: Kernel errors after upgrading from Edgy to Feisty
I have the same error except that this was on a blank install (on a machine which had previously run 6.10. The MB speaker is beeping each and every second. It stopped when I re-booted my computer, but syslogd is announcing the error occurs every second which is apparent when the console (within the GUI) is opened ... making it most useless.
EDAC MC0: UE page 0x1f908, offset 0x0, grain 4096, row 0, labels ":": i82875p UE
Funny thing: P4C800 Motherboard from ASUS
Last edited by bdowd : 1 Day Ago at 08:44 PM.
Edit/Delete Message

I'm having the kernel message problem and my drives are not in RAID config.

---

