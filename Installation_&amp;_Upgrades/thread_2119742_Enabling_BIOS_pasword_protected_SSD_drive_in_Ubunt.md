---
title: "Enabling BIOS pasword protected SSD drive in Ubuntu 12.10"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by jnelken on 2013-02-24
**Enabling BIOS pasword protected SSD drive in Ubuntu 12.10** 			
 			 			 		   		 		 		I have posted it in [Hardware, but I think better place would be in [Installation]. Sorry for the cross-posting, if some gentle soul will show me how can I reference in Area X post from Area Y - I will be thankfull.

I have IBM  Thinkpad laptop with OCZ Vertex 4 SSD drive with Windows 7 - /dev/sda.  This drive when using HD password in Bios (which I am) is automatically  encrypted.

When UBUNTU 12.10 is installed on second hard drive - /dev/sdb - (USB  attached) and booted from it - it cannot even mount Windows 7 SSD drive.

I am *not* using bitlocker. This SSD drive uses AES256 encryption.

BIOS disk password - when set - triggers encryption in firmware of the  drive. Whole disk is encrypted - including partition table and MBR.

Ubuntu can see this drive only when BIOS disk password is disabled - but  this unfortunately is in violation of the company policy :sad:

How can I make UBUNTu "see" my SSD drive? I am assuming that somehow  entering somewhere HDD password would be sufficient. I would like *NOT*  to lose my Windows 7 installation.

---

### Post by cariboo on 2013-02-24
> **istealth shadow said:**
> disable your bios password... 

then re enable it when they look at your computer.

or you can just go into windows and copy files to your usb :)

if its your computer you can do what you want. they are stupid if they wont let you do what you want on your own computer.

if its there's then just do what i said.

I guess you didn't see this part of the post:

> Ubuntu can see this drive only when BIOS disk password is disabled - but this unfortunately is in ***violation of the company policy***

---

### Post by presence1960 on 2013-02-24
If it is a company machine you will be a major fool to bypass any "security" measures they have in place. At my company that means immediate dismissal with no questions asked.

I would assume your company has a policy against installation of unauthorized software as well. I am going to take the guess ubuntu is not authorized or it would have been preinstalled by your IT department.

If you value your employment you won't pursue this as when you are connected to the company network they will most likely detect something.

Someone just got fired at my employer for bypassing our Fortinet hardware firewalls and booting off a linux live USB on a company machine to access the internet.

---

### Post by jnelken on 2013-02-25
Thank you all for your comments; I will try to simplify problem description:

I have Thinkpad with SSD with AES encryption in firmware.
I am booting Ubuntu 12.10 from USB.
No other drives are present.

When HDD BIOS password is enabled, SSD drive is not accessible to UBUNTU.
When HDD BIOS password is disabled, I am able to install UBUNTU on this drive.

