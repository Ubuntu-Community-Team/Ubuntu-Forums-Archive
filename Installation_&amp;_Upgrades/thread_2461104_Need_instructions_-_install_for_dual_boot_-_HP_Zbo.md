---
title: "Need instructions - install for dual boot - HP Zboook fury 17"
date: 2021-04-24
forum: Installation &amp; Upgrades
---

### Post by ipsewfacto on 2021-04-24
Hello, 
Me = rookie. Used linux 10+ yrs ago. 
Now = Downloading Ubuntu 20.04.2.0

Aim: Dual boot windows and Ubuntu on HP Zbook Fury 17 g7. 

PROBLEM: I don't understand partitioning drives - so I need to find good instructions that can show me what to do, or that can do it for me well.  Can you point me to a website page or video that will show me what to do? 

Hardware: HP Zbook Fury 17 g7
(Am assuming since HP Zbooks offer Ubuntu versions, then my laptop which came with Windows should run ubuntu fine? If that's not the case, please tell me.) 

My Use Plans:  
Enable Firewall & whatever privacy and security is offered for Ubuntu (need to learn about this)
Enable ProtonVPN
Probably mostly use Brave browser and DuckDuckGo.
Writing  (fiction and journaling - security / privacy an aim here)
Watching news videos (privacy an aim - I don't want to be profiled by my news channel choices.)
Possibly do some work with Inkscape and similar software. 

Security-wise, I'm not interesting. I don't do risky things. I'm not a journalist. No social media. I don't even do gaming. Once I get the software installed that I need, I probably will not add anything over time. Will stick with software offered directly through repository but not outside PPAs. I just don't want my journaling, work, and other information accessible by others. (Physical / in-person access is not a concern)

I use Mac, Win, and now hopefully Linux to help with my privacy concerns.

Would like to do - but unsure if privacy would be compromised. Might keep separate browser (Firefox?) just for this: 
- log into Amazon to place orders (+ a few other known safe sites)
- banking occasionally 

Thoughts and suggestions are welcome. 
Thank you in advance.

---

### Post by tea for one on 2021-04-24
> **ipsewfacto said:**
> 
Hardware: HP Zbook Fury 17 g7
(Am assuming since HP Zbooks offer Ubuntu versions, then my laptop which came with Windows should run ubuntu fine? If that's not the case, please tell me.) 


First task is to make a USB with your chosen Ubuntu ISO and run a [COLOR="#0000FF"]live[/COLOR] session.
A live session will allow you to test your hardware to your own satisfaction.

Are you familiar with this process?

---

### Post by oldfred on 2021-04-24
Since new system, it will be UEFI not old BIOS.
And UEFI uses gpt partitioning not very old MBR(msdos).

Default install now is just one partition for / (root) and it will reuse the ESP - efi system partition that Windows has.
You typically have to make several UEFI & Windows setting changes.
And depending on video card and if AMD or Intel may need other settings.

General instructions in link in my signature. 
Most of link is for specific issues & can be skipped, unless of course you have that issue.

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Depending on what tool you use to create USB flash drive installer, it may make one that only boots in either BIOS/MBR or UEFI/gpt. You want UEFI. Most create bootable flash drive that can boot in either UEFI or BIOS and in your UEFI must select the UEFI boot option often UEFI:flash where flash is a name or label of flash drive.

---

