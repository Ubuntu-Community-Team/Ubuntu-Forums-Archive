---
title: "boot problems: failed to set xfermode / exception emask...frozen"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by ImALittleTeaPot on 2007-12-28
Maybe the General Help forum is a better place to post my problem. 

> **ImALittleTeaPot said:**
> I'm having install/boot problems with gutsy 7.10.  

The kernal version is 2.6.22-14 generic. Its a live cd that i downloaded (32bit). 

System:
abit IP-35 Pro Mobo
Lite On DVD RW
Seagate Barracuda 320GB
ATI Radeon X1950XT Video Card


I set BIOS to boot from cd, get as far as the UBUNTU screen with the orange bar going side to side. Then this error message. 
[ATTACH]54514[/ATTACH]

_UPDATE_:
After many attempts at booting from the live cd, I finally suceeded, but don't know why. So i tried it a few more times to see what would happen. Apparently my system will boot from the live cd RANDOMLY (like 1 of 7 attempts give or take). This is weird. Also....more problems occur. I was able to install, then this screen (splash screen?) will hang when Ubuntu tries to boot from the hard drive.
[ATTACH]54512[/ATTACH]

During the hang, I pressed ctrl+alt+F1 to get a little more info about errors. Here it is.
[ATTACH]54513[/ATTACH]

Notice that its telling me that a file is missing in my /dev/disk/by-uuid/xx-xxx.
I think that this is the UUIP address of my root partition. 

After tinkering around in grub (hitting 'e' and editing boot parameters), I've found that I can boot into Desktop if I add either the parameter "irqpoll" or "acpi=off" at the end of the kernel line:
/boot/vmlinuz-2.6.22-14-generic root=UUID=7eec31fb-03e9-40cd-861a-efe58a7aec56 ro quiet splash (append here)

But this doesn't really "fix" the problem. booting from the live cd is still random, and I am told that those boot parameters might hurt performance.

Any insight into this would be greatly appreciated.

I get the same error messages when using the live 64 bit cd.
I would really appreciate any feedback anyone who might know what is causing all this.

---

### Post by Pumalite on 2007-12-28
Use the Alternate CD to install.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below sign 'Start Download'

---

### Post by ImALittleTeaPot on 2007-12-28
I'll do that. I've might've tried already, but i don't remember, will download it again.  Also..Gutsy will boot up 100% of the time if i change the SATA settings in BIOS from IDE to AHCI. But, in doing so, I cannot boot up my Window XP or VISTA. 

I want a triple boot if possible.

Update: Tried it. same error messages.
Please..why can't it find my root partition??

---