What steps are required to install UBUNTU on such SSD with BIOS password enabled - or is this scenario not supported? If so should it make its way to HCL (Hardware [in]Compatibility List?

---

### Post by presence1960 on 2013-02-25
> **jnelken said:**
> Thank you all for your comments; I will try to simplify problem description:

I have Thinkpad with SSD with AES encryption in firmware.
I am booting Ubuntu 12.10 from USB.
No other drives are present.

When HDD BIOS password is enabled, SSD drive is not accessible to UBUNTU.
When HDD BIOS password is disabled, I am able to install UBUNTU on this drive.

What steps are required to install UBUNTU on such SSD with BIOS password enabled - or is this scenario not supported? If so should it make its way to HCL (Hardware [in]Compatibility List?

It is a company computer so why don't you just ask your IT department or your supervisor how to do it. I will not help circumvent security on a company machine which may contain proprietary and intellectual information.

---

### Post by jnelken on 2013-02-25
I am confused a bit:

I am asking how to install Ubuntu *WITH* BIOS password enabled! Needless to say - *I* am the person who sets up BIOS password - and *I* am the person who does not want to have Ubuntu installed *WITHOUT* BIOS password - although I verified that this is working. 

Where do you see attempts to circumvent company security polisy here - I am trying to adhere to this policy.

It appears that Ubuntu 12.10 does not recognize SSD with encryption in drive firmware enabled - and this is scenario I am trying to implement - IN ACCORDANCE to company policy.

---

### Post by presence1960 on 2013-02-25
With all due respect, I have been a manager in a large national company for a very long time. I would suggest you ask your IT department, your supervisor or if a small company, the owner to have ubuntu and this SSD set up properly. Any company I have ever worked for does not allow for installation of software. Approved software is always pre-loaded and any new installations/upgrades are done by IT via the network.

I can not in good faith help you here because it is a company machine. If I didn't know this fact things would be different. Sorry.

---

### Post by jnelken on 2013-02-26
Thank you for sharing your views. Things are not necessarily as black or white as other people see :-)
Help[less] desk points that with PGP is the same story - dual boot Win and Linux is not working as well as is not supported by PGP.

I use Linux and Windows for work; self-installing required software is standard procedure. 

I installed Ubuntu on second drive, added it to Win7 boot manager and I am able to proceed - although with two inconveniences:

- Encrypted SSD is not recognized by Ubuntu at all - so I use shared logical partition from second HDD to exchange data.
- Ubuntu boot process is long - it tries to recognize encrypted SSD and must wait to fail to proceed with boot process.

For your "security" concerns: if I disable BIOS password thus switching off encryption - I would proceed without a glitch (tested it on my laptop); only because I am following company policy [primary disk must be encrypted] I havve tose two inconveniences.

So - if you *know* for fact, that Ubuntu supports firmware encrypted SSD with BIOS password and *can* confirm that - then I will accept fact that I am  lacking knowledge to set it up, otherwise I have to assume that Ubuntu has same limitation as PGP.

---

### Post by grahammechanical on 2013-02-26
May I make an uneducated comment?

We do not have different kinds of Ubuntu. We do not have Standard, Premium, Enterprise Ubuntu. We just have the Ubuntu that anyone can download. So, if Ubuntu is unable to access this encrypted drive, then it is unable to do that because it is not designed to do that.

They say that all things are possible. So, if it is possible to get Ubuntu to do this thing, then it would be information that should not be made public on a forum like this. If fact it would be against forum policy to publicise that kind of knowledge.

Also keep in mind that you want to do this from

> I am booting Ubuntu 12.10 from USB.

Ubuntu is not a hackers distribution. It sounds to me that you want information that would enable anyone to turn Ubuntu on USB into a hackers OS that is able to overcome hard disk encryption.

That may not be your purpose but it would be what is done if anyone provided you with the information that you seek. If your intention is to install Ubuntu on to that drive, then have you tried turning off hard disk encryption, installing Ubuntu on to the drive and then re-enabling hard disk encryption and testing to see if you can boot into both Windows and Ubuntu? Or have you already tried that?

Regards.

---

### Post by jnelken on 2013-02-26
I am sorry if I did not explain myself clearly:

I boot Ubuntu **[COLOR=Red]Installer [/COLOR]**from USB - another words I created Ubuntu Install bootable USB from Ubuntu (Server) downloaded from Ubuntu site.

This is why I posted this in Install forum - issue is with INSTALLING ubuntu on an SSD which is encrypted by SSD firmware.

Yes - I did try with HDD BIOS password disabled. Ubuntu installs fine. When BIOS HDD password is added - it won't boot- it does not see the drive at all.

Somehow it appears that  SDD drive with encryption in firmware is not seen from the Ubuntu as a valid drive - when BIOS password is enabled.

I believe that BIOS password is used by firmware to encrypt the key (AES256) which firmware is using to encrypt data on SDD. This is only my guess.

I was looking rather for a way to tell Ubuntu that disk is BIOS password protected - I don't mind entering this password second time when booting Ubuntu.

Somehow Windows appears to bypass this BIOS password/encrypted key issue - if my theory is correct.

I am surprised that with encrypted drives SSD drives (like OCZ Vertex 4 with AES 256-bit encryption being more and more popular - I am the first person encountering this problem. Perhaps I should try lottery this week? :)

---

### Post by save2 on 2013-04-22
actaully I am owner of Vertex 3 and I'm surprised the v4 support AES256. I always believed that OCZ supported the simpler 8 char password .
but as far as I understand the way to access that disk is when booting your laptop it should pop up the BIOS question for  the HDD password (just like boot password)
so the question is , at boot time, does your BIOS asks you for the HDD password ?
if not , there is always a possibility to use hdparm from command line

---

