---
title: "Lenovo not support any form of dual boot or change to OS"
date: 2022-01-06
forum: Installation &amp; Upgrades
---

### Post by dattvidc on 2022-01-06
Hi,
I just had a weird conversation with Lenovo tech support.
I asked them if my flex 5 was supporting dual booting Ubuntu, and this was the answer> 

Lenovo don't support modification to the device since the machine came originally with OS win 10 and never able to change that because it will void the warranty

so - this seems weird to me, because with my HDD partitioned (which it already was) - This should not touch WINdows.

Did I just mess up buying Lenovo ? I got this because A-Price, and B Lenovo just announced a year or two ago, that they would start working better with Linux.
I am considering just accepting that the warranty is voided and go with Ubuntu anyway - does anyone have experience with Lenovo flex 5 ?

---

### Post by QIII on 2022-01-07
If you change the size of your Windows partition to allow for Ubuntu, then you have changed the original state of the machine and they are probably well within their rights to deny warranty claims.  If you can create restore media, you might be able to use that to get it back to its original factory state.

Have you considered running Ubuntu in a virtual machine, perhaps using VirtualBox?  A Ryzen 5 and 8GB of RAM should be plenty to keep both OSes happy.  You would have Ubuntu and you would not void your warranty.

---

### Post by MAFoElffen on 2022-01-07
I am a certified Lenovo WarrantyTech..  ( along with Dell and HP)

QIII gave good advice, until the warranty is over... The loop hole on that is that Lenovo does support Ubuntu, sells Ubuntu pre-installed on certain machines they sell, and... at  their own Depot Repair Facilities, has their own proprietary PXE boot system application / service that diagnoses multitudes of systems at the same time, that is running from Ubuntu based servers in that infrastructure... As a Lenovo Service Tech, I was privy to that information... But their Tier-1 phone support staff might not know those details. In fact, while I had access, and because I have supported Ubuntu for over a decade, and been on the Ubuntu Server Team for almost as long... I downloaded their Depot Server app, just to see what they were doing, how, and why... It was in my Cert training, so why not, right?

The safest way it to keep clearly within the boundaries. That it appears to not be in conflict of any kind. In recent/current.... Since UEFI booted, it is not in conflict (but they might contest that)  as it was in the past with CSM. If is a sidelined installation. It does not over-write anything they have in the original installation... (except maybe the size of the original partitions and...) except if they replace the hard disk, and that hard disk includes a preinstalled OS. That was some of my specific service calls during the pandemic.... Most of the time, they shipped a USB drive to the User, with the original OEM Install media... and separately shipped me a blank hard disk...

Clearly within any warranty boundaries is if you add another storage disk... Then whatever you add to that disk is 'free-range'... And they cannot dispute. Lenovo supports mSATA SSD Drives from their WWAN ports....NVMe and SSD, depending on the model of, which you didn't mention. What you add, is outside of their warranty, except if it is included as one of their upgrades, which I did get sent on Service Calls to install... If you do upgrade through them, while it is under warranty, then it falls within the warranty service contract for the warranty period of the new upgrade parts...

But i know that just before I left that job, they changed one tier of "Premier (Technical) Support "that crossed over support of both Hardware and OS"... I wasn't doing that much longer after that, so I don't know how that played out specifically... I received the training for that service tier policy change that had changed right before I left, about a month ago. What is usual before that, is that vendors would end me out, just for Hardware... and if it crossed over that it was software or OS related, they had to call in (or me as a Tech called into my tech portal) and a new service ticket was started, which mean they were referred to MS or other  phone support to lead "them" through those repairs/solutions on their own.

EDIT:
I do have to admit, that I showed up to one service call where the owner was on it's third Lenovo, where the owner had a problem with "something" that "he was doing", and Lenovo replaced his laptop twice, trying to ensure he was satisfied. I mean the first time they replaced the laptop with the same model (at no cost to him)/ The second time they upgraded him from a mid-range gamer to a top-of-the-line gamer (again at no cost to him), then (additionally) paid me to diagnose and upgrade it, to what worked out for him, with what he wanted to do (again at no cost to him). I don't know many vendors that would have done that. Literally.

---

### Post by Impavidus on 2022-01-07
Maybe Lenovo's customer service desk doesn't support Linux, but that doesn't mean you can't run Ubuntu on a Lenovo laptop. Usually it works very well. Lenovo is actually one of the better brands in terms of Linux compatibility. But it may void warranty. Companies claim all the time that things will void warranty, even when in some jurisdictions the law says that it doesn't void warranty.

Only once in my life I made a claim on warranty. Four weeks after I bought a new bicycle, the first time I rode it after sunset, it appeared the light was broken. The bicycle shop replaced the light for free. In my experience, warranty is mostly useful in the sense that it forces companies to provide goods that last at least as long as the warranty (which in Europe is legally at least 2 years on most goods).

---

### Post by MAFoElffen on 2022-01-07
Impavidus is very correct in what he said.

Ask Lenovo support what kinds of thins they "warranty" on an Operating System? I can tell you that they do not warranty MS Windows and they will only answer so many questions on it off their scripts before telling your\ to call Microsoft...

And if someone tells you that Lenovo dooes not support Linux, or Ubuntu... Show them these Lenovo Offerings that you can get pre-installed with Ubuntu:
[https://www.lenovo.com/us/en/d/linux-laptops-desktops/?orgRef=https%253A%252F%252Fwww.google.com%252F](https://www.lenovo.com/us/en/d/linux-laptops-desktops/?orgRef=https%253A%252F%252Fwww.google.com%252F)

I supported the top 3 brands for warranty service. Lenovo, Dell and HP. All 3 support Linux and had models that came pre-installed with Ubuntu. 

***
The person on the other end of the phone at their Tech Support, didn't actually say that they didn't support Linux, they said they didn't support "dual booting" right?

---

### Post by dattvidc on 2022-01-07
Thanks for all the Messages.
 I guess I just never thought Of it this Way. Dual booting seemed like a right, provided I don’t mess with proprietary software. 
But honestly, my daily driver has always been Ubuntu. I can’t use win. I tried but the crap ware keeps hassling me and I like the control and choice on Linux. 

I choose Lenovo because I wanted it to work well with Linux but no machine in my (very limited) price range shipped with Linux. In EU you have the right to return the OS for a refund and your product is then only the laptop. 
(Something about not making Microsoft a monopoly). You had the right to install other OS without loosing warranty. 

Anyway- safety net removed. 

Cheers guys (gender inclusive usage)

---

### Post by MAFoElffen on 2022-01-08
You never did mention "which" Model of Lenovo you have... LOL

---

