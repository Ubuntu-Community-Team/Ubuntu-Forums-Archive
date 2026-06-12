---
title: "problem updating to 24.04"
date: 2024-09-15
forum: Installation &amp; Upgrades
---

### Post by jgw on 2024-09-15
I was told that 24.04 was ready and did I want to upgrade.  I said yes.  I have 5 systems.  One went through everything and upgraded just fine.  My system which I had previously setup before it was ready also updated for about 20 minutes which I suspect fixed stuff that needed it and its running fine.  Then there are the problems.  One was upgrading and then stuck when it was installing after it downloaded everything.  I gave it an hour before I did anything to make sure it was stuck and just not working.  then I rebooted.  The first time it booted and gifted me with a black screen.  I gave that another hour but it was stuck.  I booted again and, this time, pressed f7 and this asked me what to do and so I let it try to boot again.  This time I got stuff.  The top said something like:
first line: not syncing - v et not able to mount root, etc
last line: end kernal panic not syncing  ufs: not able to mount root fson unknown - (0,0)]___

Before I do anything else I thought I had better ask what I should do.  My thought is to create a new thing with startup disk creator and have at that but want to get thoughts before I screw everything up.

---

### Post by oldfred on 2024-09-15
Issues often are related to proprietary drivers or ppas.
Best to uninstall all drivers & ppas, then reinstall after upgrade.

Are specs posted for the system with issues?

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by jgw on 2024-09-20
Thank you for the reply - apologize for the time, had another problem..........

Anyway, you are waaay ahead of me on this stuff.  For instance, I have no idea what a bootinfo summary report is nor how to get one.  I read the suggested stuff.  The boot-repair thing is interesting but, I suspect, not going to be helpful.  This system was in the midst of installing 24.04 when it went to a black screen.  At the time it was about into installing for between 5 and 10 minutes.  I don't think that will deal with the problem.  I am quite willing to try but........

The second one, I suspect, has the same problems.  I actually think that restarting the entire install is, probably the only thing that I can do and am not even sure about that one.  My problem is that those systems were for the bad install I initially did and not this one.  I can, however, I think, take one of those, download the latest and greatest 24.04   I have some options.  First, I could setup a bootable usb stick, put a clean 1tb ssd into the machine and have at the installation.  (after that is done I can then take the screwed up ssd and take whatever I want to save off of that one and then re-partition it).  I am tending to want to do that.    The other thing I could do would be to put a new system directly onto a 1tb disc and then put it into the failed system.  I kinda like the first one.  In any case any thought you might have I would be grateful for before I started on this one.

Thanks again for the reply!!

---

### Post by 1fallen on 2024-09-20
> **jgw said:**
>  I have no idea what a bootinfo summary report is nor how to get one.

Thanks again for the reply!!

Look here, but you already know this: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by jgw on 2024-09-20
I am currently having problems with my mice freezing along with my keyboard.

Anyway, I responded to this and sent it and its not here either.  Basically I sent 3 pictures of why my system looks like when booting.  I am going to try and get those spent before something blows up. And then try and explain.

---

### Post by jgw on 2024-09-20
Now, I have sent my pictures.  I should also mention that each picture took time because each time I tried to send them my system froze (on two machines).  anyway, I got that done.  Now, My system has a problem because it was being updated to 24.04 and stopped about 5/10 minutes into installing the new ubuntu.  So, basically, it doesn't have a bunch of stuff there for it to do anything with (I think).  My systems all have 1tb sdd's for the basic system.  My thought is to just take out the old one to later check for data and install blank sdd's.  I figured this would be simple but, apparently, things have now changed so I fear doing even that before somebody tells me how I should do it.  

Incidentally, I took a bootable usb and put that into the machine to see what would happen.  What happened was nothing as the machine didn't even know it was there.  I had two and tried both, they both failed.  I am not sure what would have happened had they done something as they both had the 2400.04's that were screwed going in because they had not really been released - just available,  

I am now going to send this and, hopefully, it too will get through before something stops or freezes.

---

### Post by jgw on 2024-09-20
I have now switched to xorg from wayfare which, apparently, fixed my problem with my mouse.  Now all I need is somebody to tell me how to re-install 24.04 into my blowed up system, using a 1tb sdd,  above and, then, maybe everything will be dandy.

---

### Post by ubfan1 on 2024-09-20
Dell Optiplex 790 is 64 bit UEFI capable (probably not secure boot though), and should take a SATA SSD (not an nvme one). I'd try a new install using any UEFI options available. Note the UEFI/CMS(legacy) setup is pretty machine specific -- some have you select one mode, others allow you to "prefer" one mode over the other.  If a preference is offered, choose the UEFI, and ensure your install media was not created for legacy mode only.  The ISO boots both ways, but some tools allow you to select a mode for the install media.

---

### Post by jgw on 2024-09-21
Thanks for the reply!

If I press f12, while booting I get two choices:

LEGACY BOOT:
    CD/DVD/CD-RW Drive
    Onboard NID
OTHER OPTIONS:
    BIOS Setup
    Diagnostics
    Intel(R) ManGEWMENT eNGINE bios eXTENSION (mebX)

If I can figure out how to install a system onto an existing 1tb ssd drive then all I have to do is to install that ssd and should be on the way.  I used to do that but have forgotten how (I am old and a bit demented).  I have the ssd's just need help in doing that one.  I have tried to search the net for how ti do that.  There is a lot of stuff to try but I would feel a lot better if somebody could point me to the best one.  I also need to download the latest 24.04.?  but am not sure that I might be better off with 22.04.5 for now.  

Thoughts?

---

### Post by jgw on 2024-09-21
I somehow managed to post this twice.  I would delete it but fear everything else would go with it - sorry............

---

### Post by jgw on 2024-09-22
I am setting this one as solved as its evolved.

---

