---
title: "strange error message sometimes during boot"
date: 2005-02-28
forum: Installation &amp; Upgrades
---

### Post by olsmat on 2005-02-28
Hi, 

Every now and then I get a strange error message when booting Ubuntu (which btw is the best Linux I've had, recently used Mandrake and SUSE) and I have to reset the computer. The problem has never occured two times in a row. 

Anyone know what it is? Is it dangerous? Can it be fixed?


The error message: 

Process mount (pid: 196, treadinfo=cfa66000 task=df94a600)

Stack:  (a matrix 3x8 of hexdec numbers, ranging from (1,1): 00000001 to (3,8): c012dce3) 

Call trace:
c0115ea5   default_wake_function+0x0/0x12
c024ce48    __down_failed+0x8/0xc
c017f90d   .text.lock.inode+0x7d/0x8c
c012dce3   page_cache_read+0x53/0xb7
c012df0f    filemap_nopage+0x1c8/0x30d
c0139149    do_no_pgae+0xa6/0x2cf
c01394a6    filp_open+0x41/0x49
c0157568    dput+0x1a/0x1cc
c0145327    __fput+0xd5/0xf8
c0143f9f    filp_close+0x5a/0x63
c0114874    do_page_fault+0x0/0x49f
c0106a1d    error_code+0x2d/0x68

Code: 8b 50 04 89 44 24 0c 89 48 04 89 0a 89 54 24 10 ff 46 04 8b

<6>note: mount[196] exited with preempt_count 1


Kindly, 

Mattias Olsson 
Sweden

---

### Post by alastair on 2005-02-28
Looks like it might be a kernel panic/oops.

What kernel is this - "uname -r".

There might be more in the log file :

/var/log/syslog

---

### Post by olsmat on 2005-03-02
Hi, 

I have kernel 2.6.8.1-3-386, the error has occured on when using kernel 2.6.8.1-4-386 as well. I switched to 2.6.8.1-3-386 (2.6.8.1-4-386 is the first choice in grub on my installation (Warty 4.10, the default choice when downloading from the home page)) in hope that the error would occur less frequently, and I believe that it works better, but it's hard to tell since it's quite random. It has never happen two times directly after each other, though. 

I looked in /var/log/syslog but found nothing that I could spot as a crash. I guess that the logging hasn't yet started when the crash happens. 

I'm mostly concerned about my data on the hard drive, could there be a risk of corrupted data? 

Kindly,


Mattias Olsson

---

### Post by Cossins on 2005-03-02
Could be a corrupted module. In fact, I don't really know, but try cleaning out your modules, make a new initrd (mkinitrd - I'm not sure how this works with Ubuntu 8-[) and reinstall the kernel.

That's what I would do, anyways. :)

Harddisk corruption is not impossible.

- Simon

---

### Post by olsmat on 2005-03-10
That seems to be above my skills, seems to be difficult and risky... I don't know how to do it anyway. Maybe it'll be better if I upgrade to Hoary once the stable version is released? The only thing that really scares me is the risk of harddisk corruption. But since I store my data on a  fat32 partition shared by Linux and Windows, the risk should be small, or am I fooling myself there? 

/Mattias

---

### Post by alastair on 2005-03-10
You are probably fooling yourself - it depends what is wrong with your machine and what the error means. If it is a hard disk problem, no partition is "safe". 

It might be worth printing more of the error you get - with context (i.e. a few lines above and below). Show it "as is".

---

### Post by olsmat on 2005-03-15
I have copied everthing. There is nothing after, the computer stalls and I have to reset. The last line is
<6>note: mount[196] exited with preempt_count 1

The only thing I left out was the complete memory dump of hexdec numbers, I just copied the first and the last entry of the stack. 

The message comes immedeately after grub has started Linux. If there are lines printed on the screen before this message, they dissappear to quick and are replaced by all the lines I wrote in the first message. Normally, there's a message like: "uncompressing kernel: ok" or something like that as one of the first lines during boot. That line is not printed or is overwritten by the error message. It can't be seen, anyway. 

Anyone's got a clue? 

Kindly,
Mattias

---

### Post by alastair on 2005-03-15
Is there any more to the error messages? More context above in the logs?

Is anything connected to the PC that might cause this? Anything "hotplug"able you could remove?

---

### Post by olsmat on 2005-03-16
I have checked the logs, but there's nothing to be found. It appears as if the system crashes before the logging is initiated. 

My computer is a quite simple one; AMD Duron 750 MHz, 256 MB RAM, 60 GB IBM HD, Nvidia Riva TNT2 64 (32 MB), integrated sound (Via AC97 something), Netgear WG311 wlan card 802.11g (Atheros chipset), no USB devices, ATAPI CD R/W. 

There is an issue with the hotplug modules during boot, but that appears a lot later than the error described earlier. There are a couple of error messages but it  never causes the computer to crash; there is a delay and the hotplug things are skipped. 

I have not had the opportunity to test if USB devices even work on my Ubuntu installation. Will finally get my camera back in the end of this week. USB has not been a problem on previous Linux installations, it has been working with no need for configuring. 


/Mattias

---

### Post by olsmat on 2005-03-17
I've got more info now: 

The entire screen that shows when the computer stalls is as following. I believe, but I'm not 100% shure that the boot process started uncompressing the Linux kernel with exit status [ok]. (Btw, something must have been started, because I can type and characters show on the screen. Enter and backspace works as they use to. )

EIP: 0060: [<c024cc74>] Not tainted
EFLAGS: 00010002 (2.6.8.1-3-386)
EIP is at __down+0x44/0xef
eax: 00000008  ebx: 00000286  ecx: cfa67e18  edx: cfa66000
esi: 000000  edi: cfa67e20   ebp: cf94a600  esp: cfa67e0c
ds: 007b  es: 007b  ss: 0068 

Process mount (pid: 196, treadinfo=cfa66000 task=df94a600)

Stack: 
00000001  ef97a600  c0115ea5  00000000  00000000  00000001  00000000  00000282
c11f48a0  c028fb00  cfa45000  00013855  c024ce48  00000000  000008dc  0fa45000
c017f90d  cfbc6e00  00000000 c11f48a0  cf8dac78  00000000 cfba0560  c012dce3

Call trace:
c0115ea5 default_wake_function+0x0/0x12
c024ce48 __down_failed+0x8/0xc
c017f90d .text.lock.inode+0x7d/0x8c
c012dce3 page_cache_read+0x53/0xb7
c012df0f filemap_nopage+0x1c8/0x30d
c0139149 do_no_page+0xa6/0x2cf
c01394a6 filp_open+0x41/0x49
c0157568 dput+0x1a/0x1cc
c0145327 __fput+0xd5/0xf8
c0143f9f filp_close+0x5a/0x63
c0114874 do_page_fault+0x0/0x49f
c0106a1d error_code+0x2d/0x68

Code: 8b 50 04 89 44 24 0c 89 48 04 89 0a 89 54 24 10 ff 46 04 8b

<6>note: mount[196] exited with preempt_count 1

---

The stack seem to be identical every time. 

--

During healty boots, I noticed that the first line after uncompressing the Linux kernel is: 
mounting a tmpfs over /dev        [ok]

Could the problem have something to do with that step? 

--

You asked about hotplug. There is a problem with that. These lines occur during every boot: 

Starting hotplug subsystem ...
modprobe: FATAL : Error inserting pciehp (/lib/modules/2.6.8.1-3-386/kernels/drivers/pci/hotplug/pciehp.ko) : operation not permitted 

modprobe: FATAL : Error inserting shpchp (/lib/modules/2.6.8.1-3-386/kernels/drivers/pci/hotplug/shpchp.ko) : operation not permitted 
                                [ok]

There is obviously a problem, but it can't have anything to do with the first one. By the way, do you know how to fix it? Or should I wait for the stable version of Hoary and hope that everything will be good then? 


Kindly, 

Mattias

---

### Post by alastair on 2005-03-17
For the module errors (pciehp etc.) - this is PCI hotplug and might be safe to "blacklist" - see /etc/hotplug/blacklist.

For the kernel problem - might be worth running a "memtest" - it's a GRUB option I think. Just as a check.

---

### Post by Ti-Paul on 2005-03-25
I have the same bug on two of my systems:
Dell Inspiron 5150 laptop
and
Dell GX110 Desktop

As said by olsmat, this is occuring rarely on power-up boot...

I had this problem with all version of Ubuntu linux image (3, 4 and 5)...

Just need to CTRL-ALT-DEL to reboot and never had the freeze twice in a row...

This doesn't seem to affect partition since the system isn't mounting any partition... But cannot guaranty it... 

It's not a big headache for me but if my wife encounter this (never for the moment), she'll be blasting me...  [-o< 

NB: Never had this kind of problem with all distro i've used before... (Slack, Mandrake, RedHat, Fedora...etc...)

IF ONLY I COULD IRRADICATE THIS ONE!!!

Regards,
Ti-Paul

---

### Post by hounddog32 on 2005-03-30
I'm using a sony vaio z600 and on every single boot i get a similar message and hexdump ```
<6>note: mount[197] exited with preempt_count 1
```I'm downloading hoary to have a go, but this may end my ubuntu ambitions if I can't get it going. I have previously used mandrake 10.1 on the vaio with no problems.
If i boot into the recovery option in grub i get exactly the same modprobe error notifications as olsmat before gettin a command prompt - that's all i can get out of warty  :sad:

---

### Post by Ti-Paul on 2005-04-01
[-o< 
Hope that Hoary will help this annoying bug...
 [-o< 

This thread should be moved to the "Stumper Questions forum"
^Moderator Action Required!!!  8-[ 

This should be tracked... Never had this one before and it's very irritating when you have a server (small home one... not to critical.) that is configured to reboot when a power outage is occuring, and you got your server stuck on this bootup freeze bug and can't access it anymore...  [-X 

I'm currently considering switching back my small SAMBA server to Slackware if Hoary isn't helping me with this bug... (Switched to Ubuntu because i'm devoted to gnome, and i wanted my workstation and server to be the same...)

Regards,
Ti-Paul

---

### Post by hounddog32 on 2005-04-01
Hoary helped for me - i loaded it on a couple of days ago and have not had the problem since. Yey! I hope a mod does look in on this and hope you can get it sorted, Paul.

---

### Post by Ti-Paul on 2005-04-01
Ahhhhhhh...

Can't wait for the Hoary release... But i'll wait anyway... Just don't want to get full of packages updates to download...  :razz:

---

### Post by hounddog32 on 2005-04-01
[QUOTE=Ti-Paul]Ahhhhhhh...

Can't wait for the Hoary release... But i'll wait anyway... Just don't want to get full of packages updates to download...  :razz:[/QUOTE]
 Yeah, updates were a beast, but what else is broadband for?! And well worth it to have my baby back online again!

---

